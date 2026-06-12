---
title: "Ralink RT2500 keeps randomly disconnecting"
date: 2013-06-17
forum: Networking &amp; Wireless
---

### Post by rob888 on 2013-06-17
Update : The wireless connection is a lot better now that I've been trying to do this for a while. If you also have wireless problems with the RT2500, try simply entering into a terminal : modprobe rt2500pci

(not sure if that will work after shutting the laptop down or if it has to be entered again on startup. If so, maybe something like this will help : 
echo rt2500 >> /etc/modules 
or : 
echo rt2500pci >> /etc/modules 
)

 - - -

I'm still pretty new to Linux but have managed to get wireless working on a Thinkpad T61 after a few problems so I'm not totally useless. This problem is on another level though. I'll try to give as much info as possible, and thanks if anyone can help as it's been driving me mad for weeks now.

So the light comes on at the front of the Laptop, which is an Acer Travelmate 2303LC. It can connect for a while sometimes, for instance, last night when using Ubuntu it stayed connected for around an hour as all the updates downloaded and installed. Today though it lasted a few minutes, and it's always kind of random. So maybe a conflict somewhere? (I tried with Ubuntu thinking it might be easier, after giving up am back with Lubuntu which I prefer by far.)

The laptop is fairly new and came with Windows XP installed, but I partitioned to add Linux and then the problems started. It seems like it's because I deleted the recovery partition which also had the wireless drivers on it, because after that point not even windows would stay connected. Ever since then I've had no luck. I didn't get any windows or recovery disc with the laptop either. I've tried using Ndisgtk but when I've done all the steps listed in several posts the laptop literally won't reboot again and I have to reinstall. I tried using this but it can't find ra0 after getting so far so it also doesn't work : [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

Have also tried using the [http://rt2x00.serialmonkey.com]("http://rt2x00.serialmonkey.com/") site but also no luck with that as there's links down for the source code and so on.

The thing that bugs me is that many people don't have any connection then seem to get something sorted, but this laptop IS connected then just randomly disconnects. I saw another thread where a poster asked for info anyway so will just list that same stuff here :

lsmod :

```
Module                  Size  Used byrt73usb                26615  0 
rt2x00usb              19979  1 rt73usb
crc_itu_t              12627  1 rt73usb
bnep                   17669  2 
rfcomm                 37420  0 
bluetooth             202069  10 bnep,rfcomm
arc4                   12543  2 
rt2500pci              18467  0 
snd_intel8x0           33096  1 
rt2x00pci              14151  1 rt2500pci
snd_ac97_codec        105692  1 snd_intel8x0
rt2x00lib              48522  4 rt73usb,rt2x00pci,rt2x00usb,rt2500pci
mac80211              526519  3 rt2x00lib,rt2x00pci,rt2x00usb
ac97_bus               12670  1 snd_ac97_codec
snd_pcm                80890  2 snd_ac97_codec,snd_intel8x0
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
snd_seq_midi           13132  0 
cfg80211              436177  2 mac80211,rt2x00lib
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17097  0 
snd_rawmidi            25114  1 snd_seq_midi
eeprom_93cx6           13168  1 rt2500pci
pcmcia                 39544  0 
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
i915                  535507  2 
snd_timer              24411  2 snd_pcm,snd_seq
yenta_socket           27095  0 
pcmcia_rsrc            18191  1 yenta_socket
snd                    56485  9 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device
microcode              18286  0 
soundcore              12600  1 snd
pcmcia_core            21505  3 pcmcia,pcmcia_rsrc,yenta_socket
psmouse                81038  0 
lpc_ich                16925  0 
drm_kms_helper         47545  1 i915
drm                   228750  3 i915,drm_kms_helper
serio_raw              13031  0 
shpchp                 32129  0 
sbs                    13363  0 
sbshc                  13521  1 sbs
i2c_algo_bit           13197  1 i915
mac_hid                13037  0 
video                  18894  1 i915
lp                     13299  0 
parport                40753  1 lp
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
b44                    31137  0 
ssb                    50628  1 b44



```

iwconfig :

```
wlan0     IEEE 802.11bg  ESSID:off/any            Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.


eth0      no wireless extensions.



```

ifconfig -a :

```
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:54:f3:c4            inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe54:f3c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33545 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25875 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42148326 (42.1 MB)  TX bytes:2730652 (2.7 MB)
          Interrupt:6 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1481 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1481 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:132249 (132.2 KB)  TX bytes:132249 (132.2 KB)


wlan0     Link encap:Ethernet  HWaddr 00:0d:f0:1f:f9:2e  
          inet addr:62.169.151.91  Bcast:62.255.255.255  Mask:255.0.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



```

[COLOR=#000000]cat /etc/resolv.conf :
[/COLOR]
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search lan



```

[COLOR=#000000]route -n
[/COLOR]
```
Kernel IP routing tableDestination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
62.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
```

iwlist scan :

```

wlan0     No scan results


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.

```

rfkill list :

```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



```

And a final one that I've seen asked for often :

lspci :

```

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:02.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 Network controller: Ralink corp. RT2500 Wireless 802.11bg (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller

```

Final note : After around 20 reinstalls I just left the wireless this time and plugged the wired connection in. If anyone needs me to connect via wireless because it'll give some more helpful info via the terminal or something, will do that then post back. So all the output from the terminal above is on a new install without the wireless being used, even though it probably does register as being there still.

Thanks if anyone can help. I'm totally stuck with a wired connection for now, there's hardly anything I find on searches at this point that I haven't already tried/looked at.

---

### Post by rob888 on 2013-06-17
Just to add here so I'm not editing that post yet again : I'm almost thinking of looking at getting the wireless hardware replaced because it seems almost like this just isn't going to get fixed. Have seen quite a few people on my searches who made threads that just stopped getting posted in so it didn't seem resolved, or one or two where the poster even went back to a previous version of linux so the drivers would work. I really don't want to have to resort to that though and might consider replacing the ralink device if possible. It just seems almost broken for linux at this point.

---

### Post by rob888 on 2013-06-18
From going back to this page, the compile newer driver section : [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

1. Download the driver from here : [http://sourceforge.net/projects/rt2400/](http://sourceforge.net/projects/rt2400/)

2. tar -xzf rt73-cvs-daily.tar.gz

3. This gives me the folder rt73-cvs-2009041204, so I then cd into the module folder and type in make, which gives me this :

```
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-25-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-25-generic'
rt73.ko failed to build!
make: *** [module] Error 1

```

So will carry on trying to find a way of getting past this, but if I can't find anything it'd be really appreciated if anyone can help.

edit : Another attempt was to try this post which was linked at the top of that page : [http://ubuntuforums.org/showthread.php?t=584657&p=3595458#post3595458](http://ubuntuforums.org/showthread.php?t=584657&p=3595458#post3595458)

This fails instantly, as the first step is to enter : 

```
sudo apt-get install rt2500-source
```

Which gives the result :

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package rt2500-source
```


The biggest question of all this is : what makes my wireless light turn on and allows me to be connected sometimes for up to an hour before it disconnects? If I don't have the right drivers, what's allowing that connection in the first place?

Pulling out the wired connection and going to wireless (which will soon disconnect for whatever reason.) then typing in iwlist scanning :

```
wlan0     Scan completed :
          Cell 01 - Address: 58:98:35:98:FB:01
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"TNCAP98FB01"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 23256ms ago
                    IE: Unknown: 000B544E434150393846423031
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1E181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD8F0050F204104A00011010440001021041000100103B00010310470010473EC64797C85A6085BB40AA2E0EE1881021000B546563686E69636F6C6F721023000E546563686E69636F6C6F72205447102400043538326E104200093132313257464835561054000800060050F204000110110012546563686E69636F6C6F722054473538326E100800020084103C000101
                    IE: Unknown: DD090010180201000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:24:B2:8F:0F:94
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001d0310841f2
                    Extra: Last beacon: 24788ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD070050F202000100
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 050400010000

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

Edit : Not once since reinstalling (again.) had I been asked for the 10 digit hex password for either the wired or wireless connections, but they'd both been working. So I rebooted, started using synaptic to download VLC player and the wireless went again. Asked for password, then went straight back down after connecting with it.

---

### Post by rob888 on 2013-06-18
Latest test was to try blacklisting conflicting drivers :

sudo leafpad /etc/modprobe.d/blacklist.conf

```

blacklist rt73usb
blacklist rt2x00pci
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00usb

```

This at first made the wireless totally fail so I deleted all entries, but I then rebooted and lsmod is now without the usb drivers listed in the code above :

lsmod :

```

Module                  Size  Used by
nls_iso8859_1          12617  1 
arc4                   12543  2 
snd_intel8x0           33096  1 
rt2500pci              18467  0 
joydev                 17097  0 
rt2x00pci              14151  1 rt2500pci
snd_ac97_codec        105692  1 snd_intel8x0
rt2x00lib              48522  2 rt2x00pci,rt2500pci
ac97_bus               12670  1 snd_ac97_codec
snd_pcm                80890  2 snd_ac97_codec,snd_intel8x0
mac80211              526519  2 rt2x00lib,rt2x00pci
bnep                   17669  2 
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
rfcomm                 37420  0 
bluetooth             202069  10 bnep,rfcomm
pcmcia                 39544  0 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
microcode              18286  0 
snd_rawmidi            25114  1 snd_seq_midi
cfg80211              436177  2 mac80211,rt2x00lib
yenta_socket           27095  0 
sbs                    13363  0 
pcmcia_rsrc            18191  1 yenta_socket
i915                  535544  2 
eeprom_93cx6           13168  1 rt2500pci
pcmcia_core            21505  3 pcmcia,pcmcia_rsrc,yenta_socket
psmouse                81038  0 
sbshc                  13521  1 sbs
serio_raw              13031  0 
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
drm_kms_helper         47545  1 i915
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
shpchp                 32129  0 
drm                   228489  3 i915,drm_kms_helper
video                  18894  1 i915
mac_hid                13037  0 
lpc_ich                16925  0 
snd                    56485  9 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device
i2c_algo_bit           13197  1 i915
soundcore              12600  1 snd
lp                     13299  0 
parport                40753  1 lp
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
usb_storage            47684  1 
b44                    31137  0 
ssb                    50834  1 b44

```

Have been connected fine so far, decided to test with downloading something big in size so currently downloading wine via synaptic, (it used to often fail downloading.) and it's still working, so will wait and see how it goes. It might be that the usb drivers were conflicting though. All I'm unsure about is how they failed to reload after I'd deleted them from the blacklist, but not complaining if it works.

Will post back tomorrow or something as I want a decent bit of time to be sure that it's worked if it has.

---

### Post by rob888 on 2013-06-19
It failed again, but that time it stayed up for a few hours as far as I remember. Am giving up for now, but it does seem like some type of conflict somewhere, and thanks if anyone knows anything I can try that might help. Have decided this laptop can be something to experiment with if it doesn't get sorted as well and will probably just get another soon.

---

### Post by rob888 on 2013-06-20
Couldn't resist trying again and it seems like I'm a lot closer now, or I actually have it fixed.

After all the messing around it seems like a simple command has either fixed things or almost fixed them : modprobe rt2500pci

A few more bits of info :


modinfo rt2500pci :

```

filename:       /lib/modules/3.8.0-25-generic/kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
license:        GPL
description:    Ralink RT2500 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     60A678137D15B5F7F76861B
alias:          pci:v00001814d00000201sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.8.0-25-generic SMP mod_unload modversions 686 

```

sudo lspci | grep -i wireless :

```

02:04.0 Network controller: Ralink corp. RT2500 Wireless 802.11bg (rev 01)
```

sudo lspci -vv -s 02:04.0 :

```


02:04.0 Network controller: Ralink corp. RT2500 Wireless 802.11bg (rev 01)
    Subsystem: Device 18e8:6146
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 10
    Region 0: Memory at e0202000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: rt2500pci

```


For anyone else with this issue, hopefully this can help you either get closer or suss the problem out.

---

