---
title: "wired network"
date: 2011-04-18
forum: Networking &amp; Wireless
---

### Post by Hakimjo on 2011-04-18
strange, all of a sudden, my wired network connection doesn't work anymore, neither on Ubuntu nor on the parallel Windows.  I haven't tampered with the computer, the light is ok, etc.  I have reinitialised the modem and I am writing this through the wireless connection of the same modem.

Probably I will have to call the ISP, but before I want to make sure that things are ok in my computer.

Thanks,

Joachim

---

### Post by collisionystm on 2011-04-18
Make sure your pets did not eat your Ethernet cable ;)

Are you plugging directly into the router?

---

### Post by Hakimjo on 2011-04-18
drove off the pets, checked the cable and even changed it, do plug directly into the router

---

### Post by collisionystm on 2011-04-18
If it is a router with wireless, I would begin to assume that this router has 5 Ethernet ports on the back. 1 for internet, 4 for LAN, a wireless antenna and a possible USB. This is the standard. Have you tried another one of the 4 ethernet ports for the LAN?

---

### Post by klr on 2011-04-18
Look at my thread here, similar problem maybe:

[http://ubuntuforums.org/showthread.php?t=1732570](http://ubuntuforums.org/showthread.php?t=1732570)

---

### Post by collisionystm on 2011-04-18
If this does not work, you can do an easy test to check your NIC card on the laptop. Its called a loop-back test.

You take an extra Ethernet cord, cut the end off. Pull back the coating.

There are 8 wires. 

Brown, White/brown
Blue, White/blue
Orange, White/Orange
Green, White/Green

Strip the ends on the Orange pairs and the green pairs.

Connect Solid Orange to solid Green, and white/green to white/orange

This is a simple loopback. All you do is plug it into your laptop and see if it says connection found or w.e and you should see it start looking for an ip address with the indicator icon.

If this happens you know its a problem with the modem, if not , its your laptop.

It wont break your computer, I just did it on mine to check =)

Brand new Dell.... How brave am I?????

---

### Post by Hakimjo on 2011-04-18
it is a combi thing, with two ethernet to computers, two to TV decoders (Acatel for Belgacom).  I have tried on all positions.  It is a brand new standard installation.  The TV works nicely and so does the wireless internet.  That's why I suspect my ethernet card.  But it too is brand new (Asus motherboard) and had worked just nicely not long ago.  Before what ?  I don't know.  I am up-to-date with Ubuntu 10.10.  Isn't there a command line that would check the situation and tell me what's wrong ?

THE WIRED CONNECTION PROBLEM ALSO APPLIES TO WINDOWS, WHICH I HAVE INSTALLED LATER AND WHICH ALSO HAS PROBLEMS WITH THE D-LINK WIRELESS.  MAYBE WINDOWS HAS DONE SOMETHING BAD TO THE BIOS ?

---

### Post by collisionystm on 2011-04-18
yeah well you do not want to go to deep into commands. Your best bet is to keep it simple. If it does not work in Ubuntu or Windows, it is probably hardware.
1.) Boot into the bios on the computer and check the settings. There is an on/off setting for on board NIC cards.
2.) Plug your laptop into the same place another computer works. If another computer works there and yours doesn't, its your card.
3.) Just because you have lights on the card does not mean the hardware is okay.

---

### Post by collisionystm on 2011-04-18
> **Hakimjo said:**
> THE WIRED CONNECTION PROBLEM ALSO APPLIES TO WINDOWS, WHICH I HAVE INSTALLED LATER AND WHICH ALSO HAS PROBLEMS WITH THE D-LINK WIRELESS.  MAYBE WINDOWS HAS DONE SOMETHING BAD TO THE BIOS ?

Windows did nothing to the bios. It is impossible unless you ran a bios updater program. The bios is locked and the chips can only be unlocked with special protocols and algorithms..but in the event that you did that, you wouldn't be on this forum, would you?? =)

You sir just have a bad NIC card. It happens. Did you make the loop back I suggested? You could be saving yourself alot of WHAT IF's right now.

---

### Post by Hakimjo on 2011-04-18
I have checked with with a laptop.  It makes the right light on the router go ON.  Good.  The Kubuntu on the laptop, however, says that the interface is not supported.  But it odes work nicely with the Windows on that machine.

Pardon me, I did not have the courage to do the Ethernet cable thing yet.

I have looked into the BIOS of the desktop having problems, but have not found anything that looks like a NIC on/off.

I don't think the card itself is spoiled, since it is new and has worked very well.  Hence, I might just try a BIOS default reset ?

---

