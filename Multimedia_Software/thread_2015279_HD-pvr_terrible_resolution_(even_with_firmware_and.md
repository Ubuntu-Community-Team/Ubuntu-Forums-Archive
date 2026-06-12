---
title: "HD-pvr terrible resolution (even with firmware and driver update)"
date: 2012-07-03
forum: Multimedia Software
---

### Post by IamHungry on 2012-07-03
This may turn into a pretty long post trying to explain the problem I am up against.

The short version:
My new HD-PVR (ver f2) has bad resolution.  With 720p component input cat/dev/videoX looks like this:
[http://i.imgur.com/VrBIa.jpg](http://i.imgur.com/VrBIa.jpg)     [http://i.imgur.com/5rBuR.jpg](http://i.imgur.com/5rBuR.jpg)

I get the same picture quality regardless of the input signal resolution (yes, the picture size changes, but the picture quality is always like the pic above)

Tried newest drivers and firmware, and all the v4l2-ctl commands I could find.  On it's own usb bus, and very solid.  No matter what resolution I throw at it, it looks like the above pic.

WTF, right?


The long version:
I have a fresh 12.04 64bit 3.2.0-24-generic install.  (When I started, I was on a 11.10 64 bit system and had the exact same problem)
An old pvr-350 analog tuner died, so I did a little research and decided on a HD-PVR to replace it.  I am in Japan, so I am limited in my choices of input devices.  I am recording the component out of my cable box Panasonic tz-dch820.  The component is from a d-terminal ([http://en.wikipedia.org/wiki/D-Terminal](http://en.wikipedia.org/wiki/D-Terminal)) to component adapter cable.  

I opened the HD-pvr, and plugged it into a windows machine to test it out.  I installed the newest 1.7.1 firmware and it ran great.  No problems at all.  (So from this I am thinking cables are OK)

Plug it into Ubuntu, and the driver isn't loaded.  I do lsusb, and find:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 002: ID 2040:4983 Hauppauge 
Bus 005 Device 002: ID 04e6:511a SCM Microsystems, Inc. 
Bus 001 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 005: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver

* Originally, the HD-PVR was on the same USB bus as other devices, but I read that can cause problems, so I isolated it on its own bus.
*Not using hd-pvr ir blaster, I am using a separate usb ir receiver/blaster.  Tried unplugging it, but got same result.

The ID 2040:4983 is not recognized by the driver.  I guess the driver doesn't support it yet.
So I think, I am sure I can beat this... (a month later, I am here looking for help :()
I don't have links for everything I read and tried, but here is a little list:

1) Grab newest HD-PVR Linux driver and add the USB ID to two files before compiling.  Compile and install the hd-pvr driver.  This seems to work, I can load the driver with modprobe, but as soon as I plug in the device I get a long error in dmesg that talks about my mother board and such, I get the same error if I don't add the USB ID to the driver, and simply load it using the method below. I also have a pt1 DVB tuner that the newest linux drivers don't work on, so I was just compiling and installing hd-pvr (all other choices=n).
here is a snippit of dmesg when the device is plugged in with the newest kernel driver:

[  202.959396] WARNING: at /build/buildd/linux-3.2.0/drivers/media/video/v4l2-dev.c:559 __video_register_device+0x441/0x4e0 [videodev]()
[  202.959398] Hardware name: Blitz Extreme
[  202.959400] Modules linked in: hdpvr(O) mceusb bnep rfcomm bluetooth parport_pc ppdev vesafb snd_hda_codec_analog nvidia(P) snd_hda_intel snd_hda_codec ir_lirc_codec snd_hwdep lirc_dev snd_pcm ir_mce_kbd_decoder ir_sony_decoder snd_seq_midi snd_rawmidi ir_jvc_decoder snd_seq_midi_event snd_seq joydev ir_rc6_decoder snd_timer bttv i2c_algo_bit ir_rc5_decoder snd_seq_device videobuf_dma_sg videobuf_core ir_nec_decoder snd btcx_risc rc_core tveeprom hid_logitech_dj v4l2_common earth_pt1 dvb_core asus_atk0110 serio_raw soundcore videodev snd_page_alloc v4l2_compat_ioctl32 shpchp mac_hid lp parport firewire_ohci firewire_core skge crc_itu_t pata_jmicron sky2 floppy usbhid hid
[  202.959435] Pid: 23, comm: khubd Tainted: P           O 3.2.0-24-generic #39-Ubuntu
[  202.959437] Call Trace:

2) Use stock kernel driver and get the USB ID loaded this way: [http://www.ha19.no/usb/](http://www.ha19.no/usb/)
This seems to work. If I do:
sudo modprobe hdpvr
sudo echo 2040 4983 > /sys/bus/usb/drivers/hdpvr/new_id 

Then plug in the device.  /dev/videoX is created, and I can use the device like normal.  I do have the color saturation problems, but the help [here]("http://www.mythtv.org/wiki/Hauppauge_HD-PVR") gets the colors fixed.  However, no matter what resolution I throw at it, the picture is like the link above.  The only way I can describe it is the resolution looks terrible.

3) 3.4 beta kernel - same results

4) Tried the older 1.5.7 firmware, and got the same results with both 3.2 and 3.4 kernels

5) Tried all inputs (video and audio) on hd-pvr - same results

Does anyone have any suggestions for me to try to get it to work?
Is there an appropriate mailing list for hd-pvr driver specific questions?
Should I just burn the hd-pvr with fire and cancel my cable?

Thanks

---

### Post by BicyclerBoy on 2012-07-03
Did you set the encoder bitrates ?

[http://www.mythtv.org/wiki/Hauppauge_HD-PVR#Miscellaneous_Kernel_Module_Options](http://www.mythtv.org/wiki/Hauppauge_HD-PVR#Miscellaneous_Kernel_Module_Options)

Have a look at the example startup script & try it out..

Can you confirm that an externally sourced example test mpeg-ts h264 video plays okay on your system..

---

### Post by IamHungry on 2012-07-04
Thanks for the help BicyclerBoy.  I am a bit of a bicycler myself, but on the question at hand.

>Did you set the encoder bitrates ?
I think you mean this section here:
# bitrate_mode   0=VBR, 1=CBR
sudo /usr/bin/v4l2-ctl --verbose -d $MPEG4_IN -c video_bitrate_mode=0
sudo /usr/bin/v4l2-ctl --verbose -d $MPEG4_IN -c video_bitrate=10000000
sudo /usr/bin/v4l2-ctl --verbose -d $MPEG4_IN -c video_peak_bitrate=16500000

Yes, I have set those.  I have used the start up script on the wiki page, as a single script file, and doing all the commands in the script by hand.

The system is a Myth/XBMC combo, and has never had any trouble playing anything I have thrown at it before.  Definitely not a playback issue, same results when played back on different hardware.

Do the screen shots look like a bitrate problem to you?
I don't have many settings in the STB to play with, are there any I should take a look at in particular?  I have tried 1080i, 480p, and 720p for the resolution settings in the STB.

I could forgo the whole HD-pvr if I could get firewire to work.  The STB won't recognize the ubuntu box as a valid link partner, and only an empty file gets recorded.

---

### Post by BicyclerBoy on 2012-07-04
The facts seem to me to be:
- works fine in windows (no HDCP handshaking)
- original hd-pvr works with std kernel (lot of them in the wild)
- your USB ids do not appear anywhere on the web!

You should **not** have needed to trick the hdpvr driver.

Maybe your hdpvr is a newer version that has some important differences to that supported by v4l-dvb.
Could be the video parameter/mode configuration thru' the D-terminal connector is not supported..although your sample looks worse than 480i60

Temp work around:
Could use the hdpvr device as pass-thru USB device to windows VM running on ubuntu.

I guess you may need to ask on the LinuxTV v4l-dvb forums.

---

### Post by IamHungry on 2012-07-04
I agree with your facts :)

I tried, and got the same picture quality with the composite (yellow) cable, and S-vid cable, so I don't think it is the d-terminal cable.

I think there must be some new setting that the driver isn't handling correctly.
Running a windows VM just to capture HD video is not the option for me now.

Anyways, thanks for the help BicyclerBoy.

If anyone has any other ideas, I would love to hear them.

---

### Post by fixitdude on 2012-07-04
Suggestions:

Work on changes to the display part, meaning possibly changing the screen resolution of the computer or the way it puts the video on the screen, direct write or not etc..

Record something using mencoder and play it back, possibly on another computer and see if anything changes.

If you do get it working, check out my DVR automatic TV recording script.
[http://ubuntuforums.org/showthread.php?t=2009778](http://ubuntuforums.org/showthread.php?t=2009778)

---

### Post by IamHungry on 2012-07-05
The files playback the same on other ubuntu machines, and a xp machine as well.  Pretty sure it is not the display settings of the HD-PVR box.

Cool little script you are working on!

---

### Post by IamHungry on 2012-07-09
Just a follow up,

So according to this 2ch sled: [http://toro.2ch.net/test/read.cgi/avi/1254520764/](http://toro.2ch.net/test/read.cgi/avi/1254520764/)

The Japanese version of the HD-PVR is a little different than the American version.  The main difference being cgms-a compliance.  All Japanese TV is sent with cgms-a analog copy protection.  On linux, you can record things fine, but the picture has bad resolution, and is unwatchable.  In windows, it lets you record the video, but only lets you play it using the software it was recorded with.

The good news is my stb has HDMI out, so a HDMI component converter should do the trick.  Saw quite a few online for about $50. 

If you are in Japan and looking at the HD-PVR, find an older version from the US.  The Japanese versions are cheaper, but they do not allow Japanese TV to be recorded freely (or at all in Linux).

---

### Post by BicyclerBoy on 2012-07-17
My mistake was assuming your analogue signal was not copy protected (in some way).
Could be macrovision ?? The HD-PVR in US are not effected by macrovision..

Quite a good trick to protect the old analogue signals (no HDCP) at the recorder & protect the digital output (HDMI etc) with HDCP at Tx end.
The analogue outputs of DVD & BD players etc are not protected just non-HD.

I would think the HDMI output of your set-top-box requires HDCP i.e. HDFury like device.. Are these devices avail for around $50?

The HDCP private keys were leaked into the wild about Sept 2010..

Do you think you can use the non-Japan firmware ?

---

