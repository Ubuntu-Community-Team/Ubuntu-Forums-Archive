---
title: "Xubuntu 11.04 drivers installed but no wireless on Acer Extensa 5220 laptop"
date: 2011-07-17
forum: Networking &amp; Wireless
---

### Post by Rytron on 2011-07-17
Hi.

I installed Xubuntu 11.04 today on my Acer Extensa 5220 laptop. The drivers are installed but I cannot get wireless with the built in wireless card. I could get wireless with my D-Link USB dongle though (I need that for my desktop).

This is odd as I've not had a wireless problem with that laptop with Ubuntu based distros for a very long time.

In 'Additional Drivers' window it says "This driver is activated and currently in use"

---

### Post by chili555 on 2011-07-17
Please open a terminal and run and post:```
rfkill list all
lsmod | grep -e acer -e b43 -e wl

```Thanks.

---

### Post by Rytron on 2011-07-18
> **chili555 said:**
> Please open a terminal and run and post:```
rfkill list all
lsmod | grep -e acer -e b43 -e wl

```Thanks.

Hi chili555. Here is the output [image attached].

---

### Post by chili555 on 2011-07-18
The wireless is not blocked and the module wl is loaded and no other conflicting drivers are loaded. So far, so good! Let's be certain that wl is correct for your device:```
lspci -nn | grep 0280
dmesg | grep -e wl -e eth1
```Thanks.

---

### Post by Rytron on 2011-07-18
> **chili555 said:**
> The wireless is not blocked and the module wl is loaded and no other conflicting drivers are loaded. So far, so good! Let's be certain that wl is correct for your device:```
lspci -nn | grep 0280
dmesg | grep -e wl -e eth1
```Thanks.

Output:
```
:~$ lspci -nn | grep 0280
04:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
rytron@AcerE:~$ dmesg | grep -e wl -e eth1
[   23.529111] wl: module license 'MIXED/Proprietary' taints kernel.
[   24.001746] wl 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   24.001756] wl 0000:04:00.0: setting latency timer to 64
```

---

### Post by chili555 on 2011-07-18
I believe the driver b43 and its associate ssb are correct for your device, not wl.> Broadcom Corporation BCM4311 802.11b/g WLAN [[COLOR="Red"]14e4:4311[/COLOR]] (rev 01)As a temporary measure, please do:```
sudo rmmod -f wl
sudo modprobe b43
```If your wireless springs to life, we'll tweak a couple of files and you'll be all set.

If not, please post:```
ls /lib/firmware/b43
```Thanks.

---

### Post by Rytron on 2011-07-18
After I ran
```
sudo rmmod -f wl
sudo modprobe b43
```
I clicked on network icon and next to wireless it said "Wireless Networks device not ready (firmware missing)"
So I went back to look at 'Additional Drivers' window and it now says "This driver is activated but **not** currently in use"

```
ls /lib/firmware/b43
```
gave this
```
ls: cannot access /lib/firmware/b43: No such file or directory
```

---

### Post by chili555 on 2011-07-18
Do you have an available ethernet connection? Please do:```
sudo apt-get install b43-fwcutter
```Then try again:```
sudo rmmod -f b43
sudo rmmod -f wl
sudo modprobe b43
```

---

### Post by Rytron on 2011-07-18
I installed **b43-fwcutter**.

No error from other commands except **sudo rmmod -f wl** gave this
```
ERROR: Removing 'wl': No such file or directory
```

**ls /lib/firmware/b43** still gives
```
ls: cannot access /lib/firmware/b43: No such file or directory
```

:confused:

---

### Post by chili555 on 2011-07-18
Another try before I turn in my scalpels:```
sudo apt-get install firmware-b43-installer
sudo rmmod -f b43
sudo modprobe b43
```If it works, we will still need a small tweak to make it persistent.

---

### Post by Rytron on 2011-07-19
> **chili555 said:**
> Another try before I turn in my scalpels:```
sudo apt-get install firmware-b43-installer
sudo rmmod -f b43
sudo modprobe b43
```If it works, we will still need a small tweak to make it persistent.

You did it! Fair play to you. :)

This line gave the following output:
```
sudo rmmod -f b43
ERROR: Removing 'b43': No such file or directory
```

The internal wireless card works now though.

What is the final step?

---

### Post by chili555 on 2011-07-19
The final step is that the installation of the other driver wl blacklists b43 and ssb. Let's fix that so the correct driver b43 loads on boot with no terminal commands. Please do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo gedit /etc/modprobe.d/blacklist.conf
```Look in the file we are editing and make sure there is no sign of blacklists for b43 or ssb. If there are, remove them, proofread, save and close gedit. Next do:```
sudo gedit /etc/modules
```At the end, add one line:```
b43
```Proofread, save and close gedit. You should be all set.

Finally, use thread tools at the top to Mark Solved.

---

### Post by Rytron on 2011-07-19
Thank you very much chili555.

Just a few side notes: for **sudo rm /etc/modprobe.d/blacklist-bcm43.conf** I got this reply
```
rm: cannot remove `/etc/modprobe.d/blacklist-bcm43.conf': No such file or directory
```

and for **sudo gedit /etc/modprobe.d/blacklist.conf** instead of removing I just added a # in front of references to **b43** and **ssb**.

You are a star. :popcorn:

---

### Post by chili555 on 2011-07-19
> Just a few side notes: for sudo rm /etc/modprobe.d/blacklist-bcm43.conf I got this reply
Code:

rm: cannot remove `/etc/modprobe.d/blacklist-bcm43.conf': No such file or directoryExcellent. That just means --purge did its job. It does no harm to double-check. I'm glad it's sorted now.

---

### Post by ssuuddoo on 2012-01-04
thnx, excellent help. works.
ubu 11.10, 32-bit, ACER Extensa 5220

---

### Post by cartisdm on 2012-03-25
> **ssuuddoo said:**
> thnx, excellent help. works.
ubu 11.10, 32-bit, ACER Extensa 5220

There's nothing like an old thread that still fixes problems.  Just revived my old Acer as well!

---

### Post by robhills on 2012-07-25
Worked for me too! :guitar:

Obvious, but needs a restart at the end.

---

