---
title: "ASUS N13 dongle at ubuntu 10.10 (kernel 35-22)"
date: 2011-11-13
forum: Networking &amp; Wireless
---

### Post by DarksonDAP on 2011-11-13
Hello everybody!!

First of all, congratulations for your work and your community, i can surely say i'm impressed!!

Secondly, i hope you can help me solve a problem i face 

I own a toshiba Sattelite A300 running ubuntu 10.10 (kernel 35-22), which i have abandoned for a little while. 3 days ago, when i booted up the computer again, there was NO wireless adaptor shown in the network manager. Afraid for the worst, i started a terminal and typed iwconfig and ifconfig to see if the card was still there. To my dismay, the internal network card was not there, proving it has broken down. The WORST thing is that about 2 months ago the ethernet port broke down too. (stupid laptop i guess)

Long story short, i bought an ASUS N-13 usb receiver, and borrowed my girlfriend's laptop for surfing the net, till i set my dongle up (my gf's laptop runs ubuntu 10.10 kernel 35-30).

No matter what i tried, how many tutorials i have read, i still haven't got the dongle to work. The good news is that the dongle is recongnized with the lsusb command, and the bad news is that my laptop doesn't have installed the built-essentials, so i could build the driver

i tried blacklisting rt2800usb with no luck(if i did it right).

As my dear friend chili55 suggested, i opened a terminal and typed the following:

lsmod | grep rt2
cat /etc/modprobe.d/blacklist.conf | tail -n5
dmesg | grep rt2

the result was this:


> darksondap@darksondap:~$ lsmod | grep rt2
rt2870sta                            405890 0
crc_ccitt                                       1351  1 rt2870sta
darksondap@darksondap:~$ cat /etc/modprobe.d/blacklist.conf | tail -n5

blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
darksondap@darksondap:~$ dmesg | grep rt2
[   17.861281] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned
[   17.861312] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned
[   17.867792]  rt2870sta: module is from the staging directory, the quality is unknown, you have been warned
[   17.869992] usbcore: registered new interface driver rt2870
[   17.872130]  rt2870sta: module is from the staging directory, the quality is unknown, you have been warned
[   17.878911]  rt2870sta: module is from the staging directory, the quality is unknown, you have been warned

---

### Post by chili555 on 2011-11-13
Your readings look perfect so far. Let's see:```
lsusb
iwconfig
```Thanks.

---

### Post by praseodym on 2011-11-13
Hi,

do you still have the installation CD/DVD? If yes, insert it, add it to your software sources and install **build-essential** from there. You also need the suitable kernel-headers for building, so please show additionally

```
uname -a
rfkill list
iwconfig
```
We can post the links to the .deb packages for them

---

### Post by chili555 on 2011-11-13
> If yes, insert it, add it to your software sources and install build-essential from there. You also need the suitable kernel-headers for building, so please show additionallyI don't believe he has downloaded a file to compile and nor do I believe he needs to.

---

### Post by DarksonDAP on 2011-11-14
> **chili555 said:**
> Your readings look perfect so far. Let's see:```
lsusb
iwconfig
```Thanks.


darksondap@darksondap:~$  lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 046d:c05a Logitech, Inc.
Bus 004 Device 002: ID 050d:0012 Belkin Components F8T012 BlueTooth Adapter
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c31c  Logitech, Inc.
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:8204  Hewlett Packard Printing Support
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0b05:1784 ASUSTek Computer, Inc. 902.11n Network Adapter
Bus 001 Device 004: ID 046d:0825 Logitech, Inc.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

darksondap@darksondap:~$ iwconfig
lo no wireless extensions
eth0 no wireless extensions

---

### Post by DarksonDAP on 2011-11-14
> **praseodym said:**
> Hi,

do you still have the installation CD/DVD? If yes, insert it, add it to your software sources and install **build-essential** from there.


unfortunately i don't have the CD anymore

---

### Post by praseodym on 2011-11-14
Ok, add the device ID to the module rt2870sta:

```
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
```This is [COLOR="Red"]one[/COLOR] line, you better copy/paste it! After that reload the driver
```
sudo modprobe -rfv rt2870sta
sudo modprobe -v rt2870sta
```
and replug the stick. Check:

```
lsmod
iwconfig
sudo iwlist scan
```

---

### Post by chili555 on 2011-11-14
> ID [COLOR="Red"]0b05:1784[/COLOR] ASUSTek Computer, Inc. 902.11n Network Adapterrt2870sta is correct for your device:> $ modinfo rt2870sta | grep 1784
alias:          usb:v[COLOR="Red"]0B05[/COLOR]p[COLOR="Red"]1784[/COLOR]d*dc*dsc*dp*ic*isc*ip*The module is loading and competing modules are properly blacklisted. I hope we can query the system logs and see what's incorrect. Please post:```
dmesg | grep 1784
sudo cat /var/log/syslog | grep -i rt2
```If the output is sparse, also check:```
sudo cat /var/log/syslog.1 | grep -i rt2
```> Ok, add the device ID to the module rt2870sta:That's not necessary; it's already included.

---

### Post by praseodym on 2011-11-14
Thanks chili555,

I am using Lucid, there the driver lacks this ID.

@ DarksonDAP: Install the backported modules and the latest firmware for this driver. Please show

```
uname -a
```

and I can give you the links to the .deb packages

---

### Post by DarksonDAP on 2011-11-15
> **chili555 said:**
>  Please post:```
dmesg | grep 1784
sudo cat /var/log/syslog | grep -i rt2
```.

darksondap@darksondap:~$ dmesg | grep 1784
darksondap@darksondap:~$ sudo cat /var/log/syslog | grep -i rt2
Nov 14 21:51:35 darksondap kernel: [  17.681583] rt2870sta module is from the staging directory, the quality is unknown, you have been warned
Nov 14 21:51:35 darksondap kernel: [  17.684256] rt2870sta module is from the staging directory, the quality is unknown, you have been warned
Nov 14 21:51:35 darksondap kernel: [  17.687437] rt2870sta module is from the staging directory, the quality is unknown, you have been warned
Nov 14 21:51:35 darksondap kernel: [  17.691964] usbcore: registered new interface driver rt2870
Nov 14 21:51:35 darksondap kernel: [  17.692201] rt2870sta module is from the staging directory, the quality is unknown, you have been warned
Nov 14 21:51:35 darksondap kernel: [  17.695362] rt2870sta module is from the staging directory, the quality is unknown, you have been warned
Nov 14 21:51:35 darksondap kernel: [  17.700407] rt2870sta module is from the staging directory, the quality is unknown, you have been warned

---

### Post by DarksonDAP on 2011-11-16
bump

---

### Post by praseodym on 2011-11-16
```
uname -a
lsmod
cat /etc/modprobe.d/rt2870sta.conf
cat /etc/Wireless/RT2870STA/RT2870STA.dat
iwconfig
```

please

---

### Post by DarksonDAP on 2011-11-16
ok ok just a second :)

darksondap@darksondap:~$ uname -a
Linux darksondap 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux
darksondap@darksondap:~$ lsmod
Module                  Size  Used by
hidp                   11664  0 
saa7134_alsa           10412  1 
rfcomm                 33811  4 
binfmt_misc             6599  1 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  17 hidp,rfcomm,bnep
joydev                  8735  0 
tda827x                 9252  1 
usbhid                 36882  0 
hid                    67742  2 hidp,usbhid
tda8290                12538  1 
tuner                  20578  1 
rc_asus_pc39            1024  0 
snd_usb_audio          86704  1 
snd_usbmidi_lib        17413  1 snd_usb_audio
snd_hda_codec_atihdmi     2411  1 
btusb                  10969  2 
uvcvideo               55847  0 
usblp                  10651  0 
bluetooth              50500  10 hidp,rfcomm,sco,bnep,l2cap,btusb
rt2870sta             405890  0 
snd_hda_codec_via      51755  1 
ir_lirc_codec           3092  0 
lirc_dev                9393  1 ir_lirc_codec
ir_sony_decoder         1889  0 
ir_jvc_decoder          1950  0 
fglrx                2252513  87 
saa7134               148613  1 saa7134_alsa
ir_rc6_decoder          2334  0 
ppdev                   5556  0 
ir_rc5_decoder          1950  0 
v4l2_common            17329  2 tuner,saa7134
snd_hda_intel          22107  2 
snd_hda_codec          87552  3 snd_hda_codec_atihdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep               5040  2 snd_usb_audio,snd_hda_codec
snd_pcm                71475  4 saa7134_alsa,snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                59033  0 
ir_nec_decoder          2014  0 
videodev               43098  4 tuner,uvcvideo,saa7134,v4l2_common
v4l1_compat            13359  2 uvcvideo,videodev
videobuf_dma_sg         9806  2 saa7134_alsa,saa7134
videobuf_core          16907  2 saa7134,videobuf_dma_sg
parport_pc             26058  1 
serio_raw               4022  0 
asus_atk0110           11423  0 
snd                    49006  20 saa7134_alsa,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_common               5167  1 saa7134
intel_agp              26360  0 
ir_core                14654  10 rc_asus_pc39,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,saa7134,ir_rc5_decoder,ir_nec_decoder,ir_common
tveeprom               11178  1 saa7134
led_class               2633  0 
soundcore                880  1 snd
crc_ccitt               1351  1 rt2870sta
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
agpgart                32011  2 fglrx,intel_agp
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
floppy                 54311  0 
r8169                  36489  0 
mii                     4425  1 r8169
darksondap@darksondap:~$ cat /etc/modprobe.d/rt2870sta.conf
cat: /etc/modprobe.d/rt2870sta.conf: there is no such file or directory
darksondap@darksondap:~$ cat /etc/Wireless/RT2870STA/RT2870STA.dat
cat: /etc/Wireless/RT2870STA/RT2870STA.dat: there is no such file or directory

---

### Post by praseodym on 2011-11-16
Did you execute the first command from #7? Reboot after that

---

### Post by DarksonDAP on 2011-11-17
i did the following

> echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf

sudo modprobe -rfv rt2870sta
sudo modprobe -v rt2870sta

and replug the stick.and IT WORKED!!!!!!! :popcorn::guitar: (i haven't rebooted yet though)

i'd like to thank both chili555 and especially you for your interest and your help!!

---

### Post by DarksonDAP on 2011-11-17
two last questions

first,does the adapter work at -n speeds or do i need to do anything additional in order to?

and second, if i upgrade to a newer kernel will the driver remain as is or i must do everything again?

---

### Post by praseodym on 2011-11-17
1.) You should adjust the file

```
gksu gedit /etc/Wireless/RT2870STA/RT2870STA.dat
```
to your country code, ESSID wireless key, etc. At least the following lines:

[http://wiki.ubuntuusers.de/wlan/ralink#RT2860STA-und-Draft-N](http://wiki.ubuntuusers.de/wlan/ralink#RT2860STA-und-Draft-N)

(grey box, for Germany there). Maybe install the package **linux-firmware**, too.

2.) The file **/etc/modprobe.d/rt2870sta.conf** works automatically for kernels until 2.6.38 (Natty, 11.04) because both modules rt2870sta and rt2800usb are present. In kernel 3.x the module **rt2870sta** is _completely_ replaced by **rt2800usb**. We'll see then, but you'll find some similar workarounds for that module to add the device ID.

---

