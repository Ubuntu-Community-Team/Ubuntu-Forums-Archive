---
title: "WinTV-PVR-250 card working...almost"
date: 2006-01-02
forum: Multimedia &amp; Video
---

### Post by dcroxton on 2006-01-02
After much weeping and gnashing of teeth, I finally managed to get the ivtv module installed and (apparently) working on Breezy.  It must be working, because I can do the "cat /dev/video0 > test.mpg" and I do get the video, although it is only a very, very small picture for some reason.

Apart from that, however, I can't get the input in any other way -- xawtv, TVTime, or Zapping TV Viewer.  (I haven't tried MythTV yet.)  TVTime reports "no signal," and at the bottom of the screen "ivtv:  Invalid Argument.  Cannot open capture device /dev/video0."  The other programs simply give a blank screen, with no further hints of why.  I've tried via the cable t.v. and from my camcorder, via a composite input, and I've tested all possible inputs (Zapping lists 5 of them).  Nothing works.

I don't have any idea what else to try, so I would be greatful for any help people could provide.  Here is the relevant part of dmesg, and if there is any other diagnostic information that would be helpful, let me know:

[4294703.120000] ivtv: ==================== START INIT IVTV ====================[4294703.120000] ivtv: version 0.3.8 (tagged release) loading
[4294703.120000] ivtv: Linux version: 2.6.12-10-686 686 gcc-3.4
[4294703.120000] ivtv: In case of problems please include the debug info
[4294703.120000] ivtv: between the START INIT IVTV and END INIT IVTV lines when
[4294703.121000] ivtv: mailing the ivtv-devel mailinglist.
[4294703.126000] ivtv: Autodetected WinTV PVR 250 card (iTVC16 based)
[4294703.126000] ivtv: Unreasonably low latency timer, setting to 64 (was 32)
[4294703.225000] ivtv: i2c attach to card #0 ok [client=tveeprom[50], addr=50]
[4294703.263000] tuner: chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[4294703.263000] ivtv: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4294703.504000] ivtv: i2c attach to card #0 ok [client=saa7115[50], addr=21]
[4294703.557000] msp34xx: ivtv version
[4294703.894000] ivtv: i2c attach to card #0 ok [client=MSP3448W-B3, addr=40]
[4294703.930000] ivtv: i2c attach to card #0 ok [client=tda9887, addr=43]
[4294704.559000] ivtv: loading /lib/modules/ivtv-fw-enc.bin
[4294704.846000] ivtv: Encoder revision: 0x02040024
[4294704.846000] ivtv warning: Encoder Firmware can be buggy, use version 0x02040011!!!!
[4294704.865000] ivtv: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[4294704.887000] ivtv: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[4294704.906000] ivtv: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[4294704.927000] ivtv: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[4294704.947000] ivtv: Create encoder radio stream
[4294704.947000] tuner: type set to 47 (LG NTSC (TAPE series)) by ivtv i2c driver #0
[4294705.887000] ivtv: Initialized WinTV PVR 250, card #0
[4294705.887000] ivtv: ====================  END INIT IVTV  ====================

Sincerely,
Derek

---

### Post by luna6 on 2006-01-08
Im in exactly the same boat...have the wintv-pvr 250 card installed....went through the mythtv how to install in this forum and finished up to installing the ivtv drivers. The card is recording a video file for me when I do "cat /dev/video0 > test.mpg"...unfortunately I cannot get any of the tv viewing programs to work (tvtime, kdetv, xawtv - I dont want to install mythtv at the moment since this is my primary workstation - just want to watch tv in a window occasionally) ....tvtime gives me this error 
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/luna6/.tvtime/tvtime.xml"
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

..but I have the ati fglrx drivers installed (9600 radeon SE) doubt I need to install the gatos driver....and the wintv card works fine in windows. Xawtv makes my screen completely black and locks up my computer completely, and kdetv launches but program seems frozen, does not respond to any clicks nor does the video window show anythign but a solid black screen. when I launch kdetv via console it says :
ALSA lib control.c:739:(snd_ctl_open_noupdate) Invalid CTL
kdetv: WARNING: Device does not support streaming interface or is not a V4L2 device.
kdetv: WARNING: Device does not support streaming interface or is not a V4L2 device.
Creating vbi proxy client, rev.
$Id: proxy-client.c,v 1.9 2005/01/20 20:56:11 mschimek Exp $
proxy_msg: connect: error 2, No such file or directory
kdetv: WARNING: VBIDecoder: vbi_capture_proxy_new error: Connection via socket failed, server not running.
Try to open V4L2 0.20 VBI device, libzvbi interface rev.
  $Id: io-v4l2.c,v 1.31 2004/12/30 02:24:11 mschimek Exp $
Opened /dev/vbi0
Try to open V4L2 2.6 VBI device, libzvbi interface rev.
  $Id: io-v4l2k.c,v 1.28 2005/05/25 02:26:41 mschimek Exp $
Opened /dev/vbi0
/dev/vbi0 (WinTV PVR 250) is a v4l2 vbi device,
driver ivtv, version 0x00000401
Using read interface
Current scanning system is 525
Querying current vbi parameters... success
VBI capture parameters supported: format 59455247 [GREY], 27000000 Hz, 1439 bpl, offs 248, F1 10...21, F2 273...284, flags 00000000
VBI capture parameters granted: format 59455247 [GREY], 27000000 Hz, 1439 bpl, offs 248, F1 10...21, F2 273...284, flags 00000000
Nyquist check passed
Request decoding of services 0x60000c7f, strict level -1
Will capture services 0x00000060, added 0x60 commit:1
Capture buffer allocated
Successful opened /dev/vbi0 (WinTV PVR 250)
kdetv: WARNING: MainWindow::setupInfraRed(): Lirc not available
kdetv: WARNING: ... failed. kdetv likely does not to work with your device and/or your current filter config.

.....pulling my teeth as well. How the heck to get video working on this card!!! so close as well...

---

### Post by dcroxton on 2006-01-09
I was lucky and able to get mine to work.  The key was to forget about all the other clients and just run MythTV.  All the others seem to have some problem or other.

Sincerely,
Derek

---

### Post by Bladerunner on 2006-01-09
I have the same problem. Have a PVR 250 setup and working fine in Mythtv but would like to watch tv occasionally without using Mythtv. However none of the tv viewing apps. seem to work. I've tried xawtv, Zapping, TVTime and a couple others. None of them work at all. Anybody have a clue or hints to get one of these apps. working.

---

### Post by luna6 on 2006-01-10
Will say the problems I had in tvtime was bad settings in xorg.conf with the fglrx setting which I fixed by using overlay, but it didnt help in getting the tv apps to work. I went ahead and installed mythtv and am quite impressed by it. Although I wish I could watch tv in a window, mythtv is impressive, and now thinking planning to run a sole mythtv box.

---

### Post by dbeckham32 on 2006-02-14
Same here. I can not get my WinTV 250 to work with any of those applications, except for MythTV. However, mplayer does work for me:

mplayer /dev/video0

And you can try turning on deinterlacing, too:

mplayer -vf pp=lb /dev/video0

---

### Post by bb002 on 2006-02-22
I have this problem occasionally, too.

so far opening a terminal and running the following two commands has always fixed.

```

sudo modprobe -r ivtv
sudo modprobe ivtv

```
Dunno what goes wrong originally because I can't find anything in dmesg but this has always fixed me having a blank screen problem.

---

### Post by dlai on 2006-05-20
look at this link... xawtv now supporting ivtv [http://ubuntuforums.org/showthread.php?t=170884]("http://ubuntuforums.org/showthread.php?t=170884")

---

