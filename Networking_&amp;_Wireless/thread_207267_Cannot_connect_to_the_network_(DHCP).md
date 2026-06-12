---
title: "Cannot connect to the network (DHCP)"
date: 2006-07-01
forum: Networking &amp; Wireless
---

### Post by Pyro MX on 2006-07-01
Hi,

I recently recieved my Kubuntu 6.06 CDs, so I took it for a test run before installing it. Everything worked pretty fine, except for the networking. It. I was a bit frustrated - especially that I am on a wired network. It was doing the same thing in Ubuntu 5.10 with the wireless networking with wpasupplicant, but now with Kubuntu 6.06 even the wired network isn't working.

There's a couple of things like "No IPv6 routers" and "No DHCP offers" that appears in the log. I am connected to a 3Com OfficeConnect switch, which is linked on a 3Com OfficeConnect router. There's another computer with Ubuntu 5.10 installed on it and it is connected, no problems with it. My brother uses Suse 10.1 on yet another computer, and it works fine too. But then there's my computer :lol: , which isn't able to connect (not in Kubuntu 6.06 at least, network runs fine in Windowx XP).

Well, is there a simple, easy way to make the network in Kubuntu 6.06 with DHCP? Because I saw multiple threads having this issue. I've read pages and pages of this and it seems that no actual fix has been found. Some methods work, some don't. What should I do :confused:

---

### Post by Pyro MX on 2006-07-02
Tryed Kubuntu on my friend's computer, he has a D-Link router, everything works fine.

By the way, I have a NVIDIA nForce networking controller. Is there any problem with this one in Linux?

And... bump...

---

### Post by mips on 2006-07-02
Disable IPv6 in Ubuntu. Just search here for IPv6

---

### Post by Pyro MX on 2006-07-02
[QUOTE=mips]Disable IPv6 in Ubuntu. Just search here for IPv6[/QUOTE]

Thx, I'll try that out for sure. :) 

But in [the method I found]("http://ubuntuforums.org/showthread.php?t=202838&highlight=ipv6+disable"), the system needs to be rebooted. I run on the Live CD and I don't want to install a system that isn't able to work with a wired connection. I know that what needs to work for me in the future is wireless with WPA, but if the system is not even able to connect through wired connection, I won't even bother lol,  I don't see how it could work better with wireless!

Anyway, is there a method to disable IPv6 without rebooting the system?

PS: Can IPv6 actually prevent my computer to connect on the network anyway?

---

### Post by mips on 2006-07-02
Try configuring static IP address, Subnet mask, gateway & DNS servers and see if you can then connect to the net.

---

### Post by Pyro MX on 2006-07-03
I tryed to configure the network connection for Static IP, and it is still unable to connect to the network. When I ping the router, it says "Destination host unreachable".

---

### Post by Fedup on 2006-07-03
[QUOTE=Pyro MX]
By the way, I have a NVIDIA nForce networking controller. Is there any problem with this one in Linux?
[/QUOTE]

Yup - certainly seems there's problems with nForce motherboards.

---

### Post by Pyro MX on 2006-07-03
[QUOTE=Fedup]Yup - certainly seems there's problems with nForce motherboards.[/QUOTE]

Lucky me! Especially it's a brand new computer! ;) I tought it would work better with Kubuntu! Oh well, the other 4 I gave the CDs were pretty happy at least! The only one that is not in the whole batch is me lol! What an unexpected situation:cry: .

**But**, I won't give up. If anybody has suggestions, go ahead! Even if it takes 3 pages of talking... I went through all this for the wireless before!

---

### Post by Fedup on 2006-07-03
[QUOTE=Pyro MX]Lucky me! Especially it's a brand new computer! ;) I tought it would work better with Kubuntu! Oh well, the other 4 I gave the CDs were pretty happy at least! The only one that is not in the whole batch is me lol! What an unexpected situation:cry: .

**But**, I won't give up. If anybody has suggestions, go ahead! Even if it takes 3 pages of talking... I went through all this for the wireless before![/QUOTE]


You could disable the onboard ethernet and plug on a PCI card.. I might have to try that myself until things get fixed :neutral:

---

### Post by Pyro MX on 2006-07-03
Good idea, but I already have a wireless card installed in it and I put up enough money on my compter for now lol. I know that an ethernet card doesn't cost a lot, but also there's only one PCI and one PCI Express slot left on my board. I want to keep'em for more important stuff I could install later.

I'll test Kubuntu 6.06 for the wireless network with WEP soon and get my stuff ready with it and install the needed packages to make it work with WPA (let's hope it's not as complicated as in 5.10). I don't believe it can work better for the wireless if I'm not even able to connect with the wired connection lol! But if it works, well it would be fine. Just inconveniant for the next month since the wireless router will be gone soon. But I will dual-boot. Need windows for my games and scanner anyway.

But keep the suggestions coming! I'd really like that stuff working!

---

### Post by mips on 2006-07-05
Which motherboard & nForce chipset do you have. I also have a nForce MB which has two onboard lan cards, one nforce and the other marvell. I have problems with the marvell one but the nforce one works fine.

---

### Post by Pyro MX on 2006-07-05
I'll have to check that. I have a nvidia chipset that's for sure, but I don't know which one.

Well, my brother installed, against my will, SUSE 10.1, saying that "it could manage the drivers better than Kubuntu". Network still doesn't work and the clock speed of my computer is monitored at 1ghz, and it's a AMD64 3400+ 2.2Ghz. Needless to say I'm not happy of his move. Fine distro that's for sure, but it didn't fix anything and I'm way more familiar with the Ubuntu system. I don't like having distro-custom versions of programs (They change the name of the programs, change stuff in it and I'm getting lost...)

That said, my brother have a spare 3Com network card and one RealTek. We'll try that real soon. Phew... and if it works, I'll have back my Kubuntu. I'll get you back with my mobo info and the results with the new network card.

Side question here, between SUSE 10.1 and Kubuntu 6.06, which one will handle the wireless (especially with WPA) networking better?

---

### Post by Pyro MX on 2006-07-11
Fixed networking. Now there's another frickin problem (I think I start to turn red...) the Nvidia drivers aren't working and X doesn't work anymore. GAH! Gonna make another thread for this one.

---

