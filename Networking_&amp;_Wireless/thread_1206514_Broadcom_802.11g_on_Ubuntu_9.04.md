---
title: "Broadcom 802.11g on Ubuntu 9.04"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by Pierre3400 on 2009-07-07
Hey

I got Ubuntu installed on my laptop, but i am un able to work out how to get the wireless working on ubuntu 9.04. The Laptop has a Broadcom 802.11g wireless card. 

I did a search online but didnt find anything i could understand on how to get this wireless card working?

---

### Post by t0mppa on 2009-07-07
Ok, first open up a terminal, run **lshw -C network** and post back with the output to get an idea what chipset your card has and what state it is in now that doesn't work.

There are plenty of Broadcom cards that support 802.11g, but knowing the exact type will help in deciding what drivers it needs to work properly.

---

### Post by Pierre3400 on 2009-07-07
I will try, but its a pain going back and forth between ubuntu and vista.

I got the network slightly working?

The light for the wireless isnt "on" on the the laptop in ubuntu like it is in windows, but it s
ays connected, but only for short periods of time. About 30secs.

---

### Post by t0mppa on 2009-07-07
You can save the output to a text file and just mount the Vista HDD or partition on Ubuntu and drop it there, if you have a dual-boot.

If it actually works from time to time though, it sounds like the configuration is working and there's no need to troubleshoot the driver installation problems. I never run into the intermittent connection issues myself, so don't know how to handle them, but [here]("http://ubuntuforums.org/showthread.php?t=1146367")'s a thread which hopefully provides some help on the matter.

Oh and the wireless light can be a little tricky, as it isn't automatically used by the wireless driver, but needs to get set up separately. The wireless still works just fine without the light, it's just harder to spot whether the on/off button that's so common on laptops these days is on or off.

---

### Post by Bucky Ball on 2009-07-07
Plug an ethernet cable in and get your updates. That may then offer you some Restricted Third Party drivers. Accept.

Check:

System->Administration->Hardware Drivers

What is there?

---

### Post by Pierre3400 on 2009-07-07
> **t0mppa said:**
> Ok, first open up a terminal, run **lshw -C network** and post back with the output to get an idea what chipset your card has and what state it is in now that doesn't work.

There are plenty of Broadcom cards that support 802.11g, but knowing the exact type will help in deciding what drivers it needs to work properly.

Exactly what should i be typing in the terminal?

Here is a screenshot of the drivers. From what i could read im suppose to use B43, but  doesnt seem to work? 
[http://peecee.dk/uploads/072009/Screenshot.png](http://peecee.dk/uploads/072009/Screenshot.png)

---

### Post by t0mppa on 2009-07-07
Like I said, as your drivers actually worked - even if intermittently, no need to consult the terminal on that account anymore.

Since Hardware Drivers is also offering you the STA, you probably have one of the chipsets that are supported by it. Try disabling the b43 and enabling the STA instead, as it's a newer driver and preferable for the chips that it supports. Maybe that'll work better and solve the case alltogether without a need for more complex methods. You will need network access for that to work properly though, so do you have wired connection available?

---

### Post by Pierre3400 on 2009-07-07
Alright, useing the STA, the wireless finds my wireless network, I have WPA 2 security on the network. Its a Linksys router.

Like i said with the STA it works, finds network, but it wont connect?

---

### Post by Pierre3400 on 2009-07-23
> **Pierre3400 said:**
> Alright, useing the STA, the wireless finds my wireless network, I have WPA 2 security on the network. Its a Linksys router.

Like i said with the STA it works, finds network, but it wont connect?

Its been 2 weeks now, and not one reply :( My wireless doesnt work anywhere! It finds connections, but cannot connect to any of them.:(

---

### Post by t0mppa on 2009-07-23
Sorry, went on a holiday a few weeks back, so must've missed your earlier post.

Anyway, did you have Internet access (through wired interface) when enabling the STA? Have seen a few threads where that's been the issue, as it wants to download some files when it gets enabled and without a working Internet connection that fails and then it won't work. But since I personally haven't used the STA, as it doesn't support my card, don't have much experience in troubleshooting it beyond that.

The reason why I'm recommending it to you, is that a lot of users have reported that it is indeed a step forward from b43 and thus worth a little trouble in setting up. However, if you can't get it to work, b43 will work pretty well too, so you can just swap to that.

However, same thing about the Internet connection actually applies for b43. It requires firmware (binary-only closed source program) to be set up, which doesn't get automatically installed by Ubuntu, since it's not open source. [Here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")'s a page with more information about it.

---

### Post by Pierre3400 on 2009-07-24
> **t0mppa said:**
> Sorry, went on a holiday a few weeks back, so must've missed your earlier post.

Anyway, did you have Internet access (through wired interface) when enabling the STA? Have seen a few threads where that's been the issue, as it wants to download some files when it gets enabled and without a working Internet connection that fails and then it won't work. But since I personally haven't used the STA, as it doesn't support my card, don't have much experience in troubleshooting it beyond that.

The reason why I'm recommending it to you, is that a lot of users have reported that it is indeed a step forward from b43 and thus worth a little trouble in setting up. However, if you can't get it to work, b43 will work pretty well too, so you can just swap to that.

However, same thing about the Internet connection actually applies for b43. It requires firmware (binary-only closed source program) to be set up, which doesn't get automatically installed by Ubuntu, since it's not open source. [Here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")'s a page with more information about it.

There was a cable conection at the time i set it to STA, b43 doesnt work at all.

I'll look at the link :)

---

### Post by Mechwizard on 2009-07-24
Hi guy's,
I will be following this thread as this is my same issue. (see all, connect to none)Wired has worked from set-up. Both native drivers and ndiswrapper have given same results.

dell studio 1735
broadcom 4322 chipset on wl
have used GUI: network manager, Wicd, network tools (which says that none of my connections exist), terminal.

---

### Post by t0mppa on 2009-07-24
> **Pierre3400 said:**
> There was a cable conection at the time i set it to STA, b43 doesnt work at all.

I'll look at the link :)

Allright then, one last thing that comes to mind is to check if your dmesg shows any issues with the STA that would point towards the problem by running **dmesg | grep -e wl** from terminal.

Did you set up the firmware, when trying b43? It won't work without that.

---

