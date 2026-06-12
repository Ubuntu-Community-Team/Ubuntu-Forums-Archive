---
title: "No video with Plextor ConvertX PX-M402U"
date: 2007-04-12
forum: Multimedia &amp; Video
---

### Post by danb35 on 2007-04-12
I'm running Edgy on a Mac Mini, and wanting to use a Plextor PX-M402U as a A/V capture device.  I've downloaded, built, and installed the go7007 drivers from [http://oss.wischip.com/](http://oss.wischip.com/) (with the patch for the 2.6.17 kernel), and the appropriate modules seem to load during startup without any trouble.  However, when I try to record sample video using the gorecord app, there doesn't seem to be any video recorded with the file.  Audio is recorded just fine.

I tried setting the format in the command line to mjpeg and to mpeg2, in case the encoding format was causing a problem, but in both cases (as well as when I didn't specify a format, which IIRC would mean it was using MPEG4) the video player window will come up showing nothing.  I've verified the connections to the VCR I was using as a video source, and they're all fine.

Another issue I'm seeing, which may or may not be related (and if it isn't, I can take it to another thread), is that the /dev/video0 device doesn't always exist after a reboot--sometimes it does, and sometimes it doesn't, with no apparent reason for the difference.

The modules loaded are:
dan@myth-greatroom:~/wis-go7007-linux-0.9.8/apps$ lsmod | grep go7007
go7007                 57472  0 
v4l2_common            17280  1 go7007
videodev               10752  1 go7007
snd_go7007              8836  1 go7007
i2c_core               23424  2 i2c_ec,go7007
snd_pcm                84612  4 snd_go7007,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd                    58372  9 snd_go7007,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer

I've tried some web searching, but I haven't been able to find references to this particular issue.  Any suggestions on where to start would be appreciated.

---

### Post by danb35 on 2007-04-13
Anybody?

---

### Post by WiryLattice on 2007-08-28
Hi, 

I am thinking of buying one of these cards, and I was wondering whether you managed to make it work?

---

### Post by tedder on 2007-09-17
I have one of these cards (well, boxes, since it is USB), and have the same type of issues. I can modprobe go7007_usb, but don't seem to get anything after that.

```

# lsusb
Bus 002 Device 003: ID 0518:0001 EzKEY Corp.
Bus 002 Device 002: ID 045e:0053 Microsoft Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 093b:a004 Plextor Corp.
Bus 001 Device 001: ID 0000:0000
# lsmod | grep 7007
go7007_usb             15748  0
go7007                 55808  1 go7007_usb
snd_go7007              8580  1 go7007
snd_pcm                80388  5 snd_go7007,snd_bt87x,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    54660  12 snd_go7007,snd_bt87x,snd_intel8x0,snd_ac97_codec,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               29312  3 go7007,bttv
v4l2_common            18432  6 go7007,cx25840,tuner,tvaudio,bttv,videodev
i2c_core               26112  10 go7007_usb,go7007,cx25840,tuner,tvaudio,nvidia,bttv,i2c_algo_bit,tveeprom,i2c_nforce2
usbcore               138248  6 go7007_usb,lirc_imon,usbhid,ohci_hcd,ehci_hcd
# ls -l /dev/vid*
crw-rw---- 1 root video 81, 0 2007-09-15 13:59 /dev/video0
(video0 is another device)

```

---

### Post by tedder on 2007-09-17
Some more:
```
# gorecord -verbose -duration 2 -tvchan ntsc-bcast:2 /tmp/test.avi
Driver loaded but no GO7007 devices found.
Is the device connected properly?

```

which makes sense. Googling, there isn't a lot of help for the "driver loaded" line, but this seems to be on the right path:
[http://ubuntuforums.org/showpost.php?p=1805385&postcount=29]("http://ubuntuforums.org/showpost.php?p=1805385&postcount=29")

However, that doesn't run on Ubuntu Gutsy, because /proc/bus/usb/005/019 doesn't exist- /proc/bus/usb/ is empty on my system, at least. Can someone point me in the right direction for using fxload on Gutsy?

---

### Post by tedder on 2007-09-17
Okay, making progress. Mounted usbfs:

mount -t usbfs none /proc/bus/usb

found my device: (hint- Vendor=093b,  ProdID=a104)

less /proc/bus/usb/devices

loaded the driver:

fxload -t fx2 -D /proc/bus/usb/001/004 -I /lib/firmware/ezusb/hpi_PX-TV402U.hex


I can now see it in mythtv, and 'gorecord' works too. However, I can't figure out how to get the channels to scan on it. My setup:

HDHomeRun device (2 HDTV inputs)
Plextor ConvertX device

When I go to "scan for channels", even using the Plextor tuner input,  the "capture card" is set to the HDHomeRun device and I can't change it to the Plextor. WTF?

---

### Post by pyman on 2007-12-03
When I upgraded to gutsy my PX-TV402U quit working your instruction worked great thanks
This is what I did
went here and followed the Ubuntu install
[http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Ubuntu_Dapper.2FEdgy.2FFeisty.2FGutsy](http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Ubuntu_Dapper.2FEdgy.2FFeisty.2FGutsy)
then
make install USE_UDEV=y

fxload -t fx2 -D /proc/bus/usb/005/008 -I /lib/firmware/ezusb/hpi_PX-TV402U.hex

mount the stbfs
mount -t usbfs none /proc/bus/usb

find it use q to quit e to move down one line
less /proc/bus/usb/devices
load the driver
do an lsusb to get the 005 and 018 correct
sudo fxload -t fx2 -D /proc/bus/usb/005/018 -I /lib/firmware/ezusb/hpi_PX-TV402U.hex

Test gorecord by recording first 22 saeconds
(sleep 22; killall gorecord) & gorecord -input 1 test-video.avi

thanks guys it works again :guitar:
:)

---

### Post by tedder on 2008-01-06
> **pyman said:**
> When I upgraded to gutsy my PX-TV402U quit working your instruction worked great thanks

aha, it's the updated drivers that make it work. Thanks for posting, pyman!

---

