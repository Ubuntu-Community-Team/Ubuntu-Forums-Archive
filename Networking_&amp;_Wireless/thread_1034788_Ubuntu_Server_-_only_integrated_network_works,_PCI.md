---
title: "Ubuntu Server - only integrated network works, PCI card's not"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by pkovak on 2009-01-09
I have tried for several days now to fix this and no luck:
I installed Ubuntu Server Edition on PC1 (AMD64 CPU), i386 distribution. Internet worked fine, no problem there. Updated all packages, installed generic kernel, because the target platform I want Linux to use is based on old P150.
Then I unpluged HDD, moved to P150, powered up, and selected generic kernel in GRUB.
Everything I saw works fine except network, ifconfig returns only "lo" interface.
/etc/network/interfaces :
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.254
As I said, this setting worked perfectly for integrated network, P150 does not have it, only PCI cards.
When I try ifconfig eth0 I get responce that eth0 is not there.
I have tried this with 3 PCI network cards:
1) 8139C revision 10 Realtek
2) 3COM 3C905C-TX-M
3) 3COM - there is a text on chip, reads 3COM 40-0196 etc.
I found 3Com cards cards on [http://www.idhw.com/textual/chip/3com/chippicture.html](http://www.idhw.com/textual/chip/3com/chippicture.html) if you want to look how chip looks.

lspci gives back similar names, so it looks good.
When Realterk 9139 is plugged in, Linux loads 8139cp and 8139too drivers - to prevent conflicts, I unloaded them with modprobe -vr 8139cp; modprobe -vr 8139too;
Then I tried to load 8139cp and in verbose mode got responce that it may not work with this revision and I should use 8139too, so I unloaded driver again and loaded 8139too, no error message. After that, I tried
/etc/init.d/networking force-restart , again, eth0 is not found.
Turned of PC, unpluged Realtek and tried it with 3COM 3C905C - this time driver 3c95x was loaded, again, eth0 not found.
I am not sure what driver if any was loaded for third card, but again, does not work.
I moved the HDD back to AMD64 based PC and tried all 3 network cards again, even with integrated network disabled in BIOS. Results are same, eth0 not found.
Oh and when 8139too driver failed, I tried 8139cp again of course, eth0 not found.

What I am missing? What tests and changes I should do to make it work? Prior to that, I had no problems with Ubuntu. If needed, I will copy-paste what you want. I don't want to switch to Debian or other distro simply because of this...

---

