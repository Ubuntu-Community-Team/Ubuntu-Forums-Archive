---
title: "jackd crashes on startup"
date: 2013-10-08
forum: Multimedia Software
---

### Post by ozarkbunnyboy on 2013-10-08
I installed guitarix on my Xubuntu 12.04 and this is my first experience using jackd.  When I launch guitarix and it prompts me to start jackd, I get this error message:

[FONT=courier new]15:49:53.547 Patchbay deactivated.
15:49:53.560 Statistics reset.
15:49:53.899 ALSA connection change.
15:49:54.231 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
15:49:54.798 D-BUS: JACK server could not be started. Sorry
Tue Oct  8 15:49:54 2013: Starting jack server...
Tue Oct  8 15:49:54 2013: JACK server starting in non-realtime mode
Tue Oct  8 15:49:54 2013: control device hw:1
Tue Oct  8 15:49:54 2013: control device hw:0
Tue Oct  8 15:49:54 2013: [1m[31mERROR: Failed to acquire device name : Audio1 error : Cannot allocate memory[0m
Tue Oct  8 15:49:54 2013: [1m[31mERROR: Audio device hw:1,0 cannot be acquired...[0m
Tue Oct  8 15:49:54 2013: [1m[31mERROR: Cannot initialize driver[0m
Tue Oct  8 15:49:54 2013: [1m[31mERROR: JackServer::Open() failed with -1[0m
Tue Oct  8 15:49:54 2013: [1m[31mERROR: Failed to open server[0m
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
15:49:56.671 ALSA connection graph change.
Tue Oct  8 15:49:55 2013: Saving settings to "/home/oranmor/.config/jack/conf.xml" ...
15:50:02.061 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started[/FONT]

I have no clue, please advise.

---

