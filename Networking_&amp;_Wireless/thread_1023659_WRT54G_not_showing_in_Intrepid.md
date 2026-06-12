---
title: "WRT54G not showing in Intrepid"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by SammoJ on 2008-12-28
Hi folks,

seriously losing my mind here. My Dell XPS M1330 will not detect my linksys WRT54G v7 wireless network. It will show my two neighbour's networks fine and has no problem connecting to public networks. I have tried setting the wireless network to unsecured and I usually have it as WPA2 but no luck. The same laptop connects fine when booted into Vista and every other computer in the house connects fine.

The output of lshw shows the driver as iwl3945. Please help because this is driving me absolutely mad!

Thanks

---

### Post by Tom--d on 2008-12-28
Your wireless card should be working.

When you want to connect, go to connect to a hidden network. Type in from there. See if it connects.

---

### Post by SammoJ on 2008-12-28
This puts me in a loop of network password prompts. I am prompted for the password about once every minute continuously and the network manager icon says 'Attempted to join the network...'.

Running NetworkManager --no-daemon it says roughly:

eth1 state change 0 -> 2
Activation (eth1/wireless) association took too long.
(eth1): device state change 5->6
Activation (eth1/wireless) asking for new secrets
(eth1): supplicant state change: 2 -> 0

And then I get the prompt.

---

### Post by SammoJ on 2008-12-28
I reckon ndiswrapper might fix this but that seems like a rather dirty approach seeing as I can detect other networks? I can also connect to the network from a Acer Aspire 1 running Linpus.

---

### Post by SammoJ on 2008-12-28
Still nothing, looks like I'll be forced to use windows here...bah!

---

### Post by namdung on 2008-12-28
Pls try once with Ubuntu 8.04.1 LiveCD. I reckon the issue is with Intrepid.

---

### Post by SammoJ on 2008-12-28
Got the problem solved by upgrading the WRT54G firmware to version 7.00.4 and swearing lots at it, smacking it repeatedly against the stone shelf it lives on and resetting it lots. I feel much better now, thanks for your help though everyone, much appreciated!

---

### Post by albinootje on 2008-12-28
> **SammoJ said:**
> Got the problem solved by upgrading the WRT54G firmware to version 7.00.4 and swearing lots at it, smacking it repeatedly against the stone shelf it lives on and resetting it lots. I feel much better now, thanks for your help though everyone, much appreciated!

Interesting to hear about the firmware upgrade. Well done! :)

---

### Post by kevdog on 2008-12-28
Not that you have too, but I would flash your wrt54g with either tomato, or ddwrt firmware if you really want to turn your router into an enterprise solution.  It has nothing to do with this problem, however you will be amazed by this firmware upgrade.

---

### Post by albinootje on 2008-12-28
> **kevdog said:**
> Not that you have too, but I would flash your wrt54g with either tomato, or ddwrt firmware if you really want to turn your router into an enterprise solution.  It has nothing to do with this problem, however you will be amazed by this firmware upgrade.

That can be a lot of fun.

But I'd like to add some serious warnings.
First of all newer version of Linksys WRT routers don't have Linux on it anymore (Some VxWorks propietary software instead since v5), and Linksys has put less memory on some of the newer models.
You can only play with OpenWRT, DD-wrt and others on the earlier versions, and then again YMMV..
There's also the chance to brick your WRT :(
I have a friend who has grown into an expert to un-brick almost all WRT (and Asus WL) routers, and I have a bit of experience on that too, but I can tell you it's no fun having worked on a router like that and thinking that it's ... dead.
Think twice before you're gonna play with this!
If you're new on the command-line, I recommend sticking with the default Linksys software on your Linksys router.

---

### Post by kevdog on 2008-12-28
I in new sense of the word didn't imply to not do your research before flashing your router.  I purposely bought a wrt54gl for my last router to avoid the confusing mess, since I know that this router was specifically designed with the intent for 3rd party firmware.  Older wrt54g routers are even better than the modern 54gl since they possess greater on-board memory.

I'm just throwing out this suggestion since many haven't heard of such project.  The ability however to run a openvpn server, run a ssh daemon, and run a repeater bridge are my favorite capabilities of the modified firmware.

---

### Post by albinootje on 2008-12-28
> **kevdog said:**
>  I'm just throwing out this suggestion since many haven't heard of such project.  The ability however to run a openvpn server, run a ssh daemon, and run a repeater bridge are my favorite capabilities of the modified firmware.

I agree that it's very cool.
You can also run a "mesh" network with neighbors (done that in the past) by using special software for that, and having ssh to login remotely is very handy in that case.

Here's an example of a fairly big project which does that :
[http://en.wikipedia.org/wiki/Freifunk](http://en.wikipedia.org/wiki/Freifunk)
See also :
[http://en.wikipedia.org/wiki/OpenWrt](http://en.wikipedia.org/wiki/OpenWrt)

---

### Post by SammoJ on 2008-12-29
Yeah I've played with Tomato before and was going to go for this option before discovering that the router is a WRT54G v7. No support for tomato after v5. It seems that the later versions of the WRT are pretty pants, this one in particular often crashes due to having reduced RAM compared to previous versions. However hopefully the firmware upgrade will fix that too...seems relatively stable for the past day anyway,

Cheers for all the help guys, this is why I love Ubuntu and the community. I've just managed to convert all of my family to Ubuntu running on Acer Aspire One netbooks. They now love it to and I can actually give them all support again *groan*!

Thanks

---

### Post by albinootje on 2008-12-29
> **SammoJ said:**
>  Cheers for all the help guys, this is why I love Ubuntu and the community. I've just managed to convert all of my family to Ubuntu running on Acer Aspire One netbooks. They now love it to and I can actually give them all support again *groan*!

Awesome! Cheers! :)

---

### Post by SerpicoUK on 2009-01-03
Hi all,

I have the same issue with Intrepid not displaying our (very old) WRT54G. My problem is that the router was set up by the landlord so I don't have access to upgrade the firmware.

I'll try and get hold of the landlord but are there any other possible solutions to try?

This is a bit disappointing as it finds every other network in the area (compared to those displayed in Windows) - I wonder why it fails with this linksys?

Serp

---

### Post by frans0023 on 2009-01-09
Hello,

I have the same problem with a fresh installed Ubuntu Intrepid and a WRT54G router (last dd-wrt firmware on it). My network is not detected with the last kernel 2.6.27-9-generic. Same problem with 2.6.27-7-generic.

My 2 laptops have a Intel 3945 wireless card.

On the other laptop, when I upgraded to Intrepid, there was the same problem: my network was not present in the list.
I tried to install an older kernel (2.6.24-18-generic) and it solved the problem with this one. My wifi connection is OK with this kernel.

So I try to install 2.6.24-18-generic on my fresh-installed Ubuntu and I can't find it anymore in the packages list. There are only 2 kernel versions.


- Is someone know something about this Ubuntu Intrepid <-> Linksys WRT54G bug ?!
- How could find the linux-image-2.6.24-18-generic for Intrepid ?

I hope that you understood my poor english. Yes I'm french but you guessed ;)

---

### Post by kevdog on 2009-01-09
You could always compile any version of a generic kernel if you wanted.  I think kernel check (post within tutorials and tips section) has a utility that allows you to compile and prior or newer version of a kernel that you want.  Yes I know its a pain, however if you really want to learn something its actually very fun (and it really doesn't take all that long).

---

### Post by frans0023 on 2009-01-09
> **kevdog said:**
> You could always compile any version of a generic kernel if you wanted.  I think kernel check (post within tutorials and tips section) has a utility that allows you to compile and prior or newer version of a kernel that you want.  Yes I know its a pain, however if you really want to learn something its actually very fun (and it really doesn't take all that long).

Hi kevdog and thank you for your answer but I compiled many kernels for my debian box and I hate that :D I would like to install it using apt on my laptop.

Anyway, I don't understand why i can't see MY network ! Fortunatelly, I can connect to the Internet using a FON box !

---

### Post by frans0023 on 2009-01-10
I tried to install on older linux-image from the hardy repository on my intrepid, but wifi doesn't want to work. Maybe I don't select good packages.

Well I decide to install Hardy and to make an upgrade to Intrepid. In this way, I will be able to boot on 2.6.24 kernel and to keep my wifi connection OK.

If someone have an idea for the Ubuntu Intrepid <-> Linksys WRT54G problem, please post something !

Thank you

---

### Post by frans0023 on 2009-01-11
I downloaded and installed (i'm not sure for the order):

[http://packages.ubuntu.com/linux-image-2.6.24-21-generic](http://packages.ubuntu.com/linux-image-2.6.24-21-generic)
[http://packages.ubuntu.com/linux-headers-2.6.24-21-generic](http://packages.ubuntu.com/linux-headers-2.6.24-21-generic)
[http://packages.ubuntu.com/hardy/linux-headers-2.6.24-21](http://packages.ubuntu.com/hardy/linux-headers-2.6.24-21)
[http://packages.ubuntu.com/hardy/linux-restricted-modules-2.6.24-21-generic](http://packages.ubuntu.com/hardy/linux-restricted-modules-2.6.24-21-generic)
[http://packages.ubuntu.com/hardy/linux-ubuntu-modules-2.6.24-21-generic](http://packages.ubuntu.com/hardy/linux-ubuntu-modules-2.6.24-21-generic)

Intrepid works great ! WRT54G connection is OK ! :p

It's such a strange thing !

---

### Post by frans0023 on 2009-01-14
The wifi signal is detected when my computer is very close from the router !
I think there is a problem with the signal power !
It's strange because this router is known for it's high transmission power. Anyway, it's well detected with a 2.6.24 kernel.

---

### Post by frans0023 on 2009-02-11
I found the solution !!!
My Wifi was on the 13 channel and it's not detected anymore since 2.6.27
You just have to set the Wifi channel from 1 to 11 !

---

