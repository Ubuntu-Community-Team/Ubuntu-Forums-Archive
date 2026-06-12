---
title: "Web video slow and extremely choppy!"
date: 2011-02-01
forum: Multimedia Software
---

### Post by avocadorange on 2011-02-01
Streamed videos on various Web sites are **slow** and **choppy** for me. The problem seems to be a cross-browser issue, today I did an informal test of various sites I frequently use on both [COLOR="SeaGreen"]Mozilla Firefox[/COLOR] and [COLOR="Red"]Chrome[/COLOR]. 

The results of my informal test are below, and as you can see they are [COLOR="Blue"]*mostly*[/COLOR] the same for both Firefox and Chrome.

[FONT="Impact"]Google Chrome-[/FONT]
You tube-- no problems once video loads, but loading is slow
Daily show-- very slow loading, sound ok, video extremely slow, choppy, unwatchable
ESPN--slow to load, sound ok, picture is very slow, choppy
eHOW--slow to load, sound ok, picture is very slow, choppy

[FONT="Impact"]Mozilla Firefox[/FONT]
You tube-- no problems but sometimes slow loading
Daily show-- a little slow loading but sound and picture ok
ESPN--sound ok but picture very choppy
eHOW--slow to load, sound ok, picture is very slow, choppy[FONT="Arial Narrow"][/FONT]

Please respond with any suggestions for trouble shooting! I've looked at various Websites and the Network Tools in the System Administration but I'm pretty lost. Other data:

Ubuntu 10.04 
Toshiba Satellite A100 
432.8 MiB memory; 
Intel Celeron (R)M: 1.40 GHz.

---

### Post by avocadorange on 2011-02-02
Anyone...?

---

### Post by kindbudz on 2011-02-20
Same problem here.  AVIs stored on the hard drive play fine, but youtube and other streaming video is very choppy in Firefox and Chrome. 

System monitor shows that playing hi-def AVIs uses less CPU than playing a youtube video, which taxes the CPU at a constant 100 percent.  Full-screen streaming is worse yet. 

I tried FlashVideoReplacer in Firefox, but that worked much worse than just using the flash player. the FVR script would stall really long before opening the player, then both video and especially audio were choppy.

10.04
Kernel 2.6.32-28-generic
Memory 495 mb
Intel Pentium 4 CPU 2.4 ghz
Intel 82845G[Brookdale-g]/GE/PE DRAM controller graphics card

Also, there seems to be a problem with the graphics driver.  All resolution options work fine, but the Ant and GLSlideShow screensavers cause the system to crash. GLXGears works just fine tho.

---

### Post by avocadorange on 2011-02-24
Thanks for that post, kindbudz. Hopefully someone will see this and help out with some suggestions.

---

### Post by avocadorange on 2011-03-21
Update to this situation: thanks to the helpful advice of Varun on another thread, I tried to install [COLOR="Blue"]flashplugin-nonfree[/COLOR] while uninstalling all other flash plugins.

This made some difference but unfortunately the basic problem remains. So now I will provide more background info and ask further questions in case anyone out there can help with this:

**1) **Before installing '[COLOR="Blue"]flashplugin-nonfree[/COLOR]' I had been trying '[COLOR="Green"]adobe-flashplugin[/COLOR]' and 'ubuntu-restricted-extras' per the recommendation of qjmoss:
[http://ubuntuforums.org/showthread.php?t=1165338](http://ubuntuforums.org/showthread.php?t=1165338)

**what is the difference** between [COLOR="Green"]adobe-flashplugin[/COLOR] and [COLOR="Blue"]flashplugin-nonfree[/COLOR]?

2) The performance problems persist, so I am now posting some further info here in the hopes **[COLOR="Blue"]*someone*[/COLOR]** can help. 

I did a lot of digging and found the following information:

my system is as follows: [COLOR="Purple"]
Ubuntu 10.04
Kernel Linux 2.6.32-30-generic
GNOME 2.30.2

memory 432.8 MiB
Processor: Intel (R) Celeron (R) 1.40GHz
Avail disk space: 126.8 GiB

video card is: VGA compatible controller [0300]: ATI Technologies Inc RC410 [Radeon Xpress 200M] [1002:5a62][/COLOR]

(If I can provide any other info let me know.)

I also looked up system requirements for Adobe Flash Player 10.2
and found the following for linux:

Intel Pentium 4 2.33GHz, AMD Athlon 64 2800+ or faster processor (or equivalent)
512MB of RAM
graphic memory: 128MB of graphics memory (but I have no idea how to figure what my computer's graphic memory capacity is)
[http://www.adobe.com/products/flashplayer/systemreqs/](http://www.adobe.com/products/flashplayer/systemreqs/)

My **_amateur conclusion_**: [COLOR="Green"]adobe flash plugin [/COLOR]maxes out my CPU and uses up a great portion of memory when playing videos in browsers. The system monitor shows that usally I'm using 75% of memory and approaching 100% of CPU. Now that I'm using the "[COLOR="Blue"]flashplugin-nonfree[/COLOR]" I get more or less the same results as with [COLOR="SeaGreen"]adobe flash plugin[/COLOR].

So the questions continue:

4) The system requirements for adobe flash may have increased sometime after I originally installed ubuntu 10.04 in August 2010. Does anyone know what the requirements were for previous versions?


5) Given my system limitations, is there an older version of flash player or a non-adobe equivalent such as gnash I should try? 

6) Should I install an older version of Ubuntu?

7) Any other ideas? _**[COLOR="DarkRed"]Anyone?[/COLOR]**_

Most importantly thanks to anyone who has time to look through all this and reply with *[COLOR="Purple"]**any**[/COLOR]* potential solutions.

---

### Post by lukejohnson on 2013-04-04
I am also experiencing very similar problems. It is not just youtube but many website.

---

### Post by QIII on 2013-04-04
This is an old thread.

From the Ubuntu Forums Code of Conduct [http://ubuntuforums.org/misc.php?do=showrules:](http://ubuntuforums.org/misc.php?do=showrules:)


> If a post is older than a year or so and hasn't had a new reply in that  time, instead of replying to it, create a new thread. In the software  world, a lot can change in a very short time, and doing things this way  makes it more likely that you will find the best information. You may  link to the original discussion in the new thread if you think it may be  helpful.

Regards,

QIII

*Thread **Closed.***

---

