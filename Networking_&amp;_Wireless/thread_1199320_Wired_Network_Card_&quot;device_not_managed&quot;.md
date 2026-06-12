---
title: "Wired Network Card: &quot;device not managed&quot;"
date: 2009-06-28
forum: Networking &amp; Wireless
---

### Post by ForMar on 2009-06-28
Hello,

I have a total of three network cards on my computer, two wired (built in) and one wireless. I need all three up and running. One of the cards says the the device is not managed.
**Question:** How do I get my computer to manage my network card. The card is..."88E8056 PCI-E Gigabit Ethernet controller" 
**Attempted solutions:** I have attempted to solve this problem a few ways the most recent by editing "sudo gedit /etc/NetworkManager/nm-system-settings.conf" and changing the only true on that page to false. Not only did it not work but now the computer hangs for several minutes on starting NFS daemon and NFS does not work. (Which I use alot)Changing it back did not solve the problem either so I have restored ( yet to be tested ). 
I am running ubuntu 9.04. Thank you for your help and time

Anthony

---

### Post by Iowan on 2009-06-28
I'm not sure Network Manager is capable of managing more than one interface at a time.  Although my laptop can go wired or wireless, I haven't tried to connect with both.  Last thread I remember trying to do both was unsuccessful... but maybe that's changed by now. You *should* be able to set up configurations via */etc/network/interfaces*, but that won't  solve the "unmanaged" issue.

---

### Post by SecretCode on 2009-06-29
(Network Manager can manage multiple interfaces ... although mine struggles with the wireless interfaces.)

Something I've just discovered is that if the interface is listed in /etc/network/interfaces, Network Manager will be unable to manage the interface. I think /etc/network/interfaces should only list [FONT="Courier New"]auto l0[/FONT].

---

### Post by computer13137 on 2009-06-29
My eeePC does this sometimes... where I'll disable\re-enable my WiFi and suddenly the interface is not managed.  I have internal WiFi which I can only turn off in the BIOS.  Sometimes I do, sometimes I don't.  Due to range issues when I'm at work, I use a Linksys WUSB54G.  It has no trouble with having 2 interfaces, but I'm not using the both at once (although sometimes they are both managed at once, I don't connect to 2 networks at once).

Whenever I encounter this problem, a quick reboot fixes it.  Unfortunately, I have not found a long term solution to this problem.  I'm subscribing to this thread in case anyone else has, however. :)

Good luck.

-Kirk

---

