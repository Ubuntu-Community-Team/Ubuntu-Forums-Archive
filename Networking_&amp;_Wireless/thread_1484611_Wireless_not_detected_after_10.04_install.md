---
title: "Wireless not detected after 10.04 install"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by John Wiersba on 2010-05-15
During the 10.04 Lucid install, my wireless is detected and DHCP is setup.  (Wireless works perfectly in 9.04 Jaunty that I just tried from the live CD).  But after the 10.04 install, Network Manager keeps prompting for the WEP password.

This is a fresh and fully updated install on a Dell Latitude C640, but I don't know what kind of wireless card it has because it is not reported by lspci (or lsusb).

During the install of 10.04, it detects:
   - eth1: wireless ethernet (802.11x)
which is properly highlighted instead of:
   - eth0: 3Com Corporation 3c905C--Tx/Tx-M (Tornado)
which I had unplugged during the install.  The install accepts the WEP key of the form s:XXXXX and reports that network autoconfiguration succeeded.  The installation proceeds without any problems.

However, after the install, NM keeps prompting for the WEP password as if it is bad, which it is not.  Also, I can see the WEP password in /etc/network/interfaces, recorded correctly during the install.

$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)

$ lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I have seen similar reports elsewhere in the forums, but since I don't know the wireless card I have (because it's not reported by lspci) I'm not quite sure what to do.  Is there some other way of determining which wireless card I have?  Wired ethernet works fine.  Wireless works fine in a 9.04 Live CD.  I have tried a few of the less invasive suggestions to try to cure this but without luck.

---

### Post by purelinuxuser on 2010-05-16
> **John Wiersba said:**
> I have seen similar reports elsewhere in the forums, but since I don't know the wireless card I have (because it's not reported by lspci) I'm not quite sure what to do.  Is there some other way of determining which wireless card I have?  Wired ethernet works fine.  Wireless works fine in a 9.04 Live CD.  I have tried a few of the less invasive suggestions to try to cure this but without luck.

For finding the wireless card, try```
lshw -c network
```  ;) Also, is it a PCI, or USB?

Please post the output of```
ifconfig
iwconfig
``` too.

---

### Post by John Wiersba on 2010-05-16
Thanks for the reply, Pure.  Here is the output (BTW, apparently lshw should be run with sudo): 

```

$ sudo lshw -c network
  *-network
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:0b:db:a2:99:a7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.40 latency=32 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: irq:11 ioport:ec80(size=128) memory:f8fffc00-f8fffc7f memory:4c000000-4c01ffff(prefetchable)
  *-network
       description: TrueMobile 1150 Series PC Card
       product: Version 01.01
       vendor: Dell
       physical id: 0
       slot: Socket 2
       resources: irq:5
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:6b:71:50
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:db:a2:99:a7  
          inet addr:192.168.1.40  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:dbff:fea2:99a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:921 errors:0 dropped:0 overruns:0 frame:0
          TX packets:776 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:812431 (812.4 KB)  TX bytes:114730 (114.7 KB)
          Interrupt:11 Base address:0xcc00 

eth1      Link encap:Ethernet  HWaddr 00:02:2d:6b:71:50  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Base address:0xe100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"*********"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by wideaperture on 2010-05-16
I had this issue and spent several days on IRC and elsewhere trying to figure it out.  My wireless card had been detected by a previous install and was nowhere to be found when I wiped and installed 10.04 (note: I was installing Lubuntu, not Ubuntu but the base system should still have been the same).  What I finally did that worked—and it may be a bit extreme for some—was to wipe everything and start over, this time not with the full install disk, but using a minimal install disk and installing the rest of the system from the command line via an ethernet connection.  I'm still resolving a few issues with wireless, but the system now recognizes my wireless card, which is a big step.

Here's the URL for the i386 minimal install iso ("mini.iso") if anyone needs it:

[http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/netboot/)

---

### Post by John Wiersba on 2010-05-16
> **wideaperture said:**
>  What I finally did that worked—and it may be a bit extreme for some—was to wipe everything and start over, this time not with the full install disk, but using a minimal install disk and installing the rest of the system from the command line via an ethernet connection.  


That makes sense to me, because my wireless **was** recognized during the install.  It's only after the install that it doesn't work.

---

### Post by wideaperture on 2010-05-16
The full installer didn't recognize my wireless card during installation and the subsequent installation didn't either.  However, the minimal installer *did* recognize my wireless card, and the subsequent installation does.

However, I'm still in the same boat with folks (in the other threads) whose network managers are suddenly telling them in 10.04 that their correct WEP passwords are incorrect when trying to connect to a wireless hub.  But that's an entirely separate problem.  It annoys the hell out of me, though, since *during* installation I actually used the same wireless card with the same wireless router successfully, yet the subsequent install doesn't want to let me connect.  Grr. </rant>

---

### Post by rhyz on 2010-05-16
Im having the same problem still not any closer to sorting it out, I've had it working fine in older versions 9.04 8.10 but now it is messed up! When installing with initrd and vmlinuz it asks to connect to the internet and startds downloading using wireless but i cant download as slow and unstable, So i also have alternate iso which it used but if it uses alternate iso it wont find the network its a right pain people have tried to help but nothing Sorry to say If i still didnt have XP i would be stuffed.

---

### Post by NUboon2Age on 2010-05-16
> **rhyz said:**
> Im having the same problem still not any closer to sorting it out, I've had it working fine in older versions 9.04 8.10 but now it is messed up! When installing with initrd and vmlinuz it asks to connect to the internet and starts downloading using wireless but i cant download as slow and unstable, So i also have alternate iso which it used but if it uses alternate iso it wont find the network its a right pain people have tried to help but nothing Sorry to say If i still didnt have XP i would be stuffed.

Is it the same problem? Do you have the same computer model as this person and have a TrueMobile 1150 Series PC Card?  If so, please provide the results of 

sudo lshw -C network
sudo ifconfig
sudo iwconfig

If not please start a new thread and post these details.

---

### Post by rhyz on 2010-05-17
Hi same problem but different model.

Rm cy25 with a melco wireless card,

Have already got one open nothing fixed yet :/

---

### Post by xolotl4 on 2011-01-26
Hi i have a dell C640 with truemobille 1150 wireless card, i was using hardy without problems, i switched to 10.10 and i was not able to connect to any wireless net, i installed from Synaptic the software called **Wicd** and i used it to connect and manage mi wireless card, now every ting is ok.

---

### Post by rhyz on 2011-01-26
Hi i didnt try wicd in 10.10 but did in 10.04 and had no luck! :/

---

