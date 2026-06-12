---
title: "TV Time not detecting MCE PVR-150 in 7.10"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by Deadpool14 on 2007-11-10
Hi,
I'm trying to get a MCE  PVR-150 to get setup using 7.10 with TVTime.  The error I get is this "ivtv: Invalid Argument Cannot open capture device /dev/video0"  I ran dmesg and this what i got out of it:

[   16.308000] ivtv:  ==================== START INIT IVTV ====================
[   16.308000] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
[   16.308000] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   16.308000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   16.308000] ACPI: PCI Interrupt 0000:03:0a.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 22
[   16.308000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   16.480000] usb 1-1: reset full speed USB device using ohci_hcd and address 2
[   16.684000] lirc_dev: lirc_register_plugin: sample_rate: 0
[   16.692000] lirc_mceusb2[2]: Topseed eHome Infrared Transceiver on usb1:2
[   16.692000] usbcore: registered new interface driver lirc_mceusb2
[   16.964000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (3753780072 bytes)
[   17.180000] ivtv0: Encoder revision: 0x02050032
[   17.180000] ivtv0: Recommended firmware version is 0x02060039.
[   17.232000] tveeprom 2-0050: Hauppauge model 26552, rev F1A3, serial# 10302512
[   17.232000] tveeprom 2-0050: tuner model is TCL MFNM05-4 (idx 103, type 43)
[   17.232000] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[   17.232000] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[   17.232000] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[   17.232000] tveeprom 2-0050: has radio, has no IR receiver, has no IR transmitter
[   17.232000] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   17.244000] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   17.244000] tda9887 2-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   17.248000] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   17.268000] cx25840 2-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   20.472000] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   20.548000] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   20.592000] tuner 2-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[   20.908000] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   20.908000] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   20.908000] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   20.908000] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   20.908000] ivtv0: Registered device radio0 for encoder radio
[   20.932000] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   20.932000] ivtv:  ====================  END INIT IVTV  ====================


Another odd thing I noticed is that it says it can't find the IR receiver but Immmediately above that there is this:
[   16.284000] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.33 $
[   16.284000] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>


But that my just be I need to install a seperate version of that LIRC driver.


Thanks.

---

### Post by rsambuca on 2007-11-10
I am not 100% positive on this, but in the past, TV Time could not be used with the pvr150.  I just use VLC with mine.

---

### Post by Deadpool14 on 2007-11-11
Really, how were you able to set that up? I tried selecting it in VLC but the only thing I got  was a channel I didn't recogonize but did refer to my geographical area....

---

### Post by rsambuca on 2007-11-11
If you open VLC, go to "File -> Open Capture Device".  Go to the PVR tab and make sure that "/dev/video0" is selected in the top row for "Device".  Press OK and it will open up a window and play from your tuner.

To change channels, you first have to install ivtv-utils (you can just enter in a terminal:  sudo apt-get install ivtv-utils).

Then to change channels, you would enter in a terminal:

v4l2-ctl -c #

Where the # is the channel you want to watch.  If you search around, others have GUI methods of changing channels, but I have never bothered since I just use the composite input and change channels via my satellite box.

---

### Post by Jovec on 2007-11-11
Yeah, TVTime only works with framegrabber cards, not mpeg-encoder cards.

As mentioned above, you can use VLC, but you can also use Totem.  File - Open, change to show all files, and navigate to /dev/video0 and open (you might need to install codecs).  You still need to change channels with ivtv-tune -cXX from a command line though.  I imagine there has to be a small gui app to issue channel change commands if I bothered to look.

---

### Post by rsambuca on 2007-11-11
> **Jovec said:**
> Yeah, TVTime only works with framegrabber cards, not mpeg-encoder cards.

As mentioned above, you can use VLC, but you can also use Totem.  File - Open, change to show all files, and navigate to /dev/video0 and open (you might need to install codecs).  You still need to change channels with ivtv-tune -cXX from a command line though.  I imagine there has to be a small gui app to issue channel change commands if I bothered to look.
Totem doesn't play the hauppauge, as far as I know.

---

### Post by Jovec on 2007-11-11
Sure it does. Any mpeg-capable player will work if you open the file /dev/video0.  On some players that don't let you view all files and only show files by extension, you may have to add a symlink such as "ln -s /dev/video0 tv.mpeg" and open that.  Of course you'll still have to manually issue channel change commands.

Currently, only MythTV and Mplayer use the full encoder api on the hauppauge though.

---

### Post by rsambuca on 2007-11-11
What  version of Totem are you using?  I don't even have a "File" on the title menu bar.  I am using 2.20.

---

### Post by Jovec on 2007-11-12
> **rsambuca said:**
> What  version of Totem are you using?  I don't even have a "File" on the title menu bar.  I am using 2.20.

2.20.0

The Movie menu is just Totem's name for the file menu, so it would be:

Movie -> Open -> Browse to /dev ( FIlesystem - > /dev) -> Change from "Supported Files" to "All Files" and open video0.

As I mentioned, it's easier to place a symlink to /dev/video0 in a more convenient location with a better name so programs will filter it a movie file (due to the extension)

ln -s /dev/video0 tv.mpeg

---

### Post by rsambuca on 2007-11-12
Thanks Jovec,  I had actually figured it out, but it doesn't seem to be a viable option for me.  It seems the deinterlacer on Totem is nowhere near as good as the VLC one.  Even with deinterlacing "on" on Totem, the artifacting makes it virtually unwatchable if there is any movement on the screen.

---

### Post by Jammerdelray on 2007-12-03
I have PVR-150 and it works in VLC Media Player.

---

### Post by rsambuca on 2007-12-03
> **Jammerdelray said:**
> I have PVR-150 and it works in VLC Media Player, get it from synaptic package manager. Start Vlc up and click file then open file and the PVR tab, hit ok and voila it should work. If this does not work you might have to do a clean install of Ubuntu Gutsy Gibbon for it to work since it was conflicting with some other players that I had downloaded.

I have not figured out how to change channels yet tho. Everything else besides VLC I tried did not work sicne they don't support mpeg 2 hardware coding. (Xawtv, Tvtime, Mythtv do not work)

Have fun.

You should read the entire thread prior to posting.  I had already outlined how to use VLC and change channels way back in post #4.

---

### Post by Mud.Knee.Havoc on 2008-01-05
I don't mean to hijack the thread, but you say that you use VLC for encoding MPEG.  Whenever I try this, it saves the .mpg file but closes the video window, so I can't see what point I'm at.  How do you get around this?  I tried "mplayer /dev/video0" at the same time to see if it would just show me the video as it streamed, but no luck.

---

