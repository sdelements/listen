listen
======

Simple but powerful signal handling to process OS signals in python

##Example Usage:

    import listen
    import subprocess

### Instanciate Signal Handle
    sig_hand = listen.SignalHandler()

### Start external process
    external_process = subprocess.Popen(['sh', '-c', 'sleep 30'])

### Register some signal handlers to kill external process on SIGINT (ctrl-c)
    message_event = sig_hand.reg_on_status(print('Killing subprocess'))
    kill_event = sig_hand.reg_on_status(external_process.kill)

### Wait for external process
    external_process.wait()

### Now press ctrl-c to send SIGINT or unregister an the event
    sig_hand.del_status_event(kill_event)


For a more detailed example including interaction with bash please see
the tests/example.py and tests/external_process.bash
