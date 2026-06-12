---
title: "Extigy and Qjack..."
date: 2010-05-01
forum: Multimedia Software
---

### Post by samos255 on 2010-05-01
Hello,i want to play via Rakarrack on Guitar with my Extigy,but i have a  problem in qjack...

So this is Qjack log - 
22:09:11.211 Startup  script...
22:09:11.212 artsshell -q terminate
sh: artsshell: not  found
22:09:11.614 Startup script terminated with exit status=32512.
22:09:11.614  JACK is starting...
22:09:11.615 /usr/bin/jackd -m -dalsa -r48000  -p256 -n3 -D -Chw:1,0 -Phw:1,0 -Xseq
22:09:11.637 JACK was started  with PID=8561.
jackd 0.118.0
Copyright 2001-2009 Paul Davis,  Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with  ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to  redistribute it
under certain conditions; see the file COPYING for  details
Memory locking is unlimited - this is dangerous. You should  probably alter the line:
     @audio   -  memlock    unlimited
in  your /etc/limits.conf to read:
     @audio   -  memlock    1545369
no  message buffer overruns
JACK compiled with System V SHM support.
loading  driver ..
apparent rate = 48000
creating alsa driver ...  hw:1,0|hw:1,0|256|3|48000|0|0|nomon|swmeter|-|32bit
control device  hw:1
configuring for 48000Hz, period = 256 frames (5.3 ms), buffer = 3  periods
ALSA: final selected sample format for capture: 16bit  little-endian
ALSA: use 3 periods for capture
ALSA: final selected  sample format for playback: 16bit little-endian
ALSA: use 3 periods  for playback
22:09:11.763 ALSA connection graph change.
22:09:11.790  ALSA connection graph change.
ALSA: could not start playback (Broken  pipe)
DRIVER NT: could not start driver
cannot start driver
22:09:12.074  JACK was stopped successfully.
22:09:12.075 Post-shutdown script...
22:09:12.076  killall jackd
jackd: no process found
22:09:12.487 Post-shutdown  script terminated with exit status=256.
22:09:13.798 Could not  connect to JACK server as client. - Overall operation failed. - Unable  to connect to server. Please check the messages window for more info

I  was looking whole day for solutions,but nothing worked  [IMG]http://linuxmusicians.com/images/smilies/icon_rolleyes.gif[/IMG]

---

