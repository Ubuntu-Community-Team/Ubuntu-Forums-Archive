---
title: "Via vt1708s Azalia No sound when starting jack sound server."
date: 2011-06-07
forum: Multimedia Software
---

### Post by tt50 on 2011-06-07
Hi, i am very new to ubuntu, and have only just installed it for the very first time (ubuntu studio 11.04). After installing I was not able to get many of the audio programmes to work. After some reading, I realised that this was probably due to jack not starting.   
 
I was unable to get jack to start normally but have been able to get it started with the playback only option selected.  Programmes that use jack now work, however there is no sound once jack has been started.  The sound does work in   other programs when jack is not started. Strangely, I only have to open qjackctl for the sound to stop, and jack is not even started.  Initially I thought these problems were due to my sound card not being supported, but I believe that alsa support was added for the via 1708 codec at some point.  I found that support had been added in a document showing the changes between alsa versions;  however I cannot find the exact model listed as a supported sound card on the alsa site. 
 
I believe that altering jack settings could fix the problem, as i have been able to get audio to work in hydrogen by selecting plughw:0 but there is still no sound in other programs.  I have tried altering many other settings but to no avail, however I do not really understand the meaning of the settings that i am adjusting. 
 
Does anyone know what settings to adjust or know something else that might fix this problem so that sound works once jack has been started? 
 
Also, would programmes that use jack such as audacity, hydrogen, and ardour work with pulseaudio as the main sound server if I were to install normal ubuntu - it might be worth seeing if my soundcard works with the puleaudio sound server 
 
if this helps, here is the error message received when jack does not start when the normal duplex option is selected.

21:24:04.867 Patchbay deactivated.
21:24:04.868 Statistics reset.
21:24:04.886 ALSA connection change.
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
21:24:04.900 ALSA connection graph change.
21:24:06.469 JACK is starting...
21:24:06.470 /usr/bin/jackd -r -dalsa -dhw:0 -r44100 -p1024 -n2 -S
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
no message buffer overruns
21:24:06.517 JACK was started with PID=1552.
no message buffer overruns
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in non-realtime mode
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|16bit
control device hw:0
Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xfe8f4000 irq 16
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
21:24:13.534 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.
JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
Driver is not running
Cannot create new client
JackSocketClientChannel read fail
Cannot open qjackctl client
21:24:35.589 JACK is stopping...
jack main caught signal 15

_Here is the message with playback only when jack can be started_

21:26:35.540 Patchbay deactivated.
21:26:35.540 Statistics reset.
21:26:35.571 ALSA connection change.
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
21:26:35.580 ALSA connection graph change.
21:26:36.366 JACK is starting...
21:26:36.367 /usr/bin/jackd -r -dalsa -dhw:0 -r44100 -p1024 -n2 -S -P
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
21:26:36.402 JACK was started with PID=1576.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in non-realtime mode
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|-|1024|2|44100|0|0|nomon|swmeter|-|16bit
control device hw:0
Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xfe8f4000 irq 16
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
**** alsa_pcm: xrun of at least 0.040 msecs
**** alsa_pcm: xrun of at least 0.060 msecs
**** alsa_pcm: xrun of at least 0.071 msecs
**** alsa_pcm: xrun of at least 0.058 msecs
**** alsa_pcm: xrun of at least 0.061 msecs
**** alsa_pcm: xrun of at least 0.060 msecs
**** alsa_pcm: xrun of at least 0.060 msecs
**** alsa_pcm: xrun of at least 0.059 msecs
**** alsa_pcm: xrun of at least 0.045 msecs
**** alsa_pcm: xrun of at least 0.060 msecs
**** alsa_pcm: xrun of at least 0.055 msecs
**** alsa_pcm: xrun of at least 0.056 msecs
**** alsa_pcm: xrun of at least 0.054 msecs
**** alsa_pcm: xrun of at least 0.052 msecs
**** alsa_pcm: xrun of at least 0.060 msecs
**** alsa_pcm: xrun of at least 0.060 msecs
21:26:38.457 JACK connection change.
21:26:38.458 Server configuration saved to "/home/fox/.jackdrc".
21:26:38.458 Statistics reset.
21:26:38.511 Client activated.
21:26:38.517 XRUN callback (1).
21:26:38.518 JACK connection graph change.
**** alsa_pcm: xrun of at least 0.074 msecs
JackPosixMutex::Unlock res = 1
**** alsa_pcm: xrun of at least 0.063 msecs
JackPosixMutex::Unlock res = 1
**** alsa_pcm: xrun of at least 0.060 msecs
JackPosixMutex::Unlock res = 1
**** alsa_pcm: xrun of at least 0.052 msecs

_here is a list of my capture and playback devices_

fox@ubuntu:~$ arecord -l && aplay -l
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
fox@ubuntu:~$

and my alsa information is here
[http://www.alsa-project.org/db/?f=e7461ef8eb264da5cf3686abd95e43437980cf4f](http://www.alsa-project.org/db/?f=e7461ef8eb264da5cf3686abd95e43437980cf4f)
 
 
also, when i open alsamixer in the terminal for some reason the headphone part is greyed out, even when the sound is working before qjackctl is opened.  
 
Thanks

---

### Post by lidex on 2011-06-07
Scroll down to this section "Ubuntu Studio and Jack" on this page:
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by tt50 on 2011-06-08
Thanks for the reply
 
I've had a look at the link and done some more reading, in particular to the link below which was another link off the page that you showed me. [https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)
However after adjusting settings I still can't get the sound to work once jack has started.
 
I thought perhaps I needed to suspend pulseaudio when jack is being used as mentioned on jack faq; I suspect this is already configured for ubuntu studio though. I following the instructions by pasting "pasuspender --" before whats ever typed into the server path but after it says "could not start jack. sorry." so that didnt work.
 
I might try normal ubuntu and install audacity and hydrogen, if these can be used with pulseaudio as the sound server?

---

### Post by lidex on 2011-06-09
Try posting to the ubuntu studio forum:
[http://ubuntuforums.org/forumdisplay.php?f=335](http://ubuntuforums.org/forumdisplay.php?f=335)
The guys there are a lot more experienced with this particular software.

---

### Post by tt50 on 2011-06-09
Ok, i will try that.  Thanks

---

