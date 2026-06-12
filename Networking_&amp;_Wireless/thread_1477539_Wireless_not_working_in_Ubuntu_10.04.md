---
title: "Wireless not working in Ubuntu 10.04"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by Sean Hayes on 2010-05-08
Wireless keeps dropping out at random intervals, but usually still shows up as connected when not working.

I tried installing linux-backports-modules-wireless-lucid and restarted, but then I couldn't connect at all (Wicd hung at "Obtaining IP Address"). I uninstalled it and now have my semi-working connection back.

1. My laptop: [http://www.amazon.com/Acer-AS5542-5547-15-6-Inch-Laptop-Blue/dp/B0031M9ZSM/ref=sr_1_7?ie=UTF8&s=pc&qid=1272762199&sr=1-7](http://www.amazon.com/Acer-AS5542-5547-15-6-Inch-Laptop-Blue/dp/B0031M9ZSM/ref=sr_1_7?ie=UTF8&s=pc&qid=1272762199&sr=1-7)

Acer Aspire AS5542-5547

2. ```
$ lspci -nn | grep 'Atheros'
09:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
```

3. ```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:2d:71:a0:0b  
          inet6 addr: fe80::226:2dff:fe71:a00b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4244 (4.2 KB)  TX bytes:492 (492.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1926 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:250946 (250.9 KB)  TX bytes:250946 (250.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:c4:ca:43:76  
          inet addr:192.168.10.191  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::217:c4ff:feca:4376/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:791 errors:0 dropped:0 overruns:0 frame:0
          TX packets:692 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:689772 (689.7 KB)  TX bytes:170301 (170.3 KB)
```

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Sphynx Router"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:14:D1:C2:61:3E   
          Bit Rate=0 kb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-25 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.
```

4. ```
$ lsmod
Module                  Size  Used by
cryptd                  8116  0 
aes_x86_64              7912  1 
aes_generic            27607  1 aes_x86_64
binfmt_misc             7960  1 
ppdev                   6375  0 
vboxnetadp              5235  0 
vboxnetflt             12242  0 
vboxdrv              1768311  2 vboxnetadp,vboxnetflt
arc4                    1473  2 
ath9k                 328829  0 
snd_hda_codec_atihdmi     3023  1 
mac80211              238128  1 ath9k
snd_hda_codec_realtek   278890  1 
ath                     9723  1 ath9k
snd_hda_intel          25645  1 
snd_hda_codec          85727  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
uvcvideo               62403  0 
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2353422  32 
joydev                 11072  0 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
snd                    70978  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              148386  3 ath9k,mac80211,ath
acer_wmi               15829  0 
psmouse                64608  0 
serio_raw               4918  0 
edac_core              45423  0 
edac_mce_amd            9214  0 
led_class               3732  2 ath9k,acer_wmi
i2c_piix4               9639  0 
shpchp                 33679  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
video                  20623  0 
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 40988  0 
hid                    83376  1 usbhid
ahci                   37646  4 
tg3                   122350  0 
```

5. ```
$ dmesg | grep 'ath9k'
[   14.526948] ath9k 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.526958] ath9k 0000:09:00.0: setting latency timer to 64
[   14.964589] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   14.965152] Registered led device: ath9k-phy0::radio
[   14.965165] Registered led device: ath9k-phy0::assoc
[   14.965180] Registered led device: ath9k-phy0::tx
[   14.965192] Registered led device: ath9k-phy0::rx
[   31.220131] ath9k: Two wiphys trying to scan at the same time
```

6. ```
$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 00:26:2d:71:a0:0b
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=sb v2.19 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: irq:28 memory:f0300000-f030ffff
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 01
       serial: 00:17:c4:ca:43:76
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.10.191 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f0400000-f040ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

7. ```
$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:14:D1:C2:61:3E
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=70/70  Signal level=-27 dBm  
                    Encryption key:on
                    ESSID:"Sphynx Router"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002f2cd600a7
                    Extra: Last beacon: 2600ms ago
                    IE: Unknown: 000D537068796E7820526F75746572
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340305070000000F000000000000000000000000000000
                    IE: Unknown: 2D1A4E101FFFFF000000000000000000000000000004000000000000
                    IE: Unknown: 3D160305030000000F000000000000000000000000000000
                    IE: Unknown: DD7D0050F204104A0001101044000102103B00010310470010D82C0C438E883E4187193CC2537956B91021000E5452454E446E65742C20496E632E102300095445572D3633334752102400024131104200046E6F6E651054000800060050F204000110110013576972656C6573732031316E20526F75746572100800020004
```

8. ```
$ lsb_release -d
Description:	Ubuntu 10.04 LTS
```

9. ```
$ uname -mr
2.6.32-22-generic x86_64
```

10. ```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ]
```

---

### Post by Sean Hayes on 2010-05-12
Bump.

It's now disconnecting after a few minutes.

---

### Post by Sean Hayes on 2010-06-19
bump

---

### Post by jrowland on 2010-06-22
I'm having the same issue.  I seem to have narrowed down my network dropping out to when I attempt to do some "heavy lifting" like watch a youtube video, or run the Ubuntu update manager.

I posted a separate thread here:
[http://ubuntuforums.org/showthread.php?p=9494481](http://ubuntuforums.org/showthread.php?p=9494481)

I know it doesn't answer your question, but you're definitely not the only one.

---

### Post by Sean Hayes on 2010-06-22
Yeah, I've noticed it tends to drop out during heavy network use too. Not all the time though, maybe 1/3 of the time I start heavy use.

---

### Post by upover on 2010-06-25
I'm having a similar problem. I'm using a Sony Vaio VGN CS11-S, which has an Intel Wifi 5100 wireless  card and I'm running Ubuntu 10.04. Unfortunately, I can't give you any information on how previous versions of Ubuntu work as I only converted from Windows this week (it's been a good thing so far, other than this access point issue).

I have noted that my wireless access point connection at home drops out exactly 59 seconds after it last connected. It then takes about 45 seconds to connect, and, Voila!... 59 seconds later - another drop out. 

I have set up a wired connection at home through the access point with  exactly the same settings as the wireless...and it runs fine! - same  static ip/netmask/gateway/dns, same MAC address, etc.

Please note that my wireless connection at work connects straight to a router, not an access point connecting to a router, and this works fine, too! Actually, the router at work is exactly the same router as the router connected to the Internet on my home connection, the only difference being that at home I have to run through another router acting as an access point to get to it.

By the way, my problem is not related to heavy usage or anything else. From the time I boot up Ubuntu, it connects, drops 59 seconds later, reconnects (after a long 45ish seconds), drops again 59 seconds later, etc. I can sit there, do nothing and watch it. It doesn't seem related to anything else on my system. It just seems to be a wireless access point issue, as it works fine straight into a router, and it works fine through the access point with a wired network with the same settings.

I do apologize, but after only converting to Ubuntu this week I don't have any more technical information for you. Guru's... please feel free to grab me by the nose and lead me through any testing you would like me to do. I am happily engaging in the spirit of open source and will send you anything you need (if you can tell me how to do it).

---

### Post by Sean Hayes on 2010-06-25
> **upover said:**
> I'm having a similar problem. I'm using a Sony Vaio VGN CS11-S, which has an Intel Wifi 5100 wireless  card and I'm running Ubuntu 10.04. Unfortunately, I can't give you any information on how previous versions of Ubuntu work as I only converted from Windows this week (it's been a good thing so far, other than this access point issue).

I have noted that my wireless access point connection at home drops out exactly 59 seconds after it last connected. It then takes about 45 seconds to connect, and, Voila!... 59 seconds later - another drop out. 

I have set up a wired connection at home through the access point with  exactly the same settings as the wireless...and it runs fine! - same  static ip/netmask/gateway/dns, same MAC address, etc.

Please note that my wireless connection at work connects straight to a router, not an access point connecting to a router, and this works fine, too! Actually, the router at work is exactly the same router as the router connected to the Internet on my home connection, the only difference being that at home I have to run through another router acting as an access point to get to it.

By the way, my problem is not related to heavy usage or anything else. From the time I boot up Ubuntu, it connects, drops 59 seconds later, reconnects (after a long 45ish seconds), drops again 59 seconds later, etc. I can sit there, do nothing and watch it. It doesn't seem related to anything else on my system. It just seems to be a wireless access point issue, as it works fine straight into a router, and it works fine through the access point with a wired network with the same settings.

I do apologize, but after only converting to Ubuntu this week I don't have any more technical information for you. Guru's... please feel free to grab me by the nose and lead me through any testing you would like me to do. I am happily engaging in the spirit of open source and will send you anything you need (if you can tell me how to do it).
That issue sounds a little different, mine sometimes stays up for hours, sometimes seconds. It's probably a good idea if you open a new thread for your issue as there may be a different cause/solution. The sticky thread here: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) has instructions for posting debug info (like my 1st post above has). After you've done that feel free to post a link to it here.

---

### Post by Sean Hayes on 2010-06-26
I *may* have found a solution. I use Wicd, and while looking through the options I noticed the dhcp client settings; it's set to automatic, but the only option available was dhclient (I remember there being more than 1 option in previous versions of Ubuntu). While looking around for solutions earlier I came across some other wireless problems and people reported that dhclient didn't work well for them and that dhcpcd was better. I went into Synaptic, installed the dhcpcd package, and restarted my machine. I left the Wicd setting to automatic, but dhcpcd is now an option. I restarted my computer ~6 hours ago and haven't noticed any problems. I'll report back in a few days with further results.

---

### Post by Sean Hayes on 2010-06-26
OK, it just stopped working again (didn't disconnect but no network activity), but that's only once in 20+ hours, normally it would have happened 4+ times by now. Also, when trying to reconnect it'll fail within 30 seconds instead of going on for several minutes. Reconnecting did take 4-5 tries over a period of a few minutes as usual though. Another difference is half the time the router would show up as ~100% and the other half 30%-60%, but now it's always ~100%.

---

### Post by Arundel_MTL on 2010-06-27
> **Sean Hayes said:**
> I *may* have found a solution. I use Wicd, and while looking through the options I noticed the dhcp client settings; it's set to automatic, but the only option available was dhclient (I remember there being more than 1 option in previous versions of Ubuntu). While looking around for solutions earlier I came across some other wireless problems and people reported that dhclient didn't work well for them and that dhcpcd was better. I went into Synaptic, installed the dhcpcd package, and restarted my machine. I left the Wicd setting to automatic, but dhcpcd is now an option. I restarted my computer ~6 hours ago and haven't noticed any problems. I'll report back in a few days with further results.
I'Ve had the same problem now for over 2 months, and all I found to help on this problem was to have a 30 feet yellow ethernet cable going from my acer aspireone zg5 to my router, both at home and work.  Tried what you said, and although I do not use wicd, it works perfectly with the default connection manager of 10.04. No longer feels like being back on a 14.4 !

---

### Post by sdavis3911 on 2010-06-30
I had the same problems and tried the various solutions listed with no joy.   Finally went out to [http://linuxwireless.org/en/users/Drivers](http://linuxwireless.org/en/users/Drivers) and got their ath9k driver.   

Beforehand I was able to consistently "break" the connection by transferring a big file.  After installing the driver and a few hours of trying I haven't been able to get the connection to drop again.

I'm keeping my fingers crossed, but I'm pretty hopeful at this point.

---

### Post by Sean Hayes on 2010-06-30
Thanks for posting. I've tried the linux-backports-modules-wireless-lucid-generic package, which I think contains the same stuff as compat-wireless, and it caused kernel panicks for me. Hopefully it'll work for other people though.

---

### Post by eptii on 2010-10-06
does anyone have a fix for this yet? I have a compaq 2510p and have seen this issue on my laptop with Windows XP, Windows 7 and Ubuntu. I have tried working with Cisco, Intel, and Compaq and nobody has a fix yet. I have updated the bios, tried different drivers for both windows XP and Windows 7 with no luck. It happens radomly but U can make it happen by transferring a large file. With Windows XP and Windows 7 only a reboot fixes it. With Ubuntu it disconnects and reconnects on its own.

---

### Post by aspora.isernia on 2010-10-08
My laptop also shows the same symptoms! The wireless connection works for a random amount of minutes after connect, but suddenly it stops its activity! The strange thing is that with 8.04 it worked perfectly! Another strange thing is that it does so only when I use a WPA cryptography... With WEP it is always up.
Any suggestion on how to proceed with debugging? Thanks

---

### Post by zdenal on 2010-10-11
Maybe this how-to will helps:

[http://polach.cc/howto-fix-broadcom-wifi-adapter-wpa-network-access-on-ubuntu-10-04-lucid-lynx](http://polach.cc/howto-fix-broadcom-wifi-adapter-wpa-network-access-on-ubuntu-10-04-lucid-lynx)

---

### Post by skrawboy on 2011-06-25
This worked for me. Ubuntu 10.04
[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

---

### Post by NielOlsson on 2012-02-03
I recently purchase a new Wireless router (Linksys E2500) for my home and immediately started having issues with Wireless speeds but only with Ubuntu.  The Apple devices and Windows PC's were unaffected.  I researched the topic carefully and tried many of the suggested fixes but was making no headway until I read a post indicating issues with WPA.  So I connected my Ubuntu 10.04 PC to other wireless networks that were not WPA and wireless speeds were consistent (I use speakeasy.net to monitor).  This began iterative testing with different router settings and I learned that my router default was WPA2/WPA Mixed Mode.  When I changed the setting to WEP or simply WPA all of my issues went away.  My only concern now is that if I bring the laptop to a company site that has wireless routers using WPA2/WPA Mixed Mode I'll be screwed.  Best of luck, I hope this helps!

---

