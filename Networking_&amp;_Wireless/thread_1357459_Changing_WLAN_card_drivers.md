---
title: "Changing WLAN card drivers"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by jackvaughn on 2009-12-17
Hi there,

I'm using Ubuntu 9.10 on a fairly old laptop which has an Intersil Prism 2.5 WLAN PCI card in it.

I have updated the card Firmware (via Windows) as advised in another thread.
The card should now support WPA encryption as far as I understand.

However, when the Network Manager applet finds my WPA Personal encrypted wireless network, and the dialog appears, it only gives me the options of WEP encryption (WEP 40/128-bit Key, WEP 128 Bit passphrase, LEAP or Dynamic WEP).

After some digging about, I found that the Prism card is using the orinoco driver, whereas it would be better using the Hostap driver which supports WPA.

How can I change this?

I've tried advice given on other threads including adding the orinoco driver to the banlist (which prevented the laptop from finding the hard disk so had to install Ubuntu from scratch!) and using 
```
modprobe -r orinoco
```
which failed as the driver was in use at the time.

Either way, can anybody help.
I'm something of a Linux novice but have some understanding, but please assume i'm a moron who knows very little.

Thanks in advance

---

### Post by jackvaughn on 2009-12-20
I received the following advice from an Ubuntu user who had a similar problem in another thread...

> [FONT=Prelude]You should simply have to append the following lines to /etc/modprobe.d/blacklist.conf to disable the loading of it:

blacklist orinoco
blacklist orinoco_pci
blacklist orinoco_plx
blacklist orinoco_cs
blacklist hermes
blacklist airport

And then make sure that you have the 'hostap-utils' package installed.
[/FONT]Unfortunately, this had the effect of halting Ubuntu while it was starting up.
Running in recovery mode gave the following output before the machine halted...

```
fsck from util-linux-ng 2.16
/dev/sda6: clean, 153845/289152 files, 700247/1154664 blocks
[    91.270382] BUG: soft lockup - CPU#0 stuck for 61s! [init:1]
```I experienced the same problem last time I tried blacklisting orinoco and the only way to recover was to re-install Ubuntu (remember i'm a novice so there probably was another way but I didn't know what it was).
Last time the machine would halt at around the same place, always while trying to perform operations involving the filesystem (which in this case is ext4). 
I'm not sure why it's having this affect though, and I wonder if this is a totally unrelated problem.

Any help or advice would still be very much appreciated.

---

### Post by jackvaughn on 2010-01-05
Anyone? Please?

---

### Post by jackvaughn on 2010-03-05
OK, after very little help, found out that the only ban required is orinoco_cs
This seems to prevent the orinoco driver from taking control of the Prism WLAN card, without preventing the filesystem from being mounted on reboot.

Having had this problem for sometime, it has become very clear why people don't migrate from Windows to Linux.
The Ubuntu community seems to find it  very difficult to speak in plain English or give simple instructions on even the most basic subjects, making it nearly impossible for anyone who doesn't having a good deal of computing experience to resolve basic problems.

---

### Post by jackvaughn on 2010-03-05
Right, I give up.
Still can't see the wireless network.
Going back to Windows. I may have it's faults but at least it works.

---

### Post by chili555 on 2010-03-05
If you can wait just a few more minutes, let me slip in my Prism card and see what makes it tick. I am pretty sure we can work this out. I will try as hard as I can to speak in clear English.

Please reply if I can help. I will be installing my Prism for a few moments.

---

### Post by chili555 on 2010-03-05
I am back and on line. My details are:```
lsmod | grep orinoco
orinoco_cs             13312  1 
orinoco                63600  1 orinoco_cs
pcmcia                 36808  1 orinoco_cs
pcmcia_core            36528  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
```There are no hostap drivers loaded.```
iwconfig
eth1      Link encap:Ethernet  HWaddr 99:02:6f:09:5a:88 
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:6fff:fe09:5a6f/64 Scope:Link
```There is nothing in blacklist having anything to do with the Prism card. It scans four cells. I do not have Network Manager on this computer, but Wicd.

I will be happy to help you.

---

### Post by chili555 on 2010-03-05
As an experiment, I removed, through Synaptic, *hostapd* and *hostap-utils*. Wicd connects my old Prism perfectly.

---

### Post by pullmandave on 2010-03-09
I too, have the same problem with the hostap drivers in that it hangs my system with the same CPU Hung error. The orinoco drivers do not work for me, which is why I tried the hostap drivers. Also, I'd like to use the hostap utils to upgrade my firmware. I DO NOT have a winblows environment to use for the update.

---

