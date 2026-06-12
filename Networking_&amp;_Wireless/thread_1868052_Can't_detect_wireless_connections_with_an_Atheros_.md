---
title: "Can't detect wireless connections with an Atheros AR2413 on an Acer Aspire 3630"
date: 2011-10-23
forum: Networking &amp; Wireless
---

### Post by TiRSO! on 2011-10-23
This is a new installation of Ubuntu 11.10 on an acer aspire 3630. The cd drive is broken so I had to install Ubuntu over network (and I suspect it did not install all the packages in the normal installation).

The problem is that ubuntu does not list the available wireless connections and I can't manually connect to my home wifi. I have tried a lot of things and this is all the info I have:

The wireless card is an AR2413.

The physical button to switch on/off the wireless does not work.

I am using the ath5k driver.

**iwconfig:**

```
    lo        no wireless extensions.

    eth0      no wireless extensions.
    
    wlan0     IEEE 802.11bg  ESSID:off/any  
              Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
              Retry  long limit:7   RTS thr:off   Fragment thr:off
              Power Management:off

```

**lshw**

```
    *-network:1
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:17:eb:4c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.0.0-12-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:e2010000-e201ffff

```
**rfkill list all:**

```
    rfkill list all
    0: phy0: Wireless LAN
    	Soft blocked: no
    	Hard blocked: no

```

**dmesg | grep ath:**

```
nadia@ubuntu-nadia:~$ dmesg | grep ath
[   25.196070] ath5k 0000:00:0b.0: enabling device (0010 -> 0012)
[   25.196101] ath5k 0000:00:0b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   25.196179] ath5k 0000:00:0b.0: registered as 'phy0'
[   26.051891] ath: EEPROM regdomain: 0x63
[   26.051897] ath: EEPROM indicates we should expect a direct regpair map
[   26.051904] ath: Country alpha2 being used: 00
[   26.051906] ath: Regpair used: 0x63
[   26.441036] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[  146.665904] type=1400 audit(1319970160.631:26): apparmor="STATUS" operation="profile_replace" name="/usr/lib/telepathy/mission-control-5" pid=1646 comm="apparmor_parser"
[  146.666641] type=1400 audit(1319970160.631:27): apparmor="STATUS" operation="profile_replace" name="/usr/lib/telepathy/telepathy-*" pid=1646 comm="apparmor_parser"
[  200.553074] ath5k 0000:00:0b.0: PCI INT A disabled
[  200.634672] ath5k 0000:00:0b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  200.634758] ath5k 0000:00:0b.0: registered as 'phy1'
[  201.339944] ath: EEPROM regdomain: 0x63
[  201.339949] ath: EEPROM indicates we should expect a direct regpair map
[  201.339956] ath: Country alpha2 being used: 00
[  201.339958] ath: Regpair used: 0x63
[  201.353438] ath5k phy1: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[  295.671244] ath5k 0000:00:0b.0: PCI INT A disabled
[  308.485331] ath5k 0000:00:0b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  308.485414] ath5k 0000:00:0b.0: registered as 'phy2'
[  309.194674] ath: EEPROM regdomain: 0x63
[  309.194680] ath: EEPROM indicates we should expect a direct regpair map
[  309.194687] ath: Country alpha2 being used: 00
[  309.194689] ath: Regpair used: 0x63
[  309.209717] ath5k phy2: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[  349.511747] ath5k 0000:00:0b.0: PCI INT A disabled
[  368.990267] ath5k 0000:00:0b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  368.990357] ath5k 0000:00:0b.0: registered as 'phy3'
[  369.694041] ath: EEPROM regdomain: 0x63
[  369.694045] ath: EEPROM indicates we should expect a direct regpair map
[  369.694052] ath: Country alpha2 being used: 00
[  369.694054] ath: Regpair used: 0x63
[  369.709691] ath5k phy3: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
```

**lsmod:**

```
nadia@ubuntu-nadia:~$ lsmod
Module                  Size  Used by
wmi                    18744  0 
sparse_keymap          13658  0 
ath5k                 145100  0 
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
bnep                   17923  2 
joydev                 17393  0 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_intel8x0           33318  3 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
arc4                   12473  2 
snd_pcm                80468  3 snd_intel8x0,snd_ac97_codec
pcmcia                 39822  0 
snd_seq_midi           13132  0 
ath                    19387  1 ath5k
mac80211              272785  1 ath5k
snd_rawmidi            25241  1 snd_seq_midi
psmouse                73673  0 
cfg80211              172392  3 ath5k,ath,mac80211
serio_raw              12990  0 
yenta_socket           27428  0 
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
binfmt_misc            17292  1 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  12 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
sis_agp                13165  1 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
i2c_sis96x             12743  0 
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sis900                 22729  0 
```

**sudo iwlist scan:**

```
nadia@ubuntu-nadia:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

---

### Post by praseodym on 2011-10-23
Hi,

please show:

```
dmesg | grep ath
lsmod
sudo iwlist scan
```

---

### Post by TiRSO! on 2011-10-30
> **praseodym said:**
> Hi,

please show:

```
dmesg | grep ath
lsmod
sudo iwlist scan
```

I edited my previous post to add the info you requested.


Also, I found a way to fix the problem temporarily. The shell script below fixes the problem, but I have to run it almost every time I turn my laptop on:


```
#!/bin/sh

hardBlocked="xxx"

while [ -n "$hardBlocked" ]
do
	sudo modprobe -r -f ath5k
	sudo sleep 2s
	sudo modprobe ath5k
	sudo rfkill unblock all
	hardBlocked=$(sudo rfkill list all | grep 'Hard blocked: yes')
	sudo stop network-manager
	sudo start network-manager

	if [ -n "$hardBlocked" ]; then
		echo "Press the WiFi physical switch once and press ENTER"
		read line
	fi
done
```

---

### Post by praseodym on 2011-10-30
Or try this:

[http://ubuntuforums.org/showpost.php?p=10937754&postcount=12](http://ubuntuforums.org/showpost.php?p=10937754&postcount=12)

---

### Post by aleoo on 2011-10-31
> **praseodym said:**
> Or try this:

[http://ubuntuforums.org/showpost.php?p=10937754&postcount=12](http://ubuntuforums.org/showpost.php?p=10937754&postcount=12)

I have a similar problem described on this thread : [http://ubuntuforums.org/showthread.php?t=1826980&highlight=AR2413](http://ubuntuforums.org/showthread.php?t=1826980&highlight=AR2413)

Shall I try the link you provide?
I hope someone will reply to me, because I've been experiencing this issue for months, and I still haven't found the solution

---

### Post by praseodym on 2011-10-31
Hi aleoo,

yes, you can try it. Did you uninstall the madwifi driver (or blacklist it)?

---

### Post by aleoo on 2011-11-01
> **praseodym said:**
> Hi aleoo,

yes, you can try it. Did you uninstall the madwifi driver (or blacklist it)?

Hi!
First of all, thanks for your reply.
A couple of days ago I upgraded ubuntu to the 11.10 version.
Today I was trying to find madwifi with ubuntu software center, but I couldn't, so I just deleted the folders of madwifi (I don't know if it's now uninstalled, I'm really ignorant..even if I thought that it had been removed during the process of upgrading).
I followed the instructions on the link: nothing changed. My laptop is an Acer Aspire 3680.
Please, tell me what you need to know, so that I post the outputs from the terminal.

---

### Post by aleoo on 2011-11-02
Can anybody help me?

---

### Post by praseodym on 2011-11-02
Change to that folder and uninstall it via:

```
make clean
make
sudo make uninstall
sudo depmod -a
sudo update-initramfs -u
```
Reboot and check:

```
iwconfig
lsmod
grep ath /etc/modprobe.d/*
sudo iwlist scan
dmesg | grep ath
```

---

### Post by aleoo on 2011-11-02
> **praseodym said:**
> Change to that folder and uninstall it via:

```
make clean
make
sudo make uninstall
sudo depmod -a
sudo update-initramfs -u
```Reboot and check:

```
iwconfig
lsmod
grep ath /etc/modprobe.d/*
sudo iwlist scan
dmesg | grep ath
```

What do you mean with "Change to that folder"?
In the meanwhile I'm following your instructions: I'll get back to you in few minutes.
Thank you

---

### Post by aleoo on 2011-11-02
~$ make clean
make: *** No rule to make target `clean'.  Stop.
~$ make clean madwifi
make: *** No rule to make target `clean'.  Stop.

Sorry, I didn't understand whay you wrote, could you explain what do I need to do?

~$** iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

~$ **lsmod**
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   254125  1 
bnep                   17923  2 
rfcomm                 38408  0 
joydev                 17393  0 
bluetooth             148839  10 bnep,rfcomm
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
pcmcia                 39822  0 
gspca_m5602            51493  0 
gspca_main             27610  1 gspca_m5602
snd_rawmidi            25241  1 snd_seq_midi
videodev               85626  1 gspca_main
i915                  505108  3 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tifm_7xx1              12937  0 
psmouse                73673  0 
snd_timer              28932  2 snd_pcm,snd_seq
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
tifm_core              15040  1 tifm_7xx1
serio_raw              12990  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         32889  1 i915
binfmt_misc            17292  1 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
drm                   192226  4 i915,drm_kms_helper
snd                    55902  14 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 i915
soundcore              12600  1 snd
wmi                    18744  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sky2                   49317  0 
ale@pc:~$ grep ath /etc/modprobe.d/*
/etc/modprobe.d/ath9k.conf:options ath9k nohwcrypt=1
/etc/modprobe.d/blacklist-ath_pci.conf:# which ath5k cannot recover. To prevent this condition, stop
/etc/modprobe.d/blacklist-ath_pci.conf:#blacklist ath_pci
/etc/modprobe.d/blacklist-ath_pci.conf:blacklist ath5k
/etc/modprobe.d/blacklist.conf:blacklist ath5k
/etc/modprobe.d/blacklist.conf:blacklist ath5k
/etc/modprobe.d/blacklist.conf:blacklist ath5k

~$** sudo iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

~$ **dmesg | grep ath**

---

### Post by praseodym on 2011-11-02
The module isnt loaded:

Change via

```
gksu gedit /etc/modprobe.d/ath9k.conf
```
the entry "ath9k" with "ath5k", save, close, and:
```
sudo modprobe -v ath5k
```
You also need to change the three (!) entries in the file "blacklist.conf" and the one in the "blacklist-ath_pci.conf"

---

### Post by aleoo on 2011-11-02
> **praseodym said:**
> The module isnt loaded:

Change via

```
gksu gedit /etc/modprobe.d/ath9k.conf
```the entry "ath9k" with "ath5k", save, close, and:
```
sudo modprobe -v ath5k
```You also need to change the three (!) entries in the file "blacklist.conf" and the one in the "blacklist-ath_pci.conf"

Now I see the "Enable wireless" button, but it's grey..

~$ sudo modprobe -v ath5k
WARNING: All config files need .conf: /etc/modprobe.d/Untitled Document 1, it will be ignored in a future release.
insmod /lib/modules/3.0.0-12-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.0.0-12-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko nohwcrypt=1

To change those entries: do I need to type " gksu gedit /etc/modprobe.d/blacklist.conf "  and " gksu gedit /etc/modprobe.d/blacklist-ath_pci.conf " ?

Now in network manager appears : wireless is disabled by hardware switch

P.S.: first I changed from ath9k to ath5k; then, when I typed "  sudo modprobe -v ath5k " , soon after network manager began to look for wireless network, than sayed disconnected

---

### Post by praseodym on 2011-11-02
> To change those entries: do I need to type " gksu gedit /etc/modprobe.d/blacklist.conf " and " gksu gedit /etc/modprobe.d/blacklist-ath_pci.conf " ?
Yes. Please show the entries of the file **/etc/modprobe.d/Untitled Document 1**. Start the NM with

```
gksu nm-connection-editor
```
For the hardware switch try:

```
sudo rfkill unblock all
```
Check now:

```
lsmod
iwconfig
rfkill list
sudo iwlist scan
dmesg | grep ath
```

---

### Post by aleoo on 2011-11-02
> **praseodym said:**
> Yes. Please show the entries of the file **/etc/modprobe.d/Untitled Document 1**. Start the NM with

```
gksu nm-connection-editor
```For the hardware switch try:

```
sudo rfkill unblock all
```Check now:

```
lsmod
iwconfig
rfkill list
sudo iwlist scan
dmesg | grep ath
```

It seems that there's nothing in Untitled Document 1, I tried " sudo rfkill unblock all " but nothing happened..it gives me no output

```

~$ **lsmod**
Module                  Size  Used by
arc4                   12473  2 
ath5k                 145100  0 
ath                    19387  1 ath5k
mac80211              272785  1 ath5k
cfg80211              172392  3 ath5k,ath,mac80211
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   254125  1 
bnep                   17923  2 
rfcomm                 38408  0 
joydev                 17393  0 
bluetooth             148839  10 bnep,rfcomm
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
pcmcia                 39822  0 
gspca_m5602            51493  0 
gspca_main             27610  1 gspca_m5602
snd_rawmidi            25241  1 snd_seq_midi
videodev               85626  1 gspca_main
i915                  505108  3 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tifm_7xx1              12937  0 
psmouse                73673  0 
snd_timer              28932  2 snd_pcm,snd_seq
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
tifm_core              15040  1 tifm_7xx1
serio_raw              12990  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         32889  1 i915
binfmt_misc            17292  1 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
drm                   192226  4 i915,drm_kms_helper
snd                    55902  14  snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 i915
soundcore              12600  1 snd
wmi                    18744  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sky2                   49317  0 

~$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
~$ **rfkill list**
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

~$ **sudo iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

~$ **dmesg | grep ath**
[13022.650041] ath5k 0000:0a:03.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[13022.650116] ath5k 0000:0a:03.0: registered as 'phy0'
[13023.363897] ath: EEPROM regdomain: 0x63
[13023.363903] ath: EEPROM indicates we should expect a direct regpair map
[13023.363908] ath: Country alpha2 being used: 00
[13023.363911] ath: Regpair used: 0x63
[13023.655961] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)

```

---

### Post by praseodym on 2011-11-02
Remove that file via:

```
gksu gedit /etc/modprobe.d/
```

and reboot. Try to hold the button (if any) pressed during booting and/or press it repeatedly.

---

### Post by aleoo on 2011-11-03
> **praseodym said:**
> Remove that file via:

```
gksu gedit /etc/modprobe.d/
```and reboot. Try to hold the button (if any) pressed during booting and/or press it repeatedly.

Which file?
Today the "enable wireless" is not there

---

### Post by praseodym on 2011-11-03
Sorry, syntax error:

```
gksu nautilus /etc/modprobe.d/
```

remove the "Untitled Document 1" and reboot.
Check
```
lsmod
iwconfig
rfkill list
sudo iwlist scan
dmesg | grep ath
```again

---

### Post by aleoo on 2011-11-03
> **praseodym said:**
> Sorry, syntax error:

```
gksu nautilus /etc/modprobe.d/
```remove the "Untitled Document 1" and reboot.
Check
```
lsmod
iwconfig
rfkill list
sudo iwlist scan
dmesg | grep ath
```again

Done

```
:~$ lsmod
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   254125  1 
joydev                 17393  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
pcmcia                 39822  0 
snd_seq_midi_event     14475  1 snd_seq_midi
gspca_m5602            51493  0 
gspca_main             27610  1 gspca_m5602
i915                  505108  3 
videodev               85626  1 gspca_main
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tifm_7xx1              12937  0 
psmouse                73673  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
tifm_core              15040  1 tifm_7xx1
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
drm_kms_helper         32889  1 i915
serio_raw              12990  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
drm                   192226  4 i915,drm_kms_helper
snd                    55902  14 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
binfmt_misc            17292  1 
soundcore              12600  1 snd
i2c_algo_bit           13199  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
wmi                    18744  0 
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sky2                   49317  0 

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

:~$ rfkill list
ale@pc:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

:~$ dmesg | grep ath
```

---

### Post by praseodym on 2011-11-03
Now load the module again:

```
sudo modprobe -v ath5k
```

---

### Post by aleoo on 2011-11-03
> **praseodym said:**
> Now load the module again:

```
sudo modprobe -v ath5k
```

Done, now "enable wireless" button appears grey like yesterday

```
~$ lsmod
Module                  Size  Used by
arc4                   12473  2 
ath5k                 145100  0 
ath                    19387  1 ath5k
mac80211              272785  1 ath5k
cfg80211              172392  3 ath5k,ath,mac80211
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   254125  1 
joydev                 17393  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_hda_intel          24262  4 
snd_hda_codec          91754  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  4 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
pcmcia                 39822  0 
snd_seq_midi_event     14475  1 snd_seq_midi
gspca_m5602            51493  0 
gspca_main             27610  1 gspca_m5602
i915                  505108  3 
videodev               85626  1 gspca_main
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tifm_7xx1              12937  0 
psmouse                73673  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
tifm_core              15040  1 tifm_7xx1
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
drm_kms_helper         32889  1 i915
serio_raw              12990  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
drm                   192226  4 i915,drm_kms_helper
snd                    55902  17 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
binfmt_misc            17292  1 
soundcore              12600  1 snd
i2c_algo_bit           13199  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
wmi                    18744  0 
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sky2                   49317  0 

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

~$ sudo iwlist scan 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

~$ dmesg | grep ath
[ 2495.114432] ath5k 0000:0a:03.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 2495.114498] ath5k 0000:0a:03.0: registered as 'phy0'
[ 2495.840042] ath: EEPROM regdomain: 0x63
[ 2495.840048] ath: EEPROM indicates we should expect a direct regpair map
[ 2495.840053] ath: Country alpha2 being used: 00
[ 2495.840056] ath: Regpair used: 0x63
[ 2496.021029] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
```

---

### Post by praseodym on 2011-11-04
Ok:

```
sudo rmmod ath5k
sudo rfkill unblock all
sudo modprobe -v ath5k
```

---

### Post by aleoo on 2011-11-04
> **praseodym said:**
> Ok:

```
sudo rmmod ath5k
sudo rfkill unblock all
sudo modprobe -v ath5k
```

```
~$ sudo rmmod ath5k 
ERROR: Module ath5k does not exist in /proc/modules

~$ sudo rfkill unblock all

~$ sudo modprobe -v ath5k
insmod /lib/modules/3.0.0-12-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.0.0-12-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko nohwcrypt=1
```

Today the "enable wireless" button disappeared, like yesterday..then with "sudo modprobe -v ath5k" appear again

```
~$ lsmod
Module                  Size  Used by
arc4                   12473  0 
ath                    19387  0 
mac80211              272785  0 
cfg80211              172392  2 ath,mac80211
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   254125  1 
joydev                 17393  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  8 bnep,rfcomm
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
pcmcia                 39822  0 
gspca_m5602            51493  0 
gspca_main             27610  1 gspca_m5602
videodev               85626  1 gspca_main
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
i915                  505108  3 
tifm_7xx1              12937  0 
tifm_core              15040  1 tifm_7xx1
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
serio_raw              12990  0 
snd                    55902  14 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
binfmt_misc            17292  1 
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
wmi                    18744  0 
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sky2                   49317  0 

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

~$ rfkill list
~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

~$ dmesg | grep ath
[  339.801715] ath5k 0000:0a:03.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  339.801783] ath5k 0000:0a:03.0: registered as 'phy0'
[  340.515241] ath: EEPROM regdomain: 0x63
[  340.515246] ath: EEPROM indicates we should expect a direct regpair map
[  340.515252] ath: Country alpha2 being used: 00
[  340.515254] ath: Regpair used: 0x63
[  340.793891] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[  373.567249] ath5k 0000:0a:03.0: PCI INT A disabled
```

---

### Post by praseodym on 2011-11-04
The module is still blacklisted?

```
grep ath5k /etc/modprobe.d/*
```

---

### Post by aleoo on 2011-11-04
> **praseodym said:**
> The module is still blacklisted?

```
grep ath5k /etc/modprobe.d/*
```

```
~$ grep ath5k /etc/modprobe.d/*
/etc/modprobe.d/ath9k.conf:options ath5k nohwcrypt=1
/etc/modprobe.d/blacklist-ath_pci.conf:# which ath5k cannot recover. To prevent this condition, stop
/etc/modprobe.d/blacklist-ath_pci.conf:blacklist ath5k
/etc/modprobe.d/blacklist.conf:blacklist ath5k
/etc/modprobe.d/blacklist.conf:blacklist ath5k
/etc/modprobe.d/blacklist.conf:blacklist ath5k
```

---

### Post by praseodym on 2011-11-04
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
Remove those three lines. Same with "blacklist-ath_pci.conf". Be sure, that "ath_pci" is blacklisted there (if still installed). After that:

```
gksu gedit /etc/rc.local
```

add these new lines _before_ "exit 0":

```
rmmod ath5k
rfkill unblock all
modprobe ath5k
```
Reboot and check:

```
iwconfig
rfkill list
sudo iwlist scan
lsmod
dmesg | grep ath
```

---

### Post by aleoo on 2011-11-04
> **praseodym said:**
> ```
gksu gedit /etc/modprobe.d/blacklist.conf
```Remove those three lines. Same with "blacklist-ath_pci.conf". Be sure, that "ath_pci" is blacklisted there (if still installed). After that:

```
gksu gedit /etc/rc.local
```add these new lines _before_ "exit 0":

```
rmmod ath5k
rfkill unblock all
modprobe ath5k
```Reboot and check:

```
iwconfig
rfkill list
sudo iwlist scan
lsmod
dmesg | grep ath
```

Done

```
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
~$ rfkill list
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

ale@pc:~$ lsmod
Module                  Size  Used by
ath5k                 145100  0 
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   254125  1 
bnep                   17923  2 
bluetooth             148839  7 bnep
joydev                 17393  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
arc4                   12473  2 
snd_rawmidi            25241  1 snd_seq_midi
pcmcia                 39822  0 
i915                  505108  3 
gspca_m5602            51493  0 
gspca_main             27610  1 gspca_m5602
ath                    19387  1 ath5k
videodev               85626  1 gspca_main
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              272785  1 ath5k
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tifm_7xx1              12937  0 
cfg80211              172392  3 ath5k,ath,mac80211
snd_timer              28932  2 snd_pcm,snd_seq
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
tifm_core              15040  1 tifm_7xx1
psmouse                73673  0 
drm_kms_helper         32889  1 i915
serio_raw              12990  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
drm                   192226  4 i915,drm_kms_helper
snd                    55902  14 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
binfmt_misc            17292  1 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
wmi                    18744  0 
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sky2                   49317  0 

ale@pc:~$ dmesg | grep ath
[   25.837560] ath5k 0000:0a:03.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   25.837627] ath5k 0000:0a:03.0: registered as 'phy0'
[   26.586817] ath: EEPROM regdomain: 0x63
[   26.586821] ath: EEPROM indicates we should expect a direct regpair map
[   26.586826] ath: Country alpha2 being used: 00
[   26.586829] ath: Regpair used: 0x63
[   26.727928] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   29.835247] ath5k 0000:0a:03.0: PCI INT A disabled
[   29.899232] ath5k 0000:0a:03.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   29.899301] ath5k 0000:0a:03.0: registered as 'phy1'
[   30.630258] ath: EEPROM regdomain: 0x63
[   30.630262] ath: EEPROM indicates we should expect a direct regpair map
[   30.630267] ath: Country alpha2 being used: 00
[   30.630270] ath: Regpair used: 0x63
[   30.641149] ath5k phy1: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
```

---

### Post by praseodym on 2011-11-04
Well,

try Acer-Hotkeys:

```
sudo apt-get install build-essential module-assistant debhelper linux-headers-generic
wget https://launchpad.net/~cogito-16/+archive/ppa/+files/acerhk-source_0.5.35-13a_all.deb
sudo dpkg -i acer*.deb
cd /usr/src
sudo tar -xjf acerhk.tar.bz2 
sudo mv modules acerhk-0.5.35 
gksudo gedit /usr/src/acerhk-0.5.35/dkms.conf
```
Insert:
```
PACKAGE_NAME=acerhk
PACKAGE_VERSION=0.5.35

DEST_MODULE_LOCATION=/extra
BUILT_MODULE_NAME=acerhk
BUILT_MODULE_LOCATION=acerhk/

MAKE="'make' -C acerhk/ all"
CLEAN="'make' -C acerhk/ clean"
AUTOINSTALL="yes"
```
save, close, and check::
```
sudo dkms add -m acerhk -v 0.5.35 
```
If no errors occur, install via:
```
sudo dkms build -m acerhk -v 0.5.35 
sudo dkms install -m acerhk -v 0.5.35 
sudo depmod -a
sudo modprobe -v acerhk
```
Try the button (if any). If there is no button, try:
```
echo 1 | sudo tee /proc/driver/acerhk/wirelessled 
```
and check:

```
iwconfig
rfkill list
sudo iwlist scan
dmesg | egrep 'radio|switch|kill|acer|wmi'
```

---

### Post by aleoo on 2011-11-04
> **praseodym said:**
> Well,

try Acer-Hotkeys:

```
sudo apt-get install build-essential module-assistant debhelper linux-headers-generic
wget https://launchpad.net/~cogito-16/+archive/ppa/+files/acerhk-source_0.5.35-13a_all.deb
sudo dpkg -i acer*.deb
cd /usr/src
sudo tar -xjf acerhk.tar.bz2 
sudo mv modules acerhk-0.5.35 
gksudo gedit /usr/src/acerhk-0.5.35/dkms.conf
```Insert:
```
PACKAGE_NAME=acerhk
PACKAGE_VERSION=0.5.35

DEST_MODULE_LOCATION=/extra
BUILT_MODULE_NAME=acerhk
BUILT_MODULE_LOCATION=acerhk/

MAKE="'make' -C acerhk/ all"
CLEAN="'make' -C acerhk/ clean"
AUTOINSTALL="yes"
```save, close, and check::
```
sudo dkms add -m acerhk -v 0.5.35 
```If no errors occur, install via:
```
sudo dkms build -m acerhk -v 0.5.35 
sudo dkms install -m acerhk -v 0.5.35 
sudo depmod -a
sudo modprobe -v acerhk
```Try the button (if any). If there is no button, try:
```
echo 1 | sudo tee /proc/driver/acerhk/wirelessled 
```and check:

```
iwconfig
rfkill list
sudo iwlist scan
dmesg | egrep 'radio|switch|kill|acer|wmi'
```

Installed Acer-Hotkeys, but then 
```
~$ sudo dpkg -i acer*.deb
dpkg: error processing acer*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 acer*.deb

~$ sudo dpkg -i acer* .deb
dpkg: error processing acer* (--install):
 cannot access archive: No such file or directory
dpkg: error processing .deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 acer*
 .deb

~$ cd /usr/src

:/usr/src$ sudo tar -xjf acerhk.tar.bz2
tar (child): acerhk.tar.bz2: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now

:/usr/src$ sudo mv modules acerhk-0.5.35
mv: cannot stat `modules': No such file or directory
```

so I stopped

---

### Post by praseodym on 2011-11-04
Install the .deb-Package by double-clicking

---

### Post by aleoo on 2011-11-05
> **praseodym said:**
> Install the .deb-Package by double-clicking

I'm sorry for my ignorance, but I don't know where to look for this package to double-click

---

### Post by praseodym on 2011-11-05
It should be in your /home directory.

---

### Post by aleoo on 2011-11-05
> **praseodym said:**
> It should be in your /home directory.

I've tried to search with "Dash home" and "Ubuntu software center", but I couldn't find it

---

### Post by praseodym on 2011-11-05
Try it with:

```
locate *.deb | grep home
```

---

### Post by aleoo on 2011-11-05
> **praseodym said:**
> Try it with:

```
locate *.deb | grep home
```

I found  ```
buc-0.5.2_bin_full.deb
``` is this the right file?

---

### Post by praseodym on 2011-11-05
Direct link:

[https://launchpad.net/~cogito-16/+archive/ppa/+files/acerhk-source_0.5.35-13a_all.deb](https://launchpad.net/~cogito-16/+archive/ppa/+files/acerhk-source_0.5.35-13a_all.deb)

save it in "Downloads" and install it via:

```
sudo dpkg -i ~/Downlaods/*.deb
```

---

### Post by aleoo on 2011-11-05
> **praseodym said:**
> Direct link:

[https://launchpad.net/~cogito-16/+archive/ppa/+files/acerhk-source_0.5.35-13a_all.deb]("https://launchpad.net/%7Ecogito-16/+archive/ppa/+files/acerhk-source_0.5.35-13a_all.deb")

save it in "Downloads" and install it via:

```
sudo dpkg -i ~/Downlaods/*.deb
```

Thanks, done. Now I need to follow your previous instructions of message #28 ?
sudo dpkg -i acer*.deb cd /usr/src sudo tar -xjf acerhk.tar.bz2  sudo mv modules acerhk-0.5.35  gksudo gedit /usr/src/acerhk-0.5.35/dkms.conf
then insert ...

---

### Post by praseodym on 2011-11-05
Continue with

cd /usr/src

---

### Post by aleoo on 2011-11-05
> **praseodym said:**
> Continue with

cd /usr/src

```
~$ cd /usr/src
:/usr/src$ sudo tar -xjf acerhk.tar.bz2
:/usr/src$ sudo mv modules acerhk-0.5.35
:/usr/src$ gksudo gedit /usr/src/acerhk-0.5.35/dkms.conf
:/usr/src$ sudo dkms add -m acerhk -v 0.5.35
sudo: dkms: command not found
:/usr/src$ sudo dkms build -m acerhk -v 0.5.35
sudo: dkms: command not found
:/usr/src$ sudo dkms install -m acerhk -v 0.5.35
sudo: dkms: command not found
```

then I stopped

---

### Post by praseodym on 2011-11-05
You need to install the package dkms and the tools to compile:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
```

---

### Post by aleoo on 2011-11-05
> **praseodym said:**
> You need to install the package dkms and the tools to compile:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
```

Done ```
DKMS: install Completed.
:/usr/src$ sudo depmod -a
:/usr/src$ sudo modprobe -v acerhk
insmod /lib/modules/3.0.0-12-generic/updates/dkms/acerhk.ko 
:/usr/src$ echo 1 | sudo tee /proc/driver/acerhk/wirelessled
1

:/usr/src$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
:/usr/src$ rfkill list
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

:/usr/src$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

ale@pc:/usr/src$ dmesg | egrep 'radio|switch|kill|acer|wmi
> dmesg | egrep 'radio|switch|kill|acer|wmi'
> 

```

---

### Post by praseodym on 2011-11-06
Check the buttons/switches, etc., and

sudo rfkill unblock all

---

### Post by aleoo on 2011-11-06
> **praseodym said:**
> Check the buttons/switches, etc., and

sudo rfkill unblock all

```
~$ sudo rfkill unblock all
:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
:~$ rfkill list
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down
```

I remember that someone told me to write something like "wlan 0 up" some months ago..but I doubt that it would work

---

### Post by praseodym on 2011-11-06
You mean:

sudo ifup wlan0

?

---

### Post by aleoo on 2011-11-06
> **praseodym said:**
> You mean:

sudo ifup wlan0

?

```
~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
```

I don't remember.
It's strange, before it was all ok..I really don't know why wireless doesn't work

---

### Post by praseodym on 2011-11-06
Try this module (I dont know if it works, but it will not harm):

```
sudo modprobe fsam7400 radio=1
sudo rfkill unblock all
```

---

### Post by aleoo on 2011-11-06
> **praseodym said:**
> Try this module (I dont know if it works, but it will not harm):

```
sudo modprobe fsam7400 radio=1
sudo rfkill unblock all
```

```
~$ sudo modprobe fsam7400 radio=1
FATAL: Module fsam7400 not found.
:~$ sudo rfkill unblock all
```

---

### Post by praseodym on 2011-11-06
```
sudo modprobe fsam74[COLOR="Red"]4[/COLOR]0 radio=1
sudo rfkill unblock all
```
This one? I am using Lucid, maybe they took both modules out in kernel 3?!

---

### Post by aleoo on 2011-11-06
> **praseodym said:**
> ```
sudo modprobe fsam74[COLOR=Red]4[/COLOR]0 radio=1
sudo rfkill unblock all
```This one? I am using Lucid, maybe they took both modules out in kernel 3?!

Not found

---

### Post by praseodym on 2011-11-06
Maybe I am getting lost in this thread: Did you reset the BIOS? Pressed the Button/switch/key/key combination repeatedly during boot-up?

---

### Post by aleoo on 2011-11-06
> **praseodym said:**
> Maybe I am getting lost in this thread: Did you reset the BIOS? Pressed the Button/switch/key/key combination repeatedly during boot-up?

Now I've sitched off my laptop keeping pressed the button, and swithed on always with the same button..is that correct?

---

