---
title: "Unable to connect using Qualcomm Gobi 2000 on thinkpad t410"
date: 2011-03-29
forum: Networking &amp; Wireless
---

### Post by zorrak on 2011-03-29
Hello, 
I have a thinkpad t410 with a Gobi 2000 3G adapter, using kubuntu 10.10 with backports.
in Ubuntu 10.10 I can connect just fine using the steps described here: [http://ubuntuforums.org/showthread.php?t=1593581](http://ubuntuforums.org/showthread.php?t=1593581)
I  tried the same steps in Kubuntu 10.10 just after a fresh install, tried  it after adding the backports ppa and upgrading to the latest kde but I  haven't had any luck. The modem is recognised, I can set up a  connection but it just won't connect.
Any help is highly appreciated.

Thanks

---

### Post by zorrak on 2011-04-02
Just bumping this one a bit in hope for some help:P

---

### Post by verderben on 2011-08-23
Same Problem here on an Edge13 with ubuntu - modem is activated - connection set up (works with same settings over bluetooth tethering), but I get no connection with the gobi.

Would be great to get some futher information 


I followed the instructions on [http://www.thinkwiki.org/wiki/Qualcomm_Gobi_2000](http://www.thinkwiki.org/wiki/Qualcomm_Gobi_2000)
the checksums match to UMTS and 6 (which means generic)

```
uname -a
Linux ThinkPad-Edge 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

``````
lsusb
Bus 002 Device 005: ID 05c6:9205 Qualcomm, Inc. 
```Syslog:
Aug 24 00:00:03 ThinkPad-Edge NetworkManager[666]: <info> Activation (ttyUSB1) starting connection 'blau.de Vorgabe 2'
Aug 24 00:00:03 ThinkPad-Edge NetworkManager[666]: <info> (ttyUSB1): device state change: 3 -> 4 (reason 0)
Aug 24 00:00:03 ThinkPad-Edge NetworkManager[666]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) scheduled...
Aug 24 00:00:03 ThinkPad-Edge NetworkManager[666]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) started...
Aug 24 00:00:03 ThinkPad-Edge NetworkManager[666]: <info> (ttyUSB1): device state change: 4 -> 6 (reason 0)
Aug 24 00:00:03 ThinkPad-Edge NetworkManager[666]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) complete.
Aug 24 00:00:04 ThinkPad-Edge NetworkManager[666]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) scheduled...
Aug 24 00:00:04 ThinkPad-Edge NetworkManager[666]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) started...
Aug 24 00:00:04 ThinkPad-Edge NetworkManager[666]: <info> (ttyUSB1): device state change: 6 -> 4 (reason 0)
Aug 24 00:00:04 ThinkPad-Edge NetworkManager[666]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) complete.
Aug 24 00:01:04 ThinkPad-Edge NetworkManager[666]: <warn> GSM connection failed: (32) Network timeout
Aug 24 00:01:04 ThinkPad-Edge NetworkManager[666]: <info> (ttyUSB1): device state change: 4 -> 9 (reason 1)
Aug 24 00:01:04 ThinkPad-Edge NetworkManager[666]: <info> Marking connection 'blau.de Vorgabe 2' invalid.
Aug 24 00:01:04 ThinkPad-Edge NetworkManager[666]: <warn> Activation (ttyUSB1) failed.
Aug 24 00:01:04 ThinkPad-Edge NetworkManager[666]: <info> (ttyUSB1): device state change: 9 -> 3 (reason 0)
Aug 24 00:01:04 ThinkPad-Edge NetworkManager[666]: <info> (ttyUSB1): deactivating device (reason: 0).

---

### Post by praseodym on 2011-08-23
You may try [this]("https://launchpad.net/~linrunner/+archive/thinkpad-extras") PPA:

```
sudo add-apt-repository ppa:linrunner/thinkpad-extras
sudo apt-get update
```
After that install "gobi-loader" via synaptic.

Edit: Sorry, no kernel for natty there. Just try gobi-loader-tp

---

### Post by verderben on 2011-08-23
Well thanks for the tip, but I'm already using gobi-loader-tp

and the modem is recognized by networkmanager :(

---

### Post by praseodym on 2011-08-24
Some errors?

```
dmesg | egrep 'firm|gobi|error|fail'
```

---

### Post by verderben on 2011-08-24
Doesn't seem so

```
dmesg | egrep 'firm|gobi|error|fail'
[    9.809147] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    9.912262] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: errors=remount-ro
[   10.487912] thinkpad_acpi: asked for hotkey mask 0x04018070, but firmware forced it to 0x00018070
[   10.502667] iwlagn 0000:03:00.0: loaded firmware version 128.50.3.1 build 13488
[   11.116363] usb 1-1.6: device descriptor read/all, error -32
[   13.752945] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=15
[   13.758474] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=15
[   17.765903] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[  565.838395] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=15
[  566.005319] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=15
[  592.475227] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=15
[  592.683699] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=15
[  599.673732] usb 2-1.6: device firmware changed
[  606.050620] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=15
[  606.211082] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=15
[  631.998674] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=60
[  632.265435] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=60
[  746.526483] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=15
[  746.913833] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=15
[ 7616.759986] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[ 7616.760001] iwlagn 0000:03:00.0: Loaded firmware version: 128.50.3.1 build 13488
[ 7648.817044] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=15
[ 7649.269803] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=15
[ 7654.703561] usb 2-1.6: device firmware changed
[ 7661.950050] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=15
[ 7662.795362] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=15
[ 7863.315403] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[ 7863.315415] iwlagn 0000:03:00.0: Loaded firmware version: 128.50.3.1 build 13488
[ 7863.358774] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[ 7863.358780] iwlagn 0000:03:00.0: Loaded firmware version: 128.50.3.1 build 13488
[ 7893.400015] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[ 7893.400026] iwlagn 0000:03:00.0: Loaded firmware version: 128.50.3.1 build 13488
[ 9466.463898] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[ 9466.463910] iwlagn 0000:03:00.0: Loaded firmware version: 128.50.3.1 build 13488
[ 9494.953669] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[ 9494.953676] iwlagn 0000:03:00.0: Loaded firmware version: 128.50.3.1 build 13488
[ 9500.061686] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[ 9500.061694] iwlagn 0000:03:00.0: Loaded firmware version: 128.50.3.1 build 13488

```

---

### Post by praseodym on 2011-08-24
Can you show

```

usb-devices
lsmod

```

---

### Post by verderben on 2011-08-24
```
usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.38-11-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=02 Port=03 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0bda ProdID=0158 Rev=58.88
S:  Manufacturer=Generic
S:  Product=USB2.0-CRW
S:  SerialNumber=20071114173400000
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.38-11-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=02 Prnt=02 Port=03 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=17ef ProdID=4811 Rev=08.01
S:  Manufacturer=SuYin
S:  Product=Integrated Camera
S:  SerialNumber=CN2015-R877-OV02-VL-R08.00.01
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=200mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=02 Prnt=02 Port=05 Cnt=02 Dev#= 11 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=05c6 ProdID=9205 Rev=00.02
S:  Manufacturer=Qualcomm Incorporated
S:  Product=Qualcomm Gobi 2000
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=qcserial
I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=qcserial
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=qcserial

``````
lsmod
Module                  Size  Used by
ppp_deflate            12990  0 
zlib_deflate           27074  1 ppp_deflate
bsd_comp               12913  0 
ppp_async              17540  0 
crc_ccitt              12667  1 ppp_async
cryptd                 20510  0 
aes_x86_64             17208  503 
aes_generic            38279  1 aes_x86_64
joydev                 17606  0 
binfmt_misc            17565  1 
parport_pc             36959  0 
dm_crypt               22993  0 
ppdev                  17113  0 
arc4                   12529  2 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_conexant    57511  1 
thinkpad_acpi          81587  0 
iwlagn                333716  0 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
uvcvideo               72195  0 
snd_hda_intel          33176  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_seq_midi_event     14899  1 snd_seq_midi
qcserial               12822  0 
iwlcore               167502  1 iwlagn
snd_hwdep              13604  1 snd_hda_codec
usb_wwan               20407  1 qcserial
usbserial              42908  2 qcserial,usb_wwan
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              294370  2 iwlagn,iwlcore
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
videodev               82052  1 uvcvideo
psmouse                73535  0 
v4l2_compat_ioctl32    17078  1 videodev
intel_ips              18097  0 
serio_raw              13166  0 
cfg80211              178528  3 iwlagn,iwlcore,mac80211
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
snd_timer              29602  2 snd_seq,snd_pcm
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  15 snd_hda_codec_hdmi,snd_hda_codec_conexant,thinkpad_acpi,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq,snd_pcm,snd_timer,snd_seq_device
soundcore              12680  1 snd
nvram                  14419  1 thinkpad_acpi
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usb_storage            53538  0 
uas                    17996  0 
i915                  515121  8 
r8169                  48022  0 
drm_kms_helper         42136  1 i915
ahci                   25951  3 
drm                   227534  4 i915,drm_kms_helper
libahci                26642  1 ahci
i2c_algo_bit           13400  1 i915
video                  19438  1 i915

```

```

md5sum /lib/firmware/gobi/*
80fcfbb41a7d4331d4b7145972f5f3c4  /lib/firmware/gobi/amss.mbn
00cbd411048cdadc3e4caf0d89d14fca  /lib/firmware/gobi/apps.mbn
bdf27325ebb63251c1310cd3a8f7bab6  /lib/firmware/gobi/UQCN.mbn

```

---

### Post by praseodym on 2011-08-24
Did you install the firmware? Extract the Windows-.exe file, create a new folder:
```
sudo mkdir -p /lib/firmware/gobi
```
and copy the files:

[LIST]
[*]amss.mbn
[*]    apps.mbn
[*]    UQCN.mbn
[/LIST]into that folder.

Please show the following:

```
cat /var/lib/NetworkManager/NetworkManager.state
```

Link in german where the windows files are: [http://thinkpad-wiki.org/Qualcomm_Gobi_2000_unter_Linux_installieren#Firmware_beschaffen](http://thinkpad-wiki.org/Qualcomm_Gobi_2000_unter_Linux_installieren#Firmware_beschaffen)

---

### Post by verderben on 2011-08-24
I did copy them from an Windows installation ...

```
cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

```

---

### Post by edsena on 2012-08-15
Hi, did you manage to solve this ? I was using gobi 2000 for more than a year on my old t410 but just moved to a t420 and now I can't connect anymore...

---

### Post by verderben on 2012-08-15
Actually I didn't need the modem, so I didn't try anything after this posts.

But it does work for me now, could have been an ubuntu upgrade, or messing with tlp (wwan on / wwan off) and I forgot about this post.

I think it should be marked solved (for me), even if I don't know the solution

---

