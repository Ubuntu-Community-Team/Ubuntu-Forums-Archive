---
title: "Upgraded to Karmic, can't connect to my home wifi, but connecting to hotel's."
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by CheshireMac on 2009-11-11
Hey folks. I've been having issues with my wireless anyway, but not like this. 
I upgraded (not fresh install) to Karmic from Jaunty. Everything was cool with a wired connection, but when I unplugged, I was unable to connect to my personal wireless. I'm able to connect to the hotel next door, but I don't know why. 
I'm using WICD and I'm going to switch back to the default manager in a moment, but I'm hoping this will get some good ideas rolling here just in case. 
In my previous experience, my wireless kept dropping on me, and my wife. Also, a Mac lappy was disconnecting too. I couldn't resolve the issue, so I upgraded, assuming that it was my Ubuntu that was causing the issues (Everything was fine until I brought it into the mix). Now, as I stated before, I can't connect to my home network. Everyone else can, and I can connect to another network. What's up with that?
Any thoughts would be appreciated. Thanks.

---

### Post by raygj on 2009-11-11
read this post
[http://ubuntuforums.org/showpost.php?p=8295253&postcount=6]("http://ubuntuforums.org/showpost.php?p=8295253&postcount=6")

---

### Post by CheshireMac on 2009-11-11
This would probably fix the situation, had the commands given in your link been functional on my netbook. I've had issues configuring my wireless with familiar commands in the past (manual power switching is non-functional, and wlan0 is a new designation to me and doesn't seem to work). It's probably a simple syntax error, but I'm at a loss for what to do here. I Googled the issue a bit, and I've found nothing about it, probably because 9.10 is so new.

---

### Post by raygj on 2009-11-12
> **CheshireMac said:**
> This would probably fix the situation, had the commands given in your link been functional on my netbook. I've had issues configuring my wireless with familiar commands in the past (manual power switching is non-functional, and wlan0 is a new designation to me and doesn't seem to work). It's probably a simple syntax error, but I'm at a loss for what to do here. I Googled the issue a bit, and I've found nothing about it, probably because 9.10 is so new.
in a terminal 
> sudo apt-get install iw
then retry setting wireless domain zone as previous post

---

### Post by mlebaron on 2009-11-12
I'm having the same problem.  So, in trying to get IW installed using "sudo apt-get install iw" I got an error stating something about "couldn't verify <some ubuntu related domain name here>".  So I can't even install iw, let alone follow the rest of the instructions.

---

### Post by raygj on 2009-11-12
> **mlebaron said:**
> I'm having the same problem.  So, in trying to get IW installed using "sudo apt-get install iw" I got an error stating something about "couldn't verify <some ubuntu related domain name here>".  So I can't even install iw, let alone follow the rest of the instructions.
if you are running 32bit (i386 to i686) kernel
 [http://archive.ubuntu.com/ubuntu/pool/universe/i/iw/iw_0.9.14-1_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/universe/i/iw/iw_0.9.14-1_i386.deb")
<http://archive.ubuntu.com/ubuntu/pool/universe/i/iw/iw_0.9.14-1_i386.deb>


if you are running 64bit (amd64) kernel
 [http://archive.ubuntu.com/ubuntu/pool/universe/i/iw/iw_0.9.14-1_amd64.deb]("http://archive.ubuntu.com/ubuntu/pool/universe/i/iw/iw_0.9.14-1_amd64.deb")
<http://archive.ubuntu.com/ubuntu/pool/universe/i/iw/iw_0.9.14-1_amd64.deb>

---

