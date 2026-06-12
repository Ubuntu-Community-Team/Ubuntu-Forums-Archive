---
title: "i still can't figure out how to use jack"
date: 2007-09-18
forum: Multimedia Production
---

### Post by valpobro on 2007-09-18
ok so i think i mite need to get driver for the fire wire on my comp? but i have no idea. but this is what is going on........

ok i just installed ubuntu studio 7.04 i have a presonus fire pod that i have no idea how to get it to work if anyone cane give me a step by step how to that would be great. and when i try to run ardour i get this, Ardour could not connect to JACK. There are several possible reasons:

1) JACK is not running.
2) JACK is running as another user, perhaps root.
3) There is already another client called "ardour".

Please consider the possibilities, and perhaps (re)start JACK.

i don't know if that is from my fire pod deal or what

thank you

daniel
__________________



First, welcome to ubuntu! I hope you find it as enjoyable as I have. I just recently got a Focusrite Saffire firewire soundcard went through the setup process. Although they are not the same cards, the setup is very similar.
The driver you'll need is the freebob (aka fado) driver, here's a link to the site with very detailed information [http://freebob.sourceforge.net/index.php/Main_Page](http://freebob.sourceforge.net/index.php/Main_Page). You'll also need the JACK audio connection kit software to run Ardour (probably already installed if you have ardour installed but it never hurts to apt-get it anyways. How you install these is by opening a terminal and typing
Code:

sudo apt-get install libfreebob0 qjackctl

Once those are installed then open qjackctl, click settings, and in the "Driver" drop down menu select freebob. This area of qjackctl is where you should look if you're having dropouts/high latency issues etc.. take a second to look at the various settings available (don't worry if you don't understand them all just yet). Click "OK" and then click "Start" in the main window of qjackctl. As long as that is up and running fine then you can start ardour and record/edit away.

if you have any troubles let us know.

-Eric
__________________

	  	
Join Date: Jul 2007
Beans: 9
Re: need help with presonus fire pod
ok well were do i find qjackctl? there are a bunch of diferent jack apps but no qjackctl
__________________

  

ok well i figured all that out but when i try to start it i just get this
Attached Thumbnails

---

### Post by stmiller on 2007-09-18
Install the low-latency kernel:
```

sudo apt-get install linux-lowlatency

```
and reboot.

In qjackctl, check:

force 16bit
soft mode
uncheck realtime
frames/period: 64
and some (most) onboard sound cards are fixed at 48000. Try setting the sample rate to 48000 if needed.

---

### Post by valpobro on 2007-09-18
ok well how do you check force 16 bit?

---

### Post by stmiller on 2007-09-19
Hey try this in the terminal and paste the entire output back here:

```
jackd -d alsa
```

---

### Post by valpobro on 2007-09-19
here you go work your magic 

thank you

---

### Post by valpobro on 2007-09-19
maybe this is easier to read

jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback

---

### Post by Stochastic on 2007-09-19
> **stmiller said:**
> Install the low-latency kernel:
```

sudo apt-get install linux-lowlatency

```
and reboot.

In qjackctl, check:

force 16bit
soft mode
uncheck realtime
frames/period: 64
and some (most) onboard sound cards are fixed at 48000. Try setting the sample rate to 48000 if needed.

well the Presonus firewire card that you're trying to use has up to 24bit 96khz sample rates, so 48000 is probably not the best sample rate. 
44100 or 96000 would be a better choice to try at first.

It appears you're having probems getting qjackctl to start the jack server.
> jack -d alsa
is the way to start jack with your alsa device (the onboard soundcard) but whad you should try is ```
jack -d freebob
``` to get jack to start with your freebob firewire driver.  Please post what it says when you do that.  This is the only way to support your soundcard on linux, there may be hacks to get alsa to work with freebob but I don't know of any.  That link I gave you to the freebob website will explain how to troubleshoot your freebob/fado install if that is where your troubles lie.

Furthermore, the settings you're using probably need a little tweaking:

- Priority - I wouldn't set this value to 70 until you've looked into what that means, I'm pretty sure that you need to tweak other settings to make jack run at priority 70.  I'd choose 0.

- Frames/Periods - I'd start with a value like 1024 (this will give larger latency times) and if that works then try 512, and so on down the line until you've found a setting that gives low latency times and very few if any xruns.

- Sample Rate - 44100 or 96000 are good

- Periods/Buffers - I read somewhere that 3 is usually a better/faster number to use but 2 should work fine.


Try it with realtime both checked and unchecked - depends on kernels I think.  I'm running UbuntuStudio so it may be a different kernel.  When I was on regular Ubuntu feisty I didn't have a freebob device, but there was an ubuntustudio-audio package in the repos that has kernels if I'm not mistaken.  If you've got a Firepod then I'm assuming you're into music or audio enough that it wouldn't be a silly idea to try installing UbuntuStudio.

Also, I would have gotten back to you in that last post.  It's considered bad etiquette to bump threads up by reposting so early.

---

### Post by Stochastic on 2007-09-19
Oh also, i just recalled that in order to get freebob to be allowed total control over the firewire port  -**** This only applies IF when you run jackd -d freebob an error about raw1394 permissions comes up ****-  you need to: ```
 sudo gedit /etc/udev/rules.d/40-permissions.rules
```
Find the line that says KERNEL=="raw1394" and change the GROUP="disk" to GROUP="audio" and save the file.  Reboot the computer (really you only need to refresh a couple services, but just to be sure, reboot) and try again.

---

### Post by stmiller on 2007-09-19
Ah, sorry didn't notice you had a firewire device. :) Your first post on this thread was confusing.

---

### Post by swedishfrog on 2008-03-03
I posted my method for getting the Firepod working on Ubuntu here:
[http://ubuntuforums.org/showthread.php?t=713695]("http://ubuntuforums.org/showthread.php?t=713695")

---

### Post by djkilin on 2008-06-03
hi everyone I'm kinda of a linux noobe but like the thread says I still can't figure out how to get jack to work with my focusrite saffire I keep getting this error message 


15:48:00.945 /usr/bin/jackd -dfreebob -r44100 -p1024 -n3 -D
15:48:00.951 JACK was started with PID=6185.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
Freebob using Firewire port 0, node -1
Ieee1394Service::initialize: Could not get 1394 handle: Permission denied
Is ieee1394 and raw1394 driver loaded?
[31mFatal (devicemanager.cpp)[68] initialize: Could not initialize Ieee1349Service object
[0m[31mFatal (freebob.cpp)[69] freebob_new_handle: Could not initialize device manager
LibFreeBoB ERR: cannot create libfreebob handle
FreeBoB ERR: FREEBOB: Error creating virtual device
[0mcannot load driver module freebob
15:48:01.644 JACK was stopped successfully.
15:48:01.644 Post-shutdown script...
15:48:01.645 killall jackd
15:48:01.648 JACK has crashed.
jackd: no process killed
15:48:02.051 Post-shutdown script terminated with exit status=256.
15:48:03.464 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.


please help

oh p.s running it through an adaptec AUA-1422 pcmcia card cause I only have a 4 pin firewire jack on my laptop would getting a 4-6 pin adapter make a difference 
once again thanks

---

