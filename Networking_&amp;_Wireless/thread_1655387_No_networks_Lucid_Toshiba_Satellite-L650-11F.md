---
title: "No networks Lucid Toshiba Satellite-L650-11F"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by Kylen on 2010-12-29
Hello
I just installed lucid in my laptop (Toshiba Satellite L-650) and no networks are available. I cannot connect to the wireless network. Therefore I tried to connect with a cable directly from the router (and this works in a different computer with windows), but no networks were available either. Here is some information.

Output of sudo lspci | grep -i 'net' 
02:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
03:00.0 Network controller: Broadcom Corporation Device 4727 (rev 
01)

Output of lsmod:
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
binfmt_misc             6587  1 
rfcomm                 33421  4 
ppdev                   5259  0 
sco                     7885  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
joydev                  8708  0 
snd_hda_codec_atihdmi     2367  1 
snd_hda_intel          21941  2 
snd_seq_dummy           1338  0 
snd_hda_codec          74201  2 snd_hda_codec_atihdmi,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               56990  0 
fbcon                  35102  71 
videodev               34361  1 uvcvideo
tileblit                2031  1 fbcon
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
intel_agp              24119  0 
btusb                  10925  2 
v4l1_compat            13251  2 uvcvideo,videodev
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
video                  17375  0 
output                  1871  1 video
snd                    54148  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                31724  1 intel_agp
psmouse                63245  0 
serio_raw               3978  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            39425  1 
ahci                   32200  2 

Ouptut of cat /proc/modules
nls_iso8859_1 3249 1 - Live 0xf85fb000
nls_cp437 4919 1 - Live 0xf85a5000
vfat 8933 1 - Live 0xf80e9000
fat 47767 1 vfat, Live 0xf856c000
binfmt_misc 6587 1 - Live 0xf8068000
rfcomm 33421 4 - Live 0xf8666000
ppdev 5259 0 - Live 0xf861d000
sco 7885 2 - Live 0xf859e000
bridge 45582 0 - Live 0xf8590000
stp 1655 1 bridge, Live 0xf807c000
bnep 9436 2 - Live 0xf80d4000
l2cap 30624 16 rfcomm,bnep, Live 0xf857a000
joydev 8708 0 - Live 0xf802d000
snd_hda_codec_atihdmi 2367 1 - Live 0xf8065000
snd_hda_intel 21941 2 - Live 0xf867b000
snd_seq_dummy 1338 0 - Live 0xf865d000
snd_hda_codec 74201 2 snd_hda_codec_atihdmi,snd_hda_intel, Live 0xf8633000
snd_hwdep 5412 1 snd_hda_codec, Live 0xf8613000
snd_pcm_oss 35308 0 - Live 0xf85f0000
snd_mixer_oss 13746 1 snd_pcm_oss, Live 0xf85c5000
snd_pcm 70662 3 snd_hda_intel,snd_hda_codec,snd_pcm_oss, Live 0xf85b1000
snd_seq_oss 26726 0 - Live 0xf810b000
snd_seq_midi 4557 0 - Live 0xf8090000
snd_rawmidi 19056 1 snd_seq_midi, Live 0xf80bc000
snd_seq_midi_event 6003 2 snd_seq_oss,snd_seq_midi, Live 0xf8061000
snd_seq 47263 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event, Live 0xf872e000
uvcvideo 56990 0 - Live 0xf86e0000
fbcon 35102 71 - Live 0xf86b8000
videodev 34361 1 uvcvideo, Live 0xf869c000
tileblit 2031 1 fbcon, Live 0xf8688000
snd_timer 19098 2 snd_pcm,snd_seq, Live 0xf8674000
snd_seq_device 5700 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq, Live 0xf8662000
intel_agp 24119 0 - Live 0xf8651000
btusb 10925 2 - Live 0xf860e000
v4l1_compat 13251 2 uvcvideo,videodev, Live 0xf85fd000
bluetooth 49892 9 rfcomm,sco,bnep,l2cap,btusb, Live 0xf85ca000
font 7557 1 fbcon, Live 0xf85ad000
bitblit 4707 1 fbcon, Live 0xf85a1000
softcursor 1189 1 bitblit, Live 0xf80ee000
video 17375 0 - Live 0xf80dc000
output 1871 1 video, Live 0xf8070000
snd 54148 15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xf80f6000
agpgart 31724 1 intel_agp, Live 0xf8094000
psmouse 63245 0 - Live 0xf80aa000
serio_raw 3978 0 - Live 0xf8075000
vga16fb 11385 1 - Live 0xf8115000
vgastate 8961 1 vga16fb, Live 0xf8106000
soundcore 6620 1 snd, Live 0xf80f2000
snd_page_alloc 7076 2 snd_hda_intel,snd_pcm, Live 0xf80e5000
lp 7028 0 - Live 0xf80d8000
parport 32635 2 ppdev,lp, Live 0xf80c3000
usb_storage 39425 1 - Live 0xf809e000
ahci 32200 2 - Live 0xf8021000

---

### Post by PatchesTheCaveman on 2010-12-29
Hi Kylen,

Please plug in your Ethernet connection and run the following command and post the results:
```
ifconfig -a
```

We'll try and get that working first since that's usually simpler than Wireless connections, especially with Broadcom devices.

Thank you!

---

### Post by Kylen on 2010-12-29
Hi
Thank you.
Here is the output of ifconfig -a:
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6152 (6.1 KB)  TX bytes:6152 (6.1 KB)

pan0      Link encap:Ethernet  HWaddr 7e:0a:f1:e8:76:99  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by PatchesTheCaveman on 2010-12-29
Unfortunately the driver for your Ethernet card is not included with Ubuntu.  To install it, follow the instructions in this post:
[http://ubuntuforums.org/showpost.php?p=9446984&postcount=6](http://ubuntuforums.org/showpost.php?p=9446984&postcount=6)

Let us know if you have any trouble.

---

### Post by Kylen on 2010-12-29
It worked. Thank you!
With ethernet working, I simply went to System->Hardware Drivers and activated the Broadcom STA wireless driver, and now wireless works too.

---

### Post by bonde49 on 2011-03-10
> **PatchesTheCaveman said:**
> Unfortunately the driver for your Ethernet card is not included with Ubuntu.  To install it, follow the instructions in this post:
[http://ubuntuforums.org/showpost.php?p=9446984&postcount=6](http://ubuntuforums.org/showpost.php?p=9446984&postcount=6)

Let us know if you have any trouble.
Hey.Im having a similar problem with a toshiba portege r700 / satelite r630.

The netcard is a Broadcom BCM94313 (some places just refered to as bcm4313)

I've tried the tutorial from the link, i seemed like it made the installation but when finished, the machine wouldn't recognise the netcard. I am getting really frustrated. I can not get on the web on lan nor on wlan.. please help

---

