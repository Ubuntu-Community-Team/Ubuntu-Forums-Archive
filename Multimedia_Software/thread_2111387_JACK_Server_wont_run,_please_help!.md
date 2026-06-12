---
title: "JACK Server wont run, please help!"
date: 2013-02-01
forum: Multimedia Software
---

### Post by saiman159 on 2013-02-01
I just installed Kubuntu b/c UbuntuStudio stopped working for me and I never got the chance use the recording software.  I've installed most of the same software and when i try to run any of them, like qjackctl, i get this in the message window:

JACK server starting in realtime mode with priority 10
control device hw:0
control device hw:0
audio_reservation_init
Failed to acquire device name : Audio0 error : Method "RequestRelease" with signature "i" on interface "org.freedesktop.ReserveDevice1" doesn't exist
Audio device hw:0 cannot be acquired...
Cannot initialize driver
JackServer::Open failed with -1
Failed to open server
18:52:54.244 JACK was stopped with exit status=255.
18:52:56.221 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started

---

### Post by MarceloZunino on 2013-06-16
Same situation here, ¿is there any solution, clue...?
thanks

---

### Post by MarceloZunino on 2013-06-16
kill -9 pulseaudio
qjackctl

woks for me

---

