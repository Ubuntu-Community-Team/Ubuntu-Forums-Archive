---
title: "Unable to connect via WPA / 9.04 / iMac"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by Barry79 on 2009-05-03
Hi,

I am unable to use my wireless connection and was hoping you could help me out. I have an iMac machine with a Broadcom corp. BCM4328 802.11a/b/g/n (rev 03) controller. I'm using Ubuntut 9.04 with Kernal: 2.6.28-11-generic i686.

When I first installed Ubuntu, the wireless connection didn't work at all until I activated the driver via 

System >> Admin >> Drivers

and restarted. 

I now see a list of wireless accounts to connect to, including that of my own wireless router. But when I enter my WPA password and try connecting I see two circles in the desktop status bar which spin round and round - but no connection or no error message. I'm also asked for my keyring password now and again, which I give. 

The funny thing is that when I click on "Show Password" when editing the settings for this connection, its completely different to that which I have entered. It looks something like -

f952aab633d2a72d07308975427eb43f5784911ff969e33a7a441a433e46c3ed2

Is it trying to encript the password that it sends?

Any way, its not managing to connect. 

Under Applications >> Passwords >> Passwords, I have one password entry - for my wireless connection. When I click "view password" here, I see the same value as that above. This is not what I use to connect to the router from os x or windows. Should I change this? Or is it an encription of the password?

The BSSID and MAC adress fields are empty under my VPA connfiguration for this WPA connection. Is this correct?

My wired connection is working fine.

Hope you can help,

Barry.

Here are some other settings -

Network Controller: Broadcom corp. BCM4328 802.11a/b/g/n (rev 03)
 

*** ifconfig -

eth0      Link encap:Ethernet  HWaddr 00:17:f2:dd:4d:b8  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:f2ff:fedd:4db8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16630 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13992 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19234427 (19.2 MB)  TX bytes:2253783 (2.2 MB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:1b:63:14:9f:b5  
          inet6 addr: fe80::21b:63ff:fe14:9fb5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:7112
          TX packets:36 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4788 (4.7 KB)  TX bytes:4788 (4.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


*** iwconfig -

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:210  Noise level:166
          Rx invalid nwid:0  invalid crypt:21  invalid misc:0

pan0      no wireless extensions.


*** lsmod

Module                  Size  Used by
michael_mic            10496  2 
arc4                    9856  2 
ecb                    10752  2 
binfmt_misc            16776  1 
radeon                342816  2 
ppdev                  15620  0 
drm                    96296  3 radeon
btusb                  19608  2 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
uinput                 15616  2 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
applesmc               29360  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class              12036  1 applesmc
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
soundcore              15200  1 snd
hid_apple              14336  0 
appleir                12416  0 
input_polldev          11912  1 applesmc
ieee80211_crypt_tkip    16896  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
isight_firmware        10880  0 
usbhid                 42336  0 
pcspkr                 10496  0 
intel_agp              34108  0 
agpgart                42696  2 drm,intel_agp
wl                   1489748  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl
video                  25360  0 
output                 11008  1 video
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
sky2                   54916  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit


*** Network Configuration -

  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 22
       serial: 00:17:f2:dd:4d:b8
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.2 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: 00:1b:63:14:9f:b5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 16:89:10:ef:7e:2a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by hebbal1273 on 2009-05-05
Even I have the same problem. It keeps asking for the WPA/WPA2 password even though I have entered the correct password. The only difference is I have a HP compaq nx6325 laptop using AMD turion 64 bit dual core CPU.

---

### Post by hebbal1273 on 2009-05-06
My bad. I had entered the wrong password:(

---

### Post by newbie09 on 2009-05-24
Barry79 i am having the same problem u are having !!!

---

### Post by email2mickey on 2009-05-24
I am seeing the same problem on a new 9.04 installation. Wondering if anyone found a solution. Thx.

---

