---
title: "Ralink RT5390: WiFi broken after kernel update"
date: 2013-07-06
forum: Networking &amp; Wireless
---

### Post by meijin3 on 2013-07-06
A couple weeks ago after updating to what was the latest kernel update, my WiFi ceased to work. I've gotten around this by loading the old kernel on boot up but that gets a little old. :P Anyway, I just installed the latest update today and my problem has not been resolved. I'm not quite sure where
 to start trying to fix this so your help is much appreciated. Thanks!
Here are the results of the lspci command:

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Complex00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI BeaverCreek [Radeon HD 6620G]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:05.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:06.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:10.0 USB controller: Advanced Micro Devices [AMD] FCH USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices [AMD] FCH USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] FCH SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] FCH SMBus Controller (rev 13)
00:14.1 IDE interface: Advanced Micro Devices [AMD] FCH IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] FCH PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 06)
02:00.0 Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
```

---

### Post by meijin3 on 2013-07-14
Bump :)

---

### Post by varunendra on 2013-07-14
Please follow the "Wireless Script" link in my signature, run and post back the result of wireless_script as mentioned in the linked post.

Please use 'Code' tags if posting the results here. Thanks!

---

### Post by meijin3 on 2013-07-15
Here are the results:

```


*************** info trace ***************


***** uname -a *****


Linux ***** 3.8.0-26-generic #38-Ubuntu SMP Mon Jun 17 21:43:33 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring


***** lspci *****


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:358b]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Hewlett-Packard Company U98Z077.00 Half-size Mini PCIe Card [103c:1636]
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader [10ec:5209] (rev 01)


***** lsusb *****


Bus 002 Device 002: ID 5986:02ac Acer, Inc 
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 004 Device 002: ID 138a:0018 Validity Sensors, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub


***** iwconfig *****




***** rfkill *****


0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


***** lsmod *****




***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         69.251.107.246
    Prefix:          21 (255.255.248.0)
    Gateway:         69.251.104.1


    DNS:             75.75.75.75
    DNS:             75.75.76.76


  IPv6 Settings:
    Address:         2001:558:6020:185:6dcc:c067:1b09:debc
    Prefix:          128
    Gateway:         fe80::201:5cff:fe32:4e81


    Address:         fe80::121f:74ff:fe1c:fe1
    Prefix:          64
    Gateway:         fe80::201:5cff:fe32:4e81


    Address:         2001:558:6020:185:6dcc:c067:1b09:debc
    Prefix:          128
    Gateway:         ::


    DNS:             2001:558:feed::1
    DNS:             2001:558:feed::2






***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****




***** resolv.conf *****


nameserver 127.0.1.1
search hsd1.md.comcast.net


***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2860sta
blacklist rt3090sta


***** dmesg *****




****************** done ******************

```

Thank you!

Edit: I looked through the results and at hard blocked it says yes. I've flipped the switch over and over with no change. It was off because I couldn't tell if it was on or off either way so that's not the problem.

Edit 2: I fixed it! Steps below!

Using the information I got from the wireless script I gleaned that my network controller was named 'rt3090sta'. I looked at my blacklist.conf info to see if I had blacklisted that driver. rt5390 looked fairly similar so I did a Google search of "rt3090sta rt5390".

This was the first link: [http://askubuntu.com/questions/303415/ubuntu-13-04-ralink-rt5390-wont-work-after-upgrade](http://askubuntu.com/questions/303415/ubuntu-13-04-ralink-rt5390-wont-work-after-upgrade)

So I followed the steps which were:


[LIST=1]
[*]download driver [http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001](http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001)
[*]tar -xvf /home/ukbeast/USERNAME/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_v2.bz2.bz2
[*]cd 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO
[*]download patch [http://gridlox.net/diff/rt5592sta_fix_64bit_3.8.patch](http://gridlox.net/diff/rt5592sta_fix_64bit_3.8.patch)
[*]patch -p1 <rt5592sta_fix_64bit_3.8.patch (if asks for directory point it to rt_linux_dev.crt_linux.c)
[*]make sure /os/linux/config.mk reads HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
[*]make
[*]sudo make install
[*]modprobe rt5390sta
[*]sudo gedit /etc/modprobe.d/blacklist.conf

At the end of the file, add these lines:
[/LIST]
# Blacklist conflicting kernel modules
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2860sta
blacklist rt3090sta


I got an error with 'make' so I did 'sudo make'. Same thing with 'modprobe rt5390sta'. 

Thanks for getting me started, varunendra!

---

### Post by varunendra on 2013-07-15
You're welcome !:)

As a few closing tips regarding your blacklisting above (not that it is going to make any difference) :
[list=1]
[*]Blacklisting only rt2800pci is enough to prevent the other rt2xxx drivers from loading. They get loaded only as dependencies of rt2800pci.
[*]rt2x00usb has no relevancy for you. It is a driver for ralink based USB adapters.
[*]There is no driver called rt2860sta in your system, so no point in blacklisting it. It is just and 'alias' to the actual ralink drivers, like rt3090sta which you have already blacklisted.
[*]Exactly one error during 'make' (regarding tftpboot) is normal and can be safely ignored. However, 'sudo' is a must with other commands (make install, modprobe...)
[*]Since it is not a dkms package, you will need to rebuild-reinstall the driver everytime there is a kernel upgrade. So keep the downloaded package handy. :)[/list]

---

### Post by meijin3 on 2013-07-15
Thanks :)

---

### Post by erre2 on 2013-10-11
The url [http://gridlox.net/diff/rt5592sta_fix_64bit_3.8.patch]("http://www.gridlox.net/diff/rt5592sta_fix_64bit_3.8.patch") has fallen, what do I do now? :S

---

### Post by meijin3 on 2013-10-11
I have the files on my computer. I'll get them to you when I get on it.

---

### Post by varunendra on 2013-10-11
> **meijin3 said:**
> I have the files on my computer. I'll get them to you when I get on it.

Let me have the privilege :)

@erre2,
Please download the attachment and extract the patch file to the same directory where the downloaded driver source files are extracted. Then follow the instructions to patch and build.

Ignore the errors while patching. They occur because the patch was originally meant for another driver with slightly different code. I never found enough time to fix it, but the patching errors are harmless.

---

### Post by erre2 on 2013-10-14
Many thanks!

---

### Post by varunendra on 2013-10-14
No problem, and Welcome to the forums ! :)

---

