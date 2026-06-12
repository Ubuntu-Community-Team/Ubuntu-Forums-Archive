---
title: "please help me set up a small home network"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by 37fleetwood on 2009-08-29
I searched and couldn't find anything I could understand. I'm trying to set up a small home network so I can share files between my desktop PC and my laptop (media, documents, etc.). both are running Ubuntu 9.04, the desk is wired the laptop is wireless through my Westell router furnished by Verizon. also if someone else needs help with sharing with windows could someone please help to put this in layman's terms.
thank you!
Scott:(

---

### Post by DFlame on 2009-08-29
An issue like this was resolved less than a day ago, [here](http://ubuntuforums.org/showpost.php?p=7863428&postcount=8).

You say that both computers are running Ubuntu, but also say *"also if someone else needs help with sharing with windows could someone please help to put this in layman's terms."*

That doesn't really make sense too me, though I haven't woken up properly yet :P Try that link and explain a little further if you can :)

---

### Post by ahood on 2009-08-29
> **37fleetwood said:**
> I searched and couldn't find anything I could understand. I'm trying to set up a small home network so I can share files between my desktop PC and my laptop (media, documents, etc.). both are running Ubuntu 9.04, the desk is wired the laptop is wireless through my Westell router furnished by Verizon. also if someone else needs help with sharing with windows could someone please help to put this in layman's terms.
thank you!
Scott:(

Hi 37Fleetwood

It isn't quite clear what is desired exactly and the current configuration of your LAN.

I interpreted the post to indicate that the LAN configuration includes the following hardware:

Wireless/modem/gateway/router
Switch/hub (optional)
Desktop connected via ethernet cable directly to router or switch.
Laptop connected wirelessly.

Is the desire to share folder stored on the Desktop or Laptop?

Is the desire to add a new machine running file server software that will share a folder to all machines connected to the LAN?

Cheers!

---

### Post by Iowan on 2009-08-29
Oops - post got duplicated.

---

### Post by Iowan on 2009-08-29
There are (at least) a couple of steps involved. First is getting connectivity (make the machines talk to each other), then setting up a sharing protocol. First, verify that the machines get an IP address with **ifconfig -a** (on each machine). If they both have an address in the same subnet (ie 192.168.1.X - where X is different), can they **ping** each other? For linux-linux filesharing, [NFS]("http://ubuntuforums.org/showthread.php?t=249889") might be easiest. (There's also SSH, FTP, and Samba.)

---

### Post by 37fleetwood on 2009-08-29
> **DFlame said:**
> An issue like this was resolved less than a day ago, [here](http://ubuntuforums.org/showpost.php?p=7863428&postcount=8).

You say that both computers are running Ubuntu, but also say *"also if someone else needs help with sharing with windows could someone please help to put this in layman's terms."*

That doesn't really make sense too me, though I haven't woken up properly yet :P Try that link and explain a little further if you can :)

Thanks! this is exactly what I was looking for. it didn't show up in my search because the title is obscure.

my statement about Windows was that I was using Linux on both machines but someone in the future may have windows. I tried to label this post so that it would show up in a search for people looking to do what I'm trying to do so we don't have to keep bugging you more knowledgeable guys with the same stuff all the time. as you can see I totally missed the usb reference in my search.
I'm going to try setting this up right now, if I get it working, you'll know your instructions are dummy proof!

Thanks again!!
Scott:)

---

### Post by 37fleetwood on 2009-08-30
Ok, that worked fine. not in the direction I expected but I suppose it is the best way. I expected to be able to access my home computer with my laptop, instead I can access my laptop from my home computer. same thing I suppose.:)
thank you very much!
Scott

---

### Post by DFlame on 2009-08-30
Simply perform the instructions on the other computer to have it work in reverse too :)

---

