---
title: "Cannot get JACK working"
date: 2009-10-16
forum: Multimedia Software
---

### Post by BobbyS on 2009-10-16
Hello,

I am running Ubuntu Juanty 9.04

I am trying to get jack working but with no luck. I have added in the limits.conf file

@audio - rtprio 99
@audio - nice -19
@audio - memlock unlimited


made a group called audio with me as a user.
setup a rt kernel

This is the message I get


17:37:24.876 Patchbay deactivated.
17:37:25.294 Statistics reset.
17:37:25.475 ALSA connection graph change.
17:37:26.180 ALSA connection change.
17:37:29.004 Startup script...
17:37:29.005 artsshell -q terminate
sh: artsshell: not found
17:37:29.426 Startup script terminated with exit status=32512.
17:37:29.427 JACK is starting...
17:37:29.428 /usr/bin/jackd -R -p128 -t5000 -dalsa -dhw:0 -r44100 -p64 -n2 -m
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot lock down memory for jackd (Cannot allocate memory)
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|64|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 64 frames (1.5 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: cannot set period size to 64 frames for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
17:37:30.575 JACK was started with PID=21304.
17:37:30.662 JACK was stopped successfully.
17:37:30.663 Post-shutdown script...
17:37:30.663 killall jackd
jackd: no process killed
17:37:31.121 Post-shutdown script terminated with exit status=256.
17:37:33.215 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
17:38:53.852 Startup script...
17:38:53.853 artsshell -q terminate
sh: artsshell: not found
17:38:54.257 Startup script terminated with exit status=32512.
17:38:54.258 JACK is starting...
17:38:54.258 /usr/bin/jackd -R -p128 -t5000 -dalsa -dhw:0 -r44100 -p16 -n2 -m
17:38:54.261 JACK was started with PID=21316.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot lock down memory for jackd (Cannot allocate memory)
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|16|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 16 frames (0.4 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: cannot set period size to 16 frames for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
17:38:54.453 JACK was stopped successfully.
17:38:54.455 Post-shutdown script...
17:38:54.456 killall jackd
jackd: no process killed
17:38:54.867 Post-shutdown script terminated with exit status=256.
17:38:56.477 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.



I have no clue why this is not working and any help would sure be appreciated.

Thanks
BobbyS      :guitar:

---

### Post by Papa_Smurf on 2009-10-23
the very first error message about artsshell not found means that you do not have audio permissions, and thus nothing will work right if at all. To give yourself permissions, go to System->Administration->Users and Groups. Select and Unlock your user name. In your Properties, in the User Privileges tab, check "Use audio devices". Save your changes and re-boot (I select the RT kernel from Grub). Now Jack runs for me.:popcorn:

---

