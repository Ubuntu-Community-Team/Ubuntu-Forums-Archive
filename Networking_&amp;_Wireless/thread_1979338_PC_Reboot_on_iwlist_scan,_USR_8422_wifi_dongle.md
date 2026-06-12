---
title: "PC Reboot on iwlist scan, USR 8422 wifi dongle"
date: 2012-05-13
forum: Networking &amp; Wireless
---

### Post by amebaspugnosa on 2012-05-13
Hello everybody,

I am trying to give a new life to an old PC (Acer Aspire 1350) with a minimal installation of Lubuntu 12.04.

Everything went smooth, except for the wireless. The PC is equipped with a US Robotics 8422 wifi dongle, which it is supported via Ndiswrapper.

I followed the guide on Ndiswrapper and used the driver suggested on the Ndiswrapper's wiki: downloaded the latest version, disabled the default p54* drivers, compiled, loaded the .inf driver, and successfully loaded the kernel module. I also tried using the apt ndiswrapper package.

[B]When I do sudo iwlist wlan0 scan, or I use a gui tool to configure the network, the system reboots without a hint.
[/B]
Ndiswrapper -l returns:

```
rsc4usb : driver installed
	device (0BAF:0118) present (alternate driver: p54usb)

```

Dmesg returns:

```

[  278.024874] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[  278.184085] usb 1-3: reset high-speed USB device number 2 using ehci_hcd
[  278.362952] ndiswrapper: driver rsc4usb (U.S. Robotics,11/16/2005, 3.3.36.0) loaded
[  280.368145] wlan0: ethernet device 00:14:c1:01:3e:dc using NDIS driver: rsc4usb, version: 0x30324, NDIS version: 0x501, vendor: 'U.S. Robotics Wireless USB Adapter', 0BAF:0118.F.conf
[  280.368256] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[  280.368390] usbcore: registered new interface driver ndiswrapper
```

lshw -C network returns:

```
 *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:c1:01:3e:dc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rsc4usb driverversion=1.57+U.S. Robotics,11/16/2005, 3 link=no multicast=yes wireless=IEEE 802.11g
```

And iwconfig returns:

```
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:2 Mb/s   Tx-Power:19 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Since the network seems disabled, I also tried with ifconfig wlan0 up, but with no luck :/

Any idea?

---

### Post by chili555 on 2012-05-13
> disabled the default p54* driversMind if we take a look? Please run and post:```
lsmod | grep p54
cat /etc/modprobe.d/blacklist.conf | tail -n5
rfkill list all
```Did you install ndiswrapper because the native p54usb also showed as disabled? I think it is not a driver error. Thanks.

---

### Post by amebaspugnosa on 2012-05-13
Hi, thank you! Here the results:

```
lsmod | grep p54
(no results)
```

```
cat /etc/modprobe.d/blacklist.conf | tail -n5
blacklist p54usb
blacklist p54common
blacklist prism54usb
blacklist prism54common
```

I added both p54* and prism54*, because I read in the troubleshooting guide that they are seen as alias.

```
rfkill list all
(no results)
```

---

### Post by chili555 on 2012-05-13
Looks perfect so far. We need to dig deeper. Please post:```
sudo modprobe ndiswrapper
ndiswrapper -l
dmesg | grep ndis
```You might also check here to see if there is any clue as to the reboot:```
sudo less /var/log/syslog
```Scroll back and forth with the arrow keys and look for a timestamp that relates to a reboot. See what happened around that time. For example:> May 13 [COLOR="Red"]18:17:01[/COLOR] LAPTOP60 CRON[13144]: (root) CMD The highlighted part is the time of day.

Get out of less with q.

I love a mystery!

---

### Post by amebaspugnosa on 2012-05-14
Ok, thank you again. The first commands run smooth

```
luciano@ubuntu:~$ sudo modprobe ndiswrapper 
[sudo] password for luciano: 
luciano@ubuntu:~$ ndiswrapper -l
rsc4usb : driver installed
	device (0BAF:0118) present (alternate driver: p54usb)
```

and dmesg reports:

```
luciano@ubuntu:~$ dmesg | grep ndis
[  100.928613] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[  101.263653] ndiswrapper: driver rsc4usb (U.S. Robotics,11/16/2005, 3.3.36.0) loaded
[  103.267883] usbcore: registered new interface driver ndiswrapper
```

I can see wlan0 with iwconfig. In lshw I see that the device is disabled, so let enable it:

```
luciano@ubuntu:~$ sudo lshw -C network

...

  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:c1:01:3e:dc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rsc4usb driverversion=1.57+U.S. Robotics,11/16/2005, 3 link=no multicast=yes wireless=IEEE 802.11g

luciano@ubuntu:~$ sudo ifconfig wlan0 up

luciano@ubuntu:~$ sudo lshw -C network

...

 *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:c1:01:3e:dc

```

Now let's make it crash:

```
luciano@ubuntu:~$ date
lun 14 mag 2012, 08.36.35, CEST
luciano@ubuntu:~$ sudo iwlist wlan0 scan
(terminal stopped responding)
```

I had to manually restart the system (freezed screen, fan spinning after a couple of minutes)

Let's see the syslog:

```
May 14 08:29:45 ubuntu kernel: [  101.263653] ndiswrapper: driver rsc4usb (U.S. 
Robotics,11/16/2005, 3.3.36.0) loaded
May 14 08:29:47 ubuntu kernel: [  103.267659] wlan0: ethernet device 00:14:c1:01:3e:dc using NDIS driver: rsc4usb, version: 0x30324, NDIS version: 0x501, vendor
: 'U.S. Robotics Wireless USB Adapter', 0BAF:0118.F.conf
May 14 08:29:47 ubuntu kernel: [  103.267765] wlan0: encryption modes supported:
 WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
May 14 08:29:47 ubuntu kernel: [  103.267883] usbcore: registered new interface 
driver ndiswrapper
May 14 08:34:45 ubuntu kernel: [  401.448986] ADDRCONF(NETDEV_UP): wlan0: link i
s not ready
May 14 08:43:38 ubuntu kernel: imklog 5.8.6, log source = /proc/kmsg started.
May 14 08:43:38 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x
-pid="431" x-info="http://www.rsyslog.com"] start
May 14 08:43:38 ubuntu rsyslogd: rsyslogd's groupid changed to 103
May 14 08:43:38 ubuntu rsyslogd: rsyslogd's userid changed to 101
May 14 08:43:38 ubuntu rsyslogd-2039: Could not open output pipe '/dev/xconsole'
 [try http://www.rsyslog.com/e/2039 ]
May 14 08:43:38 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
May 14 08:43:38 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
May 14 08:43:38 ubuntu kernel: [    0.000000] Linux version 3.2.0-24-generic-pae
 (buildd@vernadsky) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #37-Ubun
tu SMP Wed Apr 25 10:47:59 UTC 2012 (Ubuntu 3.2.0-24.37-generic-pae 3.2.14)
May 14 08:43:38 ubuntu kernel: [    0.000000] KERNEL supported cpus:
May 14 08:43:38 ubuntu kernel: [    0.000000]   Intel GenuineIntel
May 14 08:43:38 ubuntu kernel: [    0.000000]   AMD AuthenticAMD

```

That's weird, because looks like the kernel stopped working suddendly, without giving a hint..

---

### Post by chili555 on 2012-05-14
That's quite a mystery we have there; it all looks normal except it simply doesn't work!

I'd like to explore another avenue here:> *-network [COLOR="Red"]DISABLED[/COLOR]
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:c1:01:3e:dc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rsc4usb driverversion=1.57+U.S. Robotics,11/16/2005, 3 link=no multicast=yes wireless=IEEE 802.11gQuite often, 'disabled' means the wireless switch or key combination is set to OFF. In the case of many laptops, including at least one of my Lenovos, moving the switch to OFF also disables any USB wireless network device. It may have to do with some country's requirement that wireless be able to be absolutely turned off on an airplane.

Do you have a perhaps broken internal wireless device that's turned off by the switch or key combination, such as Fn+F4? Is it turned off in the BIOS? That's what I was looking for in 'rfkill list all.'

---

### Post by amebaspugnosa on 2012-05-14
> **chili555 said:**
> Do you have a perhaps broken internal wireless device that's turned off by the switch or key combination, such as Fn+F4? Is it turned off in the BIOS? That's what I was looking for in 'rfkill list all.'

The PC is rather old and it has not any internal wifi adapter. There is a special button that could be a wireless switcher, but pressing it doesn't impact on the network status (i.e. the wlan0 remains in disabled status).

I also tried to disable "usb legacy support" in the BIOS, no luck.

Oddly, the system now refuses to shutdown completely, I guess I messed up something :(

At this point, I wouldn't exclude a faulty dongle: my girlfriend (the owner of the notebook) said that in Windows she had troubles when searching for networks too...

Go for a new adapter? (I found an Ubuntu friendly TP-Link for 10 eur)

---

### Post by chili555 on 2012-05-14
Well, the Euro ain't what it used to be, but that sounds like a sound idea to me. Please post back if we can help you get the new one going.

---

### Post by amebaspugnosa on 2012-05-15
Ok, thank you. In a couple of day I am gonna have a new adapter and plus one gigabyte of ram, let's make this oldie a little bit faster ;)

---

### Post by amebaspugnosa on 2012-05-22
At the end I decided to give up with the US Robotics and to try a different dongle. I bought a TL-WN722N for 8 eur.

It worked just out of the box under Xubuntu 12.04, while I had to install drivers under Windows XP.

After my experience, I strongly suggest to save your time with Ndiswrapper and go for such a dongle.

That's all, thanks! ):P

---

