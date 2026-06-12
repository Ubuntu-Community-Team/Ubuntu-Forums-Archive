---
title: "Onboard nic not detected (Intel 915g)"
date: 2005-03-15
forum: Networking &amp; Wireless
---

### Post by tablatom on 2005-03-15
Hi,

I just installed hoary, and all is good but for networking. During install I got a message that the network could not be detected, and there's no ethernet card in the "Network settings" applet (System->Administration->Networking).

The NIC is built in to the motherboard, an Asus P5GDC-V (Intel 915g chipset).

lspci gives:

0000:02:00.0 Ethernet Controller: Marvell Technology Group Ltd.: Unknown Device 4632 (rev 15)

I first installed warty, and had the same problem, but I found a fix - I just hit the "Add" button in "Network settings" and it found it. Annoyingly, that button is no longer present in hoary :-(

Any ideas much appreciated.

Tom.

---

### Post by GilGalad on 2005-03-15
Try "sudo modprobe sk98lin" and look  at the output of dmesg (or if it is already loaded "sudo rmmod sk98lin; sudo modprobe sk98lin).

---

### Post by tablatom on 2005-03-15
Thanks.

"modprobe sk98lin" seems to do nothing, I guess it's already there.

"rmmod  sk98lin" gives a seg-fault! 

There's alreay a message in dmesg that looks relevant, before I do this:

eth%d: - - ERROR - -
    class: Internal Software Error
    Nr: 0x2bd
    Msg: TWSI: transdfer does not complete

Then, after the seg-fault, dmesg has:

Unable to handle kernel NULL pointer dereference at virtual address 00000230
 printing eip:

...

Then a whole load of very low-level stuff, stack trace etc. I guess you don't wanna  see all that!


This is a fresh hoary install.

T.

---

### Post by GilGalad on 2005-03-15
Yeah I have a similar (maybe the same) card judging from your output. The sk98lin module in the kernel is a bit outdated. I installed the latest driver from sysknonnect (attached) and the nic is working now.

---

### Post by tablatom on 2005-03-15
[QUOTE=GilGalad]Yeah I have a similar (maybe the same) card judging from your output. The sk98lin module in the kernel is a bit outdated. I installed the latest driver from sysknonnect (attached) and the nic is working now.[/QUOTE]
 This post comes to you from a freshly network enabled Ubuntu system :-)

Thanks very much.

---

### Post by Corné van de Pol on 2005-05-12
Hello,

I am new in the Linux world and I have exactly the same problem as you (GilGalad and tablatom). I know that this topic is quite old but I hoped if you, or somebody else, could tell me what you did exactly.

I have the same NIC and the same messages in the dmesg so I downloaded the same drivers but I don't know how to install them properly. And my computer is quite useless without a netwerk connection.

Thanks in advance.

Corné

---

### Post by Rxke on 2005-06-12
Hi, Corné,

Have you downloaded the file GilGalad linked to?
it contains a readme file, have you unpacked and looked into the folder, and what did you not understand?

---

