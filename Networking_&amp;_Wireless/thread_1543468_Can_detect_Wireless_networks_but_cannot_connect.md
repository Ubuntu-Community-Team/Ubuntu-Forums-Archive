---
title: "Can detect Wireless networks but cannot connect"
date: 2010-08-01
forum: Networking &amp; Wireless
---

### Post by jon1973 on 2010-08-01
I have a [WLAN Driver Azure Wave AW-NU222 Wireless LAN Card]("http://javascript%3Cb%3E%3C/b%3E:void%280%29") in my Medion computer.  

After installing Ubuntu it seems to detect the wireless networks in my area.  However, when I try to connect to my network, it tries for several minutes and then times out with no error message.  I have set up the credentials and also tried removing the encryption **[[B](WPA-PSK)**]("http://javascript%3Cb%3E%3C/b%3E:loadhelp%28%27WLG_wireless%27,%27wpa-psk%27%29")[/B] from the network itself, but it still doesn't connect.

Connect via an Ethernet cable is fine, and I know that the network is good because I can connect via my Windows Laptop and various other wireless devices.

I suspect it's due to drivers, but I'm having trouble downloading a driver which I can try and install using Ndiswrapper.  The Medion website just a windows executable when I try and download the driver specific to my machine when I really need the .inf file.

Any help / pointers / links would be appreciated.

---

### Post by Starks on 2010-08-05
Make sure you are using an XP driver.

---

### Post by dineshs on 2010-08-05
pl post
```
sudo lshw -C network 
```and```
iwconfig

```
> Any help / pointers / links would be appreciated.

[http://beginlinux.com/twitter/1096-ubuntu-wireless-setup](http://beginlinux.com/twitter/1096-ubuntu-wireless-setup)

---

### Post by jon1973 on 2010-08-06
[SIZE=4][SIZE=3]Thanks for the reply...[/SIZE][B]

sudo lshw -c network[/B][/SIZE]

  *-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1d:92:22:99:b4
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.3-0 ip=192.168.1.8 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:25 memory:fdfc0000-fdfdffff memory:fdfff000-fdffffff ioport:ff00(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:44:68:7b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
[SIZE=4]**iwconfig**[/SIZE]

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

---

### Post by X5-655 on 2010-08-06
I got this same problem, though most of the time i can connect, but once in a while it just won't work..

---

### Post by Beady on 2010-08-06
I also have a Medion, a netbook. Connects first time every time under Windows, but while Ubuntu seems to see the networks, it refuses to connect.

To be honest I've had the same issue with a notebook some months ago, and I gave up and just stuck with Windows, if I can't get it working this time I guess I'll just have to give up and stay on the Dark Side.

Regards,
Bernard D

---

### Post by JBAlaska on 2010-08-06
If I'm not mistaken, this unit uses the same Ralink chipset as my Linksys WUSB600N.

I used this method to get it working on 10.04:
```
sudo su
echo "rt2870sta" >> /etc/modules
modprobe rt2870sta
exit
```

And if it quits after a kernel update just do:
```
sudo modprobe rt2870sta
```

---

