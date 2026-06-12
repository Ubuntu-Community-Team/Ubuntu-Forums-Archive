---
title: "USB Wireless Not Working (Realtek RTL8187L)"
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by angelkiller on 2009-09-20
Ok, I have this spare machine I'm trying to get connected to the internet. So I bought a cheap usb adapter off someone. It's [one of these](http://www.amazon.com/Wireless-802-11g-Adapter-2-4ghz-Output/dp/B000ZK2V48). Here's a pic of [the actual Realtek chip](http://img.techpowerup.org/090920/IMG_2700.resized.jpg).

I can't get this thing connected to the internet for the life of me. Ubuntu recognizes the card, but no connections. The closest I've gotten is having the Gnome-Network-Manager tell me it was connected to my network, but it had 0 bars and under 'Connection Info' the IP settings were not correct nor could I actually connect to the internet.

At this point, I'm not sure what to try. I've found numerous threads around on the internet, but no solution has worked for me. I know I haven't listed the many things that I've tried, but if you ask, I'll answer.

THANKS! :)

lsusb output:
```
user@MusicPC:~$ lsusb
Bus 001 Device 007: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 011: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by Crafty Kisses on 2009-09-20
From my knowledge this card should be supported out of the box with the newer kernels. Have you checked to see if the RTL module is running? What are the results of the following?
```
lsmod | grep rtl8187
```
If it that finds nothing, then you might want to try loading the module manually by running as root:
```
modprobe rtl8187
```

---

### Post by angelkiller on 2009-09-20
```
user@MusicPC:~$ lsmod | grep rtl8187
rtl8187                53376  0 
mac80211              217592  1 rtl8187
eeprom_93cx6           10240  1 rtl8187
cfg80211               38288  2 rtl8187,mac80211

```
I assume it found something..?

I've also read that it should be supported out of the box. This is 9.04 btw.

---

### Post by Crafty Kisses on 2009-09-20
Well according to that output the kernel has loaded the modules. What happens when you try running?
```
iwlist wlan0 scan
```

---

### Post by angelkiller on 2009-09-20
```
user@MusicPC:~$ iwlist wlan0 scan
wlan0     No scan results
```

---

### Post by Crafty Kisses on 2009-09-20
Hmm. What are the results of the following?
```
uname -r
```
Then I'd also like to know what version of Ubuntu you are using.

---

### Post by angelkiller on 2009-09-20
```
user@MusicPC:~$ uname -r
2.6.28-15-generic
```

This is Ubuntu 9.04.

---

### Post by Crafty Kisses on 2009-09-20
Hmmm, what are the results of the following?
```
lspci
```

---

### Post by angelkiller on 2009-09-20
```
user@MusicPC:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
```

It's an USB network adapter... Shows up using 'lsusb', which is in my first post.

---

### Post by Crafty Kisses on 2009-09-20
Well, let's try and use the compat wireless package. So first what you want to do is actually get the source, so run:
```
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.30/compat-wireless-2.6.30.tar.bz2
```
Then you need to extract it:
```
tar xvjf compat-wireless-2.*
```
Then you need to navigate to where you saved it (I'm using the Desktop for this example):
```
cd /home/username/Desktop/compat*
```
Then do the initial compile:
```
make
sudo make install
```
If you get any make errors make sure you have the build-essential package installed, you can install it by running:
```
apt-get install build-essential
```

---

### Post by angelkiller on 2009-09-20
> **Codename said:**
> Well, let's try and use the compat wireless package. So first what you want to do is actually get the source, so run:
```
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.30/compat-wireless-2.6.30.tar.bz2
```
Then you need to extract it:
```
tar xvjf compat-wireless-2.*
```
Then you need to navigate to where you saved it (I'm using the Desktop for this example):
```
cd /home/username/Desktop/compat*
```
Then do the initial compile:
```
make
sudo make install
```
If you get any make errors make sure you have the build-essential package installed, you can install it by running:
```
apt-get install build-essential
```

Ok, no errors. The last thing 'sudo make install' ouput was this:
```
Now run:

make unload

And then load the wireless module you need. If unsure reboot.
```
Do I do that? If I do, how do I load the correct wireless module? Or should I just reboot like it says?

Thanks for everything so far. :)

---

### Post by Crafty Kisses on 2009-09-20
Haha you don't have to thank me. ;-) You can just reboot, then once you reboot you probably want to run:
```
sudo modprobe rtl8187
```

---

### Post by angelkiller on 2009-09-20
```
user@MusicPC:~$ sudo modprobe rtl8187
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
```
Does that mean it worked or it didn't?

---

### Post by Crafty Kisses on 2009-09-20
Well I'm pretty sure you can resolve that issue by making:
```
/etc/modprobe.d/blacklist
```
To:
```
/etc/modprobe.d/blacklist.conf
```
Try that, then reboot then try to reload the module by using modprobe.

---

### Post by angelkiller on 2009-09-20
Ok so 'sudo modprobe rtl1817' gave no errors nor output. Now what?

---

### Post by Crafty Kisses on 2009-09-21
Try and run your wireless card. So you can try running:
```
sudo ifdown wlan0
sudo ifup wlan0
```

---

### Post by angelkiller on 2009-09-21
```
user@MusicPC:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
user@MusicPC:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
```
Hm. :(

---

### Post by Crafty Kisses on 2009-09-23
What are the contents of the following?
```
cat /etc/network/interfaces
```

---

### Post by angelkiller on 2009-09-23
```
user@MusicPC:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

---

