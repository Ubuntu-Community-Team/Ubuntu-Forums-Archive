---
title: "wireles conection does not work after ubuntu 9.10 upgrade"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by tvagi on 2009-12-23
Hi, let ask me for help with this thread. After instalation ubuntu 8.04 I successfully completed network connection via DSL as well as via wireless with comunity help listed here
> [http://forum.ubuntu.cz/index.php/topic,33232.0.html](http://forum.ubuntu.cz/index.php/topic,33232.0.html)After upgrade 8.10  I had lost wireless connection and did not get it even after upgrade 9.10 I have installed madwifi driver and wicd network manager. I have controled if connection is writen in /etc/modules (code adding)
```
#wifi
ath_pci
``` I heve tried to reinstall madwifi driver, but wireless stil does not work. 
I'am add codes witch, as I hope, could tell some more advanced users more and help to find solution.
```
tomas@masinka:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 14
       serial: 00:a0:d1:cb:35:37
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=192.168.1.110 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:f8000000-f8003fff ioport:3000(size=256) memory:f2000000-f201ffff(prefetchable)
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
       resources: memory:fa000000-fa00ffff
tomas@masinka:~$ ifconfig
eth0      Link encap:Ethernet  HWadr 00:a0:d1:cb:35:37  
          inet adr:192.168.1.110  Všesm&#283;r:192.168.1.255  Maska:255.255.255.0
          inet6-adr: fe80::2a0:d1ff:fecb:3537/64 Rozsah:Linka
          AKTIVOVÁNO VŠESM&#282;ROVÉ_VYSÍLÁNÍ B&#282;ŽÍ MULTICAST  MTU:1500  Metrika:1
          RX packets:16795 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13578 errors:0 dropped:0 overruns:0 carrier:0
          kolizí:0 délka odchozí fronty:1000 
          P&#345;ijato bajt&#367;: 18670019 (18.6 MB) Odesláno bajt&#367;: 1565615 (1.5 MB)
          P&#345;erušení:17 

lo        Link encap:Místní smy&#269;ka  
          inet adr:127.0.0.1  Maska:255.0.0.0
          inet6-adr: ::1/128 Rozsah:Po&#269;íta&#269;
          AKTIVOVÁNO SMY&#268;KA B&#282;ŽÍ  MTU:16436  Metrika:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          kolizí:0 délka odchozí fronty:0 
          P&#345;ijato bajt&#367;: 240 (240.0 B) Odesláno bajt&#367;: 240 (240.0 B)

tomas@masinka:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

---

### Post by theDaveTheRave on 2009-12-23
tvag,


it would seem you have 'lost' you wireless interface (looking at the output of iwlist scan). But you definately have a recognised wireless card.

can you send the output of the following

```

ifconfig

```

if that shows up any 'extra' interfaces that are not on the < iwconfig > that you ran try to "bring up" the appropriate interface.

for instanc if you get a < wlan0 > interface try

```

sudo ifconfig wlan0 up

```

then try

```

iwlist scan

```

In fact you could try that before the < ifconfig wlan0 up > command, it will show you what wireless interfaces are available and what ones are "listening" for wireless connections.

Just quickly though..

If you have the ethernet cable plugged in I have a feeling that sometimes the wireless will 'turn off' - I had this once, and I needed to re-enable wireless when I unplugged the ethernet cable.

Don't know if that helps at all.

David

---

### Post by tvagi on 2009-12-23
Hi David,
 I have tried connect wireless when cable was disconected and it does not help. Here are codes you write about:
```
tomas@masinka:~$ ifconfig
eth0      Link encap:Ethernet  HWadr 00:a0:d1:cb:35:37  
          inet adr:192.168.1.110  Všesm&#283;r:192.168.1.255  Maska:255.255.255.0
          inet6-adr: fe80::2a0:d1ff:fecb:3537/64 Rozsah:Linka
          AKTIVOVÁNO VŠESM&#282;ROVÉ_VYSÍLÁNÍ B&#282;ŽÍ MULTICAST  MTU:1500  Metrika:1
          RX packets:2114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1699 errors:0 dropped:0 overruns:0 carrier:0
          kolizí:0 délka odchozí fronty:1000 
          P&#345;ijato bajt&#367;: 2308303 (2.3 MB) Odesláno bajt&#367;: 260428 (260.4 KB)
          P&#345;erušení:17 

lo        Link encap:Místní smy&#269;ka  
          inet adr:127.0.0.1  Maska:255.0.0.0
          inet6-adr: ::1/128 Rozsah:Po&#269;íta&#269;
          AKTIVOVÁNO SMY&#268;KA B&#282;ŽÍ  MTU:16436  Metrika:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          kolizí:0 délka odchozí fronty:0 
          P&#345;ijato bajt&#367;: 0 (0.0 B) Odesláno bajt&#367;: 0 (0.0 B)

tomas@masinka:~$ sudo ifconfig wlan0 up
[sudo] password for tomas: 
wlan0: Chyba p&#345;i zjiš&#357;ování p&#345;íznak&#367; rozhraní: No such device
tomas@masinka:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

```

---

### Post by theDaveTheRave on 2009-12-23
tvagi,

so for some reason your card is 'seen' in the hardware list but not in the ifconfig ?

it could be a modules problem

post the output of the following
```

lsmod | grep "ath5k"
lsmod | grep "ath_pci"
lsmod | grep "madwifi"

```

to see what modules you have installed for the hardware.

If you get not results for any of them then post the full list from 

```

lsmod

```

to see what is installed.

David

Also I just did a quick search for your atheros chip (ar5001) and it seems that in karmic there may be a problem, [here is the bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/442031")

and [here is wiki page]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros") that goes through some potential solutions.

It sounds as though it may be a solution to your problem.

Good luck.

---

### Post by tvagi on 2009-12-23
Dave,
 before i will run through solution you listed, I'm adding codes you write about:
```
tomas@masinka:~$ lsmod | grep "ath5k"
tomas@masinka:~$ lsmod | grep "ath_pci"
tomas@masinka:~$ lsmod | grep "madwifi"
tomas@masinka:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
joydev                 10272  0 
snd_hda_codec_realtek   203328  1 
iptable_filter          3100  0 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
btusb                  11856  2 
psmouse                56500  0 
serio_raw               5280  0 
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              22276  1 snd_pcm
snd                    59204  12 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
ppdev                   6688  0 
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usbhid                 38208  0 
usb_storage            52576  0 
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
sky2                   46560  0 
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

```

---

### Post by theDaveTheRave on 2009-12-23
tvagi,

ok that will be your problem.

You don't have < ANY > modules installed for using the chip!?

The link to the wiki page should help you determine if they have been inadvertently " blacklisted" anywhere.

the output of my system is...

```

lsmod | grep "ath"
ath_pci                99224  0 
wlan                  210544  1 ath_pci
ath_hal               198864  1 ath_pci
ath5k                 107520  0 
mac80211              217592  1 ath5k
led_class              12036  2 ath5k,acer_wmi
cfg80211               38288  2 ath5k,mac80211

```

so I guess you should have a head start on the required modules. If I remember correctly, the list on the right is the module name, and on the left is name of any modules that this particular module has as a depedency...

so the module wlan   depends on ath_pci

and led_clas  depends on ath5k and acer_wmi

You need to determine exactly what modules you require. Sorry I'm not of much help on this one, I've allways done what others have told me to do on the forums.

If you have trouble though I'll see what I can do.. I'm searching for this as I type... (or rather google is!)

David

---

### Post by tvagi on 2009-12-23
Dave,
 it get some results, but still not done. After i run through > [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros) I have changed in /etc/modprobe.d/madwifi.conf that t seems like this:
> ## ath5k (mac80211)
## Comment out the following line, and uncomment all of the
## madwifi modules below to use the athk module
## blacklist ath5k

## madwifi (non-free)
#blacklist ath_hal
#blacklist ath_pci
#blacklist ath_rate_amrr
#blacklist ath_rate_onoe
#blacklist ath_rate_sample
#blacklist wlan
#blacklist wlan_acl
#blacklist wlan_ccmp
#blacklist wlan_scan_ap
#blacklist wlan_scan_sta
#blacklist wlan_tkip
#blacklist wlan_wep
#blacklist wlan_xauth
After that i hit terminal with:
```
tomas@masinka:~$ lsmod | grep "ath5k"
ath5k                 124260  0 
mac80211              181076  1 ath5k
led_class               4096  1 ath5k
ath                     8060  1 ath5k
cfg80211               93052  3 ath5k,mac80211,ath
tomas@masinka:~$ lsmod | grep "ath_pci"
tomas@masinka:~$ lsmod | grep "madwifi"^C[code]

[code]tomas@masinka:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```wlan0 seem to be there, but still does not work. Do you have an idea what can cause a problem?

---

### Post by theDaveTheRave on 2009-12-23
tvagi,

I feel we are getting somewhere... I appreciate that it is annoyin though.

it's a silly question, but I guess you have done a reboot since all the messing around??

next question when you run the 

[code]
lshw -C network
[code]

does it still report the wifi card as being 'unclaimed'
also you want to check the 'logical name' of the device.

It may also be a requirement to use the linux backports.

What version of Ubuntu are you running? As there a many reported problems with this chip "breaking" on upgrade.

It has always seemed strange to me that a device that could work fine could suddenly just die, but it is not uncommon in the Ubuntu world (I guess that is why Windows only realease a new version every 5 or 6 years!)

But also that is why we have < backports > !

David

---

### Post by tvagi on 2009-12-23
Dave,
 it looks like that wifi should work, but why it is DISABLED (?):
```
tomas@masinka:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 14
       serial: 00:a0:d1:cb:35:37
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A ip=192.168.1.110 latency=0 multicast=yes
       resources: irq:27 memory:f8000000-f8003fff ioport:3000(size=256) memory:f2000000-f201ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 04
       serial: 00:22:5f:45:d5:35
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:fa000000-fa00ffff

```

---

### Post by theDaveTheRave on 2009-12-23
tvagi,

OK so it seems you need to bring the interface up.

try

```

sudo ifconfig wmaster0

```

then check your lshw -C network output (it should no longer be saying that it is disabled).

then check to see if you are getting any local wifi networks

```

iwlist scan

```

Then you will need to find your network preferences, from the menu's you will need.

System > Preferences > Network Connections

from here you should will need to set up your network connection to log into your wifi (I assume that it is a 'secure' connection).

Alternatvely, you can set up a, 'open' wireless network, to test to see if it works, as I've read in some places that the different passwords don't allways play nice with network manager (the connection permanently drops out and then re-connects).

It should also work on a reboot? Also if you have a physical switch on your machine you may need to 'play' with it!

David.

---

### Post by peepingtom on 2009-12-23
Just a quick correction, he meant
```
sudo ifconfig wmaster0 up
```

---

### Post by tvagi on 2009-12-23
Here is result for this command:
> SIOCSIFFLADS: Operation not supported

---

### Post by theDaveTheRave on 2009-12-28
> **peepingtom said:**
> Just a quick correction, he meant
```
sudo ifconfig wmaster0 up
```


sorry I certainly did.

or should I give marks for noticing the "deliberate error" :lolflag:

tvagi,

I notice that you get the classic 
> 
SIOCSIFFLADS: Operation not supported 


So lets make sure what our situaion is.

first do a reboot then perform each of the commands we have done previously, in the following order

```

iwlist scan
lshw -C network

```

That will confirm if you have had a change that has got things to work since the reboot, it would be nice if you have a nice long list of wireless access point in the results of iwlist scan.... but....

```

lsmod | grep "ath"

```

will confirm the modules that are installed and being used for the atheros wifi chip.

Now bring up the interfaces that you have on your system (some of these may get reports like the error from earlier, just report them back to the pages.

```

sudo ifconfig wmaster0 up
sudo ifconfig wlan0 up
iwlist scan

```

if that last bit now gives a whole list of the wifi access points we have a good result.... ... .. . you should be able to now connect via the wireless (provided it isn't a "hidden" network).

David

---

