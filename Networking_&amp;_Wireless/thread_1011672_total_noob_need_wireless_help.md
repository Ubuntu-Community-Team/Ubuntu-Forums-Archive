---
title: "total noob: need wireless help"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by muxenle on 2008-12-15
okay first off sorry if this should go in the starter form, but since the problem here is dealing with wireless networks(though the problem is more likely me just missing something right under my nose).

I just instaled ubuntu studio 8.10 on a 18gig partition on my laptop; a Acer Aspire 57202. It seems to recoginize my wireless card and have some kind driver for it, but it I can't seem to figure out how to connect to my network. I've found  a help section but I can't find where it is telling me to go.... the network manager or something, and all I can find is network tools.

So ya, nothing really clear there at all but if you can offer any help it would be greatly appericated. If you want any more info I'll be glad to get it for you, but you'll mostly likely need to tell me what to do.

If this is in the wrong forum please tell me and I'll repost in the right forum(and once again sorry if I did pick the wrong forum)

Also sorry for the spelling, my I can't seem to get my web browsers spell checker to work for me, and I'm rather tired at the moment...

---

### Post by muxenle on 2008-12-15
bump

---

### Post by falcon61102 on 2008-12-15
The Network Manager app is normally in the upper-right hand corner of your screen and either looks like two monitors or some signal bars.  If you click on it, it should show you the Wireless Access Points in range.  If you do not see any access points, then it is possible that your wireless card needs some configuration.

Try clicking on the network manager.  If you don't see any access points, open up a terminal window by going to Applications>Accessories>Terminal.  Then run the following command:
```
sudo lshw -C network
```

That should display some information about your network card.

BTW, this is the right forum for this typs of problem.  And welcome to the forum.

---

### Post by yogo on 2008-12-15
My suggestion is to try Wicd, sounds like everything is there but just not communicating, I have found Wicd to work great on wireless setups, could not hurt to try.

---

### Post by muxenle on 2008-12-15
> **falcon61102 said:**
> The Network Manager app is normally in the upper-right hand corner of your screen and either looks like two monitors or some signal bars.  If you click on it, it should show you the Wireless Access Points in range.  If you do not see any access points, then it is possible that your wireless card needs some configuration.

Try clicking on the network manager.  If you don't see any access points, open up a terminal window by going to Applications>Accessories>Terminal.  Then run the following command:
```
sudo lshw -C network
```

That should display some information about your network card.

BTW, this is the right forum for this typs of problem.  And welcome to the forum.

well the thing is, there is no little computer thing or w/e there. just the time(and I think date).

could it be that I have ubuntu studio8.10 and not the normal ubuntu package?

---

### Post by falcon61102 on 2008-12-15
Yeah, that could be.  They may have changed the icon for the Network Manager for the Studio version.  What you can try doing is right click on the task bar and select Add to Task Bar (or something close to that).  That should open a window that will allow you to add all kinds of things to your task bar.  Scroll down until you see Network Manager, select it and click Ok.  Now you should see the Network Manager in you Task Bar.

---

### Post by foxfireattack on 2008-12-15
I'm totally new to ubuntu as well and I'm having problems with either the driver or the lack of recognizing it. I'm working from an HP Pavilion tx1320us tablet and I can only plug in via ethernet cable.

The router is a WPA- Personal encrypted linksys router. I'm not exactly sure what to do. please help D:

---

### Post by muxenle on 2008-12-15
okay I don't think that it even has network manager instaled on it... I wen to the add/remove apps and I found network manager on it, and it didn't have a the little box next to it checked.

I did enter that sudo command and this is what I got:

nathaniel@Nathaniel:~$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:52:c1:df
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=half firmware=5787m-v3.22 latency=0 link=yes module=tg3 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 42:98:5d:44:d6:09
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
nathaniel@Nathaniel:~$ 
nathaniel@Nathaniel:~$

---

### Post by yennik on 2008-12-15
I am having the same issues.  I have tried all the suggestions from ndiswrapper, to madwifi, and still my Sony Vaio VG-NR220E will not find or load the driver for my card.  It is a Lan Express AS IEEE 802.11g PCI Express Card by Atheros COmmunications.  I am a total newbie to Ubuntu.  I like it first because it is free, and it will work with my cat 5 cord.  I just can't seem to understand how to get it to work with the wireless card.  Can someone give me some simple, easy to follow instructions?

[email]douglaskinney_phd@yahoo.com[/email]

---

### Post by falcon61102 on 2008-12-15
muxenle,

Try going to System>Administration>Hardware Drivers to see if you card requires any restricted drivers.  If so, you will see it listed and you will be able to enable it.

foxfireattack and yennik,
Welcome to the forum and sorry that you're having some issues.  Even though your issues are similar in nature, your problems may be different.  You're best bet would be to start a new thread so that more people are likely to see your issue and be able to help you.  If you can, once you start a thread, post a link to it here and that way anyone following this one will be able to follow and help you as well.

The reason for this is that as people start posting suggestions and code to run, it's going to get very confusing trying to decipher what instructions are for what problem.  Thanks.

---

### Post by falcon61102 on 2008-12-15
muxenle,

Alright, I did some research on your Card (the Forum Search works great) and came up with a thread that has numerous people with the same issue that were able to resolve it.  

EDIT: Check out Post #3, that seems to be the fix that worked for most.

Here is the link:
[http://ubuntuforums.org/showthread.php?t=967654](http://ubuntuforums.org/showthread.php?t=967654)

If you run into problems or have any questions, post back up here and we'll work you through them.

---

### Post by muxenle on 2008-12-15
> **falcon61102 said:**
> muxenle,

Try going to System>Administration>Hardware Drivers to see if you card requires any restricted drivers.  If so, you will see it listed and you will be able to enable it.

foxfireattack and yennik,
Welcome to the forum and sorry that you're having some issues.  Even though your issues are similar in nature, your problems may be different.  You're best bet would be to start a new thread so that more people are likely to see your issue and be able to help you.  If you can, once you start a thread, post a link to it here and that way anyone following this one will be able to follow and help you as well.

The reason for this is that as people start posting suggestions and code to run, it's going to get very confusing trying to decipher what instructions are for what problem.  Thanks.

okay I'll try that in a couple of minutes, in the middle of something else atm. also putting systems into hiberinate and then 'waking up' the other system ftw!

---

### Post by muxenle on 2008-12-15
> **falcon61102 said:**
> muxenle,

Alright, I did some research on your Card (the Forum Search works great) and came up with a thread that has numerous people with the same issue that were able to resolve it.  

EDIT: Check out Post #3, that seems to be the fix that worked for most.

Here is the link:
[http://ubuntuforums.org/showthread.php?t=967654](http://ubuntuforums.org/showthread.php?t=967654)

If you run into problems or have any questions, post back up here and we'll work you through them.

I just tried that but I couldn't get past the second step I think, the one where you enter that sudo command, because I need the internet to DL those packages which I can't get(even if I plug the eithernet cord dirrictely into my laptop)

so I'm currently burning plain old ubuntu 8.10 and i'm going to see if I can get it work with that...

---

### Post by falcon61102 on 2008-12-15
Well, let's hope that you have better luck with that.  Let us know how it goes.

---

### Post by muxenle on 2008-12-15
> **falcon61102 said:**
> Well, let's hope that you have better luck with that.  Let us know how it goes.


nope :(

I might go back and try hardy herion(the last stable version) or prehaps the new alpha 9.04...*shrug* or even a different linux system.

Thanks for  all your time and help :)

---

### Post by falcon61102 on 2008-12-15
Still no luck even with the wired connection?

If you can get the wired connection, then the wireless shouldn't be too hard after that.

---

### Post by muxenle on 2008-12-15
> **falcon61102 said:**
> Still no luck even with the wired connection?

If you can get the wired connection, then the wireless shouldn't be too hard after that.

haven't tried the wired connection yet with plain ubuntu

I'll try it tommorow after school(if I have it, *crosses finger and hopes for snow day) and get back with the results. I'm just worn out switching between vista and linux; and I don't want to have to get up and untangle the cords... yes I am that lazy -_-

---

### Post by falcon61102 on 2008-12-16
Well post back with the results.  Hopefully things will work better with straight 8.10.  I haven't heard of too many people having trouble with their wired connections.

---

### Post by muxenle on 2008-12-16
> **falcon61102 said:**
> Well post back with the results.  Hopefully things will work better with straight 8.10.  I haven't heard of too many people having trouble with their wired connections.

to be honest I think all forms of wirless internet hate me

first I switched to  XP from vista and then all my drivers gave me hell, mostly all forms of internet(mostly wirelss) so I tried ubuntu at some point first 7. something or other which I couldn't get to work at all, then I tried hardy herion beta and it more or less worked, but at the time I wanted something more stable so I went back to vista...which still gave me trouble. I love computers, but computers seem to hate me...

---

### Post by falcon61102 on 2008-12-16
I know the feeling.  Well, with a little patience and lots of trial and error, I'm sure we'll get it working. :)

---

### Post by S_e_P_p on 2008-12-16
That is the way which worked for me: (Acer aspire 5020)

Start your laptop and use the lan cable for internet.
Afterwards install all updates. Restart and check again for updates. If you have new one install them also. Restart again.

Go to System --> and Hardware Drivers. Activate the Broadcom Driver.

Afterwards type the following in an terminal:

sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

THAN RESTART.

Again in an Terminal.

echo 1 > /sys/devices/platform/acer-wmi/wireless

It should be activated now. (can take some minutes)

You have to do the last step everytime you restart the laptop. But there is also a way to automate it.

Greets,
SePp

---

### Post by muxenle on 2008-12-16
> **S_e_P_p said:**
> That is the way which worked for me: (Acer aspire 5020)

Start your laptop and use the lan cable for internet.
Afterwards install all updates. Restart and check again for updates. If you have new one install them also. Restart again.

Go to System --> and Hardware Drivers. Activate the Broadcom Driver.

Afterwards type the following in an terminal:

sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

THAN RESTART.

Again in an Terminal.

echo 1 > /sys/devices/platform/acer-wmi/wireless

It should be activated now. (can take some minutes)

You have to do the last step everytime you restart the laptop. But there is also a way to automate it.

Greets,
SePp


hhmm...thanks but I can't do that-- I just got done trying to use a wired conection with ubuntu and it looked like everything was connected, but I couldn't sign on msn in pidgin, go to a website with firefox, or ping a web addresss...

---

### Post by muxenle on 2008-12-16
bump

---

### Post by muxenle on 2008-12-17
bump

---

### Post by yennik on 2008-12-18
Thanks I will post on new thread.):P

---

