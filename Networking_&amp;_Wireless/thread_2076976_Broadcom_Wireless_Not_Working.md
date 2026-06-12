---
title: "Broadcom Wireless Not Working"
date: 2012-10-27
forum: Networking &amp; Wireless
---

### Post by mweber1488 on 2012-10-27
I have netbook that I have put lubuntu 12.10 on (i386). According to what I can find it should work out of the box but it doesn't.

Running lspci -vnn I get:
```
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 902.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Foxconn International, Inc. T77H106.00 Wireless Half-size Mini PCIe Card [105b:e01b]
    Flags: bus master, Fast devsel, latency 0, IRQ 16
    Memory at 57100000 (64-bit, non-prefetchable) [size=16k]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
```Keeping in mind that I am relatively new to Linux and I don't have easy access to a wired connection, can anybody help me?

---

### Post by chili555 on 2012-10-27
Please see **Installing b43fwcutter With Out An Internet Connection** here: [https://help.ubuntu.com/community/BroadcomSTA%28Wireless%29](https://help.ubuntu.com/community/BroadcomSTA%28Wireless%29)

After you've finished, reboot and let us have your report.

---

### Post by mweber1488 on 2012-10-28
I following the instructions but it didn't work so I followed the link to the forum post at the end and it said this: > If you have a card that reads  Broadcom Corporation BCM4312 802.11b/g [COLOR=Red][SIZE=4][FONT=Arial Black]*LP-PHY*[/FONT][/SIZE][/COLOR] 
you need the **firmware-b43-lpphy-installer** not the firmware-b43-installer But there are no directions on how to get the firmware-b43-lpphy-installer.

---

### Post by chili555 on 2012-10-28
That's a sticky problem. Actually, I hoped the file you downloaded, b43-fw-all contained exactly that: *all* firmware needed. Let's see what is missing according to the message file:```
sudo modprobe b43
dmesg | grep b43
```If I have it, I'll be happy to zip it and send it.

---

### Post by mweber1488 on 2012-10-28
I got:
```
[   11.333861] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   12.880560] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   12.880572] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   12.880581] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
```

---

### Post by chili555 on 2012-10-28
Please download this to your desktop. Right-click it and select Extract Here. Now open a terminal and do:```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/firmware/*  /lib/firmware/b43
```Now we unload and reload the driver so it sees and grabs the firmware:```
sudo modprobe -r b43
sudo modprobe b43
```If it doesn't spring to life, check again:```
dmesg | grep b43
```You will be looking for entries after the timestamps above:> [   [COLOR="Red"]12.880581[/COLOR]] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and ...

---

### Post by mweber1488 on 2012-10-28
```
[ 1589.873916] b43-phy0 ERROR: Firmware file "b43/lp0initvals15.fw" not found 
[ 1589.873929] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
```

---

### Post by chili555 on 2012-10-28
Here is another. Please follow the same process, except you are copying from 'firmware2, and then add:```
sudo mkdir /lib/firmware/b43-open
sudo cp /lib/firmware/b43/*  /lib/firmware/b43-open
```Unload and reload:```
sudo modprobe -r b43
sudo modprbe b43
```Check:```
dmesg | grep b43
```

---

### Post by mweber1488 on 2012-10-28
It works now, thank you for all the help.

---

### Post by chili555 on 2012-10-28
Awesome! Glad it's working. Please use thread tools at the top to mark Solved.

---

### Post by datahh on 2012-12-18
This helped me too!  Thanks so much to you both!

---

### Post by reddevilcanada on 2013-02-21
This works, but every time I reboot I have to run:

sudo modprobe -r b43
sudo modprobe b43

Is there a way to make this permanent?

Thanks!

---

### Post by tcbuchelos on 2014-01-15
Thanks for the solution. I just used it on an HP Mini 110-1155ev and it worked like a charm!

---

