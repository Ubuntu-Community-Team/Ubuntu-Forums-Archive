---
title: "BCM4312 - Trying to get scanning working / going a bit nuts"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by raikou on 2009-12-13
Hello everyone,

I'm trying to get my BCM4312 wireless card to switch to Monitor mode to no avail.
First up, will this card even support Monitor mode - ever?

I can use networking and Internet fine, the reason I want to get monitor mode working is so I can use Kismet.

I'm really not sure what information I should be providing, i'm pretty new at all this.
so far i've been doing things like installing the b43 driver, blacklisting wl, killing the nm process, downloading a whole bunch of header files, downloading ndiswrapper and then reading that it is bad, checking iwconfig, ifconfig, lspci, lshw and all these other things that i am very new to.
i feel like im on the right track there's just something i'm missing.

Any help appreciated!

---

### Post by chili555 on 2009-12-13
I suggest:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
```Be sure you set up *kismet.conf* in accordance to the README, especially sections 9 and 12:```
less /usr/share/doc/kismet/README.gz
```Then try:```
sudo kismet
```Post back if you get stuck.

---

### Post by raikou on 2009-12-14
thank you for your response, here is what happens.


cetanu@raikou:~$ sudo ifconfig wlan0 down
wlan0: ERROR while getting interface flags: No such device
[COLOR=RoyalBlue]there are no devices called wlan0, the wireless device appears to be named eth1[/COLOR]

cetanu@raikou:~$ sudo ifconfig eth1 down
cetanu@raikou:~$ sudo iwconfig eth1 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.
[COLOR=RoyalBlue]tried with capital "M"[/COLOR]
cetanu@raikou:~$ sudo iwconfig eth1 mode Monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.

cetanu@raikou:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (eth1): Enabling monitor mode for bcm43xx source interface eth1 channel 6...
FATAL: Failed to set monitor mode: Invalid argument.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.
Done.[COLOR=RoyalBlue]

trying it with networkmanager process killed so that it does not force the device to "managed"[/COLOR]
cetanu@raikou:~$ sudo killall NetworkManager
cetanu@raikou:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (BroadcomSource): Enabling monitor mode for b43 source interface eth1 channel 6...
FATAL: Failed to set monitor mode: Invalid argument.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.
Done.

[COLOR=RoyalBlue]i then have to use these to get my connection back[/COLOR]
cetanu@raikou:~$ sudo NetworkManager
cetanu@raikou:~$ sudo modprobe wl

[CENTER]---
[/CENTER]

i'm on Ubuntu 9.04
my laptop is a lenovo g550

i've configured the kismet.conf with "b43,eth1,eth1"
i tried "bcm43xx,eth1,eth" before that.

i've tried a few guides but they all seem to be different so i'm not really sure what the right way to go is, none of them have really worked for me.

---

### Post by chili555 on 2009-12-14
I don't have very high hopes now that I see that you can't force it to monitor mode manually. Let's take a look at:```
sudo lshw -C network
```Thanks.> i then have to use these to get my connection back
cetanu@raikou:~$ sudo NetworkManager
cetanu@raikou:~$ sudo modprobe [COLOR="Red"]wl[/COLOR]
I misunderstood your original post; I thought you were using *b43*.

---

### Post by raikou on 2009-12-14
> **chili555 said:**
> I don't have very high hopes now that I see that you can't force it to monitor mode manually. Let's take a look at:```
sudo lshw -C network
```Thanks.I misunderstood your original post; I thought you were using *b43*.

[COLOR=RoyalBlue]I am really just guessing when I enter things like "modprobe wl"
All I know is that it brings back internet, but it may or may not be a step closer in the direction I want to go.
The readme says I should use b43 as the driver for my broadcom card. So I suppose I should follow that, but i'm really not sure.[/COLOR]

[COLOR=RoyalBlue]Here are the results of the lshw:[/COLOR]

root@raikou:/home/cetanu/Desktop/b43# lshw -C network  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:26:82:2d:4d:85
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.0.151 latency=0 module=wl multicast=yes promiscuous=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:26:22:c9:22:19
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 1e:85:76:c4:57:16
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
[COLOR=RoyalBlue]
Interestingly enough, when I did iwlist scan, it came up with a different result to last time.
I did this after I did "insmod wl.ko" from a driver pack i downloaded from broadcom.
However even after it showed up as "scan completed" it still will not switch to monitor mode to work for kismet.[/COLOR]

root@raikou:/home/cetanu/Desktop/b43# iwlist scan
 lo        Interface doesn't support scanning.
 

 eth0      Interface doesn't support scanning.
 

 pan0      Interface doesn't support scanning.
 

 eth1      Scan completed :
           Cell 01 - Address: 00:21:E9:B7:C1:C0
                     ESSID:"*****'s Network"
                     Mode:Managed
                     Frequency:2.412 GHz (Channel 1)
                     Quality:1/5  Signal level:-89 dBm  Noise level:-92 dBm
                     IE: IEEE 802.11i/WPA2 Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (2) : CCMP TKIP
                         Authentication Suites (1) : PSK
                     IE: WPA Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (1) : TKIP
                         Authentication Suites (1) : PSK
                     Encryption key:on
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                               9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                               48 Mb/s; 54 Mb/s
           Cell 02 - Address: 00:0F:3D:28:6F:9D
                     ESSID:""
                     Mode:Managed
                     Frequency:2.437 GHz (Channel 6)
                     Quality:4/5  Signal level:-64 dBm  Noise level:-93 dBm
                     Encryption key:on
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                               9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                               48 Mb/s; 54 Mb/s
 
[COLOR=RoyalBlue]this has me completely puzzled.
normally i'm good with problem solving. but this is madness to me =P[/COLOR]

---

### Post by chili555 on 2009-12-14
Your card is using *wl*. Please see:> description: Wireless interface
product: BCM4312 802.11b/g
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:04:00.0
logical name: eth1
version: 01
serial: 00:26:82:2d:4d:85
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.0.151 latency=0 [COLOR="Red"]module=wl[/COLOR] multicast=yes promiscuous=yes wireless=IEEE 802.11bgI am skeptical that you will ever get Kismet working with wl. Did you use b43 previously? Temporarily, I suggest:```
sudo rmmod -f wl
sudo modprobe b43 ssb
iwconfig
```Is your wireless interface there?```
sudo iwconfig <interface_you_found> mode monitor
```Didi it go?

---

### Post by raikou on 2009-12-15
[COLOR=RoyalBlue]Yeah I don't think I will get kismet working with wl either.[/COLOR]


cetanu@raikou:~$ sudo rmmod -f wl
cetanu@raikou:~$ sudo modprobe b43 ssb
[COLOR=RoyalBlue]^ this gets rid of my wireless device[/COLOR]
cetanu@raikou:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

cetanu@raikou:~$ sudo iwconfig eth1 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; No such device.

cetanu@raikou:~$ lsmod | grep "b43"
b43                   131484  0 
ssb                    41220  1 b43
mac80211              217592  1 b43
led_class              12036  1 b43
input_polldev          11912  1 b43
cetanu@raikou:~$ lsmod | grep "wl"

[COLOR=RoyalBlue]i ran networkmanager and then checked iwconf again and it shows eth1 as a device again.[/COLOR]
cetanu@raikou:~$ sudo NetworkManager
cetanu@raikou:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

[COLOR=RoyalBlue]i try to switch to monitoring mode after it has showed in my devices again[/COLOR]
cetanu@raikou:~$ sudo iwconfig eth1 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.

[COLOR=RoyalBlue]this is not looking good at all[/COLOR]
cetanu@raikou:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

---

### Post by raikou on 2009-12-15
[COLOR=RoyalBlue]edit-

am reading this now:[/COLOR]

[http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620)

---

### Post by raikou on 2009-12-17
[COLOR=RoyalBlue]The problem I seem to have at the moment is that the Kernel I am running on my laptop (Ubuntu 9.04 kernel 2.6.28-17) doesn't have the right headers to do a 'make' with compat-wireless-2.6.
I managed to get the b43 driver installed but having b43 as my driver then makes eth1 disappear and I have no wireless devices.
Also on linuxwireless.org it says that the wireless card i am using (14e4:4315) is a low-power card and not supported yet by the b43 driver but it is "in progress"

Seems I am stuck because I can't upgrade to 9.10 to get a more updated kernel because I have to either choose between a kernel that doesnt' detect my display, or a kernel that can't install synaptics touchpad.

I might actually just try to run 9.10 in command line mode and see if I can get it working that way.
[/COLOR]

---

