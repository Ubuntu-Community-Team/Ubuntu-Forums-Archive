---
title: "Random (perhaps) wireless disconnect...unable to reconnect."
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by AdamShumpisxXx on 2009-04-05
First and foremost I'd like to say that my forum experience thus far has been amazing and I thank everyone who has contributed to that. Now, on to the problem:

I bought a [Rosewill RNX-N300]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833166038") IEEE 802.11b/g/n Wireless-N 2.0 PCI card for my desktop about 2 weeks ago. I installed the RT2860 native Linux driver provided by Ralink and everything has been great up until now.

Randomly (perhaps) my connection will drop while I am seeding a torrent using uTorrent (Wine v1.1.18) and then my wireless card seems to no longer be able to even see any wireless networks until I restart my computer. Reading through topics here on Ubuntu Forums I came to the conclusion that NetworkManager Applet was to blame and have since switched to WICD v1.5.9 which I now believe to be a superior network manager. The problem however still persists.

I post my thread in this section because this might not be the fault of Wine or uTorrent but something fundamentally wrong with something I did when I installed it. If the MODS don't agree then definitely move it to the appropriate section. I never had this problem while I was using my wired connection (which is now no longer possible). I also have a laptop connected to the same wireless network that does not experience the connection drop therefor isolating the problem to the desktop. I initially thought it was my router (WRT54GL running Tomato v1.19). I cannot however isolate this issue to just happening while I seed on uTorrent because I no longer run my computer for days without restarting or shutting down as I used to when I was using a wired connection. If required I will do that for whatever amount of time and post the results.

Also for anyone who might ask here is the terminal read-out of "sudo lshw -C network":
```

*-network:0             
       description: Wireless interface
       product: RT2760 Wireless 802.11n 1T/2R Cardbus
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:03:01.0
       logical name: ra0
       version: 00
       serial: 00:02:6f:54:f7:5b
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 ip=192.168.1.106 latency=64 maxlatency=4 mingnt=2 module=rt2860sta multicast=yes wireless=RT2860 Wireless
  *-network:1
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 4
       bus info: pci@0000:03:04.0
       logical name: eth0
       version: 13
       serial: 00:1e:8c:25:a2:2a
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=64 link=no maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9e:65:5b:bb:63:09
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```
Any help in this matter would be greatly appreciated. Thank you very much in advance.

---

### Post by zigga15 on 2009-04-05
I have had a lot of crap go on with my network.

If you have a low reception then this can be a problem

Other than that there are heaps of reasons, especially as your problem appears to be "random".

Wine is an emulator, which means that it can possibly affect your wireless drivers.

You can get a temporary fix by mounting/unmounting your network card or flushing your caches etc. This would pretty much have the same affect as reseting.

If you dont know how to do all the stuff, a nice little gui hack I found is to switch the suplicant device by clicking on drivers from wicd and changing it to something else besides wext and then changing it back. Otherwise if you connect to the wired network, wait for it to say searching for IP then cancel, hit refresh and see what happens.

Basically you need to know if your network card stops working (i.e you cant see it) or its just a highlevel software problem before we can solve this in a useful way :)

~ Dan

---

### Post by AdamShumpisxXx on 2009-04-05
My experience with WICD is very limited as I am new to it so I don't exactly grasp your "GUI hack". If there is a method of which I can unmount and remount my wireless card using the terminal that you can reveal to me that would be great. Also, would I have to unmount, remount, and post the terminal read-out at any point or just when this random disconnect occurs? Thank you for your help.

---

### Post by zigga15 on 2009-04-05
> **AdamShumpisxXx said:**
> My experience with WICD is very limited as I am new to it so I don't exactly grasp your "GUI hack". If there is a method of which I can unmount and remount my wireless card using the terminal that you can reveal to me that would be great. Also, would I have to unmount, remount, and post the terminal read-out at any point or just when this random disconnect occurs? Thank you for your help.

just double click wicd and click preferences and follow what I said before.

But If you want to do something through terminal:

first check if the card is actually there:
iwconfig

you should have eth1 or wlan0 with all the data there.

if its there then type:

sudo /etc/init.d/networking restart

Let me know if the device is actually there or not. If it isn't then its a major problem with WINEs virtualization methods. Otherwise it should be easier to resolve.

~ Dan

---

### Post by AdamShumpisxXx on 2009-04-05
The command "iwconfig" gives the terminal read-out of:
```

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2860 Wireless  ESSID:"XXX"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:14:BF:16:E7:48   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-56 dBm  Noise level:-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```
As for the terminal code for restarting the network, I will try that when I get randomly disconnected again and post the results. Right now I am trying to see if just letting the computer go for a full 24 hours without running anything through Wine (especially uTorrent) will result at some point with a random disconnect. If nothing happens this will prove uTorrent is the problem and then we will proceed. It'll either end with us fixing the problem or me switching my torrent management program (which I hope I won't have to do as I find uTorrent to be the best in contrast to both native Linux and Windows based software). Thank you again!

---

### Post by AdamShumpisxXx on 2009-04-06
NEW INFORMATION:

I now know uTorrent to be the culprit. What can we do from here? Do I have to find a new torrent management program or can someone help me to correct this?

---

### Post by AdamShumpisxXx on 2009-04-07
Bump?!

---

### Post by Randomperson_1000 on 2009-04-17
I have been experiencing similar problems as you.

My problems started off with deluge and randomly i would get disconnected and my wireless card wouldnt be able to find any networks. After running ifconfig wlan0 down and then turning it back on again I wouldn't be able to connect to any network seems like the card would lock up.

I've been blaming ubuntu juanty since im using the alpha release.

However, I've recently tried another wireless card and it works flawlessly(reception is a bit random). I think the problem you are having is the one I had. I have an ALFA AWUS036H and the reception on the card doesn't go over 15%. This page is the fix for my wireless card but perhaps you can change the code for you card:
[http://mewcetti.com/2009/02/13/getting-the-alfa-awus036h-working-on-ubuntu/](http://mewcetti.com/2009/02/13/getting-the-alfa-awus036h-working-on-ubuntu/)

n.b Although the wireless would disconnect randomly, it would especially disconnect if i turned the screen off. Before I wuld get disconnected DNS would stop working and internet would crawl to 0.x kb/s down speed.

The connection drop isn't because of wine or utorrent (atleast for me). Seems to happen under heavy load usually when bitorrenting

---

### Post by tdavis25 on 2010-02-17
I have had the exact same problem as the OP. Ive noticed that it seems to happen any time there is streaming content going up and down (bittorrent, flash games, weather.com interactive map, etc). Trying to do two of these activities at once is a sure way to cause the wireless to disconnect.

dmesg produced the below text repeating about 100 times:
```
[ 1739.060299] wlan0: no probe response from AP 00:11:50:f0:4f:ae - disassociating
[ 1746.792773] wlan0: authenticate with AP 00:11:50:f0:4f:ae
[ 1746.795280] wlan0: authenticated
[ 1746.795287] wlan0: associate with AP 00:11:50:f0:4f:ae
[ 1746.797732] wlan0: RX ReassocResp from 00:11:50:f0:4f:ae (capab=0x401 status=0 aid=1)
[ 1746.797750] wlan0: associated
[ 1804.070105] wlan0: no probe response from AP 00:11:50:f0:4f:ae - disassociating
[ 1805.492785] wlan0: authenticate with AP 00:11:50:f0:4f:ae
[ 1805.494731] wlan0: authenticated
[ 1805.494739] wlan0: associate with AP 00:11:50:f0:4f:ae
[ 1805.497090] wlan0: RX ReassocResp from 00:11:50:f0:4f:ae (capab=0x401 status=0 aid=1)
[ 1805.497096] wlan0: associated

```

I take this to mean that after connecting to the access point, the wireless driver is not getting a probe response and disconnecting, the reconnecting after a short time. Ive not changed my router settings in a long time and dont have any problems at all when booting to Windows, so I dont think its a router issue.

Heres my lsmod:
```
Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
bridge                 56384  0 
stp                     3012  1 bridge
bnep                   15168  2 
nls_iso8859_1           5280  1 
nls_cp437               6976  1 
vfat                   13184  1 
fat                    59832  1 vfat
snd_hda_codec_nvhdmi     6048  1 
snd_hda_codec_realtek   277860  1 
arc4                    2144  2 
ecb                     3296  2 
ath9k                 278176  0 
mac80211              210008  1 ath9k
ath                    10304  1 ath9k
snd_hda_intel          31880  2 
snd_hda_codec          87584  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
uvcvideo               65260  0 
videodev               43360  1 uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
snd_rawmidi            27360  1 snd_seq_midi
joydev                 13088  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
iptable_filter          3872  0 
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
btusb                  14260  2 
cfg80211              109144  3 ath9k,mac80211,ath
sdhci_pci               8928  0 
sdhci                  20484  1 sdhci_pci
psmouse                57124  0 
serio_raw               6596  0 
nvidia              10316904  38 
snd_timer              26992  2 snd_pcm,snd_seq
ricoh_mmc               4480  0 
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
asus_laptop            21092  0 
led_class               5256  3 ath9k,sdhci,asus_laptop
lp                     11908  0 
parport                40528  2 ppdev,lp
usbhid                 43968  0 
r8169                  38884  0 
mii                     6368  1 r8169
ohci1394               33780  0 
video                  23612  0 
output                  3680  1 video
intel_agp              32816  0 
ieee1394              100896  1 ohci1394

```

and Im running ver 9.10 64bit on an ASUS laptop (dunno what specific wireless card it has...worked fine after install until this problem cropped up)

At first I thought it was a security setting, but Im running open right now and its giving me the same fits. Ive tried Wicd, but had the same problems. I also tried changing torrent clients, but they all have the same problem (currently using qtorrent).

Interestingly enough, lowering the number of torrent connections to 100 max (qtorrent defaulted to 500 max) has caused the problem to lessen. Instead of dropping out every 5 minuets it drops out every 30.

Also, I dont have to re-boot to reconnect. If I wait 2-3 minuets I can reconnect. It may be that Im just more patient though.

---

### Post by Techer on 2010-05-20
I have this problem as well.
It might have something to do with an overflow of bound sockets or open connections or something, for when I turn down the maximum connections in Transmission, it usually takes longer before the issue occurs.
I got disconnected twice while writing this reply; ~$sudo ifconfig wlan0 down/up fixed it.
By the way I am using Lucid Lynx -- I was really hoping for a fix when I upgraded from Jaunty (same issue with Jaunty).

A permanent solution would be greatly appreciated!

---

### Post by Slatts02 on 2010-05-30
Has anyone found a fix for this? 

I am now having this problem after upgrading from 9.10 to 10.04.

Im am using a Sony VAIO BX297XP using Deluge to download BitTorrents.   

It starts off OK but after 10-15 mins or so the Internet drops out and it "forgets" the network key. 

Ive tried dropping the max connections from 500 down to 250, 100, 50, 20 etc.  But still it happens. 

Iwconfig below.

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"XXXX"
          Mode:Managed  Frequency:2.462 GHz  Access Point:  00:22:6B:E6:86:98
          Bit Rate:48 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS throff   Fragment throff
          Power Managementoff
          Link Quality=80/100  Signal level=-49 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:8  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:0   Missed beacon:18

pan0      no wireless extensions.

---

