---
title: "Problems with broadcom BCM4312 wireless in ubuntu 10.04"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by AndrewD257 on 2011-03-22
I have just installed 10.04 on a dell inspiron laptop, but the wireless adapter will not work.
I uses a broadcom BCM4312.   When I click on the wireless icon, it says "firmware missing".  Normally, I would connect to look for proprietary drivers, but my problem is that I live in an apartment complex with only wifi.  

So my question is,  
A) does this sound like a driver problem, and
B) if so, how can I get the necessary driver installed (after downloading it with another laptop)

when I use lshw, it does show the wireless device, by says that it is disabled.

I tried following the directions here < [http://ubuntuforums.org/showthread.php?p=5636495](http://ubuntuforums.org/showthread.php?p=5636495) >
(changing "ieee80211_crypt_tkip" with "lib80211_crypt_tkip" due to the rename in 2.6.29. I think that is correct), but that did not work either.  

I am using 10.04 2.6.35-22-generic

I am pretty new to all this, so please, dumb it down for me.
 Any suggestions would be much appreciated.  Thanks.

---

### Post by Filkins on 2011-03-22
> **AndrewD257 said:**
> I have just installed 10.04 on a dell inspiron laptop, but the wireless adapter will not work.
I uses a broadcom BCM4312.   When I click on the wireless icon, it says "firmware missing".  Normally, I would connect to look for proprietary drivers, but my problem is that I live in an apartment complex with only wifi.  

So my question is,  
A) does this sound like a driver problem, and
B) if so, how can I get the necessary driver installed (after downloading with another laptop)

when I use lshw, it does does the wireless device, by says that it is disabled.

I tried following the directions here <http://ubuntuforums.org/showthread.php?p=5636495>
(changing ieee80211_crypt_tkip with lib80211_crypt_tkip due to the rename in 2.6.29), but that did not work either.  

I am using 10.04 2.6.35-22-generic

I am pretty new to all this, so please, dumb it down for me.  Any suggestions would be much appreciated.  Thanks.

Just a little fair warning, I've been using ubuntu and a few other distros of linux for around a year or so, and was initially quite impressed with ubuntu 10.04 (my first go at linux). Later I discovered that I had lucked out BIG-time due to the high compatibility with the computer I was installing it on. Everything hardware related worked flawlessly "out of the box".
Naturally, I recommended ubuntu to many friends who were coming to me with windows virus problems and of course just plain windows problems, thinking I'd solve that for them once and for all.
And then, WHAP! they took my word for it, and being the guy who got them in this mess in the first place, I was suddenly confronted with an endless list of hardware quirks and driver incompatibility issues. i.e. a wireless card (broadcom BCM4312) that I managed to get functioning on a dell after hours of $&%@ing with drivers that ultimatly failed to work after a few weeks of service (everything from reinstalling drivers to reinstalling the whole damn OS failed to fix this problem for more than a month or so at a time). Anything usb related, video problems, sound cards, you name it, didn't work/wasn't compatible, or inexplicably stopped working after a month or so of use (note the fact that i'm not the user of these computers, just the guy to to go to for a solution for the problems). Did software updates cause the problem??, cuz ubuntu has PLENTY of those..., who knows, I've tried everything from simply reinstalling the drivers to the whole damn operating system and nothing seems to last (at least not for more than a month or so).
Like I said, I've had almost zero trouble with my laptop (it's a gateway ma-7 btw) and I do love this operating system, I just want it to WORK for more people than myself.
I'm 100% behind the philosophy and all that jazz, but jeez, seriously, all you free-loving programmers out there, just please make it work and work well before creating HUNDREDS of distributions of the SAME damn operating system with a few cosmetic tweaks.

I wish I had at least a little help for you beyond the usual "additional drivers/windows drivers/ndiswrapper" crap that sometimes works, but I don't. 
Before my intro to linux, I was primarily a mac user because to me a computer is a tool to be used, and am now moving more and more back in the mac zone. Why? Not because I'm uncomfortable using a terminal, I just don't like spending over half of my time on the computer trying to make it a functional tool. The unlucky or "inexperienced" linux user will find themselves having to fight software/hardware issues every step of the way to do something as simple as import and edit a photo, watch a friggin video, listen to an online radio stream, or even access the internet in the first place. My advice to you as a new user is to try it out while bearing in mind that it's an experiment or hobby, rather than a solution to other user friendly operating systems. If you can get your computer to reliably do everything you need of it with ubuntu or some other linux flavor, use it, but don't depend on it for everyday use if you intend to do more than a small hand-full of tasks. I really would like to tell you to just say F&*% windows or whatever OS you're using, but that probably won't work for you unless you've got mad skills, or in my case, good luck and plenty of gumption.

Best of luck!

---

### Post by Filkins on 2011-03-22
> **Filkins said:**
> Just a little fair warning, I've been using ubuntu and a few other distros of linux for around a year or so, and was initially quite impressed with ubuntu 10.04 (my first go at linux). Later I discovered that I had lucked out BIG-time due to the high compatibility with the computer I was installing it on. Everything hardware related worked flawlessly "out of the box".
Naturally, I recommended ubuntu to many friends who were coming to me with windows virus problems and of course just plain windows problems, thinking I'd solve that for them once and for all.
And then, WHAP! they took my word for it, and being the guy who got them in this mess in the first place, I was suddenly confronted with an endless list of hardware quirks and driver incompatibility issues. i.e. a wireless card (broadcom BCM4312) that I managed to get functioning on a dell after hours of $&%@ing with drivers that ultimatly failed to work after a few weeks of service (everything from reinstalling drivers to reinstalling the whole damn OS failed to fix this problem for more than a month or so at a time). Anything usb related, video problems, sound cards, you name it, didn't work/wasn't compatible, or inexplicably stopped working after a month or so of use (note the fact that i'm not the user of these computers, just the guy to to go to for a solution for the problems). Did software updates cause the problem??, cuz ubuntu has PLENTY of those..., who knows, I've tried everything from simply reinstalling the drivers to the whole damn operating system and nothing seems to last (at least not for more than a month or so).
Like I said, I've had almost zero trouble with my laptop (it's a gateway ma-7 btw) and I do love this operating system, I just want it to WORK for more people than myself.
I'm 100% behind the philosophy and all that jazz, but jeez, seriously, all you free-loving programmers out there, just please make it work and work well before creating HUNDREDS of distributions of the SAME damn operating system with a few cosmetic tweaks.

I wish I had at least a little help for you beyond the usual "additional drivers/windows drivers/ndiswrapper" crap that sometimes works, but I don't. 
Before my intro to linux, I was primarily a mac user because to me a computer is a tool to be used, and am now moving more and more back in the mac zone. Why? Not because I'm uncomfortable using a terminal, I just don't like spending over half of my time on the computer trying to make it a functional tool. The unlucky or "inexperienced" linux user will find themselves having to fight software/hardware issues every step of the way to do something as simple as import and edit a photo, watch a friggin video, listen to an online radio stream, or even access the internet in the first place. My advice to you as a new user is to try it out while bearing in mind that it's an experiment or hobby, rather than a solution to other user friendly operating systems. If you can get your computer to reliably do everything you need of it with ubuntu or some other linux flavor, use it, but don't depend on it for everyday use if you intend to do more than a small hand-full of tasks. I really would like to tell you to just say F&*% windows or whatever OS you're using, but that probably won't work for you unless you've got mad skills, or in my case, good luck and plenty of gumption.

Best of luck!
get a mac

---

### Post by AndrewD257 on 2011-03-22
I agree with you one hundred percent.  I do this as more of a hobby than anything.  I have another laptop with windows 7 and ubuntu 10.10 that I use for most everything.

That said, I would still like to find a solution to this problem, so if you have any suggestions, please let me know.

---

### Post by bkratz on 2011-03-22
> **AndrewD257 said:**
> I agree with you one hundred percent.  I do this as more of a hobby than anything.  I have another laptop with windows 7 and ubuntu 10.10 that I use for most everything.

That said, I would still like to find a solution to this problem, so if you have any suggestions, please let me know.



I believe you can find what you need here.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)

---

### Post by AndrewD257 on 2011-03-24
I ended up just buying an Ethernet cable and connecting to the wifi through another computer.  Then I just had to install bcm fw-cutter and it worked like a charm.  Thank you all for your help.

---

