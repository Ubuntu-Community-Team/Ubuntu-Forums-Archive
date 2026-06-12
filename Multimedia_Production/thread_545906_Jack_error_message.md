---
title: "Jack error message"
date: 2007-09-08
forum: Multimedia Production
---

### Post by staticvoid on 2007-09-08
Hi, I'm trying to configure Jack and set up a mini recording studio.
I have a sony vaio pcg-tr3a and I am taking these tutorials to do it:
[https://help.ubuntu.com/community/HowToSeq24Introduction](https://help.ubuntu.com/community/HowToSeq24Introduction)
[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

So could someone help me out? Thanks.

StaticVoid

---

### Post by staticvoid on 2007-09-08
I'm sorry, I forgot, Here is the error message I got:





12:06:31.835 Patchbay deactivated.
12:06:31.902 Statistics reset.
12:06:32.261 Startup script...
12:06:32.262 artsshell -q terminate
12:06:32.295 MIDI connection graph change.
12:06:34.037 Startup script terminated with exit status=256.
12:06:34.037 JACK is starting...
12:06:34.038 /usr/bin/jackd -p128 -t5000 -dalsa -dhw:0 -r44100 -p64 -n2
12:06:34.393 JACK was started with PID=10849 (0x2a61).
12:06:34.599 MIDI connection change.
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|64|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
12:06:35.613 JACK was stopped successfully.
12:06:35.614 Post-shutdown script...
12:06:35.615 killall jackd
jackd: no process killed
12:06:36.134 Post-shutdown script terminated with exit status=256.
12:06:36.759 Could not connect to JACK server as client. Please check the messages window for more info.


so: I gather that I cannot connect to the JACK control server... How do I set it up so it works?

---

### Post by nalmeth on 2007-09-08
>  the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
Make sure all your other audio applications are closed and try to start it again.

---

### Post by staticvoid on 2007-09-09
I did not have something else using it... I don't think I did. How do I "setup..." JACK for use with my US-122? I followed this tutorial: 
[https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)
and this one:
[http://www.davehayes.org/2007/04/27/howto-reaper-on-ubuntu-linux-with-wineasio/](http://www.davehayes.org/2007/04/27/howto-reaper-on-ubuntu-linux-with-wineasio/)
and for some reason I just cannot get it working right.
I am using wineasio.dll in wine. To run REAPER. I also have hydrogen, seq24, VKeyBd, etc.

I really want to get a DAW setup :( Jack is only one of the difficulties for me.

staticvoid

p.s. [ftp://chuck.ucs.indiana.edu/pub/array2/linux/opensuse/distribution/SL-10.0-OSS/inst-source/suse/noarch/alsa-firmware-1.0.9-4.noarch.rpm](ftp://chuck.ucs.indiana.edu/pub/array2/linux/opensuse/distribution/SL-10.0-OSS/inst-source/suse/noarch/alsa-firmware-1.0.9-4.noarch.rpm)
do you know where I can find this package? I will use alien to convert it to a deb file.

---

### Post by nalmeth on 2007-09-10
Does your USB audio device work correctly in Ubuntu?

If that is the only error message you are getting, then it is what it says. Something is tying up ALSA, and preventing Jack from starting. If you even have a music player open (or engine running) it can stop Jack from starting.

Sometimes esd (gnome's sound daemon) hangs up the device in the background, so try killing it:
```
killall esd
```
and then try to start Jack

If that doesn't work, I think this command should restart ALSA:
```
sudo /etc/init.d/alsa-utils restart
```

If you want to use Jack a lot, I would recommend you install the realtime kernel for Ubuntu. Instructions can be found in the stickied thread in this section (Multimedia Production).

Sorry, I don't know where that firmware package can be found.

---

### Post by staticvoid on 2007-09-10
Hi nalmeth,
I tried those peices of code in the terminal and still, nothing. It says it cannot connect to ALSA server still, so I do not know what : /. I want ASIO though, right? or does ALSA get transformed by WINE to ASIO for my windows recording software, reaper? Should I just try Ardour or what? anyway, thank. I will deffinatly check out that sticky!

sv

---

