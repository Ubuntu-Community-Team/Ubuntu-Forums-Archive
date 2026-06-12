---
title: "Need help getting WUSB54GC to work in 8.10"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by jimbob on 2009-03-07
I purchased this USB dongle after reading about how it worked "out of the box" on several forum entries.  Unfortunately mine does not.  The hardware is OK because it works fine in XP.

  It is not even recognized when I plug it in (dmesg output):
> [30862.192036] usb 3-1: new high speed USB device using ehci_hcd and address 13
[30862.368255] usb 3-1: configuration #1 chosen from 1 choice


lsusb  | grep Linksys gives this:
> Bus 003 Device 013: ID 1737:0077 Linksys

ifconfig -a

> eth0      Link encap:Ethernet  HWaddr 00:14:85:bf:7c:b3  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:febf:7cb3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16672 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12004442 (12.0 MB)  TX bytes:3205262 (3.2 MB)
          Interrupt:22 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23152 (23.1 KB)  TX bytes:23152 (23.1 KB)


iwconfig

> lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


There are several procedures in the forums to download drivers but how can I tell which one I need; ralinkxxxx or rt2870xxx, etc?
It is almost as if they have used a completely different chip in this one or something.

---

### Post by jimbob on 2009-03-08
I think I might know what my problem is.  I poked around on the installation CD for Windows and found a device ID=Ralink_3070.ndi mentioned.
On the Ralink Linux driver site there was a new driver RT3070USB(RT307x)
 12/25/2008 2.0.1.0 which came out at the end of 2008.  I have been installing the rt2870 driver up until now so gave the new one a try.

  It throws off an error on the make which I cannot get by:
>   CC [M]  /home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../sta/wpa.o
  CC [M]  /home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/rt_linux.o
  CC [M]  /home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/rt_main_dev.o
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/rt_main_dev.c: In function ‘rt28xx_init’:
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/rt_main_dev.c:439: warning: unused variable ‘MacValue’
  CC [M]  /home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.o
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_giwscan’:
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1116: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1116: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1116: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1116: error: too few arguments to function ‘iwe_stream_add_event’
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1195: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1195: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1195: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1195: error: too few arguments to function ‘iwe_stream_add_event’
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1211: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1211: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1211: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1211: error: too few arguments to function ‘iwe_stream_add_point’
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1238: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1238: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1238: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1238: error: too few arguments to function ‘iwe_stream_add_event’
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1258: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1258: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1258: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1258: error: too few arguments to function ‘iwe_stream_add_event’
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1273: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1273: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1273: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1273: error: too few arguments to function ‘iwe_stream_add_event’
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1291: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1291: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1291: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1291: error: too few arguments to function ‘iwe_stream_add_point’
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1321: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1321: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1321: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1321: error: too few arguments to function ‘iwe_stream_add_value’
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1343: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1343: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1343: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1343: error: too few arguments to function ‘iwe_stream_add_point’
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1361: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1361: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1361: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.c:1361: error: too few arguments to function ‘iwe_stream_add_point’
make[2]: *** [/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.o] Error 1
make[1]: *** [_module_/home/jaspmatt/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [LINUX] Error 2
r 

I guess I'll post this on Ralink support and see what happens.

If anyone can help here it would be greatly appreciated.

---

### Post by Ayuthia on 2009-03-08
I am not 100% positive on this, but the errors look like you need a patch.  It looks like the source you are compiling is for kernels less than 2.6.27.  You might try a search on RaLink 2.6.27 patch and you might find something.

---

### Post by jimbob on 2009-03-08
Thanks for the reply.  I spent all afternoon researching the (a?) patch that applied here but couldn't find anything.  I should mention that the RT2870 source code compiles fine on my kernel 2.6.27-generic so I think that the problem is somewhere in their C-code but I could be wrong.  I have an updated chip, an RT3070, the code for which they evidently issued after bastardizing the RT2870 software.  Take a look at what this person thinks of it:
> This is my candidate for the crappiest Linux driver ever created. They
basically took the rt2870 driver and modified it to support rt3070. There is
nothing wrong for them with stealing their own code. But there were a few
issues that I had to solve:

- For some reason they took an older rt2870 driver version and modified it.
Hence the driver will not compile for Fedora kernels 2.6.25 and newer. So I had
the re-introduce our iwe-stream patch.

- They did not even bother to change the filenames or variable names in the
code. The code says "rt2870" but it actually means "rt3070". Confusing. I had
to rename the RT2870STA.DAT file to  RT3070STA.DAT to avoid conflicts with our
rt2870 kmod.

Other than these two things, both the common and the kmod package is identical
to our rt2870 packages in rpmfusion.


I admit that this package is crap. But still, there might be people who can
benefit from it.


  (from [http://www.mail-archive.com/rpmfusion-developers@lists.rpmfusion.org/msg03357.html](http://www.mail-archive.com/rpmfusion-developers@lists.rpmfusion.org/msg03357.html))

I have sent an email to Ralink Tech Support (Taiwan) requesting a fix for the compile errors so we'll see if and how they respond.

EDIT: I wonder if I converted these two rpm's to deb's it would work??

 [http://oget.fedorapeople.org/review/rt3070-kmod-2.0.1.0-1.fc10.src.rpm](http://oget.fedorapeople.org/review/rt3070-kmod-2.0.1.0-1.fc10.src.rpm)
 
  [http://oget.fedorapeople.org/review/rt3070-2.0.1.0-1.fc10.src.rpm](http://oget.fedorapeople.org/review/rt3070-2.0.1.0-1.fc10.src.rpm)

---

### Post by jimbob on 2009-03-10
if anyone has had success in getting the new RT3070 driver module from Ralink to compile please reply to this thread.

---

### Post by jimbob on 2009-03-22
I have found a patch on this site but I need help in applying the patch.

[http://lobmenschen.de/index.php/Howtos](http://lobmenschen.de/index.php/Howtos)

Do I include it inline after the original source code before I do the make or what?  I need specific directions if someone would be so kind.

---

### Post by monkeyking on 2009-03-31
I just bought one of these still unpacked in plastic.

From what I've read,
there are 3 different chipsets used in various version of wusb54gc.

Can you tell me which are good,
which are bad.

And how to check it?

thanks.

---

### Post by monkeyking on 2009-03-31
I dared to unpack it, and plug it.

It works out of the box,
afterwards I found this
[https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC)

---

### Post by jimbob on 2009-04-07
I received a new driver from Ralink for the RT3070 chipset and have been trying to get it to work.  I have a Linksys wireless router I'm trying to connect to but for some reason besides a device named ra0 being created it also creates one called ra0:avhi and this is the one that gets an IP assigned - not ra0. Here is the pertinent portion of syslog from the time I plugged in the device until the time I unplugged it:
```
Apr  7 15:49:16 user1-desktop -- MARK --
Apr  7 16:09:16 user1-desktop -- MARK --
Apr  7 16:15:04 user1-desktop kernel: [24365.133773] ATL1E 0000:01:00.0: ATL1E: eth0 NIC Link is Down
Apr  7 16:17:01 user1-desktop /USR/SBIN/CRON[6388]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  7 16:28:45 user1-desktop kernel: [25186.892034] usb 1-5: new high speed USB device using ehci_hcd and address 3
Apr  7 16:28:46 user1-desktop kernel: [25187.058770] usb 1-5: configuration #1 chosen from 1 choice
Apr  7 16:28:46 user1-desktop kernel: [25187.059722] 
Apr  7 16:28:46 user1-desktop kernel: [25187.059724] 
Apr  7 16:28:46 user1-desktop kernel: [25187.059724] === pAd = f8d5e000, size = 471500 ===
Apr  7 16:28:46 user1-desktop kernel: [25187.059725] 
Apr  7 16:28:46 user1-desktop kernel: [25187.059734] <-- RTMPAllocAdapterBlock, Status=0
Apr  7 16:28:46 user1-desktop kernel: [25187.381428] <-- RTMPAllocTxRxRingMemory, Status=0
Apr  7 16:28:46 user1-desktop kernel: [25187.383533] -->RTUSBVenderReset
Apr  7 16:28:46 user1-desktop kernel: [25187.384027] <--RTUSBVenderReset
Apr  7 16:28:46 user1-desktop kernel: [25187.697631] Key1Str is Invalid key length(0) or Type(0)
Apr  7 16:28:46 user1-desktop kernel: [25187.697674] Key2Str is Invalid key length(0) or Type(0)
Apr  7 16:28:46 user1-desktop kernel: [25187.697714] Key3Str is Invalid key length(0) or Type(0)
Apr  7 16:28:46 user1-desktop kernel: [25187.697756] Key4Str is Invalid key length(0) or Type(0)
Apr  7 16:28:46 user1-desktop kernel: [25187.699124] 1. Phy Mode = 9
Apr  7 16:28:46 user1-desktop kernel: [25187.699128] 2. Phy Mode = 9
Apr  7 16:28:46 user1-desktop kernel: [25187.730291] RTMPSetPhyMode: channel is out of range, use first channel=1 
Apr  7 16:28:46 user1-desktop kernel: [25187.743412] 3. Phy Mode = 9
Apr  7 16:28:46 user1-desktop kernel: [25187.750913] MCS Set = ff 00 00 00 01
Apr  7 16:28:46 user1-desktop kernel: [25187.815908] <==== rt28xx_init, Status=0
Apr  7 16:28:46 user1-desktop kernel: [25187.817538] 0x1300 = 00064300
Apr  7 16:28:46 user1-desktop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_usb_device_1737_77_1_0, iface: ra0): not well known
Apr  7 16:28:46 user1-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Apr  7 16:28:46 user1-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Apr  7 16:28:46 user1-desktop dhclient: All rights reserved.
Apr  7 16:28:46 user1-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr  7 16:28:46 user1-desktop dhclient: 
Apr  7 16:28:47 user1-desktop dhclient: Listening on LPF/ra0/00:23:69:0d:46:89
Apr  7 16:28:47 user1-desktop dhclient: Sending on   LPF/ra0/00:23:69:0d:46:89
Apr  7 16:28:47 user1-desktop dhclient: Sending on   Socket/fallback
Apr  7 16:28:48 user1-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
Apr  7 16:28:48 user1-desktop avahi-daemon[4484]: Registering new address record for fe80::223:69ff:fe0d:4689 on ra0.*.
Apr  7 16:28:56 user1-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 19
Apr  7 16:28:57 user1-desktop kernel: [25198.612008] ra0: no IPv6 routers present
Apr  7 16:29:15 user1-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
Apr  7 16:29:29 user1-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 16
Apr  7 16:29:45 user1-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
Apr  7 16:29:49 user1-desktop dhclient: No DHCPOFFERS received.
Apr  7 16:29:49 user1-desktop dhclient: No working leases in persistent database - sleeping.
Apr  7 16:29:49 user1-desktop avahi-autoipd(ra0)[6682]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 112).
Apr  7 16:29:49 user1-desktop avahi-autoipd(ra0)[6682]: Successfully called chroot().
Apr  7 16:29:49 user1-desktop avahi-autoipd(ra0)[6682]: Successfully dropped root privileges.
Apr  7 16:29:49 user1-desktop avahi-autoipd(ra0)[6682]: Starting with address 169.254.4.226
Apr  7 16:29:54 user1-desktop avahi-autoipd(ra0)[6682]: Callout BIND, address 169.254.4.226 on interface ra0
Apr  7 16:29:54 user1-desktop avahi-daemon[4484]: Joining mDNS multicast group on interface ra0.IPv4 with address 169.254.4.226.
Apr  7 16:29:54 user1-desktop avahi-daemon[4484]: New relevant interface ra0.IPv4 for mDNS.
Apr  7 16:29:54 user1-desktop avahi-daemon[4484]: Registering new address record for 169.254.4.226 on ra0.IPv4.
Apr  7 16:29:58 user1-desktop avahi-autoipd(ra0)[6682]: Successfully claimed IP address 169.254.4.226
Apr  7 16:30:38 user1-desktop ntpdate[6735]: can't find host ntp.ubuntu.com 
Apr  7 16:30:38 user1-desktop ntpdate[6735]: no servers can be used, exiting
Apr  7 16:36:06 user1-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
Apr  7 16:36:13 user1-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
Apr  7 16:36:21 user1-desktop dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
Apr  7 16:36:21 user1-desktop kernel: [25642.343658] usb 1-5: USB disconnect, address 3
Apr  7 16:36:21 user1-desktop kernel: [25642.343745] Bulk In Failed. Status=-108, BIIdx=0x1, BIRIdx=0x1, actual_length= 0x0
Apr  7 16:36:21 user1-desktop kernel: [25642.353692] #
Apr  7 16:36:21 user1-desktop kernel: [25642.358659] #
Apr  7 16:36:21 user1-desktop kernel: [25642.363625] #

```

I would expect an IP of something like 192.168.1.xxx so where does it come up with 169.254.4.226 (which fails as the log shows).  Also attached is my RT3070STA.dat control file.  I feel I am very close to having it work if anyone can help.

---

### Post by jimbob on 2009-04-08
Believe it or not I got it to work great by setting it up as an open AP with no encryption, so I guess my WPA2 with pass-key is not letting me connect.
Are there any wpa_supplicant experts out there?

---

### Post by DragonKeeper on 2009-04-08
> **jimbob said:**
> Believe it or not I got it to work great by setting it up as an open AP with no encryption, so I guess my WPA2 with pass-key is not letting me connect.
Are there any wpa_supplicant experts out there?

Where did you find the firmware? I can't find one on the website.

---

### Post by jimbob on 2009-04-09
Ralink sent it to me as a tarball but Ubuntu won't upload that file type.

Let me know how to send it to you and I will.

---

### Post by hmmdar on 2009-05-17
> **jimbob said:**
> Believe it or not I got it to work great by setting it up as an open AP with no encryption, so I guess my WPA2 with pass-key is not letting me connect.
Are there any wpa_supplicant experts out there?

I have an similar issue, i can connect to an open network by command line, (not with network manager), but as soon as i try it with a WPA connection the system is unable to get a response to its DHCPDICOVERY.

I did notice one thing on my router's status window.  When my wusb54gc v3 + ubuntu 9.04 system is attempting to do a DHCPDICOVERY on my router, my router shows the adapter in its status window, but it is showing it with a Sig strength of 0%, DB of -92, and Sig to Noice Ratio of 92.

The router status window will also only show the adapter attempting to connect for short periods before it is removed from the status window.  a few seconds later it reapers with same signal information.  It keeps this up for about a minute or so before the DHCPDISCOVER fails and it stops looking.

---

