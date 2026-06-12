---
title: "Can't get wifi on my new laptop after fresh install"
date: 2012-01-26
forum: Networking &amp; Wireless
---

### Post by dwivvc on 2012-01-26
I was wondering if someone could please help me I recently brought a new laptop and i would like to access a wireless network.

I'm new to linux and am using the defult network manager ( i don't know how to change it ) Wicd it can't find any wireless networks even tho my brothers laptop ( win7) can find about 10 

Could someone please help me find out whats wrong?

Thanks

---

### Post by Bucky Ball on 2012-01-26
Welcome to the forums. Please provide release number (10.04 LTS, 11.10?), make and model of laptop and the result of this command in a terminal. Just paste it into your post:

```
iwconfig
sudo lspci
```One command at a time, not both at once. ;)

Also, check 'additional drivers'. Is there anything there disabled? Have you gotten online with a cable and gotten all updates? If not, do it, then get updates and try Additional Drivers again.

---

### Post by dwivvc on 2012-01-26
hi there I'm actually using something called backtrack 5 I don't know if i'm on the wrong site as this is very new to me.   laptop pavilion g6 product number a8m63ea\abu 

> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  Mode:Monitor  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off> 
spci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Complex
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9643
00:01.1 Audio device: ATI Technologies Inc Device 1714
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:05.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:06.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode]
00:12.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB Controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB Controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 13)
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:16.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:16.2 USB Controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)


wired works fine i'm using it now

---

### Post by Bucky Ball on 2012-01-27
Checked for updates and 'Additional Drivers'?

Anyhow, go here:

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)

Download the LINUX driver (it says Unix (Linux)) which looks less than a month old. 

This is the Ubuntu forums. Backtrack seems to be based on Ubuntu. Backtrack have its own community forums? Might be more help. There is also a forum here for other OSs. ;)

Hope that link gives you some help. Don't know how to install (don't remember!) but that is the driver you are after.

*** HEY, my memory just came back. There is a 'ReadMe' file in there when you download the driver which tells you how to install the driver. You will need to use the terminal to install unless Realtek have made it easier but once installed it should stick from boot to boot. Good luck. ;)

And ps; your wireless card is listed like this in the output of 'sudo lspci':

```
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
```

---

