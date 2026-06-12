---
title: "wifi connection interrupted after a few seconds"
date: 2010-08-22
forum: Networking &amp; Wireless
---

### Post by gennarinux on 2010-08-22
Hi there,

I have installed ubuntu 10.04 on a new laptop siemens xi3650.
I have Vista installed on it, and it works perfectly.

On Ubuntu the wifi connection stops after a few seconds, and it wont reconnect until I restart the pc.
The only mean I have to connect to internet is vie ethernet on ubuntu, or ethernet or wifi with vista.

here is the results of the OS information:

```

genni@genni-laptop:~$ uname -r -m
2.6.32-21-generic x86_64
```and the result of commands related to the network manager and the wifi connection.
lsusb 
```

genni@genni-laptop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 04b3:310c IBM Corp. Wheel Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1934:0702  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0167 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 046d:09bc Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
genni@genni-laptop:~$ 


```lsmod 
```

genni@genni-laptop:~$ lsmod
Module                  Size  Used by
rfcomm                 40329  4 
binfmt_misc             7960  1 
ppdev                   6375  0 
sco                     9617  2 
bridge                 53152  0 
stp                     2171  1 bridge
bnep                   11820  2 
l2cap                  34774  16 rfcomm,bnep
snd_hda_codec_realtek   278890  1 
joydev                 11072  0 
arc4                    1473  2 
snd_hda_intel          25645  2 
snd_hda_codec          85727  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
fbcon                  39270  71 
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwlagn                121577  0 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
vga16fb                12757  1 
vgastate                9857  1 vga16fb
iwlcore               124955  1 iwlagn
led_class               3732  1 iwlcore
i915                  317872  2 
snd                    70978  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              238128  2 iwlagn,iwlcore
nouveau               515131  0 
uvcvideo               62403  0 
soundcore               8052  1 snd
lp                      9336  0 
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
btusb                  12969  2 
bluetooth              58621  9 rfcomm,sco,bnep,l2cap,btusb
lirc_mceusb            14054  0 
lirc_dev               11302  1 lirc_mceusb
cfg80211              148386  3 iwlagn,iwlcore,mac80211
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
psmouse                64608  0 
serio_raw               4918  0 
ttm                    60815  1 nouveau
drm_kms_helper         30742  2 i915,nouveau
intel_agp              29225  2 i915
drm                   198770  6 i915,nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  2 i915,nouveau
video                  20623  1 i915
output                  2503  1 video
parport                37160  2 ppdev,lp
usbhid                 40988  0 
hid                    83376  1 usbhid
usb_storage            49833  0 
ohci1394               30260  0 
ieee1394               94675  1 ohci1394
e1000e                136205  0 
ahci                   37646  2 
genni@genni-laptop:~$ 


```lspci 
```

 genni@genni-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LF Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GT] (rev a1)
04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
05:04.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
genni@genni-laptop:~$
 
```iwconfig 
```

 genni@genni-laptop:~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Alice-36243285"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 5C:33:8E:14:C9:55   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=37/70  Signal level=-73 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

genni@genni-laptop:~$ 
 
```ifconfig 
```

 genni@genni-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:0b:4f:68:e1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:f3800000-f3820000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2960 (2.9 KB)  TX bytes:2960 (2.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:5d:2f:7b:66  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:5dff:fe2f:7b66/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1556 (1.5 KB)  TX bytes:5109 (5.1 KB)

genni@genni-laptop:~$ 
 
```As possible solution o the problem I tried installing the linux backport module
```

 sudo apt-get install linux-backports-modules-wireless-lucid-generic
 
``` and as it didn't work, i removed it with the purge command.

I also have upgraded the OS to the-24 version of the kernel, but I am still suffering a very ubstable wifi connection, If I can say so, as the connection DON'T GO OFF, I am ALWAYS CONNECTED, BUT UNABLE TO SURF THE INTERNET, NOR VIA BROWSER OR BY OTHER MEANS.

I have tried editing the file /etc/sysctl.conf like this
```

 sudo gedit /etc/sysctl.conf

(added these two lines)
net.ipv4.tcp_window_scaling = 0
net.ipv4.tcp_ecn= 0

(uncommented the line:)
net.ipv4.tcp_syncookies = 1
 
```but nothing.


My ubuntu wifi connection is still a pain in the a..


I think it could be a common problem, as in italy people in my situation, with TELECOM ITALIA as service provider and ubuntu 10.04, are suffering problems with their wifi connection.


Is there someone who knows what it could be, and how to solve it? many thanks for your help.

genni

---

### Post by gennarinux on 2010-08-23
Just to be more precise, the hardware works well with Winzozz Vista, and works also with Ubuntu, I get connected and I am able to surf the internet but only for a few seconds, after that.. no surfing, but connection still established, the connection don't get lost.

any idea?

---

### Post by MAXieOne on 2010-10-26
Hello,

I have the exact same symptoms. Fist it connects and stays connected but in reality only works for the few 1 to 4 seconds, and after that the traffic goes silent. If I keep refreshing a web page it menages to send and receive some more traffic for about another second but only after 1 minute or so. 

Reconnecting makes it work again right from start for another 1 to 4 seconds when it get silent again.

It seems that it is very picky about the signal strength and I think the drop outs do not occur if you have more then 2-3 bars.  In Windows 7 it works perfect even at 1 bar. Kubuntu has the exact same problem.

I have a rt75usb wireless card.



I am a brand new user to Ubuntu and I really really want to use it and support it because i believe in a future where all software (and maybe more stuff)  will be free and donation based.

If more info is needed instruct me how to get it and I will post it.  Thank you.

---

### Post by sikshady on 2011-03-28
Hi, I got the same problem and it's really annoying.
I have a Dell xps 1330 with ubuntu 10.10 x64 and Intel 4965 agn wifi card.
On win7 everything works great, did u solve it somehow?
thanks

---

### Post by lordnemo on 2011-05-08
i have a similar problem, i'm running lubuntu 11.04 on a Dell Dimension 8100 with pentium 4 and 256 MB of ram. i just got my wireless card running but when i connect to the internet i can only load a single page before it prompts me for my WPA again, then it will continue to try and reconnect over and over until i tell it to stop. i can't make a connection until i reboot and then the process starts all over again.

this looks like a common problem, is there any fix for it?

---

### Post by sikshady on 2011-05-08
> **lordnemo said:**
> i have a similar problem, i'm running lubuntu 11.04 on a Dell Dimension 8100 with pentium 4 and 256 MB of ram. i just got my wireless card running but when i connect to the internet i can only load a single page before it prompts me for my WPA again, then it will continue to try and reconnect over and over until i tell it to stop. i can't make a connection until i reboot and then the process starts all over again.

this looks like a common problem, is there any fix for it?
I solved using these 2 files [http://www.mediafire.com/?d4cc9i6zuqq3i1w](http://www.mediafire.com/?d4cc9i6zuqq3i1w) instead of the ones in /lib/firmware/

---

### Post by lordnemo on 2011-05-08
> **sikshady said:**
> I solved using these 2 files [http://www.mediafire.com/?d4cc9i6zuqq3i1w](http://www.mediafire.com/?d4cc9i6zuqq3i1w) instead of the ones in /lib/firmware/

The links no good, mediafire has been having issues, is there a mirror?

---

### Post by sikshady on 2011-05-08
> **lordnemo said:**
> The links no good, mediafire has been having issues, is there a mirror?
tried now and it works

---

### Post by lordnemo on 2011-05-08
i'm still having trouble, mediafire isn't working for me today, is there any other site you could use?
to clarify the problem, media fire loads for me just fine but when i click the download link it doesn't work, it just relaods the page. if you could put it in hotfile or rapidshare, or anything else really, then that would be great.

---

### Post by lordnemo on 2011-05-10
alright after much digging and dead ends i found this thread:
[ubuntuforums.org/showthread.php?t=1656556]("http://ubuntuforums.org/ubuntuforums.org/showthread.php?t=1656556")
cleared the problem right up thanks to everyone who tried to help.

---

