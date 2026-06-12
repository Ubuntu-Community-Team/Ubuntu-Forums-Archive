---
title: "Enable wireless support - Ubuntu Server 8.10"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by Millzy on 2008-12-28
If i have this right wireless networking is disabled in Ubuntu Server by default. (correct me if i'm wrong).

How can i enable the existing wireless support that comes with the Ubuntu Server CD distro (8.10)?

My card which is atheros pcmcia based runs perfect off the latest live Ubuntu desktop distro (8.10), it has also been tested in the latest DSL distro. 

So i'm hoping its just a module that needs to be run or installed to the server to get the card running.

Can anyone help..?

---

### Post by kevdog on 2008-12-28
Depending on the chipset of your atheros card, it is either going to require the madwifi kernel module or ath9k module.  If you have the ability to initially use a wired connection, you more than likely will be prompted for download of these modules.  If not madwifi is part of linux-restricted-modules.  I believe ath9k is included in the kernel if you are using Intrepid.

---

### Post by Millzy on 2008-12-29
Thanks Kev,

I did try the linux-restricted-modules with semi success.

The card appeared in iwconfig, I then configured the card with iwconfig & ifconfig as i have done before with DSL & Ubuntu Desktop Intrepid 8.10.

#conf (assuming i'm root)
iwconfig ath0 mode managed essid "My WAP" key XXXXXXXXXX
ifconfig ath0 10.1.1.2 broadcast 10.255.255.255 netmask 255.0.0.0 up
route add default gw 10.1.1.1

The card then appeared to connect(card lights indicate an established connection) but on trying to ping my WAP @ 10.1.1.1 instead of success i get the "Operation not permitted" response.

Given that the above config works in other distro's i thought it might be something to do with Ubuntu Server itself. I have heard ppl talking about blacklists, is it possible that the ath driver is being restricted some how?

I will try the madwifi module when i get home and see if i get any success.

---

### Post by kevdog on 2008-12-29
Ok, seems like you have done this before.

So I can skip a couple of steps

The linux-restricted-package has a bunch of drivers, but one of them is madwifi -- so I believe you are already using madwifi.

If you list
lspci -nnm
lshw -C network

That will give more details about your card.

Blacklists enabled? I doubt it.

lsmod will list all the currently loaded modules.  To prune it down:
lsmod | grep ath

Seems like your wireless card invocation is correct as far as the manual configuration.
Did you check dmesg for errors?

---

### Post by Millzy on 2008-12-29
Thanks Kev,

Haven't yet, i was hoping i would get pointed in the right direction.

I will try lsmod to check for madwifi and dmesg for any errors.

Hopefully i will reply back with a smiley!

---

### Post by kevdog on 2008-12-29
The madwifi driver is known as ath_pci or ath-pci -- I can't remember exactly.  Just an FYI

---

### Post by Millzy on 2008-12-29
Ok,

Did the checks and found the drivers using lsmod, so that was ok. Also did the dmesg and found the cards info, everything looked fine there to.

I then decided to remove and re-install the linux-restricted-modules package, reboot, login, setup the wifi card again with the same parameters using iwconfig & ifconfig and low and behold the damn thing worked.

So i'm not 100% sure what it was stopping the card from picking up my adsl router @ 10.1.1.1

The only thing i can think of that i had done after installing the restricted-modules was setting up masquerading, so that is possibly the cause of the problem. But i'm no linux guru.

---

