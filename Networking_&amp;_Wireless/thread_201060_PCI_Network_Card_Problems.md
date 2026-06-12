---
title: "PCI Network Card Problems"
date: 2006-06-21
forum: Networking &amp; Wireless
---

### Post by digitalpardoe on 2006-06-21
I've just installed a PCI network card (wired) into my computer, but it is not being auto-detected and configured on startup.

There were no PCI card installed in the computer when I installed Ubuntu Server and i'm guessing there are modules missing from the kernel.

This is the content of /etc/modules;

```


# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse


```

What do I need to add to get the PCI Network card to be autodetected and configured at start up. Assuming this is the right place.

---

### Post by linuchsan on 2006-06-21
What kind of card is it?

---

### Post by digitalpardoe on 2006-06-21
It's a Sitecom 10/100 Mbps that's marked up as Linux comptible on the box

It was in another computer and was automatically detected and set up when I installed Debian Sarge so I assume it is Linux compatible.

The motherboard it is installed on is one of the original VIA EPIA Mini-ITX motherboards.

---

### Post by digitalpardoe on 2006-06-21
It could be one of three chipsets Realtek 8139, Sitecom or ADMtek.

---

### Post by linuchsan on 2006-06-21
What does lspci say?

---

### Post by digitalpardoe on 2006-06-21
lspci reads;

```

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8601 [Apollo ProMedia] (rev 05)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8601 [Apollo ProMedia AGP]
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8231 [PCI-to-ISA Bridge] (rev 10)
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1e)
0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1e)
0000:00:11.4 Bridge: VIA Technologies, Inc. VT8235 ACPI (rev 10)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 40)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 51)
0000:00:14.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i1 (rev 6a)

```

The ethernet is: 0000:00:14.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11).

So it is being detected and 'tulip' is being loaded which is the correct driver as far as I know. I must need to do some setting up somewhere.

Is there anyway to find the MAC address of the network card whilst it is inside the machine and is not set up? The address isn't in the manual, on the box or on the card itself.

---

### Post by digitalpardoe on 2006-06-21
I now know that is not a problem with the card. I found a monitor to borrow for 5 minutes and booted the live CD. Both interfaces were detected and I got the MAC addresses for both. I then tried to add eth1 which would be my PCI network card in Webmin and nothing. I just got errors.

---

### Post by bscbrit on 2006-06-21
"Does the card / eth1 show in System -> Administration -> Networking?"

Disregard my stupid question - you are running Server so you haven't got the menu!

---

### Post by bscbrit on 2006-06-21
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

This thread should give you a guide to setting up your network from the command line.

Sorry about my previous post - I didn't have my brain switched on!!!

---

### Post by digitalpardoe on 2006-06-21
Thanks, I've got it sorted with the help of that guide. Everything was installed OK I just didn't realise I had to set the ethernet to UP (I thought it was already done) and get and get the IP over DCHP (I thought it would do it itself over DCHP). Thanks again. I'm all sorted now.

---

### Post by javahog on 2008-04-22
Hello could you repost the link to the guide again or the updated link that got your card working? The link does not work any more.

I have replaced a worn out PCI nic card with a 3Com and it works with a new install but how do I configure the new card on the existing system?
Using: 
DSL
Linksys router (set as dhcp server for LAN)
I see ubuntu on the linksys routers dhcp list with an IP...?

thanks

---

### Post by Vic Morgan on 2008-05-01
> **javahog said:**
> Hello could you repost the link to the guide again or the updated link that got your card working? The link does not work any more.

I have replaced a worn out PCI nic card with a 3Com and it works with a new install but how do I configure the new card on the existing system?
Using: 
DSL
Linksys router (set as dhcp server for LAN)
I see ubuntu on the linksys routers dhcp list with an IP...?

thanks

Ditto - It would be helpful if the link worked.

---

### Post by acy76 on 2008-07-22
Hello all -- I was recently having a similar problem and managed to find a good post on another forum, as the link in this thread appears to be dead:

[click here]("http://www.linuxquestions.org/questions/linux-hardware-18/ethernet-card-not-recognized-ubuntu-server-620339/")

Hope this is of some help to someone.

---

