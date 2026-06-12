---
title: "iCON 515M (orange) HSconnect problem"
date: 2010-09-28
forum: Networking &amp; Wireless
---

### Post by darkworld on 2010-09-28
Hi I have gone through all the threads I can find, problems connecting with iCON 515M (orange)mobile modem dongle. The threads are marked [SOLVED]


Im on 9.10... ive pretty much followed every bodies advice across various threads on this device. Pharscape, HSconnect etc.

Problem occurs at this point in debug window of HSconnect, when trying to connect. Ive followed Alexfish thread, maybe i missed something but i dont think so. Heres the debug window error line.

Sending ->AT_OSWLED=0<<AT_OSWLED=0>>
<<ERROR>>

Whats have i missed?

---

### Post by alexfish on 2010-09-28
hi
    
    can you have a look at this post #8


    
    [LEFT][http://ubuntuforums.org/showthread.php?t=1549077](http://ubuntuforums.org/showthread.php?t=1549077)

[/LEFT]
    [LEFT][/LEFT]
    [LEFT]see if if you can send pm to Orange Response or use the details in the post

[/LEFT]
    [LEFT][/LEFT]
    [LEFT]regards[/LEFT]
    [LEFT][/LEFT]
    [LEFT]alexfish[/LEFT]

---

### Post by darkworld on 2010-10-04
No luck...all orange seemed to do was resend settings to the icon515.

Im sure ive done something wrong here because other people have this running.  One thing I think maybe a problem, resolvconf holds the dns servers for my mobile phone...pretty sure the dongle doesnt use these. But cant find the IP's I need anywhere and orange are busy please hold!!! :-(

The initial message from HSOconnect is internet control not present or installed incorrect....when it sorts itself out on next attempt it says hso linkcontrol missing.

anybody help?...ive just installed 10.4 32bit and started again.

---

### Post by alexfish on 2010-10-04
hi

did you install the debian package

or the separate files listed (tar files)

the only reason is error "  hso linkcontrol missing" 

have a look at 

[http://ubuntuforums.org/showthread.php?t=1351612](http://ubuntuforums.org/showthread.php?t=1351612)

RE:Install hsolinkcontrol:

can't find info in debian package, or any listed dependences(at present)
possible something missing in the debian package but can't confirm

alexfish

---

### Post by darkworld on 2010-10-06
Hi

No I didn't install via Debian package and ive just had some strange results. First can you confirm I have installed in a directory correctly, one package isn't supposed to be installed inside the other is it? because ive installed them like this in a folder in my home directory, sorry im not hot on this.

> student@student-desktop:~/icon515$ ls
hsoconnect-1.2.19         udev-icon5x5-pharscape-091208
hsoconnect-1.2.19.tar.gz  udev-icon5x5-pharscape-091208.tar.gz

Second, I used the patch as well here

[http://www.pharscape.org/forum/index.php/topic,809.0.html]("http://www.pharscape.org/forum/index.php/topic,809.0.html")

I run a dual boot machine, when in windows I checked dns and found different dns to my orange phone. So I thought I would put them into resolv.conf to see what would happen. Nothing at first attempt, failed to connect. Second attempt I got failed to connect......but i noticed the light had changed from flashing to solid blue.

Opened browser and was informed I was offline. Then the odd thing happened, Ubuntu latest update notification came through on pc....so a port must of connected but couldnt find DNS? .....Confused!!!

thanks in advance.

---

### Post by alexfish on 2010-10-09
Hi

you could possibly try a PPP connection (script) but can't say if it will work

Details of how to make a script

  	 	 	 	 	 	   **[http://en.gentoo-wiki.com/wiki/Option_Icon_225](http://en.gentoo-wiki.com/wiki/Option_Icon_225)**
 the important thing about Option Icon is the call to the "    	 	 	 	 	AT_OWANCALL " this connects and disconnects the device then the data "OWANDATA"

alexfish

---

