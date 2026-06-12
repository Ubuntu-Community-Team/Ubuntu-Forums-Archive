---
title: "Cannot turn on WiFi"
date: 2012-03-30
forum: Networking &amp; Wireless
---

### Post by tehchibipanda on 2012-03-30
Greetings everyone! So, I'm in a bit of a pickle as you may or may not see from the thread title. I simply can't turn on WiFi. If I push my F11 key, bluetooth turns off/on, which is supposed to me my WiFi. I've also for the lulz tried the F11 key while holding down Fn, same thing. Nothing happens. Now, that being stated...here's what I've pushed in terminal...maybe someone here can make heads or tails of this and come up with a good solution. 
```
chris@chris-Presario-CQ57-Notebook-PC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr e4:11:5b:fe:32:75  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::e611:5bff:fefe:3275/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1203900 (1.2 MB)  TX bytes:192359 (192.3 KB)
          Interrupt:43 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3840 (3.8 KB)  TX bytes:3840 (3.8 KB)

```As we see here, ifconfig states the wifi is not even on. Hmm. 

```
chris@chris-Presario-CQ57-Notebook-PC:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```Nothing is blocked via rfkill...

```
chris@chris-Presario-CQ57-Notebook-PC:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 05
       serial: e4:11:5b:fe:32:75
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.2.2 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:90104000-90104fff memory:90100000-90103fff
  *-network
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:23 memory:90200000-90203fff

```Whats slightly alarming to me is that the BCM4313 does not have a logical name like wlan0...

```
chris@chris-Presario-CQ57-Notebook-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```No wireless device shows up. Sad face. If anyone can think of something to do, let me know. I've gone into blocklist, and added the acer, commented out bcm43xx, restarted the device. Right now, I'm going to reinstall the broadcom drivers, and see if that works. Any other tips would be greatly appreciated!

I have scoured the forums to no avail; I've tried what was listed, and nothing worked. Even the stick on the main page. :(

Side note: I'm not using Lucid Lynx. It won't let me change my distro in user CP; I'm using 11.10

---

### Post by bkratz on 2012-03-30
Here is a pretty good thread which will probably give you the needed information on the BCM4313.  Also, you might check your bios and see if wireless can be enabled/disabled there.

[http://ubuntuforums.org/showthread.php?t=1889170](http://ubuntuforums.org/showthread.php?t=1889170)

---

### Post by tehchibipanda on 2012-03-30
I had done all of that! Except one very important detail. For some reason, I overlooked blacklist-local ~_~ Once I added a comment to blacklist wl, it worked without a problem! A kudos to you, kind sir, for pointing me in the direction of that link!

---

### Post by bkratz on 2012-03-31
> **tehchibipanda said:**
> I had done all of that! Except one very important detail. For some reason, I overlooked blacklist-local ~_~ Once I added a comment to blacklist wl, it worked without a problem! A kudos to you, kind sir, for pointing me in the direction of that link!



Sure glad you got it working.  Congratulations and enjoy!

---

