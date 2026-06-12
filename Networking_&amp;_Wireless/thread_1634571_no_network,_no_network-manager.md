---
title: "no network, no network-manager"
date: 2010-11-30
forum: Networking &amp; Wireless
---

### Post by jevharr on 2010-11-30
Okay, I know this is like a rash all over the forum, but I haven't been able to find a really satisfactory answer. I am unable to connect to any network, wired or wireless. Network-manager and wicd are both gone, as in no longer installed. Please don't tell me to apt-get anything. I have no network connection. I have tried downloading packages for nm onto a usb stick only to find myself in dependency hell which ended with the impassible error "Requires installation of untrusted packages". What happened with 10.10??!! This OS has never failed me like this before.

---

### Post by uncaspi on 2010-11-30
Hi San Diego. I've been there in 1987.Nice city.La Holla and the beaches.

Well we need some more info. Since nm and wicd are gone we could try to bring up the interface card manually using wifi.

1. See if the cards are associated with logical names i.e. eth0 wlan0 and so on.

sudo ifconfig
sudo iwconfig  although it should show up with the first command.
If something shows up then a driver for them are loaded. But this may not be the right driver since the network didn't work at the first place.
If it is an usb adapter please post lsusb .If not let us see 
lspci -nn

And we take it from there.

---

### Post by jevharr on 2010-11-30
ok, here goes...
ifconfig output:
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6292 (6.2 KB)  TX bytes:6292 (6.2 KB)

```
iwconfig output:
```
eth1      IEEE 802.11bg  ESSID:"x-myessid-x"  
          Mode:Managed  Frequency: 2.412 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
lspci output:
```
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]
02:00.0 CardBus bridge [0607]: Texas Instruments PCI4520 PC card Cardbus Controller [104c:ac46] (rev 01)
02:00.1 CardBus bridge [0607]: Texas Instruments PCI4520 PC card Cardbus Controller [104c:ac46] (rev 01)
02:01.0 Ethernet controller [0200]: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) [8086:101e] (rev 03)
02:02.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
```

Thanks,
James

---

### Post by jevharr on 2010-12-02
bump

---

### Post by uncaspi on 2010-12-02
Ok let's see if the driver is loaded. Please post the content of
lsmod | grep ipw2200

---

### Post by jevharr on 2010-12-02
ok, here is the output from that.

```

ipw2200               136715  0 
libipw                 39808  1 ipw2200
cfg80211              144470  2 ipw2200,libipw
lib80211                5058  2 ipw2200,libipw

```

and just for fun, here is the result of dmesg | grep ipw2200
```

[   32.320231] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   32.320234] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   32.681964] ipw2200 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   32.689589] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   33.282523] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)

```

---

### Post by uncaspi on 2010-12-02
The driver is loaded ok, but you should look in the threads and search for ipw2200

Maybe you need another firmware.


The driver also require ieee80211 to be loaded. Please check if it's loaded by
lsmod | grep ieee80211

if not then sudo modprobe ieee80211

---

