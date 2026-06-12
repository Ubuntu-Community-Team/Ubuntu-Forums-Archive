---
title: "Ubuntu 9.10 - No wireless network."
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by Michael_Parr on 2010-03-02
Ok, i'll start by saying i've never used linux before, and i just  installed Ubuntu 9.10 about an hour ago, and have done little, because i  cant do ****. Biggest issue would be the network right now, because  logging into windows 7 for internet is slow and annoying.

Ok, like i said, new to this, so i'll need clear instructions. Tell me  what additional information you may require, and how i am to acquire  requested information.

So, i have a Toshiba satellite p300,  Intel(R) WiFi Link 5100 AGN is  what i'm trying to use.

So basically its not detecting the wireless network i'm using now. Help please.

---

### Post by mark bower on 2010-03-02
I can't directly help you since I use PC's with either USB or PCI cards for wireless.  But whatever it takes, do not give up.  Once you are beyond the Ubuntu hardware issues (eg, bluetooth, wifi, printers, etc), you will love using Ubuntu.  The problem is not Ubuntu per sec, but that few hardware manufacturers look to linux when supplying drivers.  The linux community works hard to overcome the obstacles.

mark

---

### Post by jackvaughn on 2010-03-05
The disappointing thing is, if it didn't work 'Out of the box' it probably never will.
I've spent months trying to get my wireless working and have had no help whatsoever, and other support forums are just a waste of time.
Save yourself a lot of wasted hours and just use Windows.

---

### Post by Swagman on 2010-03-06
> **jackvaughn said:**
> The disappointing thing is, if it didn't work 'Out of the box' it probably never will.
I've spent months trying to get my wireless working and have had no help whatsoever, and other support forums are just a waste of time.
Save yourself a lot of wasted hours and just use Windows.

That's helpful.


Try left clicking on the network-manager icon in the right portion of your top taskbar.

What networks are available ? (Trying the obvious to start with)

---

### Post by TheConsaw on 2010-03-06
Michael, from one n00b to another, this is what I do to get wireless to work on my laptop,
firstly connect to net via Ethernet if you can, 
go to system/admin/Update manager
let it do it's thing,
after all updates go to system/admin/ hardware drivers,

it should download the appropriate graphic and wireless drivers for your machine

hope this works for you

---

### Post by old fert on 2010-03-06
I tend to agree with one of the other posters.  If it doesn't work "Out of the box," it probably will not.  I have been unable to get wireless to work with the last 3 versions of Ubuntu.  It is a great OS, but it does have some driver problems that require compromises.

I only have a laptop at home.  If I want to use Ubuntu, I have to be close to the ethernet connection (that works great).

---

### Post by Midnight Star on 2010-03-06
> **Michael_Parr said:**
> Ok, i'll start by saying i've never used linux before, and i just  installed Ubuntu 9.10 about an hour ago, and have done little, because i  cant do ****. Biggest issue would be the network right now, because  logging into windows 7 for internet is slow and annoying.

Ok, like i said, new to this, so i'll need clear instructions. Tell me  what additional information you may require, and how i am to acquire  requested information.

So, i have a Toshiba satellite p300,  Intel(R) WiFi Link 5100 AGN is  what i'm trying to use.

So basically its not detecting the wireless network i'm using now. Help please.

-----

The biggest initial problem I saw was with hardware manufacturers not directly supporting Linux. Most of the drivers out there are made for Windows, since at the moment, that's the biggest demographic: but that's slowly changing for the better. :) Ok, now back to the problem, I new too, but i've just setup my wireless network here using a Zonet 1602 modem card. This is an older discontinued card that cost me about $15 back then. It supports wirless b and g. 

The first thing I noticed after I installed it and rebooted the computer was...there was no wireless card detected. A quick search revealed that there was no driver written for linux, but all wasn't lost. On the driver disc that came with the cd were drivers for windows XP.  I could use those drivers on linux using something called "ndiswrapper".

See if this [link]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)) helps. And here are the[ instructions]("http://ubuntuforums.org/showthread.php?t=403139") ([http://ubuntuforums.org/showthread.php?t=403139](http://ubuntuforums.org/showthread.php?t=403139)) I used.

It works great, and actually stays up better and seems to have faster throughup than when it was used on my Windows machine.

-----

Mike.

---

### Post by Michael_Parr on 2010-03-10
No wireless networks show up when when right click blah blah. Thats when i noticed the problem. I'll try the Ethernet cable and hope it does find an update. Been meaning to try that, just lazy.

Thanks for the post, its not a huge issue. Ubuntu was just something to replace vista, but i'm overly impressed with windows 7.

---

### Post by Swagman on 2010-03-10
Your supposed to "**Left** click" the network manager to see wireless networks. 

Right Click to create/edit

---

### Post by pullmandave on 2010-03-10
I too, have had problems with the wireless. My IBM A30p has built in Prism 2.5 card and has not worked since I "upgraded" from 8.04. In fact the hostap drivers cause the system to freeze in a CPU hang state. The orinoco drivers do not seem to work either. If I unload/load the orinoco_pci module I see the eth1 device for a while (with ifconfig) and then it goes away....

---

