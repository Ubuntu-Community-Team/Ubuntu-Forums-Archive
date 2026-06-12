---
title: "No ethernet in ubuntu 10.10"
date: 2010-09-14
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ancau on 2010-09-14
Hi there!

I've just installed 10.10 and I can'r get my ethernet working. The device is not listed in /etc/network/interfaces
> 
cat /etc/network/interfaces 
auto lo
iface lo inet loopback

and it doesn't appear with ifconfig
> 
ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:52:a2:b6  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe52:a2b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1639 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1668 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1537486 (1.5 MB)  TX bytes:357785 (357.7 KB)

I do however think I see it with lspci
> 
lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


Can anybody help me get this working? I know 10.10 is still beta, and I haven't managed to update since installing because my wireless connection is really, really, slow. But I should also mention that I had this exact problem when I installed Karmic a while ago, and ended up moving away from ubuntu because of it.

Help me please!!!

cheers
ancau

---

### Post by chili555 on 2010-09-14
I think your ethernet is supposed to work with a driver called *e1000*. Let's try to load it and see if the kernel has any messages that will help us discover why it isn't working automagically as it should. Please open Applications > Accessories > Terminal and do:```
sudo modprobe e1000
dmesg | grep e1000
```Please post the result.> The device is not listed in /etc/network/interfacesThat's normal for an interface that is to be managed by Network Manager.

---

### Post by ancau on 2010-09-14
thanks for the help :KS

sudo modprobe e1000 did not return anything

but dmesg | grep e1000 came up with:
> 
dmesg | grep e1000
[    1.408088] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k4
[    1.408092] e1000e: Copyright (c) 1999 - 2009 Intel Corporation.
[    1.408156] e1000e 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.408182] e1000e 0000:02:00.0: setting latency timer to 64
[    1.408428] e1000e 0000:02:00.0: irq 44 for MSI/MSI-X
[    1.408821] e1000e 0000:02:00.0: Disabling ASPM L0s 
[    1.515046] e1000e 0000:02:00.0: (unregistered net_device): NVM Read Error while reading MAC address
[    1.515053] e1000e 0000:02:00.0: (unregistered net_device): Invalid MAC Address: 00:00:00:00:00:00
[    1.525396] e1000e 0000:02:00.0: PCI INT A disabled
[    1.525406] e1000e: probe of 0000:02:00.0 failed with error -5
[ 2688.346124] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k6-NAPI
[ 2688.346130] e1000: Copyright (c) 1999-2006 Intel Corporation.


---

### Post by chili555 on 2010-09-14
It appears that e1000e is being used; not e1000. I see conflicting information regarding which module is correct. May we please see the pci.id for your device? Please run:```
lspci -nn
```Strip off everything but the ethernet device and post it.> e1000e 0000:02:00.0: (unregistered net_device): NVM Read Error while reading MAC addressScary!

---

### Post by ancau on 2010-09-14
> **chili555 said:**
> .Scary!
I guess ignorance sometimes is bliss, I understood nothing of it!

the ethernet line of lspci -nn
> 
02:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a]


Thanks again!

---

### Post by chili555 on 2010-09-14
e1000e is correct for your device:```
$ modinfo e1000e | grep 109A
alias:          pci:v0000[COLOR="Red"]8086[/COLOR]d0000[COLOR="Red"]109A[/COLOR]sv*sd*bc*sc*i*
```You might try a later version. Download the latest version here: [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=2198&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=2198&lang=eng)

With your wireless attached and an internet connection, please do:```
sudo apt-get install linux-headers-generic build-essential

```By default, downloads go to your desktop. Right-click the tar.gz file and select 'Extract Here.' Open a terminal and do:```
cd Desktop/e1000e-1.2.10/src
make
sudo make install
sudo rmmod -f e1000e
sudo modprobe e1000e
sudo ifconfig eth0 up
ifconfig
```Did an ethernet interface, eth0 perhaps, appear? If not, please run:```
dmesg | grep e1000e
```Post entries after 2688.xx; that is after the entries we've already seen.

I have this exact device and the module built perfectly for me. Post back if you get stuck.

Cross your fingers, everyone!

---

### Post by KegHead on 2010-09-14
Hi Chilli555!

Just a note to let you know the help you provided for me in 10.04 is working in 10.10.

Thanks!!

KegHead

---

### Post by ancau on 2010-09-14
hmmm...

damn I messed up... did it all, didn't think it worked, then realised that I missed out your second step; the apt-get install. So I tried doing it over, but I'm not sure if it works like that. Still...

the download, make, sudo make install all went fine.

sudo modprobe e1000e
returned nothing.

```
sudo ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device
```

ifconfig still just returned lo and wlan0, no eth0 unfortunately.

running dmesg | grep e1000e didn't produce all the same numbers as last time, so there was no 26688.xx but the text seemed to be much the same other than the copyright years, so the lines after that were these:

```
[ 6330.732631] e1000e 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 6330.733713] e1000e 0000:02:00.0: setting latency timer to 64
[ 6330.734568] e1000e 0000:02:00.0: irq 46 for MSI/MSI-X
[ 6330.734591] e1000e 0000:02:00.0: Disabling ASPM L0s 
[ 6330.815196] e1000e 0000:02:00.0: (unregistered net_device): NVM Read Error while reading MAC address
[ 6330.815212] e1000e 0000:02:00.0: (unregistered net_device): Invalid MAC Address: 00:00:00:00:00:00
[ 6330.825641] e1000e 0000:02:00.0: PCI INT A disabled
[ 6330.825662] e1000e: probe of 0000:02:00.0 failed with error -5
```

It's about bed time for me i'm afraid, so I won't be on this for a while, but thanks for all the help so far :)

---

### Post by chili555 on 2010-09-14
I'm struggling to find an answer. I am reading this: [https://bugzilla.novell.com/show_bug.cgi?id=615761](https://bugzilla.novell.com/show_bug.cgi?id=615761)

I am especially mystified because I have this exact device in one of my laptops and it works perfectly; I assume it is not therefor a driver issue.

Is your computer's BIOS up to date?

Back to Google...

---

### Post by Iowan on 2010-09-14
Moved to Maverick Meerkat Testing and Discussion

---

### Post by cariboo on 2010-09-14
There is a couple of things to keep in mind, if a module is successfully loaded there won't be any results echoed back, so if your not seeing anything echoed back that means the module is being loaded. The other thing to check is to see if any other ethernet specific drivers are being loaded by default. Try

```
lsmod | grep e100
```

and post the results. If the os is loading the e1000 driver, and the device needs the e1000e driver, you're going to have to blacklist the e1000.

---

### Post by ancau on 2010-09-14
```
lsmod | grep e100
e1000e                149518  0
```

Hmmm don't know. I'll try updating the bios, fingers crossed.

---

### Post by ancau on 2010-09-15
Hi everybody!

I updated by BIOS and that didn't work, so I went and borrowed a mate's internet connection to do a full system update, rebooted, and now everything is working beautifully. 

Thanks for all the help, sucks that it was such a simple solution after all of that, but c'est la vie.

I'll mark it solved :)

cheers.
ancau

---

### Post by chili555 on 2010-09-15
Glad it's working by whatever means. Have fun!

---

### Post by extendedping on 2010-10-10
just upgraded desktop to 10.10 and have no ethernet. lsmod pipe (on cell cant find symbol) shows e1000e and I can oing my ethernet. but my linksys does not even have a light for the cable now. hmmmm this sucks.

---

