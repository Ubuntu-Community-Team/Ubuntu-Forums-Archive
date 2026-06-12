---
title: "Dell Latitude 2100 Ubuntu 12.04 wireless problem ..."
date: 2013-08-20
forum: Networking &amp; Wireless
---

### Post by machine-claudius on 2013-08-20
Colleagues ...

Since 10.04 LTS, I have had no problem on my Dell Latitude 2100 netbook  with a wireless connexion. And when I upgraded to 12.04, still no  problems ... until today. Now I can't connect to the Internet via my  wireless configuration.

Ubuntu keeps prompting me (Authentication dialog) for the password (which  I have always used) and yet it still can't connect via the wireless  router. Even though my Windows XP Home Acer netbook has no problem doing  that.
[INDENT]**[FONT=courier new]lspci -nn | grep 0280:[/FONT]**
[FONT=courier new]0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)[/FONT]

**[FONT=courier new]lsusb:[/FONT]**
[FONT=courier new]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader[/FONT]
[/INDENT]

Thanks for any help ...
Dave Cooper
Roermond
The Netherlands

---

### Post by chili555 on 2013-08-20
Let's see which driver is installed:```
lsmod | grep -e wl -e b43
```And if there are interesting clues in the message log:```
dmesg | grep -e wl -e b43
```

---

### Post by machine-claudius on 2013-08-21
Chili555 ...

Excuse my time delay; out here in the forests of the Ancient Franks, we are in your future: 9 - 10 hours ahead of New World time ...

[FONT=courier new]**lsmod | gre[ -e wl -e b43:**
wl               2906597  0
cfg80211          178877  1 wl
lib80211           14040  2 lib80211_crypt_tkip,wl[/FONT]

[FONT=courier new]**dmesg | grep -e wl -e b43:**
[   20.936134] wl: module license 'MIXED/Proprietary' taints kernel.
[   21.060744] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.060763] wl 0000:0c:00.0: setting latency timer to 64
[   21.087468] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[/FONT]
Regards ...

Dave Cooper
Roermond
The Netherlands

---

### Post by chili555 on 2013-08-21
And probably ahead in many other ways, as well!

Please get a temporary wired ethernet connection and open a terminal:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-lpphy-installer
```Detach the ethernet cable, reboot and let us hear your report.

---

### Post by machine-claudius on 2013-08-21
chili555 ...

Give me an hour or so ... I must hop my bicycle and go fetch dinner.

Groetjes ...

---

### Post by machine-claudius on 2013-08-21
chili555 ...

I complete the procedures as instructed (remove purge of the [FONT=courier new]bcmwl-kernel-source[/FONT], install of the [FONT=courier new]firmwave-b43-lpphy-installer[/FONT], and reboot) but alas, attempts to connect to the wireless does exactly the same as before: I am prompted for a password or encryption key either of which fails to make a connexion. (By the way, if I try and change the *Key *from the encryption key to the password, then the *Connect *button becomes unavailable). If I just accept the encryption key which is there by default, the *Connect *button is available, but clicking it does not give me a connexion. The authentication dialog is just presented again. No wireless connexion is achieved.

BTW ... the following occurred during the [FONT=courier new]sudo apt-get remove[/FONT] operation:
A message saying the following automatically installed packages are no longer required:
[FONT=courier new]linux-headers-3.2.0-40 firefox-globalmenu
linux-headers-3.2.0-40-generic dkms[/FONT]
I was instructed to use '[FONT=courier new]apt-get autoremove[/FONT]' to remove them.

When I confirmed to go ahead with the operation ('*y*') at the end of the operation, I got the following warnings:
[FONT=courier new]cryptsetup: WARNING: failed to detect canonical device of /dev/sda1[/FONT]
and
[FONT=courier new]cryptsetup: WARNING: could not determine root device from /etc/fstab[/FONT]

BTW ... the following occurred during the [FONT=courier new]sudo apt-get install[/FONT] operation:
The same warnings about the linux-header packages no longer needed (as above in the remove operation).
And that the [FONT=courier new]b43-fwcutter[/FONT] was installed as an *extra*
And that the [FONT=courier new]b43-fwcutter-firmwave-b43-lpphy-installer[/FONT] was installed as *NEW*

I am bracing myself for what I think you might say next ...

Regards ...

Dave Cooper
Roermond
The Netherlands

---

### Post by chili555 on 2013-08-21
Let's bifurcate the problems. As for this:```
When I confirmed to go ahead with the operation ('y') at the end of the operation, I got the following warnings:
cryptsetup: WARNING: failed to detect canonical device of /dev/sda1
and
cryptsetup: WARNING: could not determine root device from /etc/fstab

```I suggest you ask over on General Help. It is beyond my narrow area of (?) expertise. I doubt it has any significant bearing on the wireless.

Next, let's see what the wireless is doing under the hood (bonnet?):```
dmesg | grep -e 80211 -e wl -e b43  | tail -n25
```I am quite sure that Network Manager is seeking your WPA2 encryption key. I'd back out whatever is there now and re-enter what you are confident is the correct key.

---

### Post by machine-claudius on 2013-08-21
chilli555 ...

I am going to uncouple from these computers up in the loft, and end my day (it is 21:16 here). I will pick up on this tomorrow. I appreciate you help! I will take a fresh look at this and get back to you. (I think you are write about the cryptsetup warnings ... not being germane to wireless).

Tot kijk ...

Dave Cooper
Roermond
The Netherlands

---

