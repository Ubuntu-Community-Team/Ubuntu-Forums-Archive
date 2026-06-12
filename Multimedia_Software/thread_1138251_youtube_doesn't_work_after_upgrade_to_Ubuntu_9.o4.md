---
title: "youtube doesn't work after upgrade to Ubuntu 9.o4"
date: 2009-04-26
forum: Multimedia Software
---

### Post by zgembo on 2009-04-26
It says that I need to install adobe flash plugin. Before upgrading everything was fine. I tried to remove and reintall flush plugin-nonfree, but it didn't help. Can somebody help me and explain what to do from the scratch.

Edit: Maybe it's not the right place from this thread so please remove it where it belongs (maybe installation, upgrades).

---

### Post by vässlan on 2009-04-26
I think i downloaded the .deb for 8.04 from the adobe site, coz mine works fine i got 10.0.22.87

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

---

### Post by zgembo on 2009-04-26
Now I see videos don't work either.
No movie I can play now and everything was working before.
Maybe graphic card?
It's Intel 775i65G.

---

### Post by BugFixBug on 2009-04-26
there have been some related threads on the forums already. so you might find some answers in those.

have you tried installing the packages using the firefox build in feature which gave you the error? if so you might have multiple flash players that interfere with each other.

this might help you:
[http://bugfixbug.wordpress.com/2009/04/25/ubuntu-flash-does-not-work/]("http://bugfixbug.wordpress.com/2009/04/25/ubuntu-flash-does-not-work/")

---

### Post by zgembo on 2009-04-26
glxgears gives me this output:

186 frames in 5.0 seconds = 37.062 FPS
116 frames in 5.0 seconds = 23.072 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 743 requests (654 known processed) with 0 events remaining.

What is this X10, obviosly there is a problem with it.

---

### Post by zgembo on 2009-04-26
> **BugFixBug said:**
> there have been some related threads on the forums already. so you might find some answers in those.

have you tried installing the packages using the firefox build in feature which have you the error? if so you might have multiple flash players that interfere with each other.

this might help you:
[http://bugfixbug.wordpress.com/2009/04/25/ubuntu-flash-does-not-work/]("http://bugfixbug.wordpress.com/2009/04/25/ubuntu-flash-does-not-work/")


Thanks for quick replay, i am going to check it out.

---

### Post by zgembo on 2009-04-26
It didn't help, it removed swfdec-mozilla, flush plugin-ninfree was installed, but that's what I get when try to play youtube video:
Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player

---

### Post by BugFixBug on 2009-04-26
and your not getting a error message from firefox saying you dont have a flashplayer?

your not using the firefox plugin "no-script" are you?

---

### Post by zgembo on 2009-04-26
OK it works now, I enabled Shockwave Flush and the problem is fixed.
Thanks a lot.
By the way I don't now about plugin "no-script". Is that important?

---

### Post by 7th-time on 2009-07-28
Ha!
Just try to get youtube or google vids to work smoothly on a UBUNTU machine. I've been trying since release 6.06. With the sort of man (and woman) power working away at UBUNTU all these years, you'ld think they would be able to develop a slick and easy install for flash players, etc. that works. I mean, it is one of the most popular uses for P.C.'s right?
Still, good luck. With a scientific calculator, some mojo beads and befriending the neighborhood geek, you just may be seeing pictures move on your screen before the Zippy Zebra release.

---

### Post by billynair on 2009-10-14
I was all stoked because I was able to write up an"Idiots Guide" to get YouTube working with Ubuntu 8, and I went through after getting 9 installed and, GAH!! it doesnt work!?! WTF!!? yes, frustrating. I have my main computer as a Winows because... it just goes, and I have DVD editing software and other programs that I can not find acceptable replacements for on Linux. I use Ubuntu for my kids computer and all they do is flash games and YouTube, so when I cant get YouTube working, usually the Flash games dont work too, and then I have to fight them to get on my computer...

I know Adobe is all about making stuf free but not allowing anyone to distribute it, but I had an idea... what if someone went ahead and wrote some install script with al the extra DLLs (or what ever they use in Linux, not really worried what they are called right now) and then have the user go grab the TAR file and place it in the same folder, then run the script and BOOM!! n00bs from all corners of the earth could get YouTube working, and might be more tempted to keep using Ubuntu. ("But the geeks say 'HEY! That's half the fun!!' yeah... but I got a girlfriend and things to get done..." - Song: Every OS Sucks by 3 dead trolls in a Baggie)

Meanwhile, I am going into week 2 of trying to get YouTube to work with Ubuntu 9... (And 2nd Hard Disk!!)

---

### Post by billynair on 2009-10-14
w0w... I should wash me feet before sticking them in my mouth like that... after about a week and a half and breaking a hard drive (pushed in 2 of the IDE pins on accident) and trying all of the terminal commands I could find in Google, I ran across someone that tried the DEB file for Ubuntu 8.0+ as provided by Adobe (the bottom choice in the drop down list) and POOF!! YouTube ran like it was on XP!! No gray circle/triangle icon, no install other crap and type stuff into a terminal, nothing! it just worked...I remember in Ubuntu 8 needed you to grab the TAR.GZ and then uninstall something and install (or activate) another thing, then type a few commands in the terminal, so I was expecting a similar process this time too.

As said by that great cat and dog team of yesterdecade "HAPPY HAPPY JOY JOY!!"

---

