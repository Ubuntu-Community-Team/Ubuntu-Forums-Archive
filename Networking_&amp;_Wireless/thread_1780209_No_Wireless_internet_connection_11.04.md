---
title: "No Wireless internet connection 11.04"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by Jannes. on 2011-06-11
Guys,

I have no wireless internet on my 11.04. I can access my wired connection but my wireless doesn't show connections and isnt able to connect to any wireless network in the neighbourhood. (I had this probz too in 9.10 and 10.04) But none of the solutions work now.

I'll show you some stuff which maybe can help you to help me :)

_I already tried to blacklist the blacklist at76c50x_usb_

**LSUSB**
```
jannes@jannes-DY137A-B14-a540-be:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0681:001b Siemens Information and Communication Products WLL013
Bus 003 Device 002: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

**LSMOD**
```
jannes@jannes-DY137A-B14-a540-be:~$ sudo lsmod
Module                  Size  Used by
parport_pc             32111  1 
ppdev                  12849  0 
vesafb                 13449  1 
binfmt_misc            13213  1 
snd_intel8x0           33213  2 
snd_usb_audio          91410  1 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  3 snd_intel8x0,snd_ac97_codec,snd_usb_audio
snd_hwdep              13274  1 snd_usb_audio
snd_usbmidi_lib        24388  1 snd_usb_audio
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_seq,snd_rawmidi
gspca_stv06xx          32353  0 
gspca_main             27894  1 gspca_stv06xx
snd                    55295  16 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
videodev               75143  1 gspca_main
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
8139too                23208  0 
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
8139cp                 22497  0 
crc_itu_t              12627  1 firewire_core

```

**sudo lshw -C network**
```
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 10
       serial: 00:0c:76:e1:38:d5
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.109 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:23 ioport:c400(size=256) memory:df010000-df0100ff memory:40000000-4000ffff

```

---

### Post by Toz on 2011-06-11
I guess you're referring to: [http://ubuntuforums.org/showthread.php?t=1497108]("http://ubuntuforums.org/showthread.php?t=1497108") - doesn't look promising. 
There is also a recent post regarding I believe this same device: [http://ubuntuforums.org/showthread.php?p=10906990]("http://ubuntuforums.org/showthread.php?p=10906990")

You can try going through all the steps in the first post and see if there is a change for 11.04. 

The first step would be to verify the existence of the firmware. 
```
dmesg | grep at76
```
```
apt-cache policy linux-firmware
```
```
apt-cache policy atmel-firmware
```

---

### Post by Jannes. on 2011-06-11
```
dmesg | grep at76
```
does nothing ???

apt-cache policy linux-firmware
```
jannes@jannes-DY137A-B14-a540-be:~$ apt-cache policy linux-firmware
linux-firmware:
  Geïnstalleerd: 1.52
  Kandidaat:     1.52
  Versietabel:
 *** 1.52 0
        500 http://nl.archive.ubuntu.com/ubuntu/ natty/main i386 Packages
        100 /var/lib/dpkg/status
```


apt-cache policy atmel-firmware
```
jannes@jannes-DY137A-B14-a540-be:~$ apt-cache policy atmel-firmware
atmel-firmware:
  Geïnstalleerd: (geen)
  Kandidaat:     1.3-4
  Versietabel:
     1.3-4 0
        500 http://nl.archive.ubuntu.com/ubuntu/ natty/multiverse i386 Packages
jannes@jannes-DY137A-B14-a540-be:~$ 

```

---

### Post by Toz on 2011-06-11
Plug it in (or unplug and re-plug) and then post back all of dmesg. Wondering if its even being recognized.

---

### Post by Jannes. on 2011-06-12
nope still nothing... Maybe it is because i have blacklisted that one thing?

---

### Post by Toz on 2011-06-12
Try removing from blacklist, retry, and post back entire contents of dmesg.

---

### Post by Jannes. on 2011-06-12
Okay i can see my wireless again. Also the possible connections from the neighbourhood. The only problem now is Connecting. It takes a long time and then it fails...

The last code:
```
jannes@jannes-DY137A-B14-a540-be:~$ dmesg | grep at76
[   15.959812] usbcore: registered new interface driver at76c50x-usb
[   45.555952] ieee80211 phy0: at76_wait_completion failed: 7
[   47.660872] ieee80211 phy0: at76_wait_completion failed: 7
[   49.764760] ieee80211 phy0: at76_wait_completion failed: 7
jannes@jannes-DY137A-B14-a540-be:~$ 

```

---

### Post by Toz on 2011-06-12
Try installing the atmel firmware:```
sudo apt-get install atmel-firmware
```

---

### Post by Jannes. on 2011-06-12
Ok i have done that.

I can see my wireless again, and the incoming connections. But when i try to connect to my internet it fails after a period of time...
No error or smth just no internetconnection.

---

### Post by Toz on 2011-06-12
Did you reboot? If not, please do so and post back contents of **dmesg**

---

### Post by Jannes. on 2011-06-12
After a reboot

```
jannes@jannes-DY137A-B14-a540-be:~$ dmesg | grep at76
[   15.299852] Atmel at76x USB Wireless LAN Driver 0.17 loading
[   16.358644] usb 2-2: using firmware atmel_at76c503-rfmd.bin (version 1.101.0-84)
[   16.444000] usbcore: registered new interface driver at76c50x-usb
[   47.241163] ieee80211 phy0: at76_wait_completion failed: 7
[   49.345038] ieee80211 phy0: at76_wait_completion failed: 7
[   51.448953] ieee80211 phy0: at76_wait_completion failed: 7
jannes@jannes-DY137A-B14-a540-be:~$ 


```

---

### Post by superduperlinuxperson on 2011-06-12
can you run lspci -vnn | grep 14e4 and tell me what the output is
thanks

---

### Post by Jannes. on 2011-06-12
```
jannes@jannes-DY137A-B14-a540-be:~$ lspci -vnn | grep 14e4
jannes@jannes-DY137A-B14-a540-be:~$ 

```

---

### Post by josephmills on 2011-06-12
hi there could we please see a ```
lsmod
``` again and a ```
rfkill list all 
``` thanks  also what happens after a ```
modprobe at76c50x-usb
```

---

### Post by jamees on 2011-06-12
thank for information...I have to problems with wireless..and I solved the problem

---

### Post by josephmills on 2011-06-12
> **jamees said:**
> thank for information...I have to problems with wireless..and I solved the problem

what is the recipe to successiveness ?

---

### Post by Jannes. on 2011-06-12
LSMOD
```
jannes@jannes-DY137A-B14-a540-be:~$ lsmod
Module                  Size  Used by
vesafb                 13449  1 
parport_pc             32111  1 
ppdev                  12849  0 
arc4                   12473  2 
nvidia               7098106  24 
at76c50x_usb           39861  0 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
binfmt_misc            13213  1 
ac97_bus               12642  1 snd_ac97_codec
snd_usb_audio          91410  1 
snd_pcm                80244  3 snd_intel8x0,snd_ac97_codec,snd_usb_audio
snd_hwdep              13274  1 snd_usb_audio
snd_usbmidi_lib        24388  1 snd_usb_audio
snd_seq_midi           13132  0 
mac80211              257001  1 at76c50x_usb
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi
snd_timer              28659  2 snd_pcm,snd_seq
cfg80211              156212  1 mac80211
snd_seq_device         14110  3 snd_seq_midi,snd_seq,snd_rawmidi
gspca_stv06xx          32353  0 
gspca_main             27894  1 gspca_stv06xx
snd                    55295  16 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
videodev               75143  1 gspca_main
soundcore              12600  1 snd
shpchp                 32345  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
firewire_ohci          31504  0 
8139too                23208  0 
firewire_core          56138  1 firewire_ohci
8139cp                 22497  0 
crc_itu_t              12627  1 firewire_core
jannes@jannes-DY137A-B14-a540-be:~$ 

```

RFKILL
```
jannes@jannes-DY137A-B14-a540-be:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
jannes@jannes-DY137A-B14-a540-be:~$ 

```


MODPROBE
```
jannes@jannes-DY137A-B14-a540-be:~$ modprobe at76c50x-usb
jannes@jannes-DY137A-B14-a540-be:~$ 


```

---

### Post by josephmills on 2011-06-12
```
dmesg | grep -i  at76c50x-usb 
``` thanks

---

### Post by Jannes. on 2011-06-12
```
jannes@jannes-DY137A-B14-a540-be:~$  modinfo at76c50x-usb | grep firmware
firmware:       atmel_at76c505amx-rfmd.bin
firmware:       atmel_at76c505a-rfmd2958.bin
firmware:       atmel_at76c505-rfmd2958.bin
firmware:       atmel_at76c505-rfmd.bin
firmware:       atmel_at76c503-rfmd-acc.bin
firmware:       atmel_at76c503-rfmd.bin
firmware:       atmel_at76c503-i3863.bin
firmware:       atmel_at76c503-i3861.bin
jannes@jannes-DY137A-B14-a540-be:~$ 

```

---

### Post by josephmills on 2011-06-12
> **Jannes. said:**
> ```
jannes@jannes-DY137A-B14-a540-be:~$  modinfo at76c50x-usb | grep firmware
firmware:       atmel_at76c505amx-rfmd.bin
firmware:       atmel_at76c505a-rfmd2958.bin
firmware:       atmel_at76c505-rfmd2958.bin
firmware:       atmel_at76c505-rfmd.bin
firmware:       atmel_at76c503-rfmd-acc.bin
firmware:       atmel_at76c503-rfmd.bin
firmware:       atmel_at76c503-i3863.bin
firmware:       atmel_at76c503-i3861.bin
jannes@jannes-DY137A-B14-a540-be:~$ 

```

check post again copying and pasting to fast sorry and thanks ```
dmesg | grep -i  at76c50x-usb
``` thanks again

---

### Post by Jannes. on 2011-06-12
```
jannes@jannes-DY137A-B14-a540-be:~$ dmesg | grep -i  at76c50x-usb
jannes@jannes-DY137A-B14-a540-be:~$ 
```


it does nothing

---

### Post by josephmills on 2011-06-12
> **Jannes. said:**
> ```
jannes@jannes-DY137A-B14-a540-be:~$ dmesg | grep -i  at76c50x-usb
jannes@jannes-DY137A-B14-a540-be:~$ 
```


it does nothing

thats not good wheres the firmware..... lets try ```
dmesg | grep -i at76
``` thanks
lets also try to load the mods again ```
sudo -s 
``` then ```
modprobe at76c50x-usb
``` then an ```
exit 
```anything?

---

### Post by Jannes. on 2011-06-12
```
jannes@jannes-DY137A-B14-a540-be:~$  modinfo at76c50x-usb | grep firmware
firmware:       atmel_at76c505amx-rfmd.bin
firmware:       atmel_at76c505a-rfmd2958.bin
firmware:       atmel_at76c505-rfmd2958.bin
firmware:       atmel_at76c505-rfmd.bin
firmware:       atmel_at76c503-rfmd-acc.bin
firmware:       atmel_at76c503-rfmd.bin
firmware:       atmel_at76c503-i3863.bin
firmware:       atmel_at76c503-i3861.bin
jannes@jannes-DY137A-B14-a540-be:~$ dmesg | grep -i  at76c50x-usb
jannes@jannes-DY137A-B14-a540-be:~$ dmesg | grep -i  at76c50x-usb
jannes@jannes-DY137A-B14-a540-be:~$ dmesg | grep -i at76
[  670.110455] ieee80211 phy0: at76_wait_completion failed: 7
[ 2731.076919] ieee80211 phy0: at76_wait_completion failed: 7
[ 2733.180780] ieee80211 phy0: at76_wait_completion failed: 7
[ 2735.283641] ieee80211 phy0: at76_wait_completion failed: 7
jannes@jannes-DY137A-B14-a540-be:~$ sudo -s
[sudo] password for jannes: 
root@jannes-DY137A-B14-a540-be:~# modprobe at76c50x-usb
root@jannes-DY137A-B14-a540-be:~# exit
exit
jannes@jannes-DY137A-B14-a540-be:~$ 



```

---

### Post by josephmills on 2011-06-12
hmmm..... eject it then plug it back in I still dont see the firmware though have you tried to download it and extract it in the firmware dir ? lets see if it is there all ready ```
ls /lib/firmware 
``` thanks

---

### Post by Jannes. on 2011-06-12
```
jannes@jannes-DY137A-B14-a540-be:~$ ls /lib/firmware
2.6.38-8-generic                    atmel_at76c503-rfmd-acc.bin
atmel_at76c502_3com.bin             atmel_at76c503-rfmd.bin
atmel_at76c502_3com-wpa.bin         atmel_at76c504_2958-wpa.bin
atmel_at76c502.bin                  atmel_at76c504a_2958-wpa.bin
atmel_at76c502d.bin                 atmel_at76c504.bin
atmel_at76c502d-wpa.bin             atmel_at76c504c-wpa.bin
atmel_at76c502e.bin                 atmel_at76c505a-rfmd2958.bin
atmel_at76c502e-wpa.bin             atmel_at76c505-rfmd2958.bin
atmel_at76c502-wpa.bin              atmel_at76c505-rfmd.bin
atmel_at76c503-i3861.bin            atmel_at76c506.bin
atmel_at76c503-i3863.bin            atmel_at76c506-wpa.bin
atmel_at76c503-rfmd-0.90.2-140.bin  hp
jannes@jannes-DY137A-B14-a540-be:~$ 
```

so i have to eject it and plug it in again?

---

### Post by josephmills on 2011-06-12
I am at a great loss I am sorry I think that it has something to do with the firmware though I could be wrong. I guesss that I will have to buy one and play with it can you get it in the states?

---

### Post by Jannes. on 2011-06-12
Plz don't do that. 

It's a siemens santis wlan usb adapter about 6 years old or smth. When the first wireless systems came out here in belgium we bought it.

I'll buy myself an usb adapter :) My pc is already 6 years old...

---

### Post by Toz on 2011-06-12
What kind of security do you have on the router? WEP, WPA?

Also, what does:```
ifconfig
``` return?

---

### Post by Jannes. on 2011-06-13
WEP configuration. Because the adaptor doesn't support WPA2


```
jannes@jannes-DY137A-B14-a540-be:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:76:e1:38:d5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:96:8b:c1:fd  
          inet6 addr: fe80::290:96ff:fe8b:c1fd/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:8784 (8.7 KB)

jannes@jannes-DY137A-B14-a540-be:~$ 
```

---

### Post by josephmills on 2011-06-13
hardline reset the router (back to default ) anything? if not take down the security anything?try ```
sudo ifup wlan0 
``` could we also see a ```
sudo iwlist scan
``` thanks

---

### Post by Mistey82 on 2011-06-13
I have been working on this for a week trying to get examples from forums , I am very knew to linux and I need help to get my wireless working and me ethernet showing. My ethernet is working but not being list and my wireless is not working at all I listed all specs below someone please HELP 


mistey@mistey-laptop:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mistey@mistey-laptop:~$ sudo lsmod
[sudo] password for mistey: 
Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
vesafb                 13761  1 
binfmt_misc            17565  1 
joydev                 17606  0 
snd_hda_codec_conexant    57511  1 
snd_hda_intel          33211  4 
snd_hda_codec         103804  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72195  0 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2739144  51 
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
snd                    67382  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ndiswrapper           249811  0 
sp5100_tco             13744  0 
psmouse                73535  0 
i2c_piix4              13303  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
k10temp                13119  0 
sparse_keymap          13898  0 
serio_raw              13166  0 
shpchp                 37297  0 
video                  19438  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
firewire_ohci          40370  0 
sdhci_pci              13989  0 
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci                  27387  1 sdhci_pci
pata_atiixp            13165  0 
atl1c                  41171  0 
ahci                   25951  2 
libahci                26642  1 ahci
mistey@mistey-laptop:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: RTL8192E Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:1000(size=256) memory:c8000000-c8003fff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c0
       serial: 00:23:8b:fe:0a:35
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.29 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:f0300000-f033ffff ioport:b000(size=128)
mistey@mistey-laptop:~$

---

### Post by Jannes. on 2011-06-13
In my eyes it's not needed to reset my router or remove the security... 
The usb card can find networks in his area. 
Te ony problem is that It isnt able to connect to one of them.


```
jannes@jannes-DY137A-B14-a540-be:~$ sudo ifup wlan0
[sudo] password for jannes: 
Ignoring unknown interface wlan0=wlan0.
jannes@jannes-DY137A-B14-a540-be:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:00:C5:D0:42:01
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/100  Signal level=24/100  
                    Encryption key:on
                    ESSID:"Jan Van Lombergen"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b89e050d4
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 00114A616E2056616E204C6F6D62657267656E
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
          Cell 02 - Address: 90:84:0D:D7:8B:DB
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/100  Signal level=20/100  
                    Encryption key:on
                    ESSID:"Jan Van Lombergen"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000009a7d8fe4161
                    Extra: Last beacon: 764ms ago
                    IE: Unknown: 00114A616E2056616E204C6F6D62657267656E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1700039301710120000E90840DD78BDB0B90840DD78BDC64
                    IE: Unknown: DD070017F203020180

jannes@jannes-DY137A-B14-a540-be:~$ 

```

---

### Post by Toz on 2011-06-13
> 
```
Ignoring unknown interface wlan0=wlan0.
```

Please ensure that the file /etc/network/interfaces has the following lines:

```
auto wlan0
iface wlan0 inet dhcp

```

Please post back contents of /etc/network/interfaces

Then:```
sudo ifup wlan0
```

---

### Post by Jannes. on 2011-06-13
After the edit of the network interfaces...

```

jannes@jannes-DY137A-B14-a540-be:~$ sudo ifup wlan0
[sudo] password for jannes: 
jannes@jannes-DY137A-B14-a540-be:~$ sudo ifup wlan0

```

if i pressed enter then

```

jannes@jannes-DY137A-B14-a540-be:~$ sudo ifup wlan0
[sudo] password for jannes: 
jannes@jannes-DY137A-B14-a540-be:~$ sudo ifup wlan0
ifup: interface wlan0 already configured

```

The one i nee is the cell one in the post before. Jan Van Lombergen with WEP key :)

---

### Post by Toz on 2011-06-13
What does ```
ifconfig
``` say now?

And what is contents of **/etc/network/interfaces**

And result of: ```
lsmod
```

---

### Post by Jannes. on 2011-06-13
Ifconfig:

```
jannes@jannes-DY137A-B14-a540-be:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:76:e1:38:d5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1494 (1.4 KB)  TX bytes:1494 (1.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:90:96:8b:c1:fd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:90:96:8b:c1:fd  
          inet addr:169.254.12.83  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

jannes@jannes-DY137A-B14-a540-be:~$ 

```

the etc file

```
auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp
```

lsmod

```
jannes@jannes-DY137A-B14-a540-be:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
usb_storage            43946  1 
uas                    17676  0 
arc4                   12473  2 
vesafb                 13449  1 
parport_pc             32111  1 
ppdev                  12849  0 
snd_intel8x0           33213  2 
snd_usb_audio          91410  1 
snd_ac97_codec        105614  1 snd_intel8x0
nvidia               7098106  24 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  3 snd_intel8x0,snd_usb_audio,snd_ac97_codec
at76c50x_usb           39861  0 
snd_hwdep              13274  1 snd_usb_audio
snd_usbmidi_lib        24388  1 snd_usb_audio
snd_seq_midi           13132  0 
mac80211              257001  1 at76c50x_usb
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
binfmt_misc            13213  1 
snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_seq,snd_rawmidi
gspca_stv06xx          32353  0 
gspca_main             27894  1 gspca_stv06xx
cfg80211              156212  1 mac80211
snd                    55295  16 snd_intel8x0,snd_usb_audio,snd_ac97_codec,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
videodev               75143  1 gspca_main
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
lp                     13349  0 
shpchp                 32345  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
firewire_ohci          31504  0 
8139too                23208  0 
8139cp                 22497  0 
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
jannes@jannes-DY137A-B14-a540-be:~$ 

```

---

### Post by Toz on 2011-06-14
Lets take a step back and try something a little different. 

1. Comment out the two lines you added in /etc/network/interfaces so that the file looks like this:```
auto lo
iface lo inet loopback
#auto wlan0
#iface wlan0 inet dhcp
```

2. Reboot

3. When you log back in, try creating (or deleting and recreating) your wireless connection using Network Manager (the applet on the panel), and see if you connect. Let me know if it works.

4. If it doesn't work, then post back one more time:```
ifconfig
lsmod
``` and we will try a different method to load the module.

---

### Post by Jannes. on 2011-06-14
Ok i # the two lines.

I can see connections again. Trying to connect takes minutes and minutes. it keeps connecting and connecting. Problem not solved yet...

What i found by userpreferences and there the advanced preferences was my userrights. There was a point: account is allowed to make wireless conection not marked. I marked it. But again no solution.

IFCONFIG

```

jannes@jannes-DY137A-B14-a540-be:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:76:e1:38:d5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:96:8b:c1:fd  
          inet6 addr: fe80::290:96ff:fe8b:c1fd/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:9516 (9.5 KB)



```

LSMOD

```

jannes@jannes-DY137A-B14-a540-be:~$ lsmod
Module                  Size  Used by
vesafb                 13449  1 
parport_pc             32111  1 
ppdev                  12849  0 
arc4                   12473  2 
nvidia               7098106  24 
snd_intel8x0           33213  2 
at76c50x_usb           39861  0 
snd_usb_audio          91410  1 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_hwdep              13274  1 snd_usb_audio
snd_usbmidi_lib        24388  1 snd_usb_audio
mac80211              257001  1 at76c50x_usb
snd_pcm                80244  3 snd_intel8x0,snd_ac97_codec,snd_usb_audio
binfmt_misc            13213  1 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_seq,snd_rawmidi
cfg80211              156212  1 mac80211
gspca_stv06xx          32353  0 
gspca_main             27894  1 gspca_stv06xx
snd                    55295  16 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_hwdep,snd_usbmidi_lib,snd_pcm,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
videodev               75143  1 gspca_main
soundcore              12600  1 snd
shpchp                 32345  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
8139too                23208  0 
firewire_ohci          31504  0 
8139cp                 22497  0 
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
jannes@jannes-DY137A-B14-a540-be:~$ 

```

---

### Post by Toz on 2011-06-14
Okay. Next steps.

1. Lets unload the current atmel driver:
```
sudo modprobe -r at76c50x_usb
```

2. Lets load the one that was being asked for at the beginning using the included utility from the atmel-firmware package:
```
/sbin/atmel_fwl wlan0 /lib/firmware/atmel_at76c503-rfmd.bin
```

3. Try to connect now.

4. Post back:```
dmesg | grep at76
lsmod
iwconfig
ifconfig
```

---

### Post by Jannes. on 2011-06-14
The first step is impossible. It freezes and blocks my pc...

I'm not able to do the second step: Cant find it or bash error or cant access file ???

Its useless to post the other steps if these 2 aren't done yet i think.

---

### Post by Toz on 2011-06-14
Okay. Lets try it like this then.

1. Blacklist at76c50x_usb again.

2. Reboot

3. Sorry - wrong path. Try running it like this:
```
/usr/sbin/atmel_fwl wlan0 /lib/firmware/atmel_at76c503-rfmd.bin
```

4. Try to connect now.

5. Post back:
```
dmesg | grep at76
lsmod
iwconfig
ifconfig
```

---

### Post by Jannes. on 2011-06-14
Ok fine, i did it all, this was the post i was preparring for you:

I made a little bend to fix that the atc76c50x_usb won't be loaded. I have blacklisted him again.

Then i tried to load point 2 again, but again nothing as result.

So i had to search for the atmel_fwl...
with ```
sudo find / -iname "*atmel_f*"

```

I found:
```
/usr/share/man/man8/atmel_fwl.8.gz
/usr/sbin/atmel_fwl

```

Then i tried to use those directories like you did at point 2. 
But i got an error:
```
jannes@jannes-DY137A-B14-a540-be:~$ sudo /usr/sbin/atmel_fwl wlan0 /lib/firmware/atmel_at76c503-rfmd.bin
wlan0 is not an Atmel interface at /usr/sbin/atmel_fwl line 35.
jannes@jannes-DY137A-B14-a540-be:~$ 
```

I hope we are doing better right now.

---

### Post by Toz on 2011-06-14
Does wlan0 exist prior to running the atmel_fwl command?```
ifconfig
```Maybe you could try: ```
sudo /usr/sbin/atmel_fwl eth1 /lib/firmware/atmel_at76c503-rfmd.bin
```
If **eth1** works, then try setting up a connection using eth1 interface.

---

### Post by Burnout on 2011-06-18
Hi Toz,

When he doesn't blacklist the driver, there is a wlan0 interface. But when the original driver is blacklisted, the system hasn't got a wlan0 interface. Is there a solution for?

Regards,
Burn

---

### Post by Toz on 2011-06-18
It looks like the current driver isn't working, so by blacklisting it, we prevent it from getting loaded (and creating the wlan0 interface). According to the firmware documentation, there is a manual way to load the driver (see post #43). I wanted to try that to see if it works, loads a specific driver from the firmware package, and creates an eth1 interface.

I'm waiting to see if the manual method works.

---

### Post by Jannes. on 2011-06-19
IFCONFIG&#8232;```
jannes@jannes-DY137A-B14-a540-be:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:76:e1:38:d5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

jannes@jannes-DY137A-B14-a540-be:~$ 

```

CODE

```
jannes@jannes-DY137A-B14-a540-be:~$ sudo /usr/sbin/atmel_fwl eth1 /lib/firmware/atmel_at76c503-rfmd.bin
eth1 is not an Atmel interface at /usr/sbin/atmel_fwl line 35.
jannes@jannes-DY137A-B14-a540-be:~$ 

```

---

### Post by Toz on 2011-06-19
I am sorry but I am at a loss. According to what I've read, these things should work. One last attempt:

```
sudo modprobe at76c50x-usb
```
```
iwconfig
``` does wlan0 exist?
```
ifconfig wlan0 up
```and then check your configuration settings with Network Manager

Post back: ```
dmesg | grep at76
```

---

### Post by chili555 on 2011-06-20
Do you mind if I jump in a bit? I'd like to know everything there is to know about the Atmel. Is it a PCMCIA card?```
sudo lspcmcia ident -vv
dmesg | grep -i atmel
```Please tell me all the markings on it; make, model, version, etc. Thanks.

---

### Post by Jannes. on 2011-06-28
sudo modprobe at76c50x-usb
```
sudo modprobe at76c50x-usb
```

iwconfig (does wlan0 exist?)
```
jannes@jannes-DY137A-B14-a540-be:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
jannes@jannes-DY137A-B14-a540-be:~$ 

``` 

ifconfig wlan0 up
```
jannes@jannes-DY137A-B14-a540-be:~$ ifconfig wlan0 up
SIOCSIFFLAGS: Toegang geweigerd
jannes@jannes-DY137A-B14-a540-be:~$ sudo ifconfig wlan0 up
jannes@jannes-DY137A-B14-a540-be:~$ 

```

Post back: dmesg | grep at76
```
jannes@jannes-DY137A-B14-a540-be:~$ dmesg | grep at76
[  213.831327] Atmel at76x USB Wireless LAN Driver 0.17 loading
[  213.915987] usb 2-2: using firmware atmel_at76c503-rfmd.bin (version 1.101.0-84)
[  213.917784] at76c50x-usb 2-2:1.0: downloading internal firmware
[  216.342105] usbcore: registered new interface driver at76c50x-usb
[  216.607858] at76c50x-usb 2-2:1.0: downloading external firmware
[  245.632618] ieee80211 phy0: at76_wait_completion failed: 7
[  247.736024] ieee80211 phy0: at76_wait_completion failed: 7
[  249.841454] ieee80211 phy0: at76_wait_completion failed: 7
jannes@jannes-DY137A-B14-a540-be:~$ 

```

---

### Post by Jannes. on 2011-06-28
> **chili555 said:**
> Do you mind if I jump in a bit? I'd like to know everything there is to know about the Atmel. Is it a PCMCIA card?```
sudo lspcmcia ident -vv
dmesg | grep -i atmel
```Please tell me all the markings on it; make, model, version, etc. Thanks.

It is a santis wlan usb adapter S1621-Z51-A R32AR101
article no: 90028365

MAC: 009096-8BC1FD
SN: S1621-Z51-A230401669

```
jannes@jannes-DY137A-B14-a540-be:~$ sudo lspcmcia ident -vv
jannes@jannes-DY137A-B14-a540-be:~$ dmesg | grep -i atmel
[  213.831327] Atmel at76x USB Wireless LAN Driver 0.17 loading
[  213.915987] usb 2-2: using firmware atmel_at76c503-rfmd.bin (version 1.101.0-84)
jannes@jannes-DY137A-B14-a540-be:~$ 

```

---

### Post by chili555 on 2011-06-28
I have researched this driver and firmware quite a bit today. It appears that the proper driver module at76c50x-usb is loaded, firmware is loaded and a wireless interface is created. So far, so good.> wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:offrfkill indicates there is no wireless switch combination that prevents operation of the wireless radio. Does it scan?```
sudo iwconfig wlan0 scan
```Do you see networks when you click the Network Manager icon? With any ethernet cable detached, what does syslog report is going on?```
sudo modprobe at76c50x-usb
sudo cat /var/log/syslog | grep -e etwork -e wlan | tail -n25
```You might also try a static IP address. Edit connections in Network Manager and fill in an IP address that's well away from the range given out by the DHCP server in the router, netmask, gateway, ESSID and WEP key. Save and see if the little notification balloon reports that you are connected or disconnected.

---

### Post by Jannes. on 2011-07-11
```
jannes@jannes-DY137A-B14-a540-be:~$ sudo iwconfig wlan0 scan
iwconfig: unknown command "scan"
```


And the other codes say smth that 'grap' isnt installed yet...


It scans, but its not possible to connect...
Can see all the wireless connections in the neighbourhood

Damn sh*t stuff :(

---

### Post by chili555 on 2011-07-11
> $ sudo iwconfig wlan0 scanI'm sorry about that, I made a mistake.```
sudo iwlist wlan0 scan
```> And the other codes say smth that 'grap' isnt installed yet...How about gr[COLOR="Red"]e[/COLOR]p?> sudo cat /var/log/syslog | grep -e etwork -e wlan | tail -n25Does it try to connect and fail or what?

---

### Post by Jannes. on 2011-07-12
```
jannes@jannes-DY137A-B14-a540-be:~$ sudo iwlist wlan0 scan
[sudo] password for jannes: 
wlan0     Scan completed :
          Cell 01 - Address: 00:24:01:46:3D:D0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0  Signal level:0  Noise level:0
                    Encryption key:on
                    ESSID:"WIFI   20  A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000009d799da519b
                    Extra: Last beacon: 636ms ago
                    IE: Unknown: 000C574946492020203230202041
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0700E04C01020300
          Cell 02 - Address: 90:84:0D:D7:8B:DB
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=13/100  Signal level=13/100  
                    Encryption key:on
                    ESSID:"Jan Van Lombergen"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000bf059465160
                    Extra: Last beacon: 176ms ago
                    IE: Unknown: 00114A616E2056616E204C6F6D62657267656E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1700039301710120000E90840DD78BDB0B90840DD78BDC6C
                    IE: Unknown: DD070017F203020180
          [B]Cell 03 - Address: 00:00:C5:D0:42:01
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/100  Signal level=24/100  
                    Encryption key:on
                    ESSID:"Jan Van Lombergen"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000003ab0ca4f9d
                    Extra: Last beacon: 676ms ago
                    IE: Unknown: 00114A616E2056616E204C6F6D62657267656E
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106[/B]
          Cell 04 - Address: 00:1D:6A:9A:6B:1D
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0  Signal level:0  Noise level:0
                    Encryption key:on
                    ESSID:"Sakkes bbox2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013c3137181
                    Extra: Last beacon: 756ms ago
                    IE: Unknown: 000C53616B6B65732062626F7832
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706424520010D14
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000

jannes@jannes-DY137A-B14-a540-be:~$ 

```


The one at CELL03 is the one i need.



```
jannes@jannes-DY137A-B14-a540-be:~$ sudo cat /var/log/syslog | grep -e etwork -e wlan | tail -n25
Jul 12 18:39:45 jannes-DY137A-B14-a540-be NetworkManager[386]: <info> (eth0): preparing device.
Jul 12 18:39:45 jannes-DY137A-B14-a540-be NetworkManager[386]: <info> (eth0): deactivating device (reason: 2).
Jul 12 18:39:45 jannes-DY137A-B14-a540-be NetworkManager[386]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1e.0/0000:02:0c.0/net/eth0
Jul 12 18:39:45 jannes-DY137A-B14-a540-be NetworkManager[386]: <info> modem-manager is now available
Jul 12 18:39:45 jannes-DY137A-B14-a540-be NetworkManager[386]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jul 12 18:39:45 jannes-DY137A-B14-a540-be NetworkManager[386]: <info> Trying to start the supplicant...
Jul 12 18:39:45 jannes-DY137A-B14-a540-be NetworkManager[386]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:0c.0/net/eth0, iface: eth0)
Jul 12 18:39:45 jannes-DY137A-B14-a540-be NetworkManager[386]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:0c.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 12 18:39:46 jannes-DY137A-B14-a540-be NetworkManager[386]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jul 12 18:39:46 jannes-DY137A-B14-a540-be NetworkManager[386]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jul 12 18:39:46 jannes-DY137A-B14-a540-be kernel: [   15.395501] type=1400 audit(1310488786.505:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=584 comm="apparmor_parser"
Jul 12 18:39:51 jannes-DY137A-B14-a540-be NetworkManager[386]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/ieee80211/phy0/rfkill0) (driver <unknown>)
Jul 12 18:39:51 jannes-DY137A-B14-a540-be NetworkManager[386]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jul 12 18:39:51 jannes-DY137A-B14-a540-be NetworkManager[386]: <info> (wlan0): new 802.11 WiFi device (driver: 'at76c50x-usb' ifindex: 3)
Jul 12 18:39:51 jannes-DY137A-B14-a540-be NetworkManager[386]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jul 12 18:39:51 jannes-DY137A-B14-a540-be NetworkManager[386]: <info> (wlan0): now managed
Jul 12 18:39:51 jannes-DY137A-B14-a540-be NetworkManager[386]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Jul 12 18:39:51 jannes-DY137A-B14-a540-be NetworkManager[386]: <info> (wlan0): bringing up device.
Jul 12 18:39:53 jannes-DY137A-B14-a540-be NetworkManager[386]: <info> (wlan0): preparing device.
Jul 12 18:39:53 jannes-DY137A-B14-a540-be NetworkManager[386]: <info> (wlan0): deactivating device (reason: 2).
Jul 12 18:39:53 jannes-DY137A-B14-a540-be kernel: [   21.917411] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 12 18:39:53 jannes-DY137A-B14-a540-be NetworkManager[386]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/net/wlan0, iface: wlan0)
Jul 12 18:39:53 jannes-DY137A-B14-a540-be NetworkManager[386]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jul 12 18:39:53 jannes-DY137A-B14-a540-be NetworkManager[386]: <info> (wlan0): supplicant interface state:  starting -> ready
Jul 12 18:39:53 jannes-DY137A-B14-a540-be NetworkManager[386]: <info> (wlan0): device state change: 2 -> 3 (reason 42)
jannes@jannes-DY137A-B14-a540-be:~$ 

```

---

### Post by chili555 on 2011-07-13
Jannes, I have Googled this extensively. I have looked at many threads on many forums both Ubuntu and otherwise. I have found lengthy discussions of the native driver and ndiswrapper. I have found discussions from one and two years ago involving me and others involving you! What I have *_never_* found are those two magic words, "It works."

I am sorry; I have no further suggestions.

---

### Post by Jannes. on 2011-07-14
No Problem

Is there any way i can contact Ubuntu developers or smth?

---

### Post by chili555 on 2011-07-14
I hope this will be helpful: [http://wireless.kernel.org/en/users/Drivers/at76c50x-usb](http://wireless.kernel.org/en/users/Drivers/at76c50x-usb)> The maintainer of the driver is Kalle Valo <kalle.valo@iki.fi>. Send all patches to Kalle and CC linux-wireless mailing list. 

---

