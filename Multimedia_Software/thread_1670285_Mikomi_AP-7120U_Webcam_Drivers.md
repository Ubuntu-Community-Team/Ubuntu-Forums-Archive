---
title: "Mikomi AP-7120U Webcam Drivers"
date: 2011-01-18
forum: Multimedia Software
---

### Post by matt-fender on 2011-01-18
Hi everyone, i've just been given a Webcam, after plugging it in, the blue LED turns ON. and lsusb reports the following:

```
Bus 002 Device 004: ID 0c45:6130 Microdia PC Camera (SN9C120)
```

The label on the underneath of the webcam itself states:

Mikomi Webcam AP-7120U

However Canorama, Cheese nor Skype will pick the webcam up.

Can anyone please help?

---

### Post by BicyclerBoy on 2011-01-18
Your webcam only works with video4linux v4l & not v4l2.
[http://lists-archives.org/video4linux/27042-application-for-microdia-0c45-6130.html](http://lists-archives.org/video4linux/27042-application-for-microdia-0c45-6130.html)

Try in terminal..
*export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so; guvcview*
You may need to install guvcview.
You can change the menu launcher if this works..

Example for skype:
[http://gurrier.wordpress.com/2010/05/30/problem-with-running-logitech-webcam-working-in-skype-on-ubuntu-10-04-lucid-lynx/](http://gurrier.wordpress.com/2010/05/30/problem-with-running-logitech-webcam-working-in-skype-on-ubuntu-10-04-lucid-lynx/)


You can also check this out by running in terminal
gstreamer-properties
select video tab & trying the v4l & v4l2 options & webcam & test...

---

### Post by matt-fender on 2011-01-20
Thankyou very much for your reply it is much appreciated.

After running

```
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so; guvcview
```I had to

 ```
sudo apt-get install guvcview
```done

ran command again and am receiving this error in terminal



```
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
video device: /dev/video0 
ERROR opening V4L interface for /dev/video0
unable to detect video devices on your system (0)
ERROR opening V4L interface: No space left on device
Init video returned -1
Terminated.
```
I ran ```
gstreamer-properties
```Selected the Video tab and changed Plugin to V4L and V4L2, and receive the same error message when testing both.

```
Error running pipeline 'Video for Linux (v4l)': Could not open device "/dev/video0" for reading and writing. [v4l_calls.c(179): gst_v4l_open (): /GstPipeline:pipeline2/GstV4lSrc:v4lsrc2:
system error: No space left on device]
```
Any further assistance is also greatly appreciated. Thanks, Matt.

---

### Post by matt-fender on 2011-01-20
Thankyou very much for your reply it is much appreciated.

After running

```
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so; guvcview
```I had to

 ```
sudo apt-get install guvcview
```done

ran command again and am receiving this error in terminal



```
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
video device: /dev/video0 
ERROR opening V4L interface for /dev/video0
unable to detect video devices on your system (0)
ERROR opening V4L interface: No space left on device
Init video returned -1
Terminated.
```
I ran ```
gstreamer-properties
```Selected the Video tab and  changed Plugin to V4L and V4L2, and receive the same error message when  testing both.

```
Error running pipeline 'Video for Linux (v4l)': Could not open  device "/dev/video0" for reading and writing. [v4l_calls.c(179):  gst_v4l_open (): /GstPipeline:pipeline2/GstV4lSrc:v4lsrc2:
system error: No space left on device]
```
Any further assistance is also greatly appreciated. Thanks, Matt.

---

### Post by BicyclerBoy on 2011-01-20
Reboot with webcam un-plugged.

Plug webcam in & post the last 20 lines of std output from
dmesg

maybe some clues about driver & driver suggestions..

---

### Post by BicyclerBoy on 2011-01-20
Reboot with webcam un-plugged.

Plug webcam in & post the last 20 lines of std output from
dmesg

maybe some clues about driver & driver suggestions..

---

### Post by BicyclerBoy on 2011-01-20
Reboot with webcam un-plugged.

Plug webcam in & post the last 20 lines of std output from
dmesg

maybe some clues about driver & driver suggestions..

---

### Post by matt-fender on 2011-01-21
dmesg as requested, thankyou again for reply, much appreciated :)
```

[   14.371853] type=1505 audit(1295551337.429:15):  operation="profile_load" pid=847 name="/usr/lib/cups/backend/cups-pdf"
[   14.372541] type=1505 audit(1295551337.433:16):  operation="profile_load" pid=847 name="/usr/sbin/cupsd"
[   14.408242] type=1505 audit(1295551337.469:17):  operation="profile_load" pid=848 name="/usr/sbin/tcpdump"
[   15.364805] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.376427]   alloc irq_desc for 27 on node -1
[   15.376431]   alloc kstat_irqs on node -1
[   15.376443] forcedeth 0000:00:07.0: irq 27 for MSI/MSI-X
[   15.376630] eth0: no link during initialization.
[   15.377194] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.075472] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[   31.564383] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   42.368012] wlan0: no IPv6 routers present
[ 3140.502428] polkit-gnome-au[1390]: segfault at b088 ip 001529a8 sp bfa5f850 error 4 in libgobject-2.0.so.0.2400.1[129000+3d000]
[ 5119.484614] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[51296.128030] usb 2-4: new full speed USB device using ohci_hcd and address 4
[51296.333775] usb 2-4: configuration #1 chosen from 1 choice
```

---

### Post by BicyclerBoy on 2011-01-21
Can you post result of 

lsmod

I think your kernel is not recognising the webcam device, the dmesg output shows the plugged in device as a USB hub or host device I think...

Is your camera a composite USB hub/camera/audio/auto-tracking thing ?

---

### Post by matt-fender on 2011-01-21
> **BicyclerBoy said:**
> Can you post result of 

lsmod

I think your kernel is not recognising the webcam device, the dmesg output shows the plugged in device as a USB hub or host device I think...

Is your camera a composite USB hub/camera/audio/auto-tracking thing ?


Here is lsmod output

```
Module                  Size  Used by
sn9c102               137320  0 
videodev               34361  1 sn9c102
v4l1_compat            13251  1 videodev
snd_opl3_synth         10388  0 
snd_seq_midi_emul       5492  1 snd_opl3_synth
binfmt_misc             6587  1 
snd_hda_codec_realtek   203344  1 
snd_hda_intel          22005  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_cmipci             30437  2 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
gameport                9089  1 snd_cmipci
snd_opl3_lib            8966  2 snd_opl3_synth,snd_cmipci
snd_hwdep               5412  2 snd_hda_codec,snd_opl3_lib
snd_pcm                70694  4 snd_hda_intel,snd_hda_codec,snd_cmipci,snd_pcm_oss
snd_mpu401_uart         5617  1 snd_cmipci
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  8 snd_opl3_synth,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  3 snd_opl3_lib,snd_pcm,snd_seq
snd_seq_device          5700  7 snd_opl3_synth,snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
snd                    54180  24 snd_opl3_synth,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_opl3_lib,snd_hwdep,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tileblit                2031  1 fbcon
soundcore               6620  1 snd
font                    7557  1 fbcon
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
ndiswrapper           184677  0 
usb_storage            39553  0 
ppdev                   5259  0 
i2c_nforce2             5199  0 
bitblit                 4707  1 fbcon
nvidia               9961216  46 
agpgart                31724  1 nvidia
parport_pc             25962  1 
softcursor              1189  1 bitblit
psmouse                63245  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
serio_raw               3978  0 
k8temp                  3152  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0 
ohci1394               26950  0 
hid                    67032  1 usbhid
ieee1394               81181  1 ohci1394
sata_nv                19376  0 
forcedeth              49556  0 
pata_amd                8766  4 
```


As far as a i know this webcam is pretty much as basic as it gets, no mic, or movement tracking of that sort. I have noticed a button on the top for taking photographs though?.

Regards and thanks for your further assistance.

---

### Post by no2498 on 2011-01-21
im looking at these 2 lines

3140.502428] polkit-gnome-au[1390]: segfault at b088 ip 001529a8 sp bfa5f850 error 4 in libgobject-2.0.so.0.2400.1[129000+3d000]
[ 5119.484614] process `skype' is using obsolete setsockopt SO_BSDCOMPAT




does skype run at the start up
we can only use 1 cam application at a time

---

### Post by BicyclerBoy on 2011-01-21
The dmesg output does not show the kernel module driver (webcam) starting at all.
But the module is shown listed correctly AFAIK.
> sn9c102               137320  0 
videodev               34361  1 sn9c102
v4l1_compat            13251  1 videodev

Short of below I have no ideas..
Try:
# sudo  rmmode sn9c102

  # sudo modprobe videodev
# sudo modprobe compat-ioctl32  then
  # sudo insmod sn9c102.ko 

post dmesg

I note the the webcam is a SN9C120 & the driver is sn9c102...

If you try:
modinfo sn9c102
Is the camera model listed in the aliases ?
Are there any module parameter options listed at the end ?

---

### Post by no2498 on 2011-01-21
ive had to do this myself a few times

find and install xawtv
it loads a grabber

---

### Post by forgewire on 2011-10-22
Hi folks.
My mikomi webcam identified as 
Bus 003 Device 002: ID 0c45:608f Microdia PC Camera (SN9C103 + OV7630)
When I plugged it in it didn't work with a skype.
I followed instructions at [https://help.ubuntu.com/community/Webcam#See%20also](https://help.ubuntu.com/community/Webcam#See%20also) :

cd ~
echo "#! /bin/sh" > skype-cam-fix
echo "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype" >> skype-cam-fix
chmod a+x skype-cam-fix
sudo mv skype-cam-fix /usr/local/bin 

But webcam microphone still didn't work (wasn't shown in skype options). To fix this I went to System -> Preferences -> Sound (Ubuntu 11.04 Gnome) and change input to "PC Camera  (SN9C103 + OV7630)" 

To start skype type skype-cam-fix
Now everything works like a charm

Hope it helps

---

