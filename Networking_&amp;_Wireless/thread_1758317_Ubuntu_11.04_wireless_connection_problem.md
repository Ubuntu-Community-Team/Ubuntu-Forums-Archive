---
title: "Ubuntu 11.04 wireless connection problem"
date: 2011-05-14
forum: Networking &amp; Wireless
---

### Post by modmidget on 2011-05-14
I have just installed Ubuntu 11.04 on a new computer which also has Windows XP installed.  This computer is connected to the internet via a USB Zonet ZEW2590 802.11N wireless card with the Ralink RT3070 chipset.

Ubuntu sees the wireless card and it connected to my wireless router without any problems.  When I look at the connection information it says the wireless card is connected at 24mb/s and one time it said it was connected at 54mb/s.  

The problem is that when I go into Firefox and type in a url (such as [www.yahoo.com](www.yahoo.com)) I see a message at the bottom of the screen saying "Looking Up [WWW.YAHOO.COM](WWW.YAHOO.COM) and then it does nothing for several minutes.  Then I get a pop-up box that says "Server Not Found".

Am I forgetting something in the setup?????

Thank you for any help you might be able to provide.  I don't have much experience with Linux, so please try to keep any responses as simple as possible.

---

### Post by abisdad on 2011-05-14
While I'm not an expert, I take it that you can ping your router OK. 

I'm guessing your DNS is not right - that's where your computer looks up the URL to an IP address. 

If you're connecting fine, then are you using Automatic DHCP? This is the best way as long as your router is set up to do so.  If not, check your router's DNS setting, and use that - it's an IPv4 address.

Hope that helps.

Rob.

---

### Post by modmidget on 2011-05-14
I can ping my router 192.168.1.1 but it reported 26% of packets were lost.  

Yes, I have my network set for DHCP.

I don't understand what you mean about checking or using the routers' DNS setting.  How would I do that?  I do know how to log onto the router but I don't know much more than some of the basic settings.

Thanks for your help.

---

### Post by MooPi on 2011-05-14
Try this 
```
sudo su
```
```
gedit /etc/modprobe.d/blacklist.conf
```
At the end of the file add these lines
```
#blacklist to improve rt2870/3070
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```
Save and log out then back in to check connectivity.

---

### Post by modmidget on 2011-05-14
MooPi,  I made the changes you suggested and now Ubuntu will not boot.  It freezes at the initial splash screen where I see the word UBUNTU with 5 red dots under it.

**edit**

I unplugged the USB wireless nic and rebooted.  It rebooted just fine and I was able to undo the changes to blacklist.conf.  Now it's booting OK but still having the same problem I originally posted.

---

### Post by ngronewold on 2011-05-14
> **modmidget said:**
> MooPi,  I made the changes you suggested and now Ubuntu will not boot.  It freezes at the initial splash screen where I see the word UBUNTU with 5 red dots under it.

**edit**

I unplugged the USB wireless nic and rebooted.  It rebooted just fine and I was able to undo the changes to blacklist.conf.  Now it's booting OK but still having the same problem I originally posted.


If you have a Dell with a BCM4xxx wireless card you may want to check out the sticky thread at the beginning of this section. Even if the system says it can find your card something may be preventing it from actually using it. Seem like a common problem with nearly every upgrade.

---

### Post by abisdad on 2011-05-14
> **modmidget said:**
> I can ping my router 192.168.1.1 but it reported 26% of packets were lost.  

Yes, I have my network set for DHCP.

I don't understand what you mean about checking or using the routers' DNS setting.  How would I do that?  I do know how to log onto the router but I don't know much more than some of the basic settings.

Thanks for your help.

If you are using DHCP, then I doubt that DNS will be the problem, since DHCP should automatically set your DNS. Sorry. :(

Rob.

---

### Post by MooPi on 2011-05-15
> **modmidget said:**
> MooPi,  I made the changes you suggested and now Ubuntu will not boot.  It freezes at the initial splash screen where I see the word UBUNTU with 5 red dots under it.

**edit**

I unplugged the USB wireless nic and rebooted.  It rebooted just fine and I was able to undo the changes to blacklist.conf.  Now it's booting OK but still having the same problem I originally posted.

I've had similar issues with my adapter and I just pulled the usb adapter to let it boot then re-insert after boot. All was well afterward.

---

### Post by modmidget on 2011-05-15
ngronewold, this is not a Dell computer.  I built this one myself.  I've been building computers for myself and my friends for 15 years.  I bought an empty tower, installed a new MSI G31TM-P21 motherboard, an Intel dual-core 64 bit CPU, 2 gig of memory and the Zonet ZEW2590 wireless USB card.  The system works great in XP and I've got the fastest wireless connection I've ever had with the new Zonet card.

MooPi,  I thought I might get a connection by unplugging the wireless card before booting and then plugging it in after booting so I tried it yesterday.  It didn't work.  Ubuntu didn't even recognized that the wireless card had been plugged in.  I've used the same USB port to plug in my thumb drive and Ubuntu instantly saw it, so I know the usb port is working properly,  but it doesn't see the wireless card.

---

### Post by modmidget on 2011-05-16
I was tinkering around with the computer again yesterday afternoon and went into Firefox.  I typed in [www.google.com](www.google.com) and waited for the error message "server not found" to pop up.  After waiting about 2 minutes the Google web site came up.  It was extremely slow and I was not able to go from Google to any other web sites but, at least I did get to Google.  Later I went into Firefox again and typed in [www.yahoo.com](www.yahoo.com).  Once again, after a couple of minutes, the Yahoo web site came up but it was also extremely slow.  There must be some setting in Ubuntu that is causing the network connection be this slow.

---

### Post by modmidget on 2011-05-20
^

---

### Post by modmidget on 2011-05-25
It's Goodbye Ubuntu.

After posting my wireless problems on 3 or more forums with no replies that have solved my problem I've given up.  Today I removed Ubuntu from my computer and installed PCLinuxOS.  After reading all of the posts on the various forums about the problems everyone is having with Ubuntu and their attempts to connect using a wireless card I've come to realize Ubuntu has a real problem.  They seem to be spending more time trying to make their version of Linux look pretty than they are trying to make it functional.

PCLinuxOS was very easy to install and it recognized ALL of my hardware.  It took less than 2 minutes to have my wireless connection up & running and I am not having any issues with it.  

I've had PCLinuxOS connected to the internet using Firefox for over 4 hours with no disconnects whatsoever.

:guitar:

---

