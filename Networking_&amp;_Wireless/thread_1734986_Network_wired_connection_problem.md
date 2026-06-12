---
title: "Network: wired connection problem"
date: 2011-04-20
forum: Networking &amp; Wireless
---

### Post by trikinosis on 2011-04-20
hi, this is my first post, and i need help..
i can't connect to the wired connection, but i can connect to the wireless...
i'm using Ubuntus 10.04. when  i run this codes into the terminal it shows:

root@valdivia-laptop:/home/valdivia# sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:b1:8a:f8:5a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=10.9.13.114 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:ff600000-ff60ffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:05:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:ff500000-ff53ffff ioport:d000(size=128)

root@valdivia-laptop:/home/valdivia# ifconfig
lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:44 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:44 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:3474 (3.4 KB)  TX bytes:3474 (3.4 KB)

wlan0     Link encap:Ethernet  direcciónHW 00:1b:b1:8a:f8:5a  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:211004 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:144207 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:291619998 (291.6 MB)  TX bytes:14771900 (14.7 MB)


root@valdivia-laptop:/home/valdivia# cat /etc/network/interfaces
auto lo
iface lo inet loopback


i saw this codes in a old post, and i think that you can help me with that information plzzzzz

---

### Post by nfoglesbee on 2011-04-21
This is similar to the problem I'm experiencing ([http://ubuntuforums.org/showthread.php?t=1734552](http://ubuntuforums.org/showthread.php?t=1734552)).  You might try and follow some of the advice I've been given there... maybe something will work for you.

---

### Post by dandnsmith on 2011-04-21
The ethernet interface isn't configured (for whatever reason) - I'd expect it to show as eth0 or similar.
You probably need to get to System | Administration | Network Tools and configure the interface there.

HTH

---

### Post by trikinosis on 2011-04-21
> **dandnsmith said:**
> The ethernet interface isn't configured (for whatever reason) - I'd expect it to show as eth0 or similar.
You probably need to get to System | Administration | Network Tools and configure the interface there.

HTH

i can't configure the interface, i have not access to do that....
what can i do?

> **nfoglesbee said:**
> This is similar to the problem I'm experiencing ([http://ubuntuforums.org/showthread.php?t=1734552](http://ubuntuforums.org/showthread.php?t=1734552)).  You might try and follow some of the advice I've been given there... maybe something will work for you.
that problem is with the router, and i have only a cable network access, that is provided by my university..

---

### Post by josephmills on 2011-04-21
hi there could we please see a 
```

lspci

```
and
```

lsmod

```
Thanks

---

### Post by trikinosis on 2011-04-21
> **josephmills said:**
> hi there could we please see a 
```

lspci

```and
```

lsmod

```Thanks


valdivia@valdivia-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Dell Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
05:00.0 Ethernet controller: Atheros Communications AR8152 v2.0 Fast Ethernet (rev c1)

valdivia@valdivia-laptop:~$ lsmod
Module                  Size  Used by
cryptd                  8116  0 
aes_x86_64              7912  0 
aes_generic            27607  1 aes_x86_64
rfcomm                 40393  4 
sco                     9649  2 
binfmt_misc             7960  1 
bridge                 53216  0 
stp                     2171  1 bridge
ppdev                   6375  0 
bnep                   11884  2 
l2cap                  34807  16 rfcomm,bnep
snd_hda_codec_realtek   279072  1 
snd_hda_intel          25805  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
arc4                    1473  2 
wl                   1964968  0 
lib80211                6151  1 wl
snd_rawmidi            23420  1 snd_seq_midi
fbcon                  39270  71 
tileblit                2487  1 fbcon
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
font                    8053  1 fbcon
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
bitblit                 5811  1 fbcon
btusb                  13001  2 
ath9k                 329117  0 
snd_timer              23649  2 snd_pcm,snd_seq
bluetooth              58685  9 rfcomm,sco,bnep,l2cap,btusb
lp                      9336  0 
uvcvideo               62819  0 
softcursor              1565  1 bitblit
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              238896  1 ath9k
fglrx                2353486  29 
video                  20623  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
snd                    71251  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath                     9723  1 ath9k
dell_wmi                2177  0 
soundcore               8052  1 snd
vga16fb                12757  1 
v4l2_compat_ioctl32    11892  1 videodev
vgastate                9857  1 vga16fb
output                  2503  1 video
parport                37160  2 ppdev,lp
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
cfg80211              148725  3 ath9k,mac80211,ath
psmouse                64576  0 
dell_laptop             7973  0 
dcdbas                  6886  1 dell_laptop
i2c_piix4               9639  0 
edac_core              45423  0 
led_class               3764  1 ath9k
serio_raw               4918  0 
edac_mce_amd            9278  0 
shpchp                 33711  0 
usbhid                 41116  0 
hid                    83600  1 usbhid
ahci                   37870  2

---

### Post by dandnsmith on 2011-04-22
> **trikinosis said:**
> i can't configure the interface, i have not access to do that....
what can i do?

I don't understand - didn't you install the OS?

---

### Post by trikinosis on 2011-04-22
> **dandnsmith said:**
> I don't understand - didn't you install the OS?

yes i did it..but really i don't know how to configure the interface...there is an unknow interface like this:
[[IMG]http://s2.subirimagenes.com/imagen/previo/thump_6295705pantallazo.png[/IMG]]("http://www.subirimagenes.com/imagen-pantallazo-6295705.html")

when you said me that i have to configure the interface...you mean something like the image???
with this mac i haven't problem with window 7..but Ubuntus no recognize nothing XD
help me! plz

PD: i'm working in spanish..i hope you understand the image (words)

---

### Post by dandnsmith on 2011-04-23
Thanks for that picture - gives useful data, and demonstrates that I was pointing you to the wrong place. Sorry.

The configuration bit is, curiously, System |Preferences|Network Connections - I daren't put that into Spanish, as my computer technical Spanish isn't good enough (but I can recognise the stuff in your pic)

You want the 'wired' tab, select the hardware interface, and click on 'edit'.
Explore, and try the settings. I'd go for DHCP.

HTH

---

### Post by dineshs on 2011-04-23
sudo lshw -C network says network unclaimed (Driver issue?) .Connect wireless go to system-administration-additional drivers and see if it is possible to install driver for AR8152.If it fails try [this]("http://ubuntuforums.org/showthread.php?t=1505697") postcount #6.Though it is for version1 it may work for version2..You need to install build-essential before compiling.
```
sudo apt-get install build-essential
```
note:You may also search google for installing AR8152 version 2 driver

---

### Post by trikinosis on 2011-04-23
> **dineshs said:**
> sudo lshw -C network says network unclaimed (Driver issue?) .Connect wireless go to system-administration-additional drivers and see if it is possible to install driver for AR8152.If it fails try [this]("http://ubuntuforums.org/showthread.php?t=1505697") postcount #6.Though it is for version1 it may work for version2..You need to install build-essential before compiling.
```
sudo apt-get install build-essential
```note:You may also search google for installing AR8152 version 2 driver


i did it 3 times... and it doesn't work.. an error appears at the final of the process...
but i'll do again..
a question... how can i delete the files with a padlock???

---

### Post by dookiebowser on 2011-04-23
Having [similar issue]("http://ubuntuforums.org/showthread.php?t=1737741") with Intel 82573L. 

Same symptoms as trikinosis.

no eth0, but driver modules are loaded. my /etc/network/interfaces did not have eth0 either, had to manually add it. sudo lshw -C showed network unclaimed like trikinosis. if my guess is right, his network connections won't have a wired connection there already either. 

will be watching this thread for possible solutions, thanks.

---

### Post by dineshs on 2011-04-24
> i did it 3 times... and it doesn't work.. an error appears at the final of the process...Can you post the result (error)
You should have internet connection while trying this.So connect your wireless.
dookiebowser,
Did you try post #2 [here]("http://ubuntuforums.org/showthread.php?t=1473363")
or
[http://ubuntuforums.org/showpost.php?p=5785758&postcount=2](http://ubuntuforums.org/showpost.php?p=5785758&postcount=2)

---

### Post by trikinosis on 2011-04-24
> **dineshs said:**
> Can you post the result (error)
You should have internet connection while trying this.So connect your wireless.
dookiebowser,
Did you try post #2 [here]("http://ubuntuforums.org/showthread.php?t=1473363")
or
[http://ubuntuforums.org/showpost.php?p=5785758&postcount=2](http://ubuntuforums.org/showpost.php?p=5785758&postcount=2)


i did again....and it doesn't appears errors!!!
now in the network connections there are wireless and wired connections (cable)...tomorrow i have access to the cable network in my university...i hope it works fine...
so tomorrow i'll have the really answer.. anyway thanks a lot to all the people that helped me...i'm really happy :)
i used this link too: [http://sites.google.com/site/trucosubuntu/controladores/wifi/compatwireless](http://sites.google.com/site/trucosubuntu/controladores/wifi/compatwireless)
if anyone have the same problem it could be useful

finally, look this image and tell me if it is correct..
[IMG]http://ubuntuforums.org/%3Ca%20href=http://www.subirimagenes.com/imagen-pantallazo-6303620.html%20target=_blank%3E[IMG]http://s2.subirimagenes.com/imagen/previo/thump_6303620pantallazo.png[/IMG][IMG]http://s2.subirimagenes.com/imagen/previo/thump_6303620pantallazo.png[/IMG]

before in network it said NETWORK UNCLAIMED and it change..

---

### Post by trikinosis on 2011-04-25
it's working the wired connection (cable)...
thanks!

---

### Post by dineshs on 2011-04-25
Please mark the thread as [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") via thread tools

---

