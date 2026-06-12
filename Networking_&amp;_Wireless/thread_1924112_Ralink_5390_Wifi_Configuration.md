---
title: "Ralink 5390 Wifi Configuration"
date: 2012-02-12
forum: Networking &amp; Wireless
---

### Post by terp08 on 2012-02-12
Hello,

I recently did a 64 bit Ubuntu 11.04 installation and have been trying to set up my wireless network.  I've done a ton of searching and eventually have come to a point where I have located and installed the appropriate drivers for my Ralink 5390 network card, but I still can't seem to get it to actually work as this is my first time configuring wireless in linux.  Here is some additional info, any help would be appreciated.

**uname -a**

```

Linux ubuntu 2.6.38-13-server #55-Ubuntu SMP Tue Jan 24 15:52:18 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```**ifconfig -a**

```

eth0      Link encap:Ethernet  HWaddr 10:1f:74:19:30:43  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::121f:74ff:fe19:3043/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41399 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:58615469 (58.6 MB)  TX bytes:2336103 (2.3 MB)
          Interrupt:40 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

ra0       Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

```[B]

iwconfig[/B]

```

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```**sudo lshw -C network**

```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 06
       serial: 10:1f:74:19:30:43
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.028.00-NAPI duplex=full ip=192.168.1.5 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:40 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network DISABLED
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: ra0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN latency=0 multicast=yes wireless=Ralink STA
       resources: irq:17 memory:f0200000-f020ffff

```**lsmod | grep rt**

```

parport_pc             36959  0 
rt5390sta            1341093  0 
rts_pstor             440614  0 
parport                46458  3 parport_pc,ppdev,lp

```[B]


"rfkill list all[/B]" does not return anything.  Any help would be appreciated.  Thanks

---

### Post by praseodym on 2012-02-12
Please show:

```
lspci -nnk | grep -iA2 net
dmesg | egrep 'rt5|rt2'
```
Why do you use a server kernel?

---

### Post by terp08 on 2012-02-12
> **praseodym said:**
> Please show:

```
lspci -nnk | grep -iA2 net
dmesg | egrep 'rt5|rt2'
```Why do you use a server kernel?

**lspci -nnk | grep -iA2 net**

```

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:3591]
    Kernel driver in use: r8168

```**dmesg | egrep 'rt5|rt2'**

```

[   18.327519] register rt2860
[   18.327568] rt2860 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.327610] rt2860 0000:02:00.0: setting latency timer to 64
[   19.780149] !!! rt28xx Initialized fail !!!
[   19.809614] !!! rt28xx Initialized fail !!!
[   20.069598] !!! rt28xx Initialized fail !!!
[   25.041400] !!! rt28xx Initialized fail !!!
[   30.039994] !!! rt28xx Initialized fail !!!
[   35.040147] !!! rt28xx Initialized fail !!!
[   40.039620] !!! rt28xx Initialized fail !!!
[  240.064301] !!! rt28xx Initialized fail !!!

```[B]Why do you use a server kernel?
    [/B]-- To be honest with you, I don't remember installing it.  I could have picked it up on an upgrade as my previous kernels are all generic.  Or I might have just installed it unknowingly from the get go.  Since you ask, is there a reason I should stick to one over the other?  I really am pretty new to Ubuntu.  I did try and load a generic kernel but the drivers I installed for the wireless card on this one didn't appear to be on there so I just reloaded this server kernel.  Thanks

---

### Post by praseodym on 2012-02-12
The card is not recognized with "lspci". Check the BIOS settings, and you may reset the BIOS.

---

### Post by terp08 on 2012-02-12
> **praseodym said:**
> Please show:

```
lspci -nnk | grep -iA2 net
dmesg | egrep 'rt5|rt2'
```Why do you use a server kernel?

> **praseodym said:**
> The card is not recognized with "lspci". Check the BIOS settings, and you may reset the BIOS.

[B]lspci -nnk | grep -i net

```


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
02:00.0 Network controller [0280]: Ralink corp. Device [1814:5390]


```[/B]
When I run the command like this, it does show my wireless card.  Does the command have to be exactly as you posted earlier?  I'm not seeing a wifi enable/disable option in the BIOS menu.  Also, I have Ubuntu set up as a dual boot and when I log into Win7 wifi is enabled.

---

### Post by praseodym on 2012-02-12
Uninstall that driver with

```
cd [COLOR="Red"]NameOfFolder/[/COLOR]
make clean
make
sudo make uninstall
```
and try this one:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/3473742/Ralink_5390sta-2.5.0.3_dkms.tar.gz
sudo tar xvf Ralink_5390sta-2.5.0.3_dkms.tar.gz -C /usr/src
sudo dkms add -m Ralink_5390sta -v 2.5.0.3
sudo dkms build -m Ralink_5390sta -v 2.5.0.3
sudo dkms install -m Ralink_5390sta -v 2.5.0.3 
```
or the single installation from here
[http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3208747](http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3208747)
the post above.

---

### Post by terp08 on 2012-02-12
That's actually what I originally did from your other post at:   

[http://ubuntuforums.org/showthread.php?t=1901893](http://ubuntuforums.org/showthread.php?t=1901893)

I'll give it another go though.

---

### Post by terp08 on 2012-02-12
Tried what you asked above.  Here are some of the results you wanted from the other thread.  Maybe I should do a fresh re-install of Ubuntu and try this again unless you can think of anything else?  Thanks again for the assistance.
[B]
uname -a[/B]

```

Linux ubuntu 2.6.38-13-server #55-Ubuntu SMP Tue Jan 24 15:52:18 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```[B]iwconfig
[/B]
```

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```[B]
sudo iwlist scan
[/B]
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       No scan results

```

---

### Post by praseodym on 2012-02-12
Try the classis debian-way

```
sudo su
make
make install
exit
```
Or try an earlier driver version:

[http://forum.ubuntuusers.de/topic/wlan-auf-asus-a73s-laptop-einrichten/#post-2960487](http://forum.ubuntuusers.de/topic/wlan-auf-asus-a73s-laptop-einrichten/#post-2960487)

---

### Post by terp08 on 2012-02-12
I did a re-install and then followed your steps outlined above. I am now running Ubuntu 11.04 desktop version.  When I run **lspci -nnk | grep -iA2 net** I now get results.

**lspci -nnk | grep -iA2 net**

```

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:3591]
    Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Ralink corp. Device [1814:5390]
    Subsystem: Hewlett-Packard Company Device [103c:1636]
    Kernel driver in use: rt2860

```Apart from this, everything else seems the same and still no wireless.

---

### Post by praseodym on 2012-02-12
Did you blacklist the module rt2800pci?

---

### Post by terp08 on 2012-02-12
The newer driver did the trick.  Thanks bro.

---

