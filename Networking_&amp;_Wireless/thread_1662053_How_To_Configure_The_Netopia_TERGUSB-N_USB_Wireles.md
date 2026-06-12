---
title: "How To Configure The Netopia TER/GUSB-N USB Wireless Adapter"
date: 2011-01-07
forum: Networking &amp; Wireless
---

### Post by garryconn on 2011-01-07
I have a Netopia USB wireless adapter, model # TER/GUSB-N that I am having trouble configuring it. I was wondering if anyone would mind lending some support? Basically, I am setting up a webcam server in my kid's playroom so that I can monitor them from downstairs in my home office. The 10/100 network card works fine, but I need to install the wireless lan card because the computer will be far away from the router. 

I have the i386 Debian 5.0.7 installed on a headless computer, no GNOME just CLI. Here some additional information:

**lsusb**

```
camserver1:~# lsusb
Bus 004 Device 003: ID 148f:9021 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 004 Device 002: ID 046d:09a1 Logitech, Inc. QuickCam Communicate MP/S5500
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

**ifconfig**

```
camserver1:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:56:84:c1:36  
          inet addr:192.168.10.116  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fe84:c136/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:103149 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:153388251 (146.2 MiB)  TX bytes:3737897 (3.5 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:944 (944.0 B)  TX bytes:944 (944.0 B)
```

**iwconfig**

```
camserver1:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

I am following the instructions on this page: [http://wiki.debian.org/rt2500usb](http://wiki.debian.org/rt2500usb) and basically get stumped on step 5:

**ifconfig wlan0 up**

```
camserver1:~# ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
```

**/etc/network/interfaces**

#```
 This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
iface eth0 inet static
        address 192.168.10.116
        netmask 255.255.255.0
        network 192.168.10.0
        broadcast 192.168.10.255
        gateway 192.168.10.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 8.8.8.8 8.8.4.4
        dns-search ckvcom.com

iface wlan0 inet dhcp
    wpa-ssid mynetworkname
    wpa-psk mypassword

```


Thanks in advanced to anyone who is willing to offer some help. I really enjoy linux a lot. I'm learning a lot each day. I prefer doing things in shell, so if possible, please don't ask me to install GNOME. Using CLI helps me understand more about linux and how to manage the system.

---

### Post by chili555 on 2011-01-08
> Basically, I am setting up a webcam server in my kid's playroom so that I can monitor them from downstairs in my home office.Awesome!> I prefer doing things in shellEven more awesome! 

Your device is claimed by rt73usb as *modinfo* tells us:```
chili@LAPTOP60:~$ modinfo rt73usb | grep 9021
alias:          usb:v0EB0p9021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="Red"]148F[/COLOR]p[COLOR="Red"]9021[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```*modinfo* also says that firmware is required:> filename:       /lib/modules/2.6.35-24-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license:        GPL
firmware:       rt73.binYou can check for its existence with:```
ls /lib/firmware | grep rt7
```If it's not there, drag the server back to the ethernet cable and do:```
sudo rmmod -f rt73usb
sudo apt-get install linux-firmware
sudo modprobe rt73usb
iwconfig
```Did the wireless come to life?

If the firmware is present and the wireless doesn't work, there is another problem. Diagnose with:```
dmesg | grep -i rt7
lsmod | grep rt
```Please post any suspicious readings.

---

