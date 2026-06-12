---
title: "Wireless won't enable even after restoring factory settings"
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by eckscalibur on 2009-06-27
I recently purchased a Dell Inspiron 15n laptop with Ubuntu preinstalled.  Initially, the wireless drivers worked fine.  After upgrading to 9.04, I noticed that the wireless stopped working somewhere along the line.  After lots of work trying to get it to work without success, I figured that the update had made the problem, so I just restored to the original factory settings.  However, now it won't allow me to enable the drivers that it enabled from the Hardware Drivers application in the System Menu.

lspci gives me this:

0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

and ifconfig:

eth1      Link encap:Ethernet  HWaddr 00:24:2c:9c:6f:15  
          inet6 addr: fe80::224:2cff:fe9c:6f15/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

and iwconfig:

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated

pccardctl ident gives me nothing at all.

I think the firmware might be screwed up or something, but I'm stumped.

---

### Post by Ayuthia on 2009-06-27
Can you post the results of:
```
lsmod|grep -e ssb -e wl
```
It could be that the ssb module is causing the conflict.

---

### Post by eckscalibur on 2009-06-27
```
wl                   1076372  0 
ieee80211_crypt        13572  2 ieee80211_crypt_tkip,wl

```

---

### Post by Ayuthia on 2009-06-27
It looks like that it is all there.  Have you tried to see if you can connect to the site by entering in the ESSID maunally?  Also, you can try to see if you can scan from the Terminal:
```
sudo iwlist scan
```


EDIT:
By the way, are you using encryption?  If so, what kind (WPA/WP2/WEP) and is it hidden?

The issue could be with NetworkManager or hidden sites also.

---

### Post by eckscalibur on 2009-06-27
```
eth1      Failed to read scan data : Invalid argument

```

There's no encryption, only MAC address whitelist, but I have that turned off anyway.  And the network isn't hidden.  The NetworkManager applet won't even give me an option to enable wireless, so I can't see any networks.

---

### Post by Ayuthia on 2009-06-27
> **eckscalibur said:**
> ```
eth1      Failed to read scan data : Invalid argument

```

There's no encryption, only MAC address whitelist, but I have that turned off anyway.  And the network isn't hidden.  The NetworkManager applet won't even give me an option to enable wireless, so I can't see any networks.

Let's try the following:
```
sudo /etc/init.d/NetworkManager stop
sudo iwconfig eth1 essid <name of router without brackets>
sudo dhclient eth1
```This will stop NetworkManger from running and will allow you to try to connect manually.

If you want to start it up again:
```
sudo /etc/init.d/NetworkManager start
```
or reboot.

---

### Post by eckscalibur on 2009-06-27
When I tried to connect to the ESSID all I got was this:

Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; Invalid argument.

I checked my router and the SSID was correct, so it shouldn't be a problem with that.

---

### Post by Ayuthia on 2009-06-27
My guess is that your card does not like that version of the Broadcom STA driver.  You might try to compile the more recent version from the Broadcom site:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Or you might try the ndiswrapper route:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

The other thing to try is to remove the module and reload it:
```
sudo modprobe -r wl
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwconfig eth1 essid <name>
sudo dhclient eth1
```

You might also verify that NetworkManager is not still running:
```
ps -ef|grep Network
```

---

### Post by eckscalibur on 2009-06-27
Okay, sorry it took so long to get back to you.  I tried all those options and none of them worked.  NDISwrapper installed but didn't do anything, compiling from source just gave me an error message:

```
make: Entering directory `/usr/src/linux-headers-2.6.27-14-generic'
  LD      /home/user/Desktop/wl/built-in.o
  CC [M]  /home/user/Desktop/wl/src/wl/sys/wl_linux.o
  CC [M]  /home/user/Desktop/wl/src/wl/sys/wl_iw.o
  CC [M]  /home/user/Desktop/wl/src/shared/linux_osl.o
  LD [M]  /home/user/Desktop/wl/wl.o
ld: Relocatable linking with relocations from format elf64-x86-64 (/home/u/Desksertop/wl/lib/wlc_hybrid.o_shipped) to format elf32-i386 (/home/user/Desktop/wl/wl.o) is not supported
make[1]: *** [/home/user/Desktop/wl/wl.o] Error 1
make: *** [_module_/home/user/Desktop/wl] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.27-14-generic'

```I tried doing ifconfig wlan0 up and added the ESlSID and it executed without an error message, but it still didn't do anything.  Network manager definitely wasn't running.  Oh, and dhclient gave me this:
```

Listening on LPF/wlan0/00:24:2c:9c:6f:15
Sending on   LPF/wlan0/00:24:2c:9c:6f:15
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8

```Any ideas?

EDIT:

Oh, and here's my output from lshw, for good measure:

 ```
*-network                                                                                                                                                             
       description: Wireless interface                                                                                                                                  
       product: BCM4312 802.11b/g                                                                                                                                       
       vendor: Broadcom Corporation                                                                                                                                     
       physical id: 0                                                                                                                                                   
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:2c:9c:6f:15
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+Broadcom,09/20/2007, 4.170. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```

So the NDISwrapper module is clearly running, but either I don't have the right driver (it looks like it is), or there's some other problem.

---

### Post by Ayuthia on 2009-06-27
You compile error almost looks like you grabbed the wrong source code (It is showing a 64-bit to 32-bit error).

As for ndiswrapper, can you check dmesg to see if any messages come up:
```
dmesg|grep ndiswrapper
```It looks like you have ndiswrapper set up correctly.

---

### Post by eckscalibur on 2009-06-27
```
[   15.123453] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   15.215642] ndiswrapper: driver bcmwl5 (Broadcom,09/20/2007, 4.170.25.12) loaded
[   15.216149] ndiswrapper 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.216331] ndiswrapper 0000:0c:00.0: setting latency timer to 64
[   15.229430] ndiswrapper: using IRQ 17
[   15.429148] usbcore: registered new interface driver ndiswrapper
```

I tried compiling the 32 bit version, and lo and behold, it compiled.  After modprobing the new wl driver, it's listed with lsmod, but...still doesn't work.

---

### Post by Ayuthia on 2009-06-27
I am now stumped also.  We have tried the two available options for your card (wl and ndiswrapper), we compiled the most recent version of the Broadcom STA module, we even turned off NetworkManager and tried to connect manually.  Everything looks like it is configured correctly.

Have you tried running it on a liveCD to see if it works?  I am guessing that it won't since you have already restored your system once before.

Sorry.

---

### Post by eckscalibur on 2009-06-27
Tried it, and no, it didn't work.  :-/  I appreciate the help very much, though.  Lesson learned:  If it works DON'T TOUCH IT. :-P

---

### Post by eckscalibur on 2009-06-28
I figured it out!  Stupid "enable/disable wireless" button was toggled.  I didn't even know I had one.  There was *no* indication from anything that that was on, and no obvious way to turn it off on a software level.  Why they'd put a button on for that, I have no idea, but now I'm glad it works.

---

### Post by CD Baric on 2009-07-03
Don't feel bad - has happened to us all.

The purpose of the wireless On/Off switch is to disable the wireless transceiver if it isn't required and to save the power. It is also a security measure.

The Dell 15n is a great laptop for the price!

CD

---

