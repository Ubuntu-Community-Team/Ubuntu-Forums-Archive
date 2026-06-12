---
title: "Flash video streaming sets up high-fan speed in Dell Latitude E5430"
date: 2018-04-03
forum: Multimedia Software
---

### Post by moto1860 on 2018-04-03
As title says video streaming from this specific website: [http://videostream.dn.ua/videopage/videoPage.php?g=MzAxNDk%26%238470%3Bf&c=it&i=eWlxYmFocWN1YQ%26%238470%3Bf%26%238470%3Bf]("http://videostream.dn.ua/videopage/videoPage.php?g=MzAxNDk%26%238470%3Bf&c=it&i=eWlxYmFocWN1YQ%26%238470%3Bf%26%238470%3Bf")
Triggers high-fan speed immediately, like within 2-3 seconds. As soon as I shut it down normal speed is restored,
I'm using Chromium Version 65.0.3325.181 (Official Build) Built on Ubuntu , running on Ubuntu 17.10 (64-bit)

I've no issue with youtube videos and other websites streaming services that use adobe flash, I've tried opening that video streaming in firefox but it says I need to update adobe flash, when flash windows pops up I choose APT for Debian/Ubuntu  and select Download, I get another windows with APTurl or Choose another application, I select APTurl and open link at which point I get this: 

[https://image.ibb.co/e0gBXH/Screenshot_from_2018_04_03_20_15_21.png](https://image.ibb.co/e0gBXH/Screenshot_from_2018_04_03_20_15_21.png)

---

### Post by TheFu on 2018-04-03
Youtube switched to non-Flash for videos long ago. I suspect it is only flash that causes the CPU to work harder, thus forcing the fan to turn up.

You can watch which processes are using the CPU with "top".  That would be my best guess.

---

### Post by moto1860 on 2018-04-04
Forgot that youtube had switched. Although I'm positive about other websites using flash videos streaming giving me no problem*. I've just run htop and indeed that video streaming mentioned in op sets up two processes that take each 100% of cpu to a total of over 200% usage. 

*I took a SS  during use of one of these websites and there's PepperFlash running only taking 10% of cpu: [https://ibb.co/ds6PMc](https://ibb.co/ds6PMc)

---

### Post by TheFu on 2018-04-04
Not all flash videos are the same.  Flash has been a CPU hog for a long time. It is fairly recent that Adobe did something to make it better on Linux by allowing some GPU support.
[https://wiki.archlinux.org/index.php/Flash#Configuration](https://wiki.archlinux.org/index.php/Flash#Configuration)

There are different sorts of video codecs used inside each "container"; flash is just a container. Depending on how the video was encoded, your GPU might be used for some vcodec and the CPU might be used for others.  Most vcodecs have multiple compliance levels, so if the level supported by the GPU isn't used, then a SW vcodec is needed. That will force the CPU to be utilized.
 
When the CPU is at lower use, is the fan usually quieter?  
Reference: [https://help.adobe.com/en_US/as3/dev/WS5b3ccc516d4fbf351e63e3d118a9b90204-7d46.html](https://help.adobe.com/en_US/as3/dev/WS5b3ccc516d4fbf351e63e3d118a9b90204-7d46.html)

It is also possible that video link is running a crypto-miner on your system.  I didn't click it.  .UA is not somewhere I'm willing to visit. I did try to play it using a non-browser player. It failed.

Don't know if any of this is helpful or not.

---

### Post by moto1860 on 2018-04-04
How do I access all the options listed in that [example mms.cfg]("http://sources.gentoo.org/cgi-bin/viewvc.cgi/gentoo-x86/www-plugins/adobe-flash/files/mms.cfg") file? I've run [FONT=monospace]/etc/adobe/mms.cfg in the terminal:


[/FONT]```
avo@avo-Latitude-E5430-non-vPro:~$ /etc/adobe/mms.cfgbash: /etc/adobe/mms.cfg: No such file or directory



```[FONT=monospace]

Yes, fan is quiter at normal cpu usage. 
[/FONT]
[FONT=arial][SIZE=2]Wouldn't running a [COLOR=#000000]crypto-mine on my system have had an impact on cpu usage when I was using it with Windows 10 too?[/COLOR][/SIZE][/FONT]

---

### Post by TheFu on 2018-04-04
config files aren't "run", they are edited. If the file doesn't exist,then you have to create it. Be careful to follow the ownership, group and permissions for similar files in the same directory area.  System security can be compromised if you make a mistake.

---

### Post by monkeybrain20122 on 2018-04-04
I would just stay away from dubious sites running flash

---

