---
title: "Ubuntu 9: Problems with D510 Wireless Network"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by RickSimnett on 2009-06-04
Hello,
I recently upgraded my Dell D510 laptop to ubuntu 9.04. Everything seems to be working, and for the first time ever (in my experience), it detected the wireless network card and setup a driver by itself!

The problem I am having, is the fact that I CANNOT get the card to be enabled. In otherwords, when I use the NetworkManager and tell it to use my wireless network with ssid linksys, with a wep key, it simply does nothing. So I ran a command to see what was going on:

sudo lshw -c network

I got this:

rick@rick-laptop:~$ sudo lshw -c network
[sudo] password for rick: 
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:f8:17:f2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.109 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 7a:eb:17:14:24:8a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:a5:33:48:d6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
rick@rick-laptop:~$ 


I googled around and found a procedure that looked promising yet did nothing:

sudo modprobe -r b43 b44 ssb wlan
sudo modprobe ieee80211_crypt_tkip
sudo modprobe wlan0
sudo modprobe b43
sudo /etc/init.d/network restart

the result of this, is that network manager, simply pops up a window saying the device is disconnected.

Finally, I checked the ubuntuforums, and found another procedure which also did nothing:

I added a line to my /etc/network/interfaces file that read iface wlan0 inet dhcp

I then ran the following commands:

sudo iwconfig wlan0 essid $ESSID key $KEY.
sudo ifup wlan0

This also did nothing but have networkmanager tell me again that the wireless was disconnected.

Can anyone tell me how to fix this issue. Its REALLY annoying, and without the wireless internet my laptop is more or less pointless.

Thanks in advance,
Rick

---

### Post by coffeeaddict22 on 2009-06-04
Hi Rick,
The problem is almost certainly that wireless improved out of sight lately; a whole lot of drivers got incorporated into the distributions.  Unfortunately, most of the cards involved used to run on ndiswrapper, and I think it keeps it's scripts in the /home directory (which isn't touched in the upgrade), so what's tending to happen is the ndiswrapper driver and the native Linux driver compete- and crash.

Start off by checking that's your problem.  have a look at the output of ```
lsmod
```, to see if ndiswrapper is loaded.
Then try  ```
lspci -v |grep Network -A10
```
to see what driver is being loaded for the card.  
If it's the wl driver (I've got the 4322 card, but I think it was the same driver), then have a look at the wireless config with ```
iwconfig
```.  If you're running network manager, ```
nm-tool
``` is another command that might help define the problem.  

Post back if you need more help.

---

### Post by RickSimnett on 2009-06-05
Ok... I have tried the following based on your recommendations:

lsmod gave me the output of:

rick@rick-laptop:~$ lsmod
Module                  Size  Used by
i915                   65540  2 
drm                    96296  3 i915
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
rfkill_input           12800  0 
lp                     17156  0 
joydev                 18368  0 
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
arc4                    9856  2 
ac97_bus                9856  1 snd_ac97_codec
ecb                    10752  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
b43                   131484  0 
pcmcia                 44748  0 
mac80211              217208  1 b43
cfg80211               38032  1 mac80211
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd                    62628  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                61972  0 
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
led_class              12036  1 b43
soundcore              15200  1 snd
ppdev                  15620  0 
dcdbas                 15264  0 
video                  25360  0 
serio_raw              13316  0 
pcspkr                 10496  0 
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
input_polldev          11912  1 b43
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
intel_agp              34108  1 
output                 11008  1 video
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
agpgart                42696  3 drm,intel_agp
b44                    35984  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
ssb                    41220  2 b43,b44
mii                    13312  1 b44
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

I do not see ndiswrapper in here at all. (At least I dont think I do :)

so I tried the next command:

rick@rick-laptop:~$ lspci -v | grep Network -A10
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
    Subsystem: Dell Device 0005
    Flags: bus master, fast devsel, latency 64, IRQ 17
    Memory at dfdfa000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

Looks like the correct driver. 

rick@rick-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.



I do not currently have networkmanager installed. I removed it last night in a failed attempt to get the card to work. I read somewhere that sometimes the networkmanager is unreliable. So I removed it and manually configured each of the interfaces under /etc/network/interfaces and tried that approach. It didnt work. rick@rick-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

When I try to bring the networking interfaces up, the wireless DHCP fails.

rick@rick-laptop:~$ sudo /etc/init.d/networking restart
[sudo] password for rick: 
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 3511
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:12:3f:f8:17:f2
Sending on   LPF/eth0/00:12:3f:f8:17:f2
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 3401
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:14:a5:33:48:d6
Sending on   LPF/wlan0/00:14:a5:33:48:d6
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:12:3f:f8:17:f2
Sending on   LPF/eth0/00:12:3f:f8:17:f2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.1.109 from 192.168.1.1
DHCPREQUEST of 192.168.1.109 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.109 from 192.168.1.1
bound to 192.168.1.109 -- renewal in 41264 seconds.
 * if-up.d/mountnfs[eth0]: waiting for interface wlan0 before doing NFS mounts
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:14:a5:33:48:d6
Sending on   LPF/wlan0/00:14:a5:33:48:d6
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]


I also COMPLETELY reinstalled ubuntu 9 on the laptop (so no ndiswrapper at all), to make sure that any legacy drivers or software were removed. Still a no go.

Any help you can offer is greatly appreciated, as I am out of ideas. :(

---

### Post by coffeeaddict22 on 2009-06-05
Hi Rick,
Something funny happening.  

Can you post back the output of lshw -C network?
It still looks like a driver problem.  That wmaster0 is showing up when you restart the networking is usually (but not always) a bad sign; as far as I can make out it's a dummy interface the kernel uses to simplify networking.

---

### Post by RickSimnett on 2009-06-06
Sure... Here it is.

rick@rick-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:f8:17:f2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.109 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:33:48:d6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 6e:07:5c:53:b6:6e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
rick@rick-laptop:~$

---

### Post by coffeeaddict22 on 2009-06-06
OK.  The second connection- starts with Broadcom 4318 etc etc- is your wireless.  It hasn't got a driver at present.  
Have you enabled the driver in System/Admin/Hardware drivers?

---

### Post by jimmygo on 2009-06-06
Thank you coffeeaddict. I had the exact same problem as Rick. Your suggestion to dnable the driver (followed by a restart) has me thanking you via wireless.

I didn't have any idea that drivers had to be allowed like that.

Cheers,
Jim

---

### Post by coffeeaddict22 on 2009-06-06
Hi Jimmy,
 It's a bit of a Linux twitch that seems stupid when you're stuck, but makes sense.  The problem is Broadcom won't release the source code for their drivers, so there's potentially trouble using them (eg no-one gets the code to maintain if they go bankrupt/ whatever).  Debian is the distro Ubuntu bases itself on, and they have a really strict policy on what's allowed in the repositories.  That makes sense from their point of view, because the repositories are in some ways a back door into your system, so it makes sense that anyone should be able to read the source code.
  
However, when you're scratching around trying to get your card working, it's a bit frustrating that they don't install by default.

The giveaway is usually either no logical name listed for the card, or wmaster0.

---

### Post by RickSimnett on 2009-06-07
coffeeaddict,
It works! Wow all that and I just had to enable the driver :). Thank you so much for your help, the wireless now works perfectly. :)

Thanks again!

Rick

---

### Post by 4geeksonly on 2011-07-25
> **coffeeaddict22 said:**
> OK.  The second connection- starts with Broadcom 4318 etc etc- is your wireless.  It hasn't got a driver at present.  
Have you enabled the driver in System/Admin/Hardware drivers?


Hi Coffeeadict,

   I installed UBUNTU 11.04, my chip is Broadcom 4318. The Driver shows as "b43".
However,  I can not find a way to enable the driver. I do not have  System/Admin/Hardware drivers, instead in UBUNTU 11, I could find  "Additional Drivers", which is completely
empty. I do not have any network connection, have no ethernet to this desktop.

How do I enable the driver? From "rfkill list" command it seems both Hardware & Software
are enabled.

Thanks.

---

