---
title: "Jack Will Not Start"
date: 2011-04-04
forum: Multimedia Software
---

### Post by Dynamata on 2011-04-04
UBUNTU 10.10 Maverick Meerkat:

Message when Jack control panel is started:

04:26:49.393 Patchbay deactivated.
04:26:49.491 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
04:26:49.515 ALSA connection graph change.
04:26:49.780 ALSA connection change.

After starting-

Popup box: [Error - JACK Audio Connection. Could not start JACK. Sorry.]

Message:

04:38:57.283 Startup script...
04:38:57.283 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
04:38:57.684 Startup script terminated with exit status=32512.
04:38:57.684 JACK is starting...
04:38:57.684 /usr/local/sbin jackd -t2000 -dalsa -dhw:0 -r44100 -p256 -n2 -I6 -O6
04:38:57.686 Could not start JACK. Sorry.
04:39:20.216 JACK was stopped successfully.
04:39:20.216 Post-shutdown script...
04:39:20.216 killall jackd
jackd: no process found
04:39:20.624 Post-shutdown script terminated with exit status=256.

No other programs running.

ubuntu:~$ sudo cat /proc/asound/cards
[sudo] password for t: 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfcff8000 irq 45
 1 [s1000a         ]: USB-Audio - sE USB 1000a
                      SE Electronics sE USB 1000a at usb-0000:00:1d.2-2, full speed
 2 [Webcam         ]: USB-Audio - Monitor Webcam
                      OmniVision Technologies, Inc.538-2640-09.07.24.1 Monitor Webcam at usb-0000:00:
 3 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe5fc000 irq 16

Jack Setup:

[IMG]http://www.dynamata.com/images/jack_setup.jpeg[/IMG]

---

