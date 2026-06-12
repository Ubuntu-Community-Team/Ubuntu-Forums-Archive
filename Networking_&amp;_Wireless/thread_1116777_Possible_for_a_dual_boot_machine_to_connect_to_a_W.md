---
title: "Possible for a dual boot machine to connect to a Windows network?"
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by Hiroshima on 2009-04-05
First of all, this may just be a theoretical exercise, because if it gets too complex, I probably won't start. That said, here's what I'd like to do:

At work I have use an XP machine with a C and D drive.  The D drive is free, and just waiting for some nice fresh Ubuntu without the danger of messing up the original computer setup.

I have tried live CDs of various flavours on the machine, and they seem ok, but they cannot find the network, and thus cannot get to the internet.

When I log on in XP, the networks are connected as windows logs on (that is probably normal, not just a work-network thing).

So, if I install Ubuntu, is it possible for me to connect to the work networks and thus the internet?  If so, what information would I need to get from XP about the networks, and where would I find it?  (Screenshots would be great, since the XP is in Japanese... I forgot to mention that, didn't I).

Also, after I install Ubuntu, I won't have a connection, so I won't be able to use synaptic to get extra packages.  If I need more software to make this work, I will have to download it in XP and then access it after a re-boot, which I think is possible, but I don't know exactly how.

Thank you in advance.  This isn't a life or death problem, since I can work in XP, but having an Enlish based OS would be lovely.

Hiroshima.

---

### Post by Bucky Ball on 2009-04-05
Have you got access to an ethernet cable to your network or just wireless? One problem is you need to access the drivers for your wireless card, if that is what you are using, and this can be done via an ethernet cable which Ubuntu will pick up automatically without you doing anything (or should). You would need to have Ubuntu installed to get wireless up I would think as you are running off the cd and you would not be installing drivers to the cd, if you follow me. The ethernet cable drivers are already on the cd. The wireless drivers are usually restricted, therefore don't ship with the Ubuntu ISO (you must agree to conditions of use, etc ... )

If it is a spare drive, install anyhow (will be faster than the Live version) and let's see if we can't get it up from there. Shouldn't be that hard unless the wireless card is not compatible (unlikely). Provide whatever details you can about the network situation and the make and model of card so we can confirm it will work.

* ps: to connect to a wireless network you are going to need that name of the network access point ('WorkAP1' or whatever it might be) and the security key, possibly WEP key to setup your networking configuration within Ubuntu. Good luck with it. If everything is working in the Live version except your wireless, you probably aren't going to need much. :)

---

### Post by Hiroshima on 2009-04-05
It's connected via an ethernet cable.  The reason I thought I might run into difficulties is that the live CD wouldn't pick up the network, so I assume that is is password sensitive.

I won't be into the office for another 10 hours or so, but what kind of network information do I need to check?

I will take in the CD, and get it running on the spare drive, and then I can see what it gets me (not fired I hope)!

I'll post back in the morning when it is done.

Hiroshima

---

### Post by Bucky Ball on 2009-04-05
You may need to talk to a friendly IT person at work. Not sure why it is not picking up the network through ethernet, but yes, you probably need to log in using the appropriate network name and security details. This can be done through System->Administration->Network, unlock with your password then go to properties. Your work may set static IP addresses to the machines on its network or DHCP which serves a different one whenever you log on. Things you might want to check.

---

### Post by Hiroshima on 2009-04-06
The install went pretty smoothly.  It does recognize the network, I can see the names of the networks in network places, but if try to open them they look like empty folders.

Like you suggested, I will have to enlist an IT person to see what login information I need, but I am on the way!  The connections are there, but it looks like the permissions are not.

Thanks again,

Hiroshima

---

### Post by Bucky Ball on 2009-04-06
Excellent news, you look like you're well on the way. As you say, now you can see everything out there, just a case of knocking on the door and hoping you get let in! Good luck with it, you might make a few converts ... :) 

The system probably needs to assign you an IP address. Don't try and set one in Ubuntu cos this can cause all sorts of headaches if the system is serving you another back, even if they are the same IP address. The problems arise because they are both trying to force the IP onto the other. Only one device should be assigning IPs, usually the router/AP as it needs to assign a bunch to a few or many machines. If the workstations  were all choosing their own it would get nasty.

:)

---

### Post by Hiroshima on 2009-04-09
The bad news is in... and not technical news at all.  The IT chiefs said no go on using other OSs to connect.  
I am still tempted to try, but since the computer is theirs, I had better play by the rules.

Bucky Ball, thanks for the help in getting me this far.  I still have the Ubuntu install on one drive, but it won't be much use if I can't get to  all the shared files.

Ah well, at least I can live the linux life at home.

Thanks for the help,

Hiroshima

---

### Post by lisati on 2009-04-09
It's usually a good idea to co-operate with whoever manages any network you want to connect to, particularly if it's not your own network. 

If you are successful in negotiating a connection while keeping on good terms with the admins, you might need to do a little extra work in accessing shared files and printers. You might want to look using something like samba (there are other ways as wel): one "how to" can be found at [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

