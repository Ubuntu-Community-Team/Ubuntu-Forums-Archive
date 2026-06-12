---
title: "This wireless issue was aging me :)"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by onurozcelik on 2010-01-01
Hi guys

I hope someone may help.

Here is the summary of my problem.

I am using Ubuntu 9.10 with kernell release 2.6.31-17-generic
When I first install Karmic with kernel release 2.6.31-14 it does not recognize my wireless card.
After installation I got my wireless card recognized with Windows Wireless Drivers *.inf files. After restart I can connect to wireless lans.
Then I update my system to kernel release 2.6.31-17-generic
After restart my system can detect wireless networks but cannot connect any of them.
But I was determined. I googled a bit. I found that there is a package for extracting Broadcom hardware(b43-fwcutter). I removed Windows Wireless Driver *.inf files. Then I installed b43-fwcutter. But opps my wireless interface did not recognized again. So I removed b43-fwcutter package. Returned back to Windows Wireless Drivers solution.
The same thing happens again. My system detects wireless networks but could not connect any of them. It always failed when obtaining an IP adress. 

Anyone faced similar problem?

My wireless controller is: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) bye the way.

---

### Post by focwiz on 2010-01-01
> **onurozcelik said:**
> Hi guys

I hope someone may help.

Here is the summary of my problem.

I am using Ubuntu 9.10 with kernell release 2.6.31-17-generic
When I first install Karmic with kernel release 2.6.31-14 it does not recognize my wireless card.
After installation I got my wireless card recognized with Windows Wireless Drivers *.inf files. After restart I can connect to wireless lans.
Then I update my system to kernel release 2.6.31-17-generic
After restart my system can detect wireless networks but cannot connect any of them.
But I was determined. I googled a bit. I found that there is a package for extracting Broadcom hardware(b43-fwcutter). I removed Windows Wireless Driver *.inf files. Then I installed b43-fwcutter. But opps my wireless interface did not recognized again. So I removed b43-fwcutter package. Returned back to Windows Wireless Drivers solution.
The same thing happens again. My system detects wireless networks but could not connect any of them. It always failed when obtaining an IP adress. 

Anyone faced similar problem?

My wireless controller is: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) bye the way.

Try this post...?
[http://ubuntuforums.org/showthread.php?t=1368699]("http://ubuntuforums.org/showthread.php?t=1368699")

---

### Post by bkratz on 2010-01-01
The 4318 is not covered by this page.

---

### Post by onurozcelik on 2010-01-04
As kratz said BCM4318 is not covered on suggested page.
Besides these, with litte hope I tried your suggestion.
Result: No wireless networks recognized.

Different suggestions will be appreciated.

---

### Post by bkratz on 2010-01-04
> **onurozcelik said:**
> As kratz said BCM4318 is not covered on suggested page.
Besides these, with litte hope I tried your suggestion.
Result: No wireless networks recognized.

Different suggestions will be appreciated.

This was actually written for Jaunty but it looks like it should work anyway

[http://ubuntuforums.org/showthread.php?t=1233448&highlight=wmp54gs](http://ubuntuforums.org/showthread.php?t=1233448&highlight=wmp54gs)

---

### Post by puppywhacker on 2010-01-04
The 4318 is in the list of supported drivers

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

just installing the b43-fwcutter is not enough, you also need to run it so that it can fetch the firmware online (so you need wired internet connection) and you need to load the b43 driver with "modprobe b43" before the interface will be recognized.

---

### Post by onurozcelik on 2010-01-05
To bkratz and puppywhacker

First of all thank you for your suggestions.

I tried both of your suggestions.
None of them worked for me.
When I remove "Windows Wireless Drivers" wireless lan interface disappers.

Beside these I tried an odd solution. For the moment it works but it was not a stable solution. From Synaptic Package Manager I installed 2.6.31-14-generic versioned kernel. I installed  startupmanager to select the old kernel version. I configured my system to start with kernel version 2.6.31-14-generic. I reboot my system. After reboot my system do not recognize wireless networks as usual. I then checked Windows Wireless Drivers and I see they are not installed. Then I install them and tried to activate the driver from Hardware Drivers. I got an error when I want to activate the driver. After that interestingly my system recognizes wireless networks and when I try to connect my wireless network voila! Connection succeeds.

As I said this is not a stable  solution. Because after every boot I have to activate the driver and every activation try gave me an error. But then I can connect wireless networks.

I need more stable solution than this.

---

### Post by onurozcelik on 2010-01-07
Guys,


I am open to different suggestions.

---

### Post by puppywhacker on 2010-01-07
Hi,

When I read "I tried it and it doesn't work". I'd also like to see the symptoms where it fails. I know that it will work, but sometimes only after troubleshooting and persistance.

To install the drivers do this
```

sudo apt-get install b43-fwcutter
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2
tar xjf broadcom-wl-4.178.10.4.tar.bz2
cd broadcom-wl-4.178.10.4/linux
sudo ../../fwcutter/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o

```

To load the driver (you only need to do this once)
```

lsmod | grep b43
modprobe b43
lsmod | grep b43
depmod -a

```

sudo lshw -C network
```

  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 12
       bus info: pci@0001:10:12.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=[COLOR="Red"]**b43-pci-bridge**[/COLOR] latency=16
       resources: irq:52 memory:80084000-80085fff
```

dmesg | grep wlan0
```
[   19.009588] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.504170] wlan0: authenticate with AP 00:02:cf:84:86:1c
[   20.505528] wlan0: authenticated
[   20.505536] wlan0: associate with AP 00:02:cf:84:86:1c
[   20.509941] wlan0: RX AssocResp from 00:02:cf:84:86:1c (capab=0x461 status=0 aid=1)
[   20.509952] wlan0: associated
[   20.511190] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```
iwconfig
```
wlan0     IEEE 802.11bg  ESSID:"zyxel"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:02:CF:84:86:1C
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=[COLOR="Red"]**53/70**[/COLOR]  Signal level=-57 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by onurozcelik on 2010-01-08
Thank you for your intention to help me.
Most likely your solution will work on my laptop.
But when I am searching forums desperately I discover an open source driver. I tried this post [http://ubuntuforums.org/showthread.php?t=1055078&highlight=BCM4318](http://ubuntuforums.org/showthread.php?t=1055078&highlight=BCM4318)
and it is working on my laptop now.

---

