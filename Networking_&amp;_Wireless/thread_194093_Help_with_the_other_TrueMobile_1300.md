---
title: "Help with the *other* TrueMobile 1300"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by majesticturkey on 2006-06-10
Yeah, I'm sure by now these forums must really hate Dell. I know I do. :p 

Everything went fine with my installation, except for, yeah, my wireless adaptor. I have a Dell TrueMobile 1300 USB 2.0 adaptor. It doesn't use the same chipset (the bc43xx or whatever)...I've tried. I don't know if anyone else knows anything about this. I'll be contacting Dell about getting chipset information soon, I hope.

Anyway, the CD I have has a PRISMA02.SYS and DELLNIC.inf. Naturally, I tried ndiswrapper with these, and no luck. Invalid drivers, it says.

If anyone's got any ideas, I'll love you forever. 8)

---

### Post by majesticturkey on 2006-06-11
I have the drivers installed (I guess), and iwconfig shows eth2 as a wireless adaptor, but it says "Access Point: Invalid"...and in networking there's nothing under ESSID. I think I've almost got it.

---

### Post by majesticturkey on 2006-06-11
Another update.

I did the following to manually connect (all with sudos):
iwconfig eth2 mode Managed
iwconfig eth2 essid ******
dhclient eth2

It whined at me about "no DHCPOFFERS" and "no working leases." It didn't give me internet connectivity, but iwconfig does show an access point. Network Tools also shows my wireless network as an ESSID, which I selected.

I have a feeling it just requires a restart of the network, but I figured I'd still blog what's up, in case anyone else needs help.

---

### Post by masinger53 on 2006-06-12
Majesticturkey, thank you for this post.  I spent many hours this weekend on IRC, Google & forums trying to get wireless working on my laptop before I found this thread.  Config:   Dell Inspiron 9100, 512G RAM, 60Gb HDD, ATI Radeon Mobility 9600, Dell Truemobile 1350, which has BCM4306 chipset, fresh install of Xubuntu Dapper/dual-boot with WinXP  

I'm not sure why putting things in their proper places in /etc/network doesn't work, but at this point, if brute force gets the job done, then <shrug> -- even the hardest-core geek sometimes just want things to work, dammit.

Posting this reply from said laptop where everything worked out of the box -- including sound, touchpad, touchstick, USB PocketMouse, USB flash drive -- except for the PITA wireless (formerly a Gentoo 2006.0 partition built from a stage 1 developer's method install).

If I can get VPN working with Remote Desktop to my WinXP box at work, then I may finally be able to ditch the Windoze partition for good.

Thanks again  =)

---

