---
title: "Jack Audio Connection kit not starting"
date: 2015-07-23
forum: Multimedia Software
---

### Post by andrewandrew on 2015-07-23
I am completely new to Jack and have only installed it as I wanted to have a play with the muse sequencer.

I have followed a you tube tutorial - but I get the following error....



23:50:45.607 D-BUS: JACK server could not be started. Sorry
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Thu Jul 23 23:50:45 2015: Starting jack server...
Thu Jul 23 23:50:45 2015: JACK server starting in realtime mode with priority 10
Thu Jul 23 23:50:45 2015: ERROR: Cannot lock down 82274202 byte memory area (Cannot allocate memory)
Thu Jul 23 23:50:45 2015: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio0": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
Thu Jul 23 23:50:45 2015: ERROR: Failed to acquire device name : Audio0 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
Thu Jul 23 23:50:45 2015: ERROR: Audio device hw:HDMI cannot be acquired...
Thu Jul 23 23:50:45 2015: ERROR: Cannot initialize driver
Thu Jul 23 23:50:45 2015: ERROR: JackServer::Open failed with -1
Thu Jul 23 23:50:45 2015: ERROR: Failed to open server
Thu Jul 23 23:50:47 2015: Saving settings to "/home/astillie/.config/jack/conf.xml" ...
23:51:02.044 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started

---

### Post by mikul2 on 2015-07-26
I have the exact same problem.

---

### Post by Modanung on 2016-02-29
I find Rakarrack to be a good kick starter for JACK. After starting Rakarrack, hit the start button in JACK and then you can safely close Rakarrack, or use it of course.
The same works with Ardour, but requires a project to be opened. I am running Xubuntu btw, but it seems like the same problem.

---

