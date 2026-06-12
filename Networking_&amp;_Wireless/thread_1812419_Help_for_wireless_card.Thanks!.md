---
title: "Help for wireless card.Thanks!"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by elsaelsa on 2011-07-26
Hi everyone,

I have a COMPAQ PRESARIO V 5000 with a wireless card BMC4318.
I have just installed ubuntu 10.04 LTS.I have some problems with wireless botton, ' cause although ethernet works, the botton of wireless connection doesn't switch on, so how can I manage with wireless card?How can I make it work?
Thanks

---

### Post by Peter09 on 2011-07-26
First you need to ensure that the system is up to date using update manager.
Then use 'third party software' tool to find any needed drivers.
 
If still no luck can you post the output of
 
```
nm-tool
```

---

### Post by elsaelsa on 2011-07-26
Now it works!Tank u so much!

---

### Post by elsaelsa on 2011-07-28
hi,
unfortunately today both ethernet and wireless don't work again. In the upside of desktop I visualize 'Networking disabled' .

the output of 'nm-tool' is:
State: asleep
-Device: wlan0 ----------------
Tyoe: 802.11 WiFi
Driver: b43
State: unmanaged
Default: no
HW Address: 00:14:a5:6c:f2:90

Capabilities:

Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes

Wireless Access Points

- Device: eth0------------------------------------
Tyoe: Wired
Driver: 8139too
State: unmanaged
Default: no
HW Address: 00:0f:b0:c1:62:00

CApabilities:
Carrier Dectect: yes
Speed: 100 MB/s

Wired Properties
Carrier: off


Help me please :) 
what to do? thank's

---

### Post by Peter09 on 2011-07-28
Have you got a wireless on/off switch (or keyboard function switch) - try that.

Note that the wireless driver will take several seconds (30s ?) to establish.


if no success try


     
     ```
rfkill list 
```
you can unblock any thing with:

     
     ```
rfkill unblock all 
```
                                                                              Comeback and tell us what happened.

---

### Post by wildmanne39 on 2011-07-28
Hi, also you might want to change unmanaged to managed.

---

### Post by elsaelsa on 2011-07-30
@Peter09:
I have a wireless switch on/off botton, but it doesn't work.Also ethernet doesn't work.
The result of getting the first code you suggested me is:
0: phy: wireless LAN
Soft blocked: no
Hard blocked: no
Instead I have no result for the second code (rfkill unblock all)

What to do now?
Thanks so much

---

### Post by wildmanne39 on 2011-07-30
Hi, your network is unmanaged it should say managed run these commands and see if it works.
```
sudo ifconfig wlan0 down
```
```
sudo iwconfig wlan0 mode Managed
```
```
sudo ifconfig wlan0 up
```

---

### Post by elsaelsa on 2011-07-31
Hi,
thank's. With these codes the wireless botton switches on, but networking are still unworking and in the upside of the desktop on the right it appears "Networking disable".
Both ethernet and wireless don't work

What could I do?
Thanks.

---

### Post by wildmanne39 on 2011-07-31
Hi, first go to the internet icon in the top right corner of the screen and see if you can click on enable network and enable wireless, if that does not help then run these commands please.
```
sudo lshw -C network
```
```
lspci -nn | grep -e 0280 -e 0200
```
```
ifconfig
```
```
dmesg | grep wlan0
```
```
dmesg | grep eth0
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by lkjoel on 2011-07-31
> **elsaelsa said:**
> Hi,
thank's. With these codes the wireless botton switches on, but networking are still unworking and in the upside of the desktop on the right it appears "Networking disable".
Both ethernet and wireless don't work

What could I do?
Thanks.
Could you give us the output of this Terminal command?
```
sudo /etc/init.d/networking restart

```

---

### Post by elsaelsa on 2011-08-02
@ eildmanne39:
so:



sudo lshw -C network

*-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:c0200000-c0201fff
  *-network:1 DISABLED
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:c1:62:00
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:22 ioport:a000(size=256) memory:c0202000-c02020ff
  *-network DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:a5:6c:f2:90
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

lspci -nn | grep -e 0280 -e 0200
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
06:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13216 (13.2 KB)  TX bytes:13216 (13.2 KB)



dmesg | grep wlan0 

[  212.190805] ADDRCONF(NETDEV_UP): wlan0: link is not ready

dmesg | grep eth0

[    1.530966] eth0: RealTek RTL8139 at 0xa000, 00:0f:b0:c1:62:00, IRQ 22

---

### Post by elsaelsa on 2011-08-02
@lkjoel :

* Reconfiguring Network interfaces... [ok]

and nothing

---

### Post by wildmanne39 on 2011-08-02
Hi, run these commands please and post the results here.
```
lsmod | grep b43
```
```
cat /etc/modprobe.d/blacklist.conf
```

Did you change your network to manage?
Thank you

---

### Post by elsaelsa on 2011-08-02
b43                   163556  0 
mac80211              205402  1 b43
cfg80211              126144  2 b43,mac80211
led_class               2864  1 b43
ssb                    38934  1 b43
annamaria@annamaria-laptop:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

---

### Post by wildmanne39 on 2011-08-02
Hi, run this command please and post the results.
```
modinfo b43 | grep 4318
```
Thank you

---

### Post by wildmanne39 on 2011-08-02
Hi, also run these commands please.
```
iwconfig
```
```
dmesg | grep firmware
```
```
sudo iwlist scan
```
Thank you

---

### Post by elsaelsa on 2011-08-31
Code:
 	iwconfig 
 	lo     no wireless extensions.

eth0    no wireless extensions.

wlan0  IEE 802.1LBG   ESSID:off/any
mode:Managed  Access Point: Not-Associated  Tx-Power=0 dBm
Retry long limit:7 RTS thr:off Fragment thr:off
Power Managment:off


Code:
 	dmesg | grep firmware 
 	[   18.897216] Platform radeon_cp.0: firmware: Requesting radeon/R300_cp.bin


Code: sudo iwlist scan

lo  interface doesn't support scanning
eth0  interface doesn't support scanning
wlan0      interface doesn't support scanning: network is down


thank's!!

---

### Post by wildmanne39 on 2011-08-31
Hi, before we proceed we need to know is your wired connection working again or are you using another method of connecting to the internet on this computer?
Thank you

---

### Post by elsaelsa on 2011-08-31
I'm using an other pc to internet connection and write with you 'cause my Compaq (where there's ubuntu) is unabled to internet connection

---

### Post by fdrake on 2011-08-31
can you plese download this file in your desktop and run this commands:
```

sudo chmod +x ~/Desktop/net.sh
sudo bash ~/Desktop/net.sh

```
in your desktop there should be a new file: results.txt post/attach it in your next post please.

---

### Post by wildmanne39 on 2011-08-31
Hi, try this please open synaptic type bcm in the search box then everything that is there with a green square by it uninstall then restart your computer and do this.

Down load the zip file on a computer with an internet connection to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. 

Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
one at a time.
see if that works.
Thank you

---

