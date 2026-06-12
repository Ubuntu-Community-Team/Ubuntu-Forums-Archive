---
title: "How Do I Solve These Sound Problems (Jackd Audio Server Specific Problem)"
date: 2009-12-24
forum: Multimedia Software
---

### Post by sophicsage on 2009-12-24
[SIZE=2][I]**I have downloaded Rosegarden, a music composition and editing tool.  I have had issues with my laptop as far as the internal mic not working, so maybe this is related.  When I open up Rosegarden it says this**:

[COLOR=Red]Failed to connect to JACK audio server.
Rosegarden could not connect to the JACK audio server. This probably means the JACK server is not running.
If you want to be able to play or record audio files or use plugins, you should exit Rosegarden and start the JACK server before running Rosegarden again.[/COLOR]

[COLOR=Black][B]When I close that field, there is another window behind that says:
[/B]
[COLOR=Red]System timer resolution is too low
Rosegarden was unable to find a high-resolution timing source for MIDI performance.
You may be able to solve this problem by loading the RTC timer kernel module. To do this, try running sudo modprobe snd-rtctimer in a terminal window and then restarting Rosegarden.
Alternatively, check whether your Linux distributor provides a multimedia-optimized kernel. See [http://rosegarden.wiki.sourceforge.net/Low+latency+kernels](http://rosegarden.wiki.sourceforge.net/Low+latency+kernels) for notes about this.

**[COLOR=Black]Then I close that window and Rosegarden actually opens, though it obviously won't operate.  Another window then pops up that says:[/COLOR]**

Helper programs not found
Rosegarden could not find one or more helper programs which it needs to provide some features. The following features will not be available:
Export and import of Rosegarden Project files
To fix this, you should install the following additional programs:
kdialog - for project file support

[COLOR=Black]**I am at a loss here.  I have no clue how to operate or enable Jackd controls or how to manipulate them.  Not only can I not use Rosegarden, but my internal mic is not working, so I wonder if they are related issues.  I am new to Ubuntu and so far things are going great other than the mic not working.  I'm still glad I totally switched from MS, but I definitely would like to resolve this problem if anyone can help me.  Thanks!**[/COLOR]
[/COLOR][/COLOR][/I][/SIZE]

---

### Post by sophicsage on 2009-12-24
[B]I located the Jack Control located (obviously) in the Sound area in applications.  Sorry...

I opened Jackd and started it and a popup came up saying it couldn't open.  Then it referred me to the notes which were:[/B]

 p, li { white-space: pre-wrap; }  [COLOR=Red]Could not connect to JACK server as client.[/COLOR]
 [COLOR=Red]- Overall operation failed.[/COLOR]
 [COLOR=Red]- Unable to connect to server.[/COLOR]
 [COLOR=Red]Please check the messages window for more info[/COLOR]

**[COLOR=Black]The message window had the following text:[/COLOR]**


  p, li { white-space: pre-wrap; }  [COLOR=#999999]18:43:54.442 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]18:43:54.487 Statistics reset.[/COLOR]
 [COLOR=#999999]18:43:54.532 Startup script...[/COLOR]
 [COLOR=#990099]18:43:54.533 artsshell -q terminate[/COLOR]
 [COLOR=#66CC99]18:43:54.540 ALSA connection graph change.[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]18:43:54.937 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]18:43:54.938 JACK is starting...[/COLOR]
 [COLOR=#990099]18:43:54.939 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 cannot use real-time scheduling (FIFO at priority 10) [for thread -1275975952, from thread -1275975952] (1: Operation not permitted)
 cannot create engine
 [COLOR=#999999]18:43:54.979 JACK was started with PID=8991.[/COLOR]
 [COLOR=#999999]18:43:55.015 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]18:43:55.015 Post-shutdown script...[/COLOR]
 [COLOR=#990099]18:43:55.016 killall jackd[/COLOR]
 [COLOR=#CCCC99]18:43:55.142 ALSA connection change.[/COLOR]
 jackd: no process found
 [COLOR=#999999]18:43:55.435 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]18:43:57.151 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

---

### Post by Oasu4g on 2009-12-31
Use Synaptic to install linux-rt and kdebase-bin. Once you've done that come back and let me know what other problems you're having.

---

### Post by Vojta01 on 2010-02-13
Hi, I am having completely the same problem as sophicsage. I tried to install linux-rt and kdebase-bin, but there is no change. Any other suggestions please?

---

### Post by Pablo_F on 2010-02-14
Hi,
> 
cannot use real-time scheduling (FIFO at priority 10) [for thread -1275975952, from thread -1275975952] (1: Operation not permitted)
cannot create engine

Problem #1. How to launch jack with the realtime option enabled (strongly recommended) even if you don't run a linux-rt kernel

Do in a terminal:

gksudo gedit /etc/security/limits.conf

Add the following lines at the end of this file:

#Needed to run jack with the real time option enabled, see [http://jackaudio.org/faq](http://jackaudio.org/faq)
@audio - rtprio 99
@audio - memlock unlimited

Save and close. Now do a:

sudo adduser username audio

(replace username with whatever your user login name is)

Restart the computer

Check with:

ulimit -l

that your memlock is ulimited
and

ulimit -r

that rtprio is 99

(memlock also can be set to a limited value in kB, but it has to be much higher than the default)

Internal mics not working, etc are ALSA related problems, nothing to do with jack or Rosegarden. Check these links: 

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

Cheers, Pablo

---

