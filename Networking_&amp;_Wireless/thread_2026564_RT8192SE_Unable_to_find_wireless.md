---
title: "RT8192SE Unable to find wireless"
date: 2012-07-15
forum: Networking &amp; Wireless
---

### Post by da_buddar on 2012-07-15
Currently on Samsung NP-N310 Netbook, after swapping the HDD from a broken ACER ASPIRE 5100, Ubuntu 11.10, 3.0.0-22-generic i686
. The netwook initially worked and then dropped, occasionally picking wlan&#347; but not as off the last 5 reboots. 

I´ve changed the network manager to WICD

I have run all the apt-get update, upgrade, etc. Downloaded the latest rt8192SE driver, following this post: [http://ubuntuforums.org/archive/index.php/f-336-p-243.html](http://ubuntuforums.org/archive/index.php/f-336-p-243.html)

¨If the make install fails (as it did for me) you can manually install the driver using these steps:

[1] Copy the target module in HAL/rtl8192/rt8192se_pci.ko to /lib/modules/`uname -r`/kernel/drivers/net/wireless/
[2] Copy rtl8192se firmware folder to /lib/firmware/`uname -r`
[3] Run the command of `depmod -a`
[4] Run the command of 'modprobe rtl8192se_pci', or reboot.
[5] Check the NetworkManager, and see whether there's network list show out?¨

Nothing has worked after about 6hrs of trying!

So here´s my info, hopefully something really simple that will prevent further hours of frustration!

Thanks in advance, all other PC&#347; some 6, non linux machines have no issues with WLAN.

This is the problem:

**iwlist scan**

lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan2     No scan results

Here are all the details of system setup:

**LSPCI=**


02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller (rev 01)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)

**ifconfig =**

eth1      Link encap:Ethernet  HWaddr 00:24:54:0a:f2:7a  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:54ff:fe0a:f27a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9067 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7643 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7496958 (7.4 MB)  TX bytes:1109834 (1.1 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1592 (1.5 KB)  TX bytes:1592 (1.5 KB)

wlan2     Link encap:Ethernet  HWaddr 00:24:d2:f6:93:8b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:f8068000-f8068100 

**iwconfig = **

lo        no wireless extensions.

eth1      no wireless extensions.

wlan2     802.11bgn  Mode:Managed  Frequency=2.462 GHz  
          Access Point: Not-Associated   Bit Rate:1 Mb/s   
          Retry: on   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**lsmod =**

r8192e_pci            234281  0 
rtl8192se              94139  0 
rtlwifi                95614  1 rtl8192se
mac80211              393421  2 rtl8192se,rtlwifi

**dmesg | grep wlan2 = **

[   49.622228] udevd[344]: renamed network interface wlan0 to wlan2
[   66.040071] wlan2: no IPv6 routers present
[   78.729419] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   81.913821] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  128.401558] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  130.893519] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  256.045529] ADDRCONF(NETDEV_UP): wlan2: link is not ready

**sudo lshw -C network =**

*-network               
       description: Wireless interface
       product: RTL8192E/RTL8192SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan2
       version: 01
       serial: 00:24:d2:f6:93:8b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xE latency=0 multicast=yes wireless=802.11bgn
       resources: irq:16 ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 13
       serial: 00:24:54:0a:f2:7a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.105 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 memory:f0200000-f0203fff ioport:3000(size=256)

---

### Post by chili555 on 2012-07-15
> r8192e_pci 234281 0
rtl8192se 94139 0
rtlwifi 95614 1 rtl8192se
mac80211 393421 2 rtl8192se,rtlwifiI expect you need r8192e_pci *OR* rtl8192se but not both. One needs to be blacklisted for the other to work properly. Detach the ethernet cable so Network Manager works properly and unload first one and then the other:```
sudo modprobe -r r8192e_pci
sudo modprobe rtl8192se
```Is it working? Try the other and we'll blacklist the one that doesn't work well.

---

### Post by Kirk Schnable on 2012-07-15
> **chili555 said:**
> I expect you need r8192e_pci *OR* rtl8192se but not both. One needs to be blacklisted for the other to work properly. Detach the ethernet cable so Network Manager works properly and unload first one and then the other:```
sudo modprobe -r r8192e_pci
sudo modprobe rtl8192se
```Is it working? Try the other and we'll blacklist the one that doesn't work well.

That sounds correct chili555.  I had to deal with a problem with (if memory serves me) this exact chipset at work.  I had to blacklist some modules to make it work reliably.

If you guys don't have this figured out by tomorrow, I'll grab one of those laptops tomorrow while I'm at work and find the blacklist config I wrote.

Kirk

---

### Post by da_buddar on 2012-07-16
Cheers for the quick reply, this is version two as I was writing the first while experimenting with the drivers. 

**Blacklisting r8192e_pci worked**, allowing the wlan to scan, however it results in a bad password always being shown, while adding rtl8192se to the blacklist and **loading the _pci driver, resulted in a crash** and a trace call pointing to r8192e_pci. So I assume that's not the one that works!

So the modprobe commands alone didn´t do anything (unless there is a specific time delay) however when I edited the **etc/modprobe.d/blacklist.conf** after running ´**sudo nautilus**'to get admin right on the file, and then using the same commands you gave previously, network manager picked up the networks. (unsure when modprobe is used, had to read a little on wikipedia to get a grip of it)

Now that it is scanning and finding the networks, **the next issue is the bad password**. I´m using a wifi adapter (WLAN1) which connects fine, comparing the two settings, both WPA PSK and the correct P/W, however (WLAN2 the problem) still doesn´t want to connect. The work around is to MAC filter the router, however the apples in the house don´t seem to like that. Having a look now and will report back if I find any articles pertinent to solving this.

---

### Post by chili555 on 2012-07-16
> when I edited the etc/modprobe.d/blacklist.conf after running ´sudo nautilus'to get admin right on the file,You need to remove what you added and add this only on its oown new line:```
blacklist r8192e_pci
```Save, close, reboot and check:```
lsmod | grep 819
```Hopefully, only rtl8192se and its dependencies rtlwifi and mac80211 are loaded. Does it connect?

---

### Post by da_buddar on 2012-07-16
I´ve blacklisted the item as instructed

lsmod =

rtl8192se              94139  0 
rtlwifi                95614  1 rtl8192se
mac80211              393421  2 rtl8192se,rtlwifi
r8192se_pci           423358  0 

Do I need to black list r8192se_pci also? When I modprobe -r it and checked that lsmod wasn showing it, there was no difference. After reboot it reappeared.

---

### Post by chili555 on 2012-07-17
> Do I need to black list r8192**s**e_pci also? Yes, please. Then reboot and tell us if it's working. If not, what are your symptoms?

---

### Post by da_buddar on 2012-07-17
So blacklisting r8192se_pci results in WLAN2 being unable to find any results. With the item, WLAN2 does not accept any passwords.

Following the instructions by realtek:

Download = rtl8192se_linux_2.6.0010.1012.2009

> 
Release Date: 2009-1012, ver 0010 
RTL8192SE Linux driver
   --This driver supports RealTek rtl8192SE PCI Wireless LAN NIC
     for
     2.6 kernel:
     Fedora Core 2/3/4/5, Debian 3.1, Mandrake 10.2/Mandriva 2006, 
     SUSE 9.3/10.1/10.2, Gentoo 3.1, Ubuntu 7.10/8.04/8.10/9.04/9.10, 
     moblin(V2), android-x86_090916, etc.
     2.4 kernel:
     Redhat 9.0/9.1

***IT STATES:***

¨cp -rf firmware/RTL8192SE /lib/firmware
          or
            cp -rf firmware/RTL8192SE /lib/firmware/(KERNEL_VERSION)
          Note: This depends on whether (KERNEL_VERSION) subdirectory exists under /lib/firmware¨

I have checked this and the folder is present, in both, with rtl8192sfw.bin inside.

the folder ´firmware´ also contains the following

/lib/firmware/rtl8192sfw.bin
/lib/firmware/rtl8192sfw74.bin
/lib/firmware/rtl8192sfw492.bin

And the kernel contains:

/lib/modules/3.0.0-22-generic/kernel/drivers/net/wireless/r8192se_pci.ko

running sudo lshw -C network, with usb wlan2 attached.

  *-network UNCLAIMED     
       description: Network controller
       product: RTL8192E/RTL8192SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 13
       serial: 00:24:54:0a:f2:7a
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:f0200000-f0203fff ioport:3000(size=256)
  *-network
       description: Wireless interface
       physical id: 3
       bus info: usb@1:3
       logical name: wlan1
       serial: 00:1f:1f:ac:25:b9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=192.168.1.108 multicast=yes wireless=IEEE 802.11bgn

What does ´UNCLAIMED´ mean?

There is a alternative driver, from the realtek site:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

~/Downloads/92ce_se_de_linux_mac80211_0005.1230.2011.tar.gz

Is there a way of removing all the other drivers from v2009?

---

### Post by chili555 on 2012-07-17
> lsmod =

[COLOR="Red"]rtl8192se[/COLOR] 94139 0
rtlwifi 95614 1 rtl8192se
mac80211 393421 2 rtl8192se,rtlwifi
[COLOR="Red"]r8192se_pci[/COLOR] 423358 0
Is rtl8192se still loaded? What all is blacklisted now?

---

### Post by da_buddar on 2012-07-21
r8192e_pci is the only item blacklisted, when I black list the other,r8192se_pci, the wifi ceases to pickup any networks. With it the wifi networks are showing, but bad passwords is the issue.

Is there a way of finding all the items that relate to the rlt8192se? How would I completely remove them? I think its worth trying the v2011 of the drivers as these are for v2009 and corresponding ubuntu releases.

---

### Post by chili555 on 2012-07-21
> Is there a way of finding all the items that relate to the rlt8192se? How would I completely remove them? If you build the 2011 version, it will automatically replace the 2009 version. Leave the blacklist you have in place.> I think its worth trying the v2011 of the driversSure; please proceed. Do you need some additional guidance to compile?

---

### Post by da_buddar on 2012-07-27
I´ve read the readme and its just a matter of make + make install, which is as simple as it gets, i´ll report back if it solves. Thanks your help so far.

---

### Post by Superpelican12 on 2012-08-01
Don't know if this is really helpful to you guys, but 
I'm pretty sure I downloaded a 2013 version for the Rtl8192se
today from the official realtek site ;) Just google the card.

According to the name of the archive file it works up to Linux kernel 3.2.x!
So it should work with Ubuntu 12.04. I'll post the link tomorrow
when I'm online with my laptop again.

I'm going to help somebody install Xubuntu on his netbook.
Which is a Samsung Np-N210-jp01nl. I'm not sure which network card
it comes with, as each country has it's own version of the netbook.
And I read the German version had a Atheros Ar9285, while the UK
version seems to have Realtek Rtl8192se. I'm not sure which card the Dutch 
version has :(. If you don't mind I'll post my experiences installing Xubu ln the netbook in this topic (well only the wireless card part of course).

EDIT: Unfortunately the " 2013" part wasn't in the name of the linux driver, but in the name of a Windows driver I downloaded :( .
However I do think I have found a newer version of the driver for the rtl8192se here's the link to the official Realtek website's downloadpage:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE) 
Make sure you download the Unix/Linux version and the version meant for kernels up to 3.2.x

I hope this helpful ;)

Also are there specific 32-bit and 64-bit versions of drivers? I thought that only depends on whether you compile the source on either a 32 or 64-bit computer. Am I right?

---

