---
title: "rt3070 driver installation problems"
date: 2011-12-04
forum: Networking &amp; Wireless
---

### Post by sakalonys on 2011-12-04
hi therem, i have got two rt3070usb sticks from ralink 
output from lsusb :
Bus 002 Device 004: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
i used them them with k/ubuntu the last months with more or less trouble.
with a lil work i got everything working with it in the past, like monitoring, injection, wide area connections...no porblems.
but since i think two or three weeks nothing i did, helped me to get a connection, i tried two different sticks, on three workstations, with at least 10 different k/ubuntu live distributions, i tried several drivers like rt2800usb, rt3070sta, rt2x00 (which has amazing tx/rx results) & many"ways to solve the problem with this card"  but nothing works for me,i only see the ap's, but cant connect.with beini, i&#7743; able to crack keys, so the usb device is working.

i read that ubuntu 10.10 can hadle it out of the box, so i installed... but nothing. can anyone please help me... and say me how to do it right ?

i only want to connect to a wep ap, doesnt matter if i have to connect via nm or iwconfig,...

an easy way tutorial or smth like an out of the box version that really works
would be nice... 

i would be so nice if someone could help me !! please !!

---

### Post by praseodym on 2011-12-04
Hi,

which Ubuntu version did you try first? The module **rt2870sta** should work from ubuntu 10.04 and on, with the module **rt2800usb** blacklisted. From 11.10 the module **rt2800usb** is the only one part of the Linux kernel. Alternatively, try this driver with new firmware version (or the old driver with new firmware) for any Ubuntu version before 11.10:

```
echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf 
sudo apt-get install linux-headers-$(uname -r) build-essential
wget http://media.cdn.ubuntu-de.org/forum/attachments/2388926/2009_1110_RT3070_Linux_STA_v2.1.2.0_mod.tar.gz
wget http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.52_all.deb
sudo dpkg -i linux-*.deb
tar xvf 2009_1110_RT3070_Linux_STA_v2.1.2.0_mod.tar.gz
cd 2009_1110_RT3070_Linux_STA_v2.1.2.0_mod
make         [COLOR="Red"]## possible error "make: *** [LINUX] error 1" can be ignored[/COLOR]
sudo make install
cd
sudo modprobe -rfv rt2800usb
sudo modprobe -v rt3070sta
sudo depmod -a
sudo update-initramfs -u
modinfo rt3070sta | egrep 'versi|filen' 
```
Version v2.1.2.0 should be listed. Replug the stick and check the connection:
```
iwconfig
iwlist chan
sudo iwlist scan
lsmod
```

The driver needs to be compiled again after a kernel upgrade:
```
sudo apt-get install linux-headers-$(uname -r)
cd 2009_1110_RT3070_Linux_STA_v2.1.2.0_mod/
make clean
make
sudo make install
```

---

### Post by step21 on 2011-12-04
Hey, so I have a similar problem, I hope it is okay to reply to this thread as well.
I have a D-Link DWA-140 rev. B2 with a Ralink chip, lsusb output:
Bus 001 Device 006: ID 07d1:3c0a D-Link System DWA-140 RangeBooster N Adapter(rev.B2) [Ralink RT2870]
The particularly weird thing is that in principle it is recognized and works with the rt2800usb that is included with 11.10. However it only ever does so for a really short amount of time, 15 min max. After that it not only disconnects, but the whole device disappears from usb and even removing and reconnecting it won't bring it back (doesn't even show up in lsusb anymore)
When blacklisting rt2800 as described in some older guides, at least it does not disappear altogether, but of course it also does not work. (apparently starting with 11.10 (kernel 3.x) only rt2800 is available)
The next thing I would try is to compile one of the older drivers, like rt3070sta or rt5370sta, but maybe someone has a better idea?

---

### Post by praseodym on 2011-12-05
Hi step21,

see here:

[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/762987](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/762987)

Try the newest firmware

---

### Post by step21 on 2011-12-05
Actually I found this earlier, but I don't think it can help me. It can be that I missed something (I didn't look at all of the numerous comments because most seemed irrelevant) but it does not seem applicable. First off, I can actually connect, but only upon having just started the system. More importantly, as far as I can tell most people in this bug report are talking about older (and sometimes really old) ubuntu versions. In fact if you look at reply number 11 by a seemingly knowledgeable poster it states that precisely since merging drivers in kernel 3.x (which oneiric now uses) this specific bug should be fixed, which it  probably is, so this would be a new bug. That said, it might not even be a driver bug, but maybe a usb problem ... just not sure how to track it down, I did not find any relevant output in dmesg.

---

### Post by sakalonys on 2011-12-05
hi thank u very much for your fast answer... the first place where, it seems that i really get help from someone who knows what he&#347; talking about.

first 2 answer your questions :
right now i am using ubuntu 10.10, from livecd usb installation.
it would be nice,if i could use my updated kubuntu 11.10 on of my other hdd&#347; again. but i got so much partitions with installed and half died distributions,that "i wanna rescue or collect my data from them",which i all dont use,cause of this f*** damn driver problem.
but enough of this... i only wanna say, dont care which version i got for future, the only thing i really care is a working driver for this stick, which doesnt die every week, after installation.


like i said right now its 10.10 i think maverick.
tried your way slowly step by step...but i got problems again.

when i type make , i not only get the error1... also error2. and im not able to sudo make install.also tried sudo make, same problem...

what now to do ?

---

### Post by praseodym on 2011-12-05
Try it as "root":

```
sudo su
make
make install
exit
```

---

### Post by sakalonys on 2011-12-05
make[1]: *** [_module_/home/freak/2009_1110_RT3070_Linux_STA_v2.1.2.0_mod/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-31-generic'
make: *** [LINUX] Error 2
root@STATION:/home/freak/2009_1110_RT3070_Linux_STA_v2.1.2.0_mod#

---

### Post by praseodym on 2011-12-05
Ok, this doesnt work. In 10.10 the driver **rt2870sta** can be updated via:

```
sudo apt-get install linux-backports-modules-wireless-maverick-generic linux-firmware
```
Reboot. Check:

```
lsmod
iwconfig
sudo iwlist scan
dmesg | grep rt2
rfkill list
```

---

### Post by sakalonys on 2011-12-05
ok , next try... ty...
will report in a few minutes...

---

### Post by sakalonys on 2011-12-05
freak@STATION:~$ sudo apt-get install linux-backports-modules-wireless-maverick-generic linux-firmware
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
linux-backports-modules-wireless-maverick-generic ist schon die neueste Version.
linux-firmware ist schon die neueste Version.
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 340 nicht aktualisiert.
freak@STATION:~$

---

### Post by praseodym on 2011-12-05
> 0 aktualisiert, 0 neu installiert, 0 zu entfernen und **340** nicht aktualisiert.
Update?

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
Reboot.

---

### Post by sakalonys on 2011-12-05
both or only update ?

---

### Post by praseodym on 2011-12-05
"dist-upgrade" does _not_ mean you are upgrading to 11.04

---

### Post by sakalonys on 2011-12-06
hi there

sudo apt-get update sudo apt-get upgrade sudo apt-get dist-upgrade & installed all backport compat wireless things,but still nothing... here some outputs

```

freak@STATION:~$ sudo apt-get upgrade
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
freak@STATION:~$ sudo apt-get dist-upgrade
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
Paketaktualisierung (Upgrade) wird berechnet... Fertig
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.



freak@STATION:~$ lsmod
Module                  Size  Used by
ppp_deflate             4450  0 
zlib_deflate           21866  1 ppp_deflate
bsd_comp                5307  0 
ppp_async               8070  1 
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_analog    80317  1 
snd_hda_intel          26147  1 
snd_hda_codec         100919  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
nouveau               569328  2 
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
option                 16661  2 
rt2870sta             446110  1 
crc_ccitt               1699  2 ppp_async,rt2870sta
usb_wwan               12201  1 option
ttm                    68212  1 nouveau
usbserial              40364  7 option,usb_wwan
asus_atk0110           12987  0 
drm_kms_helper         32836  1 nouveau
psmouse                62080  0 
snd                    64277  11 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   206198  4 nouveau,ttm,drm_kms_helper
serio_raw               4910  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
intel_agp              32334  0 
lp                     10201  0 
i2c_algo_bit            6208  1 nouveau
parport                37032  3 parport_pc,ppdev,lp
hid_logitech           10639  0 
ff_memless              5485  1 hid_logitech
usbhid                 42030  1 hid_logitech
hid                    84710  2 hid_logitech,usbhid
usb_storage            50788  0 
ahci                   22370  1 
r8169                  42286  0 
mii                     5261  1 r8169
pata_jmicron            2771  1 
libahci                26148  1 ahci

freak@STATION:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-76 dBm  Noise level:-105 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ppp0      no wireless extensions.

freak@STATION:~$ sudo iwlist scan
[sudo] password for freak: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:15:0C:4E:E8:1C
                    Protocol:802.11b/g
                    ESSID:"Baerchen"
                    Mode:Managed
                    Channel:1
                    Quality:34/100  Signal level:-76 dBm  Noise level:-105 dBm
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:04:0E:F8:85:29
                    Protocol:802.11b/g
                    ESSID:"FRITZ!Box Fon WLAN 7141"
                    Mode:Managed
                    Channel:1
                    Quality:39/100  Signal level:-74 dBm  Noise level:-105 dBm
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:24:B2:58:AC:E5
                    Protocol:802.11b/g/n
                    ESSID:"HANNE-VAIO_Network"
                    Mode:Managed
                    Channel:2
                    Quality:5/100  Signal level:-88 dBm  Noise level:-105 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:26:4D:76:16:A5
                    Protocol:802.11b/g/n
                    ESSID:"Friederike"
                    Mode:Managed
                    Channel:2
                    Quality:15/100  Signal level:-84 dBm  Noise level:-105 dBm
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 05 - Address: 00:1F:33:4D:C4:4E
                    Protocol:802.11b/g
                    ESSID:"Unity0909"
                    Mode:Managed
                    Channel:6
                    Quality:39/100  Signal level:-74 dBm  Noise level:-105 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 06 - Address: 84:A8:E4:64:F6:52
                    Protocol:802.11b/g/n
                    ESSID:"carrera4s"
                    Mode:Managed
                    Channel:7
                    Quality:15/100  Signal level:-84 dBm  Noise level:-105 dBm
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: 00:1C:28:15:7A:D2
                    Protocol:802.11b/g
                    ESSID:"ALICE-WLAN10"
                    Mode:Managed
                    Channel:7
                    Quality:20/100  Signal level:-82 dBm  Noise level:-105 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: 1C:BD:B9:C0:9F:68
                    Protocol:802.11b/g
                    ESSID:"dlink"
                    Mode:Managed
                    Channel:9
                    Quality:10/100  Signal level:-86 dBm  Noise level:-105 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: 00:1D:19:45:7A:09
                    Protocol:802.11b/g
                    ESSID:"Arcor-457A31"
                    Mode:Managed
                    Channel:9
                    Quality:20/100  Signal level:-82 dBm  Noise level:-105 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 10 - Address: 00:1C:4A:A1:08:AA
                    Protocol:802.11g
                    ESSID:""
                    Mode:Managed
                    Channel:9
                    Quality:15/100  Signal level:-84 dBm  Noise level:-105 dBm
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: 00:26:4D:B7:3D:66
                    Protocol:802.11b/g/n
                    ESSID:"WLAN-B73D38"
                    Mode:Managed
                    Channel:11
                    Quality:15/100  Signal level:-84 dBm  Noise level:-105 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: 00:1F:3F:1B:DA:1F
                    Protocol:802.11b/g
                    ESSID:"FRITZ!Box Fon WLAN 7170"
                    Mode:Managed
                    Channel:11
                    Quality:20/100  Signal level:-82 dBm  Noise level:-105 dBm
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: 00:1A:2A:58:5A:83
                    Protocol:802.11b/g
                    ESSID:"WLAN-585A36"
                    Mode:Managed
                    Channel:11
                    Quality:29/100  Signal level:-78 dBm  Noise level:-105 dBm
                    Encryption key:on
                    Bit Rates:22 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 14 - Address: 00:1C:4A:34:9E:B1
                    Protocol:802.11b/g/n
                    ESSID:"WLAN-001C4A349EB1"
                    Mode:Managed
                    Channel:11
                    Quality:24/100  Signal level:-80 dBm  Noise level:-105 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: 88:25:2C:80:B5:0C
                    Protocol:802.11b/g/n
                    ESSID:"WLAN-80B575"
                    Mode:Managed
                    Channel:11
                    Quality:44/100  Signal level:-72 dBm  Noise level:-105 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: 00:1A:4F:96:CE:7C
                    Protocol:802.11b/g
                    ESSID:"WLAN-001A4F96CE7C"
                    Mode:Managed
                    Channel:11
                    Quality:5/100  Signal level:-88 dBm  Noise level:-105 dBm
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

ppp0      Interface doesn't support scanning.

freak@STATION:~$ dmesg | grep rt2
[   15.593522] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   15.688536] usbcore: registered new interface driver rt2870
[   17.701935] RTMPFilterCalibration - can't find a valid value, loopcnt=102 stop calibrating<==== rt28xx_init, Status=0
[   19.382639] RTMPFilterCalibration - can't find a valid value, loopcnt=102 stop calibrating<==== rt28xx_init, Status=0
[   92.360781] <==== rt28xx_init, Status=0

is this maybe the problem :


[   17.701935] RTMPFilterCalibration - can't find a valid value, loopcnt=102 stop calibrating<==== rt28xx_init, Status=0
[   19.382639] RTMPFilterCalibration - can't find a valid value, loopcnt=102 stop calibrating<==== rt28xx_init, Status=0


freak@STATION:~$ rfkill list
freak@STATION:~$ 
freak@STATION:~$ rfkill list
freak@STATION:~$ 

no output is this right ??




hope u can help me


```

---

### Post by praseodym on 2011-12-06
Which network do you want to connect to? Please show

```
iwlist chan
```
I recommend using WPA2-AES (CCMP) encryption, if possible. Checkbox all user rights in "USERS&GROUPS", login again, remove the wireless profile and set up a new one

---

### Post by sakalonys on 2011-12-06
```
 Cell 05 - Address: 00:1F:33:4D:C4:4E
                    Protocol:802.11b/g
                    ESSID:"Unity0909"
                    Mode:Managed
                    Channel:6
                    Quality:39/100  Signal level:-74 dBm  Noise level:-105 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s

```

9876543210 is the wepkey

but normally cause speed issues  it would be 

iwconfig wlan1
wlan1     IEEE 802.11bgn  ESSID:"FRITZ!Box Fon WLAN 7270"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:746F-7070-6F69-6E74-3133-3333-37
          Power Management:on

---

### Post by sakalonys on 2011-12-06
for my case wpa2 isnt possible...

only wep

---

### Post by sakalonys on 2011-12-06
```
freak@STATION:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.412 GHz (Channel 1)

ppp0      no frequency information.

freak@STATION:~$ 




```

should not be the problem ...but where are channel 12 & 13 ?

---

### Post by sakalonys on 2011-12-06
did this now :
Checkbox all user rights in "USERS&GROUPS", login again, remove the wireless profile and set up a new one

saw that many checkboxes like wireless connect werent checked... checked all & everything rebooting now

---

### Post by praseodym on 2011-12-06
I recommend deleting your key from your posting or change it ;-)

Try to disable the power-management:

```
sudo iwconfig wlan1 power off
```

---

### Post by sakalonys on 2011-12-06
freak@STATION:~$ sudo iwconfig wlan1 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan1 ; No such device.
freak@STATION:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:-74 dBm  Noise level:-105 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ppp0      no wireless extensions.

freak@STATION:~$ #

---

### Post by sakalonys on 2011-12-06
freak@STATION:~$ sudo iwconfig wlan0 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.

---

### Post by sakalonys on 2011-12-06
is this maybe the prob ? :

freak@STATION:~$ iw phy wlan0 reg get
nl80211 not found.

---

### Post by sakalonys on 2011-12-06
will sudo apt-get install libnl1 libnl-dev libnl2 libnl2-dev libnl2-dbg
 now

---

### Post by sakalonys on 2011-12-06
made probs freak@STATION:~$ sudo apt-get install --reinstall libnl1 libnl2 libnl2-dbg

---

### Post by sakalonys on 2011-12-06
rebboting

---

### Post by sakalonys on 2011-12-06
no effect

---

### Post by sakalonys on 2011-12-06
freak@STATION:~$ iw phy wlan0 infonl80211 not found.

---

### Post by praseodym on 2011-12-06
Which country do you live? Check:

```
dmesg | grep country
```

---

### Post by sakalonys on 2011-12-06
> **praseodym said:**
> Which country do you live? Check:

```
dmesg | grep country
```


same like u...

germany reg code should be DE

---

### Post by sakalonys on 2011-12-06
dmesg | grep country

has no output

---

### Post by sakalonys on 2011-12-06
freak@STATION:~$ dmesg | grep DE
[    0.000000]   NODE_DATA [0000000001d642c0 - 0000000001d692bf]
[    0.000000]   #12 [0001d642c0 - 0001d692c0]       NODE_DATA
[   16.266281] ADDRCONF(NETDEV_UP): eth0: link is not ready

---

### Post by sakalonys on 2011-12-06
```
freak@STATION:~$ dmesg | grep rt
[    0.000000] Movable zone start PFN for each node
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] Checking aperture...
[    0.011828] mce: CPU supports 4 MCE banks
[    0.040015] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.349346] ACPI: (supports S0 S1 S3 S4 S5)
[    0.411855] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.412615] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.412906] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.413009] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.413100] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.413198] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.413297] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.413617] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.413925] pci 0000:00:1f.2: PME# supported from D3hot
[    0.414484] pci 0000:03:00.0: supports D1 D2
[    0.414487] pci 0000:03:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.414747] pci 0000:02:00.0: PME# supported from D3hot
[    0.783011] pcieport 0000:00:01.0: setting latency timer to 64
[    0.783067] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.783160] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.783212] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.783329] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.783381] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.783495] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.783546] pcieport 0000:00:1c.4: irq 43 for MSI/MSI-X
[    0.790121] Linux agpgart interface v0.103
[    0.790156] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.794559] ehci_hcd 0000:00:1a.7: debug port 1
[    0.798432] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.819754] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.819941] hub 1-0:1.0: 4 ports detected
[    0.820183] ehci_hcd 0000:00:1d.7: debug port 1
[    0.824068] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.839702] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.839864] hub 2-0:1.0: 6 ports detected
[    0.840369] hub 3-0:1.0: 2 ports detected
[    0.840749] hub 4-0:1.0: 2 ports detected
[    0.841106] hub 5-0:1.0: 2 ports detected
[    0.841486] hub 6-0:1.0: 2 ports detected
[    0.841852] hub 7-0:1.0: 2 ports detected
[    0.842031] PNP: No PS/2 controller found. Probing ports directly.
[    0.844512] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.844521] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.844854] rtc_cmos 00:03: RTC can wake from S4
[    0.844911] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.844940] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.847871] rtc_cmos 00:03: setting system clock to 2011-12-06 22:57:37 UTC (1323212257)
[    0.877790] udev[74]: starting version 163
[    0.988832] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    0.988838] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pmp pio slum part ccc ems 
[    1.112487] ata3: SATA max UDMA/133 abar m2048@0xfebff800 port 0xfebff900 irq 44
[    1.112492] ata4: SATA max UDMA/133 abar m2048@0xfebff800 port 0xfebff980 irq 44
[    1.112501] ata7: SATA max UDMA/133 abar m2048@0xfebff800 port 0xfebffb00 irq 44
[    1.112505] ata8: SATA max UDMA/133 abar m2048@0xfebff800 port 0xfebffb80 irq 44
[    1.130057] ahci 0000:02:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.130063] ahci 0000:02:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.130547] ata9: SATA max UDMA/133 abar m8192@0xfe9fe000 port 0xfe9fe100 irq 16
[    1.130553] ata10: SATA max UDMA/133 abar m8192@0xfe9fe000 port 0xfe9fe180 irq 16
[    1.281606] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.309186] USB Mass Storage support registered.
[    1.562117] hub 2-1:1.0: 4 ports detected
[    1.680606] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.650631] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.651220]  sdd: unknown partition table
[    3.620629] sd 6:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.227931] kjournald starting.  Commit interval 5 seconds
[   15.047983] udev[394]: starting version 163
[   15.469336] USB Serial support registered for generic
[   15.540049] USB Serial support registered for GSM modem (1-port)
[   15.540167] option 1-2:1.0: GSM modem (1-port) converter detected
[   15.540304] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[   15.540345] option 1-2:1.1: GSM modem (1-port) converter detected
[   15.540441] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[   15.540479] option 1-2:1.2: GSM modem (1-port) converter detected
[   15.540599] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[   15.552612] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   15.560450] rtusb init --->
[   15.642863] usbcore: registered new interface driver rt2870
[   16.231967] [drm] nouveau 0000:01:00.0: 64 MiB GART (aperture)
[   16.605693] Slow work thread pool: Starting up
[   16.682992] ppdev: user-space parallel port driver
[   17.972478] RTMPFilterCalibration - can't find a valid value, loopcnt=102 stop calibrating<==== rt28xx_init, Status=0
[   19.391513] RTMPFilterCalibration - can't find a valid value, loopcnt=102 stop calibrating<==== rt28xx_init, Status=0
[   24.500071] ===>rt_ioctl_giwscan. 16(16) BSS returned, data->length = 3314
[   29.646608] ===>rt_ioctl_giwscan. 15(15) BSS returned, data->length = 3086
[   29.646961] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[   44.660111] ===>rt_ioctl_giwscan. 16(16) BSS returned, data->length = 3314
[   44.660328] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[   56.218641] RTMPFilterCalibration - can't find a valid value, loopcnt=102 stop calibrating<==== rt28xx_init, Status=0
[   74.354987] ===>rt_ioctl_giwscan. 16(16) BSS returned, data->length = 3315
[   94.160459] ===>rt_ioctl_giwscan. 16(16) BSS returned, data->length = 3318
[   94.160663] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  109.170709] ===>rt_ioctl_giwscan. 17(17) BSS returned, data->length = 3497
[  109.170939] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  124.179377] ===>rt_ioctl_giwscan. 17(17) BSS returned, data->length = 3497
[  124.179604] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  139.197598] ===>rt_ioctl_giwscan. 17(17) BSS returned, data->length = 3450
[  139.197816] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  154.144636] RTMPFilterCalibration - can't find a valid value, loopcnt=102 stop calibrating<==== rt28xx_init, Status=0
[  161.360146] ===>rt_ioctl_giwscan. 15(15) BSS returned, data->length = 3125
[  165.187422] <==== rt28xx_init, Status=0
[  184.354626] ===>rt_ioctl_giwscan. 18(18) BSS returned, data->length = 3689
[  224.357009] ===>rt_ioctl_giwscan. 18(18) BSS returned, data->length = 3690
[  274.354855] ===>rt_ioctl_giwscan. 20(20) BSS returned, data->length = 4070
[  334.354773] ===>rt_ioctl_giwscan. 18(18) BSS returned, data->length = 3714
[  394.351408] ===>rt_ioctl_giwscan. 21(21) BSS returned, data->length = 4297
[  454.351405] ===>rt_ioctl_giwscan. 19(19) BSS returned, data->length = 3873
[  495.600346] ===>rt_ioctl_giwscan. 16(16) BSS returned, data->length = 3314
[  495.600581] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  510.628093] ===>rt_ioctl_giwscan. 17(17) BSS returned, data->length = 3457
[  510.628302] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  525.644518] ===>rt_ioctl_giwscan. 18(18) BSS returned, data->length = 3681
[  525.644746] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  540.662624] ===>rt_ioctl_giwscan. 16(16) BSS returned, data->length = 3352
[  550.668195] ===>rt_ioctl_giwscan. 16(16) BSS returned, data->length = 3348
[  555.082534] RTMPFilterCalibration - can't find a valid value, loopcnt=102 stop calibrating<==== rt28xx_init, Status=0
[  574.350206] ===>rt_ioctl_giwscan. 17(17) BSS returned, data->length = 3493
[  634.354865] ===>rt_ioctl_giwscan. 19(19) BSS returned, data->length = 3873
[  694.350188] ===>rt_ioctl_giwscan. 20(20) BSS returned, data->length = 4060
[  754.352224] ===>rt_ioctl_giwscan. 18(18) BSS returned, data->length = 3640
[  814.353023] ===>rt_ioctl_giwscan. 20(20) BSS returned, data->length = 4070
[  874.352096] ===>rt_ioctl_giwscan. 21(21) BSS returned, data->length = 4386
[  934.352895] ===>rt_ioctl_giwscan. 19(19) BSS returned, data->length = 3873
[  994.352240] ===>rt_ioctl_giwscan. 17(17) BSS returned, data->length = 3452
freak@STATION:~$ 

```

---

### Post by praseodym on 2011-12-06
Country code settings are buggy in kernel 3. Try:

```
sudo apt-get install iw
sudo iw reg set DE
```

---

### Post by sakalonys on 2011-12-07
freak@STATION:~$ sudo iw reg set DE
[sudo] password for freak: 
nl80211 not found.
freak@STATION:~$

---

### Post by praseodym on 2011-12-07
Try the latest driver rt8070/etc. from the Ralink-HP:

[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

You need to manipulate the file /os/linux/config.mk according to [here]("http://wiki.ubuntuusers.de/wlan/ralink#RT28xx"), also set the Draft-N settings in the file rt2870sta.dat before compiling (scroll down there).

---

### Post by sakalonys on 2011-12-07
:-( nothing

---

### Post by sakalonys on 2011-12-07
i didnt see my hd id 148f:3070 listed

---

### Post by sakalonys on 2011-12-07
are u using this stick , by the way ?

---

### Post by praseodym on 2011-12-07
No, I dont use it.

Please show:

```
modinfo rt2870sta | egrep '148F|3070'
modinfo rt2800usb | egrep '148F|3070'
```

---

### Post by sakalonys on 2011-12-07
freak@STATION:~$ #modinfo rt2870sta | egrep '148F|3070'
freak@STATION:~$ 
freak@STATION:~$ modinfo rt2800usb | egrep '148F|3070'
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
freak@STATION:~$

---

### Post by praseodym on 2011-12-07
Did you change in the driver folder ~/os/linux/config.mk file this

```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=n


# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
```

to

```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=[COLOR="Red"]y[/COLOR]


# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=[COLOR="Red"]y[/COLOR]
```
before compiling with "sudo make"?

BTW: Sorry, this compiles the module rt5370sta, so please show:

```
locate rt5370sta.ko | grep lib
modinfo rt5370sta
```

---

### Post by sakalonys on 2011-12-07
yes ... i did and :   ```
freak@STATION:~$ locate rt5370sta.ko | grep lib freak@STATION:~$ modinfo rt5370sta filename:       /lib/modules/2.6.35-31-generic/kernel/drivers/net/wireless/rt5370sta.ko version:        2.5.0.3 license:        GPL description:    RT2870 Wireless Lan Linux Driver author:         Paul Lin  srcversion:     9545CDBE68CD5247E220296 alias:          usb:v043Ep7A22d*dc*dsc*dp*ic*isc*ip* alias:          usb:v043Ep7A12d*dc*dsc*dp*ic*isc*ip* alias:          usb:v2001p3C19d*dc*dsc*dp*ic*isc*ip* alias:          usb:v2001p3C15d*dc*dsc*dp*ic*isc*ip* alias:          usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip* alias:          usb:v13D3p3365d*dc*dsc*dp*ic*isc*ip* alias:          usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip* alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip* alias:          usb:v0DF6p0050d*dc*dsc*dp*ic*isc*ip* alias:          usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip* alias:          usb:v1EDAp2012d*dc*dsc*dp*ic*isc*ip* alias:          usb:v0586p343Ed*dc*dsc*dp*ic*isc*ip* alias:          usb:v0586p341Ed*dc*dsc*dp*ic*isc*ip* alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip* alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip* alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip* alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip* alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip* alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip* alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip* alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip* alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip* alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip* alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip* alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip* alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip* alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip* alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip* alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip* alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip* alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip* alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip* alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip* alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip* alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip* alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip* alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip* alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip* alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip* alias:          usb:v1D4Dp0011d*dc*dsc*dp*ic*isc*ip* alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip* alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip* alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip* alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip* alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip* alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip* alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip* alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip* alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip* alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip* alias:          usb:v7392p4085d*dc*dsc*dp*ic*isc*ip* alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip* alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip* alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip* alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip* alias:          usb:v2019p5201d*dc*dsc*dp*ic*isc*ip* alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip* alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip* alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip* alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip* alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip* alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip* alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip* alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip* alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip* alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip* alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip* alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip* alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip* alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip* alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip* alias:          usb:v0DF6p005Fd*dc*dsc*dp*ic*isc*ip* alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip* alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip* alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip* alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip* alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip* alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip* alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip* alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip* alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip* alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip* alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip* alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip* depends:         vermagic:       2.6.35-31-generic SMP mod_unload modversions  parm:           mac:rt28xx: wireless mac addr (charp) freak@STATION:~$   
```

---

### Post by praseodym on 2011-12-07
```
/lib/modules/2.6.35-31-generic/kernel/drivers/net/wireless/rt5370sta.ko
...
usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
```
The driver is there, try to load it:

```
sudo modprobe -v rt5370sta
```
Replug the stick and check:

```
iwconfig
lsmod
dmesg | egrep 'rt2|rt3|rt5'
rfkill list
sudo iwlist scan
```

---

### Post by sakalonys on 2011-12-07
will try another thing :
disabled wireless , rmmod rt2870sta sudo modprobe -v rt5370sta smth happened at dmesg :


```
[10562.121276] #
[10563.639325] ---> RTMPFreeTxRxRingMemory
[10563.639381] <--- RTMPFreeTxRxRingMemory
[10565.075754] rtusb init rt2870 --->
[10565.075765] Error: Driver 'rt2870' is already registered, aborting...
[10567.198545] usbcore: deregistering interface driver rt2870
[10567.198575] rtusb_disconnect: unregister usbnet usb-0000:00:1d.7-1.4
[10567.198580] RtmpOSNetDevDetach(): RtmpOSNetDeviceDetach(), dev->name=wlan0!
[10567.250161]  RTUSB disconnect successfully
[10567.250213] <--- rtusb exit
[10568.397678] rtusb init rt2870 --->
[10568.398179] 
[10568.398180] 
[10568.398181] === pAd = ffffc900179c0000, size = 552480 ===
[10568.398183] 
[10568.398625] <-- RTMPAllocTxRxRingMemory, Status=0
[10568.398702] <-- RTMPAllocAdapterBlock, Status=0
[10568.400920] usbcore: registered new interface driver rt2870
[10568.426629] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[10568.697567] RTMP_TimerListAdd: add timer obj ffffc90017a091c8!
[10568.697574] RTMP_TimerListAdd: add timer obj ffffc90017a09248!
[10568.697578] RTMP_TimerListAdd: add timer obj ffffc90017a092c8!
[10568.697581] RTMP_TimerListAdd: add timer obj ffffc90017a09148!
[10568.697586] RTMP_TimerListAdd: add timer obj ffffc90017a08fc8!
[10568.697589] RTMP_TimerListAdd: add timer obj ffffc90017a09048!
[10568.697593] RTMP_TimerListAdd: add timer obj ffffc900179d3490!
[10568.697596] RTMP_TimerListAdd: add timer obj ffffc900179c2668!
[10568.697599] RTMP_TimerListAdd: add timer obj ffffc900179c26f0!
[10568.697602] RTMP_TimerListAdd: add timer obj ffffc900179d3638!
[10568.697606] RTMP_TimerListAdd: add timer obj ffffc900179d3390!
[10568.697611] RTMP_TimerListAdd: add timer obj ffffc900179d35b0!
[10568.698985] -->RTUSBVenderReset
[10568.699109] <--RTUSBVenderReset
[10569.201134] Key2Str is Invalid key length(0) or Type(0)
[10569.201178] Key3Str is Invalid key length(0) or Type(0)
[10569.201221] Key4Str is Invalid key length(0) or Type(0)
[10569.202068] 1. Phy Mode = 5
[10569.202071] 2. Phy Mode = 5
[10569.229351] phy mode> Error! The chip does not support 5G band 5!
[10569.233601] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[10569.247849] 3. Phy Mode = 9
[10569.250599] AntCfgInit: primary/secondary ant 0/1
[10569.250601] RTMPFilterCalibration - can't find a valid value, loopcnt=102 stop calibratingMCS Set = ff 00 00 00 01
[10569.728357] <==== rt28xx_init, Status=0
[10569.730215] 0x1300 = 00064300
[10570.348697] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[10570.612034] RTMP_TimerListAdd: add timer obj ffffc90017a091c8!
[10570.612040] RTMP_TimerListAdd: add timer obj ffffc90017a09248!
[10570.612043] RTMP_TimerListAdd: add timer obj ffffc90017a092c8!
[10570.612047] RTMP_TimerListAdd: add timer obj ffffc90017a09148!
[10570.612051] RTMP_TimerListAdd: add timer obj ffffc90017a08fc8!
[10570.612054] RTMP_TimerListAdd: add timer obj ffffc90017a09048!
[10570.612058] RTMP_TimerListAdd: add timer obj ffffc900179d3490!
[10570.612061] RTMP_TimerListAdd: add timer obj ffffc900179c2668!
[10570.612064] RTMP_TimerListAdd: add timer obj ffffc900179c26f0!
[10570.612067] RTMP_TimerListAdd: add timer obj ffffc900179d3638!
[10570.612071] RTMP_TimerListAdd: add timer obj ffffc900179d3390!
[10570.612076] RTMP_TimerListAdd: add timer obj ffffc900179d35b0!
[10570.613437] -->RTUSBVenderReset
[10570.613561] <--RTUSBVenderReset
[10571.093569] Key2Str is Invalid key length(0) or Type(0)
[10571.093613] Key3Str is Invalid key length(0) or Type(0)
[10571.093656] Key4Str is Invalid key length(0) or Type(0)
[10571.094487] 1. Phy Mode = 5
[10571.094490] 2. Phy Mode = 5
[10571.121175] phy mode> Error! The chip does not support 5G band 5!
[10571.132678] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[10571.147175] 3. Phy Mode = 9
[10571.149676] AntCfgInit: primary/secondary ant 0/1
[10571.149677] MCS Set = ff 00 00 00 01
[10571.216695] <==== rt28xx_init, Status=0
[10571.218173] 0x1300 = 00064300
[10571.268137] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 159
[10573.198884] ===>rt_ioctl_giwscan. 15(15) BSS returned, data->length = 3238
[10575.589284] ===>rt_ioctl_giwscan. 19(19) BSS returned, data->length = 4249
[10578.587837] ===>rt_ioctl_giwscan. 21(21) BSS returned, data->length = 4693
[10581.589032] ===>rt_ioctl_giwscan. 22(22) BSS returned, data->length = 4920
[10584.589630] ===>rt_ioctl_giwscan. 23(23) BSS returned, data->length = 5129
[10587.609361] ===>rt_ioctl_giwscan. 21(21) BSS returned, data->length = 4764
[10590.598986] ===>rt_ioctl_giwscan. 21(21) BSS returned, data->length = 4654
[10593.291351] ===>rt_ioctl_giwscan. 22(22) BSS returned, data->length = 5001
[10596.600384] ===>rt_ioctl_giwscan. 22(22) BSS returned, data->length = 4924
[10599.619689] ===>rt_ioctl_giwscan. 22(22) BSS returned, data->length = 4924
[10602.628658] ===>rt_ioctl_giwscan. 19(19) BSS returned, data->length = 4270
[10605.629168] ===>rt_ioctl_giwscan. 20(20) BSS returned, data->length = 4473
[10608.629085] ===>rt_ioctl_giwscan. 20(20) BSS returned, data->length = 4493
[10611.647789] ===>rt_ioctl_giwscan. 23(23) BSS returned, data->length = 5088
[10614.650871] ===>rt_ioctl_giwscan. 22(22) BSS returned, data->length = 4849
freak@STATION:~$ 


```

---

### Post by sakalonys on 2011-12-07
```
[10540.131335] #
[10540.471326] #
[10540.631323] #
[10540.781318] #
[10540.931315] #
[10541.381303] #
[10541.531301] #
[10541.681297] #
[10541.831292] #
[10543.216810] rtusb init rt2870 --->
[10543.216820] Error: Driver 'rt2870' is already registered, aborting...
[10543.971362] #
[10544.471350] #
[10544.931338] #
[10545.081335] #
[10545.231330] #
[10545.381326] #
[10545.531323] #
[10545.681320] #
[10545.831316] #
[10545.981312] #
[10546.131309] #
[10546.471299] #
[10547.081282] #
[10548.471371] #
[10548.491374] #
[10549.091359] #
[10550.471324] #
[10550.931311] #
[10551.081308] #
[10551.231304] #
[10551.381301] #
[10551.841288] #
[10551.991284] #
[10552.141280] #
[10553.220128] #
[10553.521368] #
[10553.671368] #
[10553.821363] #
[10554.121355] #
[10554.471348] #
[10554.781340] #
[10555.081332] #
[10555.381325] #
[10556.931285] #
[10557.231398] #
[10558.621367] #
[10558.921360] #
[10559.221352] #
[10559.821336] #
[10560.121328] #
[10560.621316] #
[10560.921308] #
[10561.071305] #
[10561.221301] #
[10561.371297] #
[10561.521294] #
[10561.821285] #
[10562.121276] #
[10563.639325] ---> RTMPFreeTxRxRingMemory
[10563.639381] <--- RTMPFreeTxRxRingMemory
[10565.075754] rtusb init rt2870 --->
[10565.075765] Error: Driver 'rt2870' is already registered, aborting...
[10567.198545] usbcore: deregistering interface driver rt2870
[10567.198575] rtusb_disconnect: unregister usbnet usb-0000:00:1d.7-1.4
[10567.198580] RtmpOSNetDevDetach(): RtmpOSNetDeviceDetach(), dev->name=wlan0!
[10567.250161]  RTUSB disconnect successfully
[10567.250213] <--- rtusb exit
[10568.397678] rtusb init rt2870 --->
[10568.398179] 
[10568.398180] 
[10568.398181] === pAd = ffffc900179c0000, size = 552480 ===
[10568.398183] 
[10568.398625] <-- RTMPAllocTxRxRingMemory, Status=0
[10568.398702] <-- RTMPAllocAdapterBlock, Status=0
[10568.400920] usbcore: registered new interface driver rt2870
[10568.426629] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[10568.697567] RTMP_TimerListAdd: add timer obj ffffc90017a091c8!
[10568.697574] RTMP_TimerListAdd: add timer obj ffffc90017a09248!
[10568.697578] RTMP_TimerListAdd: add timer obj ffffc90017a092c8!
[10568.697581] RTMP_TimerListAdd: add timer obj ffffc90017a09148!
[10568.697586] RTMP_TimerListAdd: add timer obj ffffc90017a08fc8!
[10568.697589] RTMP_TimerListAdd: add timer obj ffffc90017a09048!
[10568.697593] RTMP_TimerListAdd: add timer obj ffffc900179d3490!
[10568.697596] RTMP_TimerListAdd: add timer obj ffffc900179c2668!
[10568.697599] RTMP_TimerListAdd: add timer obj ffffc900179c26f0!
[10568.697602] RTMP_TimerListAdd: add timer obj ffffc900179d3638!
[10568.697606] RTMP_TimerListAdd: add timer obj ffffc900179d3390!
[10568.697611] RTMP_TimerListAdd: add timer obj ffffc900179d35b0!
[10568.698985] -->RTUSBVenderReset
[10568.699109] <--RTUSBVenderReset
[10569.201134] Key2Str is Invalid key length(0) or Type(0)
[10569.201178] Key3Str is Invalid key length(0) or Type(0)
[10569.201221] Key4Str is Invalid key length(0) or Type(0)
[10569.202068] 1. Phy Mode = 5
[10569.202071] 2. Phy Mode = 5
[10569.229351] phy mode> Error! The chip does not support 5G band 5!
[10569.233601] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[10569.247849] 3. Phy Mode = 9
[10569.250599] AntCfgInit: primary/secondary ant 0/1
[10569.250601] RTMPFilterCalibration - can't find a valid value, loopcnt=102 stop calibratingMCS Set = ff 00 00 00 01
[10569.728357] <==== rt28xx_init, Status=0
[10569.730215] 0x1300 = 00064300
[10570.348697] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[10570.612034] RTMP_TimerListAdd: add timer obj ffffc90017a091c8!
[10570.612040] RTMP_TimerListAdd: add timer obj ffffc90017a09248!
[10570.612043] RTMP_TimerListAdd: add timer obj ffffc90017a092c8!
[10570.612047] RTMP_TimerListAdd: add timer obj ffffc90017a09148!
[10570.612051] RTMP_TimerListAdd: add timer obj ffffc90017a08fc8!
[10570.612054] RTMP_TimerListAdd: add timer obj ffffc90017a09048!
[10570.612058] RTMP_TimerListAdd: add timer obj ffffc900179d3490!
[10570.612061] RTMP_TimerListAdd: add timer obj ffffc900179c2668!
[10570.612064] RTMP_TimerListAdd: add timer obj ffffc900179c26f0!
[10570.612067] RTMP_TimerListAdd: add timer obj ffffc900179d3638!
[10570.612071] RTMP_TimerListAdd: add timer obj ffffc900179d3390!
[10570.612076] RTMP_TimerListAdd: add timer obj ffffc900179d35b0!
[10570.613437] -->RTUSBVenderReset
[10570.613561] <--RTUSBVenderReset
[10571.093569] Key2Str is Invalid key length(0) or Type(0)
[10571.093613] Key3Str is Invalid key length(0) or Type(0)
[10571.093656] Key4Str is Invalid key length(0) or Type(0)
[10571.094487] 1. Phy Mode = 5
[10571.094490] 2. Phy Mode = 5
[10571.121175] phy mode> Error! The chip does not support 5G band 5!
[10571.132678] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[10571.147175] 3. Phy Mode = 9
[10571.149676] AntCfgInit: primary/secondary ant 0/1
[10571.149677] MCS Set = ff 00 00 00 01
[10571.216695] <==== rt28xx_init, Status=0
[10571.218173] 0x1300 = 00064300
[10571.268137] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 159
[10573.198884] ===>rt_ioctl_giwscan. 15(15) BSS returned, data->length = 3238
[10575.589284] ===>rt_ioctl_giwscan. 19(19) BSS returned, data->length = 4249
[10578.587837] ===>rt_ioctl_giwscan. 21(21) BSS returned, data->length = 4693
[10581.589032] ===>rt_ioctl_giwscan. 22(22) BSS returned, data->length = 4920
[10584.589630] ===>rt_ioctl_giwscan. 23(23) BSS returned, data->length = 5129
[10587.609361] ===>rt_ioctl_giwscan. 21(21) BSS returned, data->length = 4764
[10590.598986] ===>rt_ioctl_giwscan. 21(21) BSS returned, data->length = 4654
[10593.291351] ===>rt_ioctl_giwscan. 22(22) BSS returned, data->length = 5001
[10596.600384] ===>rt_ioctl_giwscan. 22(22) BSS returned, data->length = 4924
[10599.619689] ===>rt_ioctl_giwscan. 22(22) BSS returned, data->length = 4924
[10602.628658] ===>rt_ioctl_giwscan. 19(19) BSS returned, data->length = 4270
[10605.629168] ===>rt_ioctl_giwscan. 20(20) BSS returned, data->length = 4473
[10608.629085] ===>rt_ioctl_giwscan. 20(20) BSS returned, data->length = 4493
[10611.647789] ===>rt_ioctl_giwscan. 23(23) BSS returned, data->length = 5088
[10614.650871] ===>rt_ioctl_giwscan. 22(22) BSS returned, data->length = 4849
freak@STATION:~$ sudo modprobe -v rt5370sta
freak@STATION:~$ lsmod
Module                  Size  Used by
rt5370sta             805025  1 
rt2800lib              42992  0 
rt2x00usb              11753  0 
rt2x00lib              39833  2 rt2800lib,rt2x00usb
kfifo                   9972  1 rt2x00lib
mac80211              292621  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              175295  2 rt2x00lib,mac80211
compat                  8739  3 rt2x00lib,mac80211,cfg80211
led_class               3393  2 rt2x00lib,compat
nls_iso8859_1           4657  1 
nls_cp437               6375  1 
vfat                   10954  1 
fat                    56244  1 vfat
ppp_deflate             4450  0 
zlib_deflate           21866  1 ppp_deflate
bsd_comp                5307  0 
ppp_async               8070  1 
option                 16661  2 
usb_wwan               12201  1 option
usbserial              40364  7 option,usb_wwan
usb_storage            50788  1 
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_analog    80317  1 
snd_hda_intel          26147  3 
snd_hda_codec         100919  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  3 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
nouveau               569328  2 
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    68212  1 nouveau
drm_kms_helper         32836  1 nouveau
crc_ccitt               1699  2 rt2800lib,ppp_async
drm                   206198  4 nouveau,ttm,drm_kms_helper
asus_atk0110           12987  0 
psmouse                62080  0 
snd                    64277  14 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               4910  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
i2c_algo_bit            6208  1 nouveau
intel_agp              32334  0 
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
hid_logitech           10639  0 
ff_memless              5485  1 hid_logitech
usbhid                 42030  1 hid_logitech
hid                    84710  2 hid_logitech,usbhid
ahci                   22370  4 
r8169                  42286  0 
libahci                26148  1 ahci
mii                     5261  1 r8169
pata_jmicron            2771  2 
freak@STATION:~$ clear

freak@STATION:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

ra0       Ralink STA  ESSID:"Unity0909"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-78 dBm  Noise level:-78 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

freak@STATION:~$ lsmod
Module                  Size  Used by
rt5370sta             805025  1 
rt2800lib              42992  0 
rt2x00usb              11753  0 
rt2x00lib              39833  2 rt2800lib,rt2x00usb
kfifo                   9972  1 rt2x00lib
mac80211              292621  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              175295  2 rt2x00lib,mac80211
compat                  8739  3 rt2x00lib,mac80211,cfg80211
led_class               3393  2 rt2x00lib,compat
nls_iso8859_1           4657  1 
nls_cp437               6375  1 
vfat                   10954  1 
fat                    56244  1 vfat
ppp_deflate             4450  0 
zlib_deflate           21866  1 ppp_deflate
bsd_comp                5307  0 
ppp_async               8070  1 
option                 16661  2 
usb_wwan               12201  1 option
usbserial              40364  7 option,usb_wwan
usb_storage            50788  1 
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_analog    80317  1 
snd_hda_intel          26147  3 
snd_hda_codec         100919  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  3 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
nouveau               569328  2 
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    68212  1 nouveau
drm_kms_helper         32836  1 nouveau
crc_ccitt               1699  2 rt2800lib,ppp_async
drm                   206198  4 nouveau,ttm,drm_kms_helper
asus_atk0110           12987  0 
psmouse                62080  0 
snd                    64277  14 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               4910  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
i2c_algo_bit            6208  1 nouveau
intel_agp              32334  0 
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
hid_logitech           10639  0 
ff_memless              5485  1 hid_logitech
usbhid                 42030  1 hid_logitech
hid                    84710  2 hid_logitech,usbhid
ahci                   22370  4 
r8169                  42286  0 
libahci                26148  1 ahci
mii                     5261  1 r8169
pata_jmicron            2771  2 
freak@STATION:~$ dmesg | egrep 'rt2|rt3|rt5'
[10259.352703] usbcore: registered new interface driver rt2800usb
[10270.748529] RTMPFilterCalibration - can't find a valid value, loopcnt=102 stop calibrating<==== rt28xx_init, Status=0
[10372.549332] <==== rt28xx_init, Status=0
[10439.739877] RTMPFilterCalibration - can't find a valid value, loopcnt=102 stop calibrating<==== rt28xx_init, Status=0
[10515.876444] rtusb init rt2870 --->
[10515.876453] Error: Driver 'rt2870' is already registered, aborting...
[10539.894509] usbcore: deregistering interface driver rt2800usb
[10543.216810] rtusb init rt2870 --->
[10543.216820] Error: Driver 'rt2870' is already registered, aborting...
[10565.075754] rtusb init rt2870 --->
[10565.075765] Error: Driver 'rt2870' is already registered, aborting...
[10567.198545] usbcore: deregistering interface driver rt2870
[10568.397678] rtusb init rt2870 --->
[10568.400920] usbcore: registered new interface driver rt2870
[10569.728357] <==== rt28xx_init, Status=0
[10571.216695] <==== rt28xx_init, Status=0
[11269.081518] <==== rt28xx_init, Status=0
[11270.587490] <==== rt28xx_init, Status=0
freak@STATION:~$ rfkill list
freak@STATION:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ppp0      Interface doesn't support scanning.

ra0       No scan results

```

---

### Post by sakalonys on 2011-12-07
```
[10540.131335] #
[10540.471326] #
[10540.631323] #
[10540.781318] #
[10540.931315] #
[10541.381303] #
[10541.531301] #
[10541.681297] #
[10541.831292] #
[10543.216810] rtusb init rt2870 --->
[10543.216820] Error: Driver 'rt2870' is already registered, aborting...
[10543.971362] #
[10544.471350] #
[10544.931338] #
[10545.081335] #
[10545.231330] #
[10545.381326] #
[10545.531323] #
[10545.681320] #
[10545.831316] #
[10545.981312] #
[10546.131309] #
[10546.471299] #
[10547.081282] #
[10548.471371] #
[10548.491374] #
[10549.091359] #
[10550.471324] #
[10550.931311] #
[10551.081308] #
[10551.231304] #
[10551.381301] #
[10551.841288] #
[10551.991284] #
[10552.141280] #
[10553.220128] #
[10553.521368] #
[10553.671368] #
[10553.821363] #
[10554.121355] #
[10554.471348] #
[10554.781340] #
[10555.081332] #
[10555.381325] #
[10556.931285] #
[10557.231398] #
[10558.621367] #
[10558.921360] #
[10559.221352] #
[10559.821336] #
[10560.121328] #
[10560.621316] #
[10560.921308] #
[10561.071305] #
[10561.221301] #
[10561.371297] #
[10561.521294] #
[10561.821285] #
[10562.121276] #
[10563.639325] ---> RTMPFreeTxRxRingMemory
[10563.639381] <--- RTMPFreeTxRxRingMemory
[10565.075754] rtusb init rt2870 --->
[10565.075765] Error: Driver 'rt2870' is already registered, aborting...
[10567.198545] usbcore: deregistering interface driver rt2870
[10567.198575] rtusb_disconnect: unregister usbnet usb-0000:00:1d.7-1.4
[10567.198580] RtmpOSNetDevDetach(): RtmpOSNetDeviceDetach(), dev->name=wlan0!
[10567.250161]  RTUSB disconnect successfully
[10567.250213] <--- rtusb exit
[10568.397678] rtusb init rt2870 --->
[10568.398179] 
[10568.398180] 
[10568.398181] === pAd = ffffc900179c0000, size = 552480 ===
[10568.398183] 
[10568.398625] <-- RTMPAllocTxRxRingMemory, Status=0
[10568.398702] <-- RTMPAllocAdapterBlock, Status=0
[10568.400920] usbcore: registered new interface driver rt2870
[10568.426629] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[10568.697567] RTMP_TimerListAdd: add timer obj ffffc90017a091c8!
[10568.697574] RTMP_TimerListAdd: add timer obj ffffc90017a09248!
[10568.697578] RTMP_TimerListAdd: add timer obj ffffc90017a092c8!
[10568.697581] RTMP_TimerListAdd: add timer obj ffffc90017a09148!
[10568.697586] RTMP_TimerListAdd: add timer obj ffffc90017a08fc8!
[10568.697589] RTMP_TimerListAdd: add timer obj ffffc90017a09048!
[10568.697593] RTMP_TimerListAdd: add timer obj ffffc900179d3490!
[10568.697596] RTMP_TimerListAdd: add timer obj ffffc900179c2668!
[10568.697599] RTMP_TimerListAdd: add timer obj ffffc900179c26f0!
[10568.697602] RTMP_TimerListAdd: add timer obj ffffc900179d3638!
[10568.697606] RTMP_TimerListAdd: add timer obj ffffc900179d3390!
[10568.697611] RTMP_TimerListAdd: add timer obj ffffc900179d35b0!
[10568.698985] -->RTUSBVenderReset
[10568.699109] <--RTUSBVenderReset
[10569.201134] Key2Str is Invalid key length(0) or Type(0)
[10569.201178] Key3Str is Invalid key length(0) or Type(0)
[10569.201221] Key4Str is Invalid key length(0) or Type(0)
[10569.202068] 1. Phy Mode = 5
[10569.202071] 2. Phy Mode = 5
[10569.229351] phy mode> Error! The chip does not support 5G band 5!
[10569.233601] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[10569.247849] 3. Phy Mode = 9
[10569.250599] AntCfgInit: primary/secondary ant 0/1
[10569.250601] RTMPFilterCalibration - can't find a valid value, loopcnt=102 stop calibratingMCS Set = ff 00 00 00 01
[10569.728357] <==== rt28xx_init, Status=0
[10569.730215] 0x1300 = 00064300
[10570.348697] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[10570.612034] RTMP_TimerListAdd: add timer obj ffffc90017a091c8!
[10570.612040] RTMP_TimerListAdd: add timer obj ffffc90017a09248!
[10570.612043] RTMP_TimerListAdd: add timer obj ffffc90017a092c8!
[10570.612047] RTMP_TimerListAdd: add timer obj ffffc90017a09148!
[10570.612051] RTMP_TimerListAdd: add timer obj ffffc90017a08fc8!
[10570.612054] RTMP_TimerListAdd: add timer obj ffffc90017a09048!
[10570.612058] RTMP_TimerListAdd: add timer obj ffffc900179d3490!
[10570.612061] RTMP_TimerListAdd: add timer obj ffffc900179c2668!
[10570.612064] RTMP_TimerListAdd: add timer obj ffffc900179c26f0!
[10570.612067] RTMP_TimerListAdd: add timer obj ffffc900179d3638!
[10570.612071] RTMP_TimerListAdd: add timer obj ffffc900179d3390!
[10570.612076] RTMP_TimerListAdd: add timer obj ffffc900179d35b0!
[10570.613437] -->RTUSBVenderReset
[10570.613561] <--RTUSBVenderReset
[10571.093569] Key2Str is Invalid key length(0) or Type(0)
[10571.093613] Key3Str is Invalid key length(0) or Type(0)
[10571.093656] Key4Str is Invalid key length(0) or Type(0)
[10571.094487] 1. Phy Mode = 5
[10571.094490] 2. Phy Mode = 5
[10571.121175] phy mode> Error! The chip does not support 5G band 5!
[10571.132678] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[10571.147175] 3. Phy Mode = 9
[10571.149676] AntCfgInit: primary/secondary ant 0/1
[10571.149677] MCS Set = ff 00 00 00 01
[10571.216695] <==== rt28xx_init, Status=0
[10571.218173] 0x1300 = 00064300
[10571.268137] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 159
[10573.198884] ===>rt_ioctl_giwscan. 15(15) BSS returned, data->length = 3238
[10575.589284] ===>rt_ioctl_giwscan. 19(19) BSS returned, data->length = 4249
[10578.587837] ===>rt_ioctl_giwscan. 21(21) BSS returned, data->length = 4693
[10581.589032] ===>rt_ioctl_giwscan. 22(22) BSS returned, data->length = 4920
[10584.589630] ===>rt_ioctl_giwscan. 23(23) BSS returned, data->length = 5129
[10587.609361] ===>rt_ioctl_giwscan. 21(21) BSS returned, data->length = 4764
[10590.598986] ===>rt_ioctl_giwscan. 21(21) BSS returned, data->length = 4654
[10593.291351] ===>rt_ioctl_giwscan. 22(22) BSS returned, data->length = 5001
[10596.600384] ===>rt_ioctl_giwscan. 22(22) BSS returned, data->length = 4924
[10599.619689] ===>rt_ioctl_giwscan. 22(22) BSS returned, data->length = 4924
[10602.628658] ===>rt_ioctl_giwscan. 19(19) BSS returned, data->length = 4270
[10605.629168] ===>rt_ioctl_giwscan. 20(20) BSS returned, data->length = 4473
[10608.629085] ===>rt_ioctl_giwscan. 20(20) BSS returned, data->length = 4493
[10611.647789] ===>rt_ioctl_giwscan. 23(23) BSS returned, data->length = 5088
[10614.650871] ===>rt_ioctl_giwscan. 22(22) BSS returned, data->length = 4849
freak@STATION:~$ sudo modprobe -v rt5370sta
freak@STATION:~$ lsmod
Module                  Size  Used by
rt5370sta             805025  1 
rt2800lib              42992  0 
rt2x00usb              11753  0 
rt2x00lib              39833  2 rt2800lib,rt2x00usb
kfifo                   9972  1 rt2x00lib
mac80211              292621  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              175295  2 rt2x00lib,mac80211
compat                  8739  3 rt2x00lib,mac80211,cfg80211
led_class               3393  2 rt2x00lib,compat
nls_iso8859_1           4657  1 
nls_cp437               6375  1 
vfat                   10954  1 
fat                    56244  1 vfat
ppp_deflate             4450  0 
zlib_deflate           21866  1 ppp_deflate
bsd_comp                5307  0 
ppp_async               8070  1 
option                 16661  2 
usb_wwan               12201  1 option
usbserial              40364  7 option,usb_wwan
usb_storage            50788  1 
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_analog    80317  1 
snd_hda_intel          26147  3 
snd_hda_codec         100919  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  3 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
nouveau               569328  2 
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    68212  1 nouveau
drm_kms_helper         32836  1 nouveau
crc_ccitt               1699  2 rt2800lib,ppp_async
drm                   206198  4 nouveau,ttm,drm_kms_helper
asus_atk0110           12987  0 
psmouse                62080  0 
snd                    64277  14 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               4910  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
i2c_algo_bit            6208  1 nouveau
intel_agp              32334  0 
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
hid_logitech           10639  0 
ff_memless              5485  1 hid_logitech
usbhid                 42030  1 hid_logitech
hid                    84710  2 hid_logitech,usbhid
ahci                   22370  4 
r8169                  42286  0 
libahci                26148  1 ahci
mii                     5261  1 r8169
pata_jmicron            2771  2 
freak@STATION:~$ clear

freak@STATION:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

ra0       Ralink STA  ESSID:"Unity0909"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-78 dBm  Noise level:-78 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

freak@STATION:~$ lsmod
Module                  Size  Used by
rt5370sta             805025  1 
rt2800lib              42992  0 
rt2x00usb              11753  0 
rt2x00lib              39833  2 rt2800lib,rt2x00usb
kfifo                   9972  1 rt2x00lib
mac80211              292621  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              175295  2 rt2x00lib,mac80211
compat                  8739  3 rt2x00lib,mac80211,cfg80211
led_class               3393  2 rt2x00lib,compat
nls_iso8859_1           4657  1 
nls_cp437               6375  1 
vfat                   10954  1 
fat                    56244  1 vfat
ppp_deflate             4450  0 
zlib_deflate           21866  1 ppp_deflate
bsd_comp                5307  0 
ppp_async               8070  1 
option                 16661  2 
usb_wwan               12201  1 option
usbserial              40364  7 option,usb_wwan
usb_storage            50788  1 
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_analog    80317  1 
snd_hda_intel          26147  3 
snd_hda_codec         100919  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  3 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
nouveau               569328  2 
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    68212  1 nouveau
drm_kms_helper         32836  1 nouveau
crc_ccitt               1699  2 rt2800lib,ppp_async
drm                   206198  4 nouveau,ttm,drm_kms_helper
asus_atk0110           12987  0 
psmouse                62080  0 
snd                    64277  14 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               4910  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
i2c_algo_bit            6208  1 nouveau
intel_agp              32334  0 
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
hid_logitech           10639  0 
ff_memless              5485  1 hid_logitech
usbhid                 42030  1 hid_logitech
hid                    84710  2 hid_logitech,usbhid
ahci                   22370  4 
r8169                  42286  0 
libahci                26148  1 ahci
mii                     5261  1 r8169
pata_jmicron            2771  2 
freak@STATION:~$ dmesg | egrep 'rt2|rt3|rt5'
[10259.352703] usbcore: registered new interface driver rt2800usb
[10270.748529] RTMPFilterCalibration - can't find a valid value, loopcnt=102 stop calibrating<==== rt28xx_init, Status=0
[10372.549332] <==== rt28xx_init, Status=0
[10439.739877] RTMPFilterCalibration - can't find a valid value, loopcnt=102 stop calibrating<==== rt28xx_init, Status=0
[10515.876444] rtusb init rt2870 --->
[10515.876453] Error: Driver 'rt2870' is already registered, aborting...
[10539.894509] usbcore: deregistering interface driver rt2800usb
[10543.216810] rtusb init rt2870 --->
[10543.216820] Error: Driver 'rt2870' is already registered, aborting...
[10565.075754] rtusb init rt2870 --->
[10565.075765] Error: Driver 'rt2870' is already registered, aborting...
[10567.198545] usbcore: deregistering interface driver rt2870
[10568.397678] rtusb init rt2870 --->
[10568.400920] usbcore: registered new interface driver rt2870
[10569.728357] <==== rt28xx_init, Status=0
[10571.216695] <==== rt28xx_init, Status=0
[11269.081518] <==== rt28xx_init, Status=0
[11270.587490] <==== rt28xx_init, Status=0
freak@STATION:~$ rfkill list
freak@STATION:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ppp0      Interface doesn't support scanning.

ra0       No scan results

```

but now its called ra0

---

### Post by praseodym on 2011-12-07
"rmmod" only unloads this specific module without its dependenccies (rt2x00usb, rt2800lib, rt2x00lib), try this:

```
sudo modprobe -rfv rt5370sta rt2x00usb rt2800lib rt2x00lib
sudo modprobe -v rt5370sta
echo "blacklist rt2870sta" | sudo tee /etc/modprobe.d/blacklist-rt2870sta.conf
```
Replug the stick, remove (not edit!) your wireless profile (because the interface name changed to ra0), create a new profile, and check again as decribed above.

---

### Post by sakalonys on 2011-12-07
```
freak@STATION:~$ ifconfig ra0 down
SIOCSIFFLAGS: Permission denied
freak@STATION:~$ sudo ifconfig ra0 down
freak@STATION:~$ sudo ifconfig ra0 up
freak@STATION:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ppp0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:22:3F:35:18:82
                    Protocol:802.11b/g
                    ESSID:"NETGEAR"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/100  Signal level=-78 dBm  Noise level=-73 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:04:0E:F8:85:29
                    Protocol:802.11b/g
                    ESSID:"FRITZ!Box Fon WLAN 7141"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/100  Signal level=-70 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:1F:3F:A6:C1:D9
                    Protocol:802.11b/g
                    ESSID:"FRITZ!Box Fon WLAN 7270"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/100  Signal level=-80 dBm  Noise level=-75 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 04 - Address: 00:1C:4A:68:13:C6
                    Protocol:802.11b/g
                    ESSID:"FRITZ!Box Fon WLAN 7113"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/100  Signal level=-80 dBm  Noise level=-75 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:26:4D:76:16:A5
                    Protocol:802.11b/g/n
                    ESSID:"Friederike"
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality=24/100  Signal level=-80 dBm  Noise level=-75 dBm
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 06 - Address: 00:15:0C:4E:E8:1C
                    Protocol:802.11b/g
                    ESSID:"Baerchen"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/100  Signal level=-70 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: 00:23:08:CE:54:BD
                    Protocol:802.11b/g/n
                    ESSID:"MichisUnglaublicheDSLVerbindung"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/100  Signal level=-80 dBm  Noise level=-75 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD130050F204104A0001101044000102103C000103
          Cell 08 - Address: 00:1D:19:45:7A:09
                    Protocol:802.11b/g
                    ESSID:"Arcor-457A31"
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality=10/100  Signal level=-86 dBm  Noise level=-81 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 09 - Address: 00:1C:4A:A1:08:AA
                    Protocol:802.11g
                    ESSID:""
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality=20/100  Signal level=-82 dBm  Noise level=-77 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: 00:1F:3F:1B:DA:1F
                    Protocol:802.11b/g
                    ESSID:"FRITZ!Box Fon WLAN 7170"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=10/100  Signal level=-86 dBm  Noise level=-81 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: 88:25:2C:80:B5:0C
                    Protocol:802.11b/g/n
                    ESSID:"WLAN-80B575"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/100  Signal level=-68 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD130050F204104A0001101044000102103C000103
          Cell 12 - Address: 00:1A:2A:58:5A:83
                    Protocol:802.11b/g
                    ESSID:"WLAN-585A36"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=15/100  Signal level=-84 dBm  Noise level=-79 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 13 - Address: 00:1C:4A:34:9E:B1
                    Protocol:802.11b/g/n
                    ESSID:"WLAN-001C4A349EB1"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/100  Signal level=-76 dBm  Noise level=-71 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 14 - Address: 00:22:B0:F2:89:1B
                    Protocol:802.11b/g
                    ESSID:"Stefan"
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality=20/100  Signal level=-82 dBm  Noise level=-77 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000101

freak@STATION:~$ sudo iwconfig ra0 essid Unity0909 key 9876543210 channel 6
freak@STATION:~$ sudo dhclient ra0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/ra0/00:0e:e8:dc:aa:9e
Sending on   LPF/ra0/00:0e:e8:dc:aa:9e
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

scan worked but still no connection

---

### Post by sakalonys on 2011-12-07
trying at the moment ... 

so step by step unplugged stick , then

```
freak@STATION:~$ sudo modprobe -rfv rt5370sta rt2x00usb rt2800lib rt2x00libsudo
rmmod /lib/modules/2.6.35-31-generic/kernel/drivers/net/wireless/rt5370sta.ko
rmmod /lib/modules/2.6.35-31-generic/updates/compat-wireless-2.6.39/rt2x00usb.ko
rmmod /lib/modules/2.6.35-31-generic/updates/compat-wireless-2.6.39/rt2800lib.ko
rmmod /lib/modules/2.6.35-31-generic/updates/compat-wireless-2.6.39/rt2x00lib.ko
rmmod /lib/modules/2.6.35-31-generic/updates/compat-wireless-2.6.39/mac80211.ko
rmmod /lib/modules/2.6.35-31-generic/updates/compat-wireless-2.6.39/cfg80211.ko
rmmod /lib/modules/2.6.35-31-generic/updates/compat-wireless-2.6.39/kfifo.ko
rmmod /lib/modules/2.6.35-31-generic/updates/compat-wireless-2.6.39/compat.ko
rmmod /lib/modules/2.6.35-31-generic/kernel/drivers/leds/led-class.ko
FATAL: Module rt2x00libsudo not found.
freak@STATION:~$ sudo modprobe -rfv rt5370sta rt2x00usb rt2800lib rt2x00lib
freak@STATION:~$ sudo modprobe -v rt5370sta
insmod /lib/modules/2.6.35-31-generic/kernel/drivers/net/wireless/rt5370sta.ko 
freak@STATION:~$ echo "blacklist rt2870sta" | sudo tee /etc/modprobe.d/blacklist-rt2870sta.conf
blacklist rt2870sta
freak@STATION:~$ 

```

done until here.

now ?

replug or first delete ? ....remove (not edit!) your wireless profile -
exactly means delete the ap details in network-manager,right ?

---

### Post by sakalonys on 2011-12-07
worked about two hours, to fix dmesg error messages, problem was RT2870STA.dat.maybe you take a look at it,not sure if i did the config right.by the way... still cant connect.

some outputs :
```
[   21.162051] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.162061] nouveau 0000:01:00.0: setting latency timer to 64
[   21.175586] rtusb init rt2870 --->
[   21.175897] 
[   21.175898] 
[   21.175899] === pAd = ffffc90010570000, size = 552480 ===
[   21.175901] 
[   21.176312] <-- RTMPAllocTxRxRingMemory, Status=0
[   21.176384] <-- RTMPAllocAdapterBlock, Status=0
[   21.185742] usbcore: registered new interface driver rt2870
[   21.215236] [drm] nouveau 0000:01:00.0: Detected an NV40 generation card (0x04b200a2)
[   21.219588] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[   21.284928] [drm] nouveau 0000:01:00.0: ... appears to be valid
[   21.284934] [drm] nouveau 0000:01:00.0: BIT BIOS found
[   21.284939] [drm] nouveau 0000:01:00.0: Bios version 05.73.22.14
[   21.284944] [drm] nouveau 0000:01:00.0: TMDS table script pointers not stubbed
[   21.284947] [drm] nouveau 0000:01:00.0: BIT table 'd' not found
[   21.284951] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 3.0
[   21.284956] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 01000300 00000028
[   21.284960] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 03000302 00000000
[   21.284964] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 04011310 00000028
[   21.284967] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 020223f1 00c0c080
[   21.284972] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x30 5 10 2
[   21.284977] [drm] nouveau 0000:01:00.0:   0: 0x00002030: type 0x30 idx 0 tag 0x08
[   21.284981] [drm] nouveau 0000:01:00.0:   1: 0x00000100: type 0x00 idx 1 tag 0xff
[   21.284985] [drm] nouveau 0000:01:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
[   21.284988] [drm] nouveau 0000:01:00.0:   3: 0x00000211: type 0x11 idx 3 tag 0xff
[   21.284992] [drm] nouveau 0000:01:00.0:   4: 0x00000213: type 0x13 idx 4 tag 0xff
[   21.285007] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xDD8D
[   21.285090] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xE3CE
[   21.401303] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xEADF
[   21.401331] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xEC5F
[   21.421849]   alloc irq_desc for 22 on node -1
[   21.421855]   alloc kstat_irqs on node -1
[   21.421868] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   21.421933]   alloc irq_desc for 46 on node -1
[   21.421936]   alloc kstat_irqs on node -1
[   21.421951] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   21.421991] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   21.460863] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xEE4D
[   21.460874] [drm] nouveau 0000:01:00.0: Detected 512MiB VRAM
[   21.511526] [TTM] Zone  kernel: Available graphics memory: 511018 kiB.
[   21.511530] [TTM] Initializing pool allocator.
[   21.515455] [drm] nouveau 0000:01:00.0: 64 MiB GART (aperture)
[   21.516842] [drm] nouveau 0000:01:00.0: Allocating FIFO number 0
[   21.521829] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 0
[   21.521842] [drm] nouveau 0000:01:00.0: Initial CRTC_OWNER is 0
[   21.521852] [drm] nouveau 0000:01:00.0: Saving VGA fonts
[   21.591622] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector
[   21.591974] [drm] nouveau 0000:01:00.0: Detected a VGA connector
[   21.592185] [drm] nouveau 0000:01:00.0: Detected a TV connector
[   21.594421] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[   21.594428] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 1)
[   21.594432] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 2)
[   21.594437] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on TV encoder (output 3)
[   21.842929] [drm] nouveau 0000:01:00.0: allocated 1280x1024 fb: 0x49000, bo ffff880028cd5800
[   21.854860] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 2)
[   21.854867] [drm] nouveau 0000:01:00.0: Output VGA-1 is running on CRTC 0 using output C
[   21.856150] Console: switching to colour frame buffer device 160x64
[   21.857338] fb0: nouveaufb frame buffer device
[   21.857341] drm: registered panic notifier
[   21.857346] Slow work thread pool: Starting up
[   21.857444] Slow work thread pool: Ready
[   21.857455] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
[   81.744001] EXT3-fs (sda1): using internal journal
[   83.245519] type=1400 audit(1323313479.170:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1003 comm="apparmor_parser"
[   83.246331] type=1400 audit(1323313479.170:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1003 comm="apparmor_parser"
[   83.246766] type=1400 audit(1323313479.170:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1003 comm="apparmor_parser"
[   83.321631] type=1400 audit(1323313479.250:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1002 comm="apparmor_parser"
[   83.584928] type=1400 audit(1323313479.510:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1018 comm="apparmor_parser"
[   83.585907] type=1400 audit(1323313479.510:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1018 comm="apparmor_parser"
[   83.588140] type=1400 audit(1323313479.510:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1009 comm="apparmor_parser"
[   83.589114] type=1400 audit(1323313479.510:15): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1009 comm="apparmor_parser"
[   83.603242] type=1400 audit(1323313479.530:16): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1023 comm="apparmor_parser"
[   83.690123] type=1400 audit(1323313479.620:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1015 comm="apparmor_parser"
[   84.042476] ppdev: user-space parallel port driver
[   84.711251] r8169 0000:03:00.0: eth0: link down
[   84.711559] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   84.744741] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[   85.005779] RTMP_TimerListAdd: add timer obj ffffc900105b91c8!
[   85.005785] RTMP_TimerListAdd: add timer obj ffffc900105b9248!
[   85.005788] RTMP_TimerListAdd: add timer obj ffffc900105b92c8!
[   85.005792] RTMP_TimerListAdd: add timer obj ffffc900105b9148!
[   85.005796] RTMP_TimerListAdd: add timer obj ffffc900105b8fc8!
[   85.005799] RTMP_TimerListAdd: add timer obj ffffc900105b9048!
[   85.005802] RTMP_TimerListAdd: add timer obj ffffc90010583490!
[   85.005806] RTMP_TimerListAdd: add timer obj ffffc90010572668!
[   85.005809] RTMP_TimerListAdd: add timer obj ffffc900105726f0!
[   85.005812] RTMP_TimerListAdd: add timer obj ffffc90010583638!
[   85.005816] RTMP_TimerListAdd: add timer obj ffffc90010583390!
[   85.005820] RTMP_TimerListAdd: add timer obj ffffc900105835b0!
[   85.007236] -->RTUSBVenderReset
[   85.007361] <--RTUSBVenderReset
[   85.525639] Key2Str is Invalid key length(0) or Type(0)
[   85.525680] Key3Str is Invalid key length(0) or Type(0)
[   85.525720] Key4Str is Invalid key length(0) or Type(0)
[   85.526430] 1. Phy Mode = 0
[   85.526434] 2. Phy Mode = 0
[   85.553866] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[   85.568114] 3. Phy Mode = 0
[   85.570616] AntCfgInit: primary/secondary ant 0/1
[   85.570618] MCS Set = 00 00 00 00 00
[   85.652389] <==== rt28xx_init, Status=0
[   85.653864] 0x1300 = 00073200
[   85.957494] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
[   85.962167] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
[   86.249872] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[   86.510822] RTMP_TimerListAdd: add timer obj ffffc900105b91c8!
[   86.510829] RTMP_TimerListAdd: add timer obj ffffc900105b9248!
[   86.510832] RTMP_TimerListAdd: add timer obj ffffc900105b92c8!
[   86.510836] RTMP_TimerListAdd: add timer obj ffffc900105b9148!
[   86.510840] RTMP_TimerListAdd: add timer obj ffffc900105b8fc8!
[   86.510843] RTMP_TimerListAdd: add timer obj ffffc900105b9048!
[   86.510847] RTMP_TimerListAdd: add timer obj ffffc90010583490!
[   86.510850] RTMP_TimerListAdd: add timer obj ffffc90010572668!
[   86.510853] RTMP_TimerListAdd: add timer obj ffffc900105726f0!
[   86.510856] RTMP_TimerListAdd: add timer obj ffffc90010583638!
[   86.510860] RTMP_TimerListAdd: add timer obj ffffc90010583390!
[   86.510865] RTMP_TimerListAdd: add timer obj ffffc900105835b0!
[   86.512365] -->RTUSBVenderReset
[   86.512489] <--RTUSBVenderReset
[   87.003833] Key2Str is Invalid key length(0) or Type(0)
[   87.003874] Key3Str is Invalid key length(0) or Type(0)
[   87.003913] Key4Str is Invalid key length(0) or Type(0)
[   87.004621] 1. Phy Mode = 0
[   87.004624] 2. Phy Mode = 0
[   87.032744] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[   87.047004] 3. Phy Mode = 0
[   87.049495] AntCfgInit: primary/secondary ant 0/1
[   87.049497] MCS Set = 00 00 00 00 00
[   87.103899] <==== rt28xx_init, Status=0
[   87.105369] 0x1300 = 00073200
[   87.464419] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 1254
[   89.107250] ===>rt_ioctl_giwscan. 17(17) BSS returned, data->length = 3630
[   91.967215] ===>rt_ioctl_giwscan. 19(19) BSS returned, data->length = 4073
[   94.978729] ===>rt_ioctl_giwscan. 21(21) BSS returned, data->length = 4603
[   98.052005] ===>rt_ioctl_giwscan. 19(19) BSS returned, data->length = 4109
[   98.052404] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=6)
[  100.967150] ===>rt_ioctl_giwscan. 18(18) BSS returned, data->length = 3849
[  103.957181] ===>rt_ioctl_giwscan. 19(19) BSS returned, data->length = 4065
[  106.948487] ===>rt_ioctl_giwscan. 19(19) BSS returned, data->length = 4144
[  109.947272] ===>rt_ioctl_giwscan. 21(21) BSS returned, data->length = 4643
[  109.950774] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=6)
[  112.947224] ===>rt_ioctl_giwscan. 21(21) BSS returned, data->length = 4597
[  115.947233] ===>rt_ioctl_giwscan. 21(21) BSS returned, data->length = 4597
[  118.947259] ===>rt_ioctl_giwscan. 19(19) BSS returned, data->length = 4225
[  120.947259] ===>rt_ioctl_giwscan. 19(19) BSS returned, data->length = 4188
[  122.948491] ===>rt_ioctl_giwscan. 19(19) BSS returned, data->length = 4094
[  122.952326] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=6)
[  125.967128] ===>rt_ioctl_giwscan. 19(19) BSS returned, data->length = 4093
[  128.957127] ===>rt_ioctl_giwscan. 18(18) BSS returned, data->length = 3961
[  130.948374] ===>rt_ioctl_giwscan. 18(18) BSS returned, data->length = 3846
[  133.948387] ===>rt_ioctl_giwscan. 17(17) BSS returned, data->length = 3658
[  133.951968] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=6)
freak@STATION:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"Unity0909"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-84 dBm  Noise level:-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

freak@STATION:~$ sudo iwlist scan
[sudo] password for freak: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:1C:4A:68:13:C6
                    Protocol:802.11b/g
                    ESSID:"FRITZ!Box Fon WLAN 7113"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/100  Signal level=-82 dBm  Noise level=-77 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:04:0E:F8:85:29
                    Protocol:802.11b/g
                    ESSID:"FRITZ!Box Fon WLAN 7141"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/100  Signal level=-74 dBm  Noise level=-69 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:22:3F:35:18:82
                    Protocol:802.11b/g
                    ESSID:"NETGEAR"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/100  Signal level=-80 dBm  Noise level=-75 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:26:4D:76:16:A5
                    Protocol:802.11b/g/n
                    ESSID:"Friederike"
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality=24/100  Signal level=-80 dBm  Noise level=-75 dBm
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 05 - Address: 00:22:B0:F2:89:1B
                    Protocol:802.11b/g
                    ESSID:"Stefan"
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality=15/100  Signal level=-84 dBm  Noise level=-79 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000101
          Cell 06 - Address: 00:15:0C:CA:E1:53
                    Protocol:802.11g
                    ESSID:"FRITZ!Box Fon WLAN 7170"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/100  Signal level=-78 dBm  Noise level=-73 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: 84:A8:E4:64:F6:52
                    Protocol:802.11b/g/n
                    ESSID:"carrera4s"
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality=15/100  Signal level=-84 dBm  Noise level=-79 dBm
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A0001101044000102104700104A5196FD5EEEC0E26EFA10AACBE602E9103C000103
          Cell 08 - Address: 00:1D:19:45:7A:09
                    Protocol:802.11b/g
                    ESSID:"Arcor-457A31"
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality=24/100  Signal level=-80 dBm  Noise level=-75 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 09 - Address: 00:1C:4A:A1:08:AA
                    Protocol:802.11g
                    ESSID:""
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality=15/100  Signal level=-84 dBm  Noise level=-79 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: 00:1A:2A:58:5A:83
                    Protocol:802.11b/g
                    ESSID:"WLAN-585A36"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=15/100  Signal level=-84 dBm  Noise level=-79 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 11 - Address: 00:1C:4A:34:9E:B1
                    Protocol:802.11b/g/n
                    ESSID:"WLAN-001C4A349EB1"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/100  Signal level=-80 dBm  Noise level=-75 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 12 - Address: 00:1A:4F:96:CE:7C
                    Protocol:802.11b/g
                    ESSID:"WLAN-001A4F96CE7C"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=10/100  Signal level=-86 dBm  Noise level=-81 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: 88:25:2C:80:B5:0C
                    Protocol:802.11b/g/n
                    ESSID:"WLAN-80B575"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/100  Signal level=-72 dBm  Noise level=-67 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD130050F204104A0001101044000102103C000103
          Cell 14 - Address: 00:15:0C:4E:E8:1C
                    Protocol:802.11b/g
                    ESSID:"Baerchen"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/100  Signal level=-74 dBm  Noise level=-69 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: 00:24:FE:A6:08:EC
                    Protocol:802.11b/g/n
                    ESSID:"Diensberg.WLAN"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=10/100  Signal level=-86 dBm  Noise level=-81 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 16 - Address: 00:1C:28:15:7A:D2
                    Protocol:802.11b/g
                    ESSID:"ALICE-WLAN10"
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality=20/100  Signal level=-82 dBm  Noise level=-77 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: 00:1F:3F:1B:DA:1F
                    Protocol:802.11b/g
                    ESSID:"FRITZ!Box Fon WLAN 7170"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=10/100  Signal level=-86 dBm  Noise level=-81 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: 00:1F:33:4D:C4:4E
                    Protocol:802.11b/g
                    ESSID:"Unity0909"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/100  Signal level=-78 dBm  Noise level=-73 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 19 - Address: 00:1E:2A:D8:C8:64
                    Protocol:802.11b/g
                    ESSID:"chiko"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/100  Signal level=-80 dBm  Noise level=-75 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: 00:1F:3F:A6:C1:D9
                    Protocol:802.11b/g
                    ESSID:"FRITZ!Box Fon WLAN 7270"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/100  Signal level=-82 dBm  Noise level=-77 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s

freak@STATION:~$ lsmod
Module                  Size  Used by
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_analog    80317  1 
snd_hda_intel          26147  1 
snd_hda_codec         100919  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
rt5370sta             805025  1 
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
nouveau               569328  2 
snd                    64277  11 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    68212  1 nouveau
asus_atk0110           12987  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
drm_kms_helper         32836  1 nouveau
psmouse                62080  0 
serio_raw               4910  0 
intel_agp              32334  0 
drm                   206198  4 nouveau,ttm,drm_kms_helper
lp                     10201  0 
i2c_algo_bit            6208  1 nouveau
parport                37032  3 parport_pc,ppdev,lp
hid_logitech           10639  0 
ff_memless              5485  1 hid_logitech
usbhid                 42030  1 hid_logitech
hid                    84710  2 hid_logitech,usbhid
ahci                   22370  1 
libahci                26148  1 ahci
r8169                  42286  0 
pata_jmicron            2771  1 
mii                     5261  1 r8169
```


and my RT2870STA.dat

```
#The word of "Default" must not be removed
Default
CountryRegion=1
CountryRegionABand=7
CountryCode=DE
SSID=Unity0909
NetworkType=Infra
WirelessMode=0
Channel=11
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
WmmCapable=0
AckPolicy=0;0;0;0
AuthMode=WEPAUTO
EncrypType=WEP
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=9876543210
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
FastRoaming=0
RoamThreshold=70
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=1
HT_MpduDensity=4
HT_BW=1
HT_AutoBA=1
HT_BADecline=0
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
EthConvertMode=
EthCloneMac=
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
MeshId=MESH
MeshAutoLink=1
MeshAuthMode=OPEN
MeshEncrypType=NONE
MeshWPAKEY=
MeshDefaultkey=1
MeshWEPKEY=9876543210
CarrierDetect=0
```

---

### Post by sakalonys on 2011-12-07
is there a way that maybe someone outthere, got a ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter, stable working on one of the million linux dists.?? If so - Would it be possible to get his complete system like a livecd or a compiled kernel with modules,drivers and all needed things?

PLS HELP ME GUYS

---

### Post by praseodym on 2011-12-08
Try WPA2-AES encryption in your router with these settings:

[http://wiki.ubuntuusers.de/wlan/ralink#RT2860STA-und-Draft-N](http://wiki.ubuntuusers.de/wlan/ralink#RT2860STA-und-Draft-N)

Router firmware is up-to-date? MAC-address filter is off? BTW: your channel is 6 not 11 in the rt2870sta.dat

---

