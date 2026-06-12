---
title: "linux wireless is cracking my head"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by shif on 2010-11-29
im new to linux, i just installed ubuntu along with windows, the only problem was that wireless didnt worked, i searched the internet and found about ndiswrapper, i followed this guide [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") and here are some of my results

[IMG]http://traynet.com/Screenshot1.png[/IMG]

the graphic ndis tells me that the hardware is present and that it correctly installed

and when i run iwconfig i get
```

arosemena@Shif-LINUX:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

my wireless still says that the device isnt active and i cant figure out what to do next, help please

---

### Post by TBABill on 2010-11-29
What device is it? Looks like a Broadcom but can you post the output of ```
lspci
``` from a terminal? That will identify not only the chip mfr, but also the specific type. You may not have needed to use ndiswrapper, but we'll see what the output is so we can go on from there.

---

### Post by Kernelingus on 2010-11-29
TBABill's assuming you're talking about a built-in adaptor.  If it's a USB, instead do:

```
lsusb
```

---

### Post by shif on 2010-11-29
i get this 
```
arosemena@Shif-LINUX:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


```

sorry if i take long to answer i need to jump to linux and then back to windows to access internet

---

### Post by shif on 2010-11-29
i got the drivers i installed from here
[http://pryds.eu/ubuntu/7.04.php]("http://pryds.eu/ubuntu/7.04.php")

my laptop is an inspiron 1300

---

### Post by shif on 2010-11-29
i ran this if its of any help

```
arosemena@Shif-LINUX:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

arosemena@Shif-LINUX:~$ ifup wlan0
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
arosemena@Shif-LINUX:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
arosemena@Shif-LINUX:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured


```

---

### Post by TBABill on 2010-11-29
You only need to enable the b43 driver for that wireless device. You should be able to follow the instructions [https://help.ubuntu.com/community/WifiDocs/Driver/b43](https://help.ubuntu.com/community/WifiDocs/Driver/b43) in order to get it going. No need for ndiswrapper since the b43 is the preferred driver for your device. Can you go to System>>>Administration>>>Hardware and see if the system offers you the Broadcom drivers? They will be listed as B43 and STA I think. Just choose the B43 and click activate, install, restart, enjoy.
 
Have you tried that already? My understanding is the newer drivers from Broadcom (Oct release?) may also come either soft or hard blocked. To find out ```
sudo rfkill list
``` and if either one is marked YES, then just ```
sudo rfkill unblock all
```

---

### Post by shif on 2010-11-29
Both appear as no and i cant find "hardware" in system -> administration :S

---

### Post by TBABill on 2010-11-29
If it's 10.10 you are using it shows up as "additional hardware" or something like that. I think it's at the top of the menu under administration, but I can't recall exactly. I'm at work right now, not near my machine.

---

### Post by shif on 2010-11-29
heres the list of the administration items, and if u mean additionals drivers it just says that theres no network connection and displays an empty list

[IMG]http://traynet.com/Screenshot2.png[/IMG]

---

### Post by TBABill on 2010-11-29
Additional drivers is correct. Can you get a wired connection so you can download the driver?

---

### Post by shif on 2010-11-29
it worked.... i had to go to buy an ethernet cable but finally its working now i'll sleep im so tired, thanks for all your help  

```
karma++;
```

---

### Post by TBABill on 2010-11-29
Very welcome! Glad you have it sorted. Just remember the steps for next time in case you ever reinstall.

---

