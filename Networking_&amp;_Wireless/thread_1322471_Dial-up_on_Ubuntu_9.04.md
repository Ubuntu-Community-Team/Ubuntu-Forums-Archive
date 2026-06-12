---
title: "Dial-up on Ubuntu 9.04?"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by jbeave on 2009-11-11
This is frustrating the hell out of me and I really need help. I've got everything set up except the internet and dial-up is my only means of doing so. I've downloaded Wvdial, it won't work. I've downloaded the gnome-ppp, it won't work either. But I have installed the modem correctly, supposedly. I just can't get the dialers to work. I've found several tutorials and I get stuck in the same place every time, it just won't install. And on top of all this not working right, I have to switch between 3 different harddrives (1 with WinXP, 1 with Ubuntu, and 1 external HDD) to even get files from 1 to another.
 
I want to make the switch from WinXP but this dial-up thing is killing me, why isn't it supported from the beginning anyway?? Please help, I don't know what information is needed to explain the situation better but I'll try to find out anything that is asked. 
 
Thanks again for any responses.

---

### Post by TopEnder on 2009-11-11
jbeave,  Suggest you install pppconfig it fairly straight forward to set-up once you get it working and get on the net you should be able to get Wvdial & gnome-pp working.  I only use pppconfig & gnome-ppp simple does what I want.  I watch your posts to see if you get it working.  TopEnder

---

### Post by jbeave on 2009-11-11
I've already tried pppconfig, it works I guess but how do I run the connection that I made?
 
And here's the error I got trying to install Wvdial with "sudo apt-get install wvdial":
 
"Package wvdial is not available, but is referred to by another package. May mean package is missing, has been obsoleted, or available from another source."
 
"Wvdial has no installation candidate."
 
So did I just get a crappy download of wvdial or what? Where can I get a good one?

---

### Post by jbeave on 2009-11-11
Just wanted to add that I've figured out my original problem, it seems I was an idiot and downloaded the .zip source packages of wvdial and gnome-ppp rather than the .deb packages...yes, I feel stupid.
 
Now after installing both of those, I still can't get it to work. When I use scanModem it picks up my modem, I've already downloaded the drivers for my modem, it knows it's there. All of my information (username, password, ISP number) is correct as well. I've edited in my info on the wvdial.config file too, and I noticed on my speakerphone that it DOES dial, it just hangs. 
 
So what's the deal? I'm just about out of options here, but I still want this to work...I'd love some help rather than this getting lost amongst the other topics. Please help, thanks.

---

### Post by TopEnder on 2009-11-12
jbeave,
Is your moden an external or internal modem if it is the latter then it is probable a Winmodem then I suggest you read the posts [http://ubuntuforums.org/showthread.php?t=1318926&highlight=win+modem](http://ubuntuforums.org/showthread.php?t=1318926&highlight=win+modem). TopEnder

---

### Post by jbeave on 2009-11-12
Yeah, I already did a search and read that topic. My modem is an internal one so I suppose my only option left is to go out and buy an external one...great. Thanks for the help, TopEnder. Too bad there aren't more people like you willing to help a guy out.
 
But I will give it one last try, I'll go and download the sl-modem-daemon and the slamr0 module or whatever and see how it works out. I'll post back if I get it working.

---

### Post by jbeave on 2009-11-12
I downloaded it and installed it, but when I ran it through the terminal it seems I was still missing some stuff. But I guess I'm going to give up on this modem.
 
I guess I shouldn't expect any answers but will any external modem work? Any advice?

---

### Post by TopEnder on 2009-11-14
jbeave,

I believe any 56K external modem should do, I have a a couple of Swann Smart modems I use on my two computers:
Swann Smart Pro Surfer 56k Data/Fax Modem
SwannSmart Turbo Model E210, I also picked up two very old external modems Hayes 56k & a no visible name 56K (H52PT-3020) modem from the local Recycle Centre both work with all version of Ubuntu I installed over the last 3 years.  I did not remove the internal modem (use it with Win XP) I just switch the external modem on when booting Ubuntu.  Happy modem hunting, TopEnder

---

### Post by hoss2001 on 2009-12-17
Did you say you connected using pppconfig and the pon command? I'm surfing the net right now connecting from a terminal with pon, then opening Firefox. I had to tinker with the settings at first before Firefox recognized the connection. Sorry, I don't remember exactly what it took.

---

### Post by jbeave on 2009-12-17
It tried to connect through pppconfig and the pon command, but it never went through. It's like it dialed over and over without getting anywhere. Anyway, since I posted this I've found a much easier solution to my problem. I jumped over to using Puppy Linux, and lo and behold, it recognized my modem and everything right off the bat. No problems whatsoever getting connected with dial-up. I can't believe I wasted DAYS messing with this when all I had to do was use a different OS. 
 
To anyone who reads this a few weeks or months down the road with the same problem, give Puppy Linux a try.

---

