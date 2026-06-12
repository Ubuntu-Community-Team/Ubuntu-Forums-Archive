---
title: "Got firefox 3.6 from channel today and flash doesn't work"
date: 2010-01-25
forum: Multimedia Software
---

### Post by phorgan1 on 2010-01-25
I got firefox 3.6 from the channel today and all flash video from YouTube won't work.  I have plug-ins for 10.0 r42 and 9.0 r999 installed.  I get a black rectangle and no video, no errors, no warnings.  If I disable the 9.0 r999 I get no black rectangle and no video.

Linux dell 2.6.31-18-generic #55-Ubuntu SMP Fri Jan 8 14:55:26 UTC 2010 i686 GNU/Linux

Firefox 3.6.1pre

Shockwave Flash

    File: libflashplayer.so
    Version: 
    Shockwave Flash 10.0 r42

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

Shockwave Flash

    File: libswfdecmozilla.so
    Version: 
    Shockwave Flash 9.0 r999

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Adobe Flash movie 	swf 	Yes
application/futuresplash 	FutureSplash movie 	spl 	Yes

---

### Post by lovinglinux on 2010-01-25
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by Rhemat on 2010-01-26
Try starting FireFox in Terminal.  In fact, try starting any program in terminal, and copy and paste the output from Terminal.  I'm betting you'll see this:

ALSA lib pulse.c:229pulse_connect) PulseAudio: Unable to connect: Timeout

I've found that PulseAudio has been crashing anything that uses sound.  PRBoom, RhythmBox, FlashVideos.
I'm still trying to fix it myself.
I started my own thread, and found plenty of other threads about programs crashing that involve sound.  Maybe there should be a PulseAudio bug thread, if there isn't one already.

---

### Post by selectstar on 2010-01-27
Hi am having exactly the same problem on ubuntu 9.10 amd64
I have tried the suggestion of lovinglinux but nothing changed really.
The browser is still detected as without the plugin, nothing is played. I am being prompted with a message "install flash plugin..." if I selecte Adobe Flash Player (install) it tell's me that the package is already installed. 
I have remove the package and reinstalled it several times. No hope

---

### Post by lovinglinux on 2010-01-29
> **selectstar said:**
> Hi am having exactly the same problem on ubuntu 9.10 amd64
I have tried the suggestion of lovinglinux but nothing changed really.
The browser is still detected as without the plugin, nothing is played. I am being prompted with a message "install flash plugin..." if I selecte Adobe Flash Player (install) it tell's me that the package is already installed. 
I have remove the package and reinstalled it several times. No hope

For 64bit remove flashplugin-nonfree and follow the tutorial at [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

---

### Post by selectstar on 2010-02-01
> **lovinglinux said:**
> For 64bit remove flashplugin-nonfree and follow the tutorial at [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)


No guys, please don't start saying "please do a search first" or "try this topic" etc... I have already tried most of the recent topics. 

Thank you anyway lovinglinux, I spent some time following again the instructions in that topic. And again no success at all. I tried also following instructions on fully removing all flash plugins and then following that tutorial again... and again no luck. The browser keeps prompting for the flash plugin to be installed.

---

