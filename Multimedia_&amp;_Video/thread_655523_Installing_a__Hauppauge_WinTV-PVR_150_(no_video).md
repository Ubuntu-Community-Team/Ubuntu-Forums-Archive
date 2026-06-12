---
title: "Installing a  Hauppauge WinTV-PVR 150 (no video)"
date: 2008-01-01
forum: Multimedia &amp; Video
---

### Post by jonberling on 2008-01-01
Hello Everyone, 

I got a  Hauppauge WinTV-PVR 150 for Chirstmas, so that I could play my PS2 on the PC and not hog up the TV. The only problem is I'm having trouble getting it to work.

Here's the steps I've followed so far:

1) Remove my old KWorld video capture card (which doesn't work with linux)

2) Place the  Hauppauge WinTV-PVR 150 in the same slot

3) boot up the machine

4) configure VLC to use channel 2 (which should be s-video)

I had no love, so I then tried:

5) reinstall Ubuntu 7.10, just in case parts of the KWorld card were still lying around

6) search the net for info...

Still, no love...

Here's the problem, when I try the command 
```
 cat /dev/video0 > ~/testfile.mpg 
```

and then play that file, I get sound, but only a black box where the video should be.

Am I doing something wrong? Did I miss a step? Is there a chance my video card is defective? Any help would be [SIZE="3"][COLOR="Red"] GREATLY [/COLOR][/SIZE] appreciated.

Thanks in advance,
Jonathan

Here's a copy of the last 15% of my /var/log/dmesg, just in case

```

[   28.775785] PCI: Setting latency timer of device 0000:00:19.0 to 64
[   28.782985] Linux agpgart interface v0.102 (c) Dave Jones
[   28.899090] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:1a:a0:8c:d9:f9
[   28.940205] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   28.943424] input: PC Speaker as /class/input/input1
[   28.959985] Linux video capture interface: v2.00
[   28.996575] ivtv:  ==================== START INIT IVTV ====================
[   28.996579] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
[   28.996646] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   28.996688] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 21 (level, low) -> IRQ 17
[   29.190596] nvidia: module license 'NVIDIA' taints kernel.
[   29.195732] usbcore: registered new interface driver hiddev
[   29.467666] input: Honey Bee           AIRFLO              as /class/input/input2
[   29.467798] input: USB HID v1.00 Joystick [Honey Bee           AIRFLO             ] on usb-0000:00:1a.1-2
[   29.493272] input: PS2/USB KVM PS2/USB KVM as /class/input/input3
[   29.493301] input: USB HID v1.10 Keyboard [PS2/USB KVM PS2/USB KVM] on usb-0000:00:1a.1-1.2
[   29.507665] input: PS2/USB KVM PS2/USB KVM as /class/input/input4
[   29.507704] input: USB HID v1.10 Mouse [PS2/USB KVM PS2/USB KVM] on usb-0000:00:1a.1-1.2
[   29.539661] input: Dell Dell USB Keyboard as /class/input/input5
[   29.539706] input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1a.1-1.1.1
[   29.569649] input: Chicony USB Wireless HID Receiver as /class/input/input6
[   29.569688] input: USB HID v1.10 Keyboard [Chicony USB Wireless HID Receiver] on usb-0000:00:1a.1-1.1.2
[   29.680430] input: Chicony USB Wireless HID Receiver as /class/input/input7
[   29.680502] input,hiddev96: USB HID v1.10 Device [Chicony USB Wireless HID Receiver] on usb-0000:00:1a.1-1.1.2
[   29.689770] ivtv0: loaded v4l-cx2341x-enc.fw firmware (3752693880 bytes)
[   29.707577] input: Chicony USB Wireless HID Receiver as /class/input/input8
[   29.707637] input: USB HID v1.10 Mouse [Chicony USB Wireless HID Receiver] on usb-0000:00:1a.1-1.1.2
[   29.707652] usbcore: registered new interface driver usbhid
[   29.707655] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   29.707745] usbcore: registered new interface driver xpad
[   29.707748] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   29.901872] ivtv0: Encoder revision: 0x02050032
[   29.901876] ivtv0: Recommended firmware version is 0x02060039.
[   29.959329] tveeprom 0-0050: Hauppauge model 26582, rev F0B2, serial# 9655209
[   29.959333] tveeprom 0-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[   29.959335] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   29.959338] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[   29.959340] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[   29.959342] tveeprom 0-0050: has no radio, has no IR receiver, has no IR transmitter
[   29.959345] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   29.980837] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   30.006412] cx25840 0-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   33.474885] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   33.558142] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   33.605993] tuner 0-0061: type set to 50 (TCL 2002N)
[   33.921497] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   33.921648] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   33.921824] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   33.921892] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   33.945051] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   33.945068] ivtv:  ====================  END INIT IVTV  ====================
[   33.945461] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   33.945486] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   34.151417] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   34.255640] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.255650] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   34.255789] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   34.460409] lp: driver loaded but no devices found
[   34.501673] Adding 128512k swap on /dev/sda2.  Priority:-1 extents:1 across:128512k
[   34.870673] EXT3 FS on sda1, internal journal
[   35.440648] kjournald starting.  Commit interval 5 seconds
[   35.441060] EXT3 FS on sda3, internal journal
[   35.441067] EXT3-fs: mounted filesystem with ordered data mode.


```

---

### Post by Mud.Knee.Havoc on 2008-01-04
I'm bumping this thread... I'm having a similar problem getting the Hauppauge 150 up and running.  People have said that it's "plug and play" with Ubuntu, but no such luck with the one I just got.

Keeping my eyes on this thread, hoping for some info.

---

### Post by malty on 2008-01-05
I have a WINTV-PVR 150 installed (originally in Windows XP) this works 100%. It will not work in Gutsy, I tried installing the Hauppage CD using Crossover  "Cannot find the board, aborting installation". Nothing in Gutsy that should recognise a TV card does that.
             I also tried the same terminal command as you, got a snowstorm in MPlayer.  I have punted about out there on the web but as usual there is more misinformation than the genuine kind.
              Considering the fact that the Hauppage 150 is one of the better cards out there, and must be pretty commonplace, the lack of support is frustrating, mind you it just joins the list of unrecognised hardware..
Dell 962 printer, Nikon D40X, Hauppage 150 etc.
                                                     Sorry I could not be of any help, you have my sympathies
                               Kind Regards                  Malty

---

### Post by aBitLater on 2008-01-21
same problem here.  I've got a PCI WinTV PVR 150 (PCI card).  I'm a newb and don't know what I'm doing though!!!

(watching thread...)

---

### Post by dlanor78 on 2008-02-16
I'm really new at using this card so far, but here's a couple things I found out that I don't see mentioned yet.

Make sure you install the ivtv-utils package.  Then you need to use the terminal to set which input the card is capturing from.  I use the composite so I need to run

```

v4l2-ctl -i 2

```

To see what input is currently being used run

```

v4l2-ctl -I

```

To see what inputs are available and what number to use after the -i run

```

v4l2-ctl -n

```

So far it seems that I have to run the v4l2-ctl -i 2 every time I reboot to make it use the composite input.  There may be a way to have it automatically set each time I log in but haven't found it yet.

Also, so far for viewing/recording I'm using vlc.  Just use File>Open Capture Device...>PVR tab and make sure /dev/video0 is in the Device section.

Hope this helps a bit :)

---

### Post by miguel20 on 2008-07-19
Sorry this is another ME TOO BUMP.

I love Ubuntu but for me it's been the worst nightmare with video capture.
I'm on my 3rd tv card and I'm about to go over the edge...

I'm now running version Ubuntu 8.04 and Hauppage TV PVR 150.

Like many people I've got no video being displayed, in any application I try TVtime, VLC using capture, XAWTV etc.

TV time seems to give the most useful error which is [COLOR="Red"]ivtv: invalid argument. cannot open capture device /dev/video0[/COLOR]

I've read every thread and tried every tweek and still a card that took 2 mins to congiure in Doze XP is still f£%$%$"%^ dead after a month in Ubuntu. :-(
I've tweeked every aspect I can....

using every app I get no video... using cat /dev/video0 > ~/test.mpg i just get funny patterns scrolling about on the screen.
I'm just inputting raw video from an external satellite box.

everything looks ok accept the results.

I'm an amature in Ubuntu environs but I know my way round hardware and software very well.  PLEASE PLEASE someone help with a suggestion other than try a 4th TV card!

Thanks

M

Jul 19 15:13:31 mikeb-ubuntu kernel: [   46.050673] ivtv0: Autodetected Hauppauge WinTV PVR-150
Jul 19 15:13:31 mikeb-ubuntu kernel: [   46.599457] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #0)
Jul 19 15:13:31 mikeb-ubuntu kernel: [   46.599504] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
Jul 19 15:13:31 mikeb-ubuntu kernel: [   46.599508] tuner 1-0043: type set to tda9887
Jul 19 15:13:31 mikeb-ubuntu kernel: [   46.602536] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
Jul 19 15:13:31 mikeb-ubuntu kernel: [   46.657965] Driver for 1-wire Dallas network protocol.
Jul 19 15:13:31 mikeb-ubuntu kernel: [   46.718610] NET: Registered protocol family 17
Jul 19 15:13:31 mikeb-ubuntu kernel: [   46.862936] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
Jul 19 15:13:31 mikeb-ubuntu kernel: [   47.018115] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
Jul 19 15:13:31 mikeb-ubuntu kernel: [   47.045542] tuner-simple 1-0061: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
Jul 19 15:13:31 mikeb-ubuntu kernel: [   47.045552] tuner 1-0061: type set to Philips PAL/SECAM m
Jul 19 15:13:31 mikeb-ubuntu kernel: [   47.046069] ivtv0: Registered device video0 for encoder MPG (4096 kB)
Jul 19 15:13:31 mikeb-ubuntu kernel: [   47.046108] ivtv0: Registered device video32 for encoder YUV (2048 kB)
Jul 19 15:13:31 mikeb-ubuntu kernel: [   47.046128] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
Jul 19 15:13:31 mikeb-ubuntu kernel: [   47.046150] ivtv0: Registered device video24 for encoder PCM (320 kB)
Jul 19 15:13:31 mikeb-ubuntu kernel: [   47.046173] ivtv0: Registered device radio0 for encoder radio
Jul 19 15:13:31 mikeb-ubuntu kernel: [   47.046177] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
Jul 19 15:13:31 mikeb-ubuntu kernel: [   47.046214] ivtv:  End initialization
Jul 19 15:13:31 mikeb-ubuntu kernel: [   47.054061] matrox_w1 0000:01:00.0: Matrox G400 GPIO transport layer for 1-wire.
Jul 19 15:13:31 mikeb-ubuntu kernel: [   47.322722] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 20
Jul 19 15:13:31 mikeb-ubuntu kernel: [   50.819311] lp0: using parport0 (interrupt-driven).
Jul 19 15:13:31 mikeb-ubuntu kernel: [   50.924680] Adding 465844k swap on /dev/sda5.  Priority:-1 extents:1 across:465844k
Jul 19 15:13:31 mikeb-ubuntu kernel: [   51.537788] EXT3 FS on sda1, internal journal
Jul 19 15:13:31 mikeb-ubuntu kernel: [   52.197267] NET: Registered protocol family 10
Jul 19 15:13:31 mikeb-ubuntu kernel: [   52.197619] lo: Disabled Privacy Extensions
Jul 19 15:13:31 mikeb-ubuntu kernel: [   53.705293] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 19 15:13:31 mikeb-ubuntu kernel: [   54.375452] No dock devices found.
Jul 19 15:13:35 mikeb-ubuntu kernel: [   60.175732] apm: BIOS not found.
Jul 19 15:13:35 mikeb-ubuntu kernel: [   60.449238] ppdev: user-space parallel port driver
Jul 19 15:13:36 mikeb-ubuntu kernel: [   60.998127] audit(1216476816.376:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5137 profile="/usr/sbin/cupsd" namespace="default"
Jul 19 15:13:37 mikeb-ubuntu dhcdbd: Started up.
Jul 19 15:13:39 mikeb-ubuntu kernel: [   64.117580] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
Jul 19 15:13:39 mikeb-ubuntu kernel: [   64.315243] ivtv0: Encoder revision: 0x02060039
Jul 19 15:13:42 mikeb-ubuntu kernel: [   67.524333] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
Jul 19 15:13:43 mikeb-ubuntu kernel: [   68.331638] eth1: link down
Jul 19 15:13:43 mikeb-ubuntu kernel: [   68.331883] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jul 19 15:13:48 mikeb-ubuntu kernel: [   73.528153] Bluetooth: Core ver 2.11
Jul 19 15:13:48 mikeb-ubuntu kernel: [   73.529719] NET: Registered protocol family 31
Jul 19 15:13:48 mikeb-ubuntu kernel: [   73.529728] Bluetooth: HCI device and connection manager initialized
Jul 19 15:13:48 mikeb-ubuntu kernel: [   73.529735] Bluetooth: HCI socket layer initialized
Jul 19 15:13:49 mikeb-ubuntu kernel: [   73.698258] Bluetooth: L2CAP ver 2.9
Jul 19 15:13:49 mikeb-ubuntu kernel: [   73.698269] Bluetooth: L2CAP socket layer initialized
Jul 19 15:13:49 mikeb-ubuntu kernel: [   73.767734] Bluetooth: RFCOMM socket layer initialized
Jul 19 15:13:49 mikeb-ubuntu kernel: [   73.767776] Bluetooth: RFCOMM TTY layer initialized
Jul 19 15:13:49 mikeb-ubuntu kernel: [   73.767779] Bluetooth: RFCOMM ver 1.8
Jul 19 15:13:51 mikeb-ubuntu kernel: [   75.616689] [drm] Initialized drm 1.1.0 20060810
Jul 19 15:13:51 mikeb-ubuntu kernel: [   75.699111] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 21
Jul 19 15:13:51 mikeb-ubuntu kernel: [   75.699302] [drm] Initialized mga 3.2.1 20051102 on minor 0
Jul 19 15:13:51 mikeb-ubuntu kernel: [   75.700683] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Jul 19 15:13:51 mikeb-ubuntu kernel: [   75.700707] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
Jul 19 15:13:51 mikeb-ubuntu kernel: [   75.700761] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
Jul 19 15:13:51 mikeb-ubuntu kernel: [   75.703583] [drm] Initialized card for AGP DMA.
Jul 19 15:33:30 mikeb-ubuntu -- MARK --
Jul 19 15:44:55 mikeb-ubuntu kernel: [ 1937.794318] bttv: driver version 0.9.17 loaded
Jul 19 15:44:55 mikeb-ubuntu kernel: [ 1937.794331] bttv: using 8 buffers with 2080k (520 pages) each for capture

---

### Post by dlanor78 on 2008-07-19
> **miguel20 said:**
> 
using every app I get no video... using cat /dev/video0 > ~/test.mpg i just get funny patterns scrolling about on the screen.
I'm just inputting raw video from an external satellite box.


Can you post a screen shot of the funny patterns so we can see what they look like?  It doesn't sound like it's just static, but if that's the case look to my previous post about ivtv-utils and the v4l2-ctl command.  If you get it working with that then keep in mind that every time you reboot the computer you have to use the v4l2-ctl command again (as far as I know).

If you already have ivtv-utils and already set the input and are still getting funny patterns on the file you get from a /dev/video0 > ~/test.mpg file, then depending on what program you're using to play the mpg file you may need to install more gstreamer packages such as gstreamer0.10-plugins-good (there's good, bad, and ugly).  Keep in mind that the bad and ugly are called that due to using restrictive file formats.  I use Kubuntu which doesn't use gstreamer so I'm not sure which one to install, but I'd start with gstreamer0.10-ffmpeg.

If you're using vlc to playback the mpg file, then I'm stumped so far because vlc plays just about everything even if those gstreamer packages aren't installed.

By the way, just give up on using tvtime with the Hauppauge cards.  It just won't work but I can't remember the reason why.  Kaffeine and xine will work, but I don't remember the command to do so.  I just find it easier to use vlc as posted in my previous post:

> 
Also, so far for viewing/recording I'm using vlc. Just use File>Open Capture Device...>PVR tab and make sure /dev/video0 is in the Device section.


Hopefully this will help you get up and running.  If I remember correctly, all I had to do to get the hauppauge working in a freshly booted live cd environment was install vlc and ivtv-utils.  Set the input with v4l2-ctl -i 2 then open in vlc.  That might be something to try as a last resort if all else fails.

Good luck!

---

### Post by miguel20 on 2008-07-20
Thanks very much dlanor... that has helped me I'm sure, I have now got a little futher.
I've switched completely to VLC as you advised and done the other bit.

Now in my VLC capture window I've got static instead. :-)

Is that a step forward or backwards.. it feels like forwards. :-)

I wonder if NOW I just have a tuning issue within the PVR-150?
The input to this card comes from a satellite receiver (SKY+ UK in PAL format).  I know this is ok as I had it working in WinXP but I used a prog which just found the input on it's own...

This input is what I call a raw feed (I'd appreciate someone correcting me on the naming for future reference) I don't use my PVR-150 to tune in to lots of channels I just use it to display this raw feed on my PC.
(Under Win if I wanted to change channel I change it on my SAT box. I'm happy with this for now.)

So what channel am I supposed to set the PVR-150 to? It is a mystery to me!

The only thing I could find on my SKY+ Sat box settings was RF was set to 68?  Is this a frequency or a channel?  How can I set my PVR-150 to this? Or do I just not get what's going on here?

Thanks

M


> **dlanor78 said:**
> Can you post a screen shot of the funny patterns so we can see what they look like?  It doesn't sound like it's just static, but if that's the case look to my previous post about ivtv-utils and the v4l2-ctl command.  If you get it working with that then keep in mind that every time you reboot the computer you have to use the v4l2-ctl command again (as far as I know).

If you already have ivtv-utils and already set the input and are still getting funny patterns on the file you get from a /dev/video0 > ~/test.mpg file, then depending on what program you're using to play the mpg file you may need to install more gstreamer packages such as gstreamer0.10-plugins-good (there's good, bad, and ugly).  Keep in mind that the bad and ugly are called that due to using restrictive file formats.  I use Kubuntu which doesn't use gstreamer so I'm not sure which one to install, but I'd start with gstreamer0.10-ffmpeg.

If you're using vlc to playback the mpg file, then I'm stumped so far because vlc plays just about everything even if those gstreamer packages aren't installed.

By the way, just give up on using tvtime with the Hauppauge cards.  It just won't work but I can't remember the reason why.  Kaffeine and xine will work, but I don't remember the command to do so.  I just find it easier to use vlc as posted in my previous post:



Hopefully this will help you get up and running.  If I remember correctly, all I had to do to get the hauppauge working in a freshly booted live cd environment was install vlc and ivtv-utils.  Set the input with v4l2-ctl -i 2 then open in vlc.  That might be something to try as a last resort if all else fails.

Good luck!

---

### Post by dlanor78 on 2008-07-20
This definitely sounds like a step forward.  Now I need to know how you're connecting the sat. box with the hauppauge card.  If you're using a coaxial cable (the kind you usually screw in) then you may need to change the channel on the hauppauge card to get it to work.  I don't use my card this way so I can't be sure, but you can try

```

ivtv-tune --channel=#

```

and put the channel where the # is.  Sounds like 68 would be the case here, but no guarantees.  

Or maybe the command

```

ivtv-tune -teurope-west -c68 -d/dev/video0

```

would be right (assuming that the UK is in Western Europe; geography was never my best subject in school ;-P).

Please see

> 
[http://ivtvdriver.org/index.php/Ivtv-tune](http://ivtvdriver.org/index.php/Ivtv-tune)


for a little more info on how to use ivtv-tune.  

Someone else might have to jump in here if this is how you're connecting.

If you're using a rca connection (yellow, red, and white plugs) to connect then you need to change the card to use composite connection.  This is how I use my card, so when I want to watch tv on the computer I have to do the command

```

v4l2-ctl -i 2

```

That tells my card to use the Composite 1 input.  Using

```

v4l2-ctl -n

```

I see that my card also has a Composite 2 input.  To use that I would need to issue a

```

v4l2-ctl -i 4

```

command.  For s-video 1 it would be

```

v4l2-ctl -i 2

```

and for s-video 2 it would be

```

v4l2-ctl -i 3

```

The easiest thing to do here if possible would be to connect with rca composite or s-video.  If you use coax then you have to tune the card to a channel first which should be possible, but to me just complicates things just a bit more.

Also, on the off chance that my card is slightly different from yours (mine might be a mce edition of the hauppauge pvr 150) then in a terminal just run

```

v4l2-ctl -n

```

to see what inputs are available on your card and what number they are.  Here's what my card says on that command:

```

ioctl: VIDIOC_ENUMINPUT                 
        Input   : 0                     
        Name    : Tuner 1               
        Type    : 0x00000001            
        Audioset: 0x00000007            
        Tuner   : 0x00000000            
        Standard: 0x0000000000001000 ( NTSC )
        Status  : 0                          

        Input   : 1
        Name    : S-Video 1
        Type    : 0x00000002
        Audioset: 0x00000007
        Tuner   : 0x00000000
        Standard: 0x0000000000FFFFFF ( PAL NTSC SECAM )
        Status  : 0                                    

        Input   : 2
        Name    : Composite 1
        Type    : 0x00000002 
        Audioset: 0x00000007 
        Tuner   : 0x00000000 
        Standard: 0x0000000000FFFFFF ( PAL NTSC SECAM )
        Status  : 0                                    

        Input   : 3
        Name    : S-Video 2
        Type    : 0x00000002
        Audioset: 0x00000007
        Tuner   : 0x00000000
        Standard: 0x0000000000FFFFFF ( PAL NTSC SECAM )
        Status  : 0

        Input   : 4
        Name    : Composite 2
        Type    : 0x00000002
        Audioset: 0x00000007
        Tuner   : 0x00000000
        Standard: 0x0000000000FFFFFF ( PAL NTSC SECAM )
        Status  : 0

```

Wow, long post here but I'm trying to cover everything I can think of.  I'm still kind of a newbie, so please be patient while we both try to figure this all out.  Please keep us updated on your progress and I'll keep trying to help out.  I personally only have time to do this stuff on Saturday and Sunday but if you need help on other days hopefully someone else can jump in here.

---

### Post by miguel20 on 2008-07-20
Hi dlanor,
thanks for sticking with me on this one!

I tried this 
setting v4l2-ctl -i 0

which on my PVR-150 is called tuner and that is the RF cable.
over here they are just a push on cable (also known as aerial cable)
i'm pretty sure this is different to the US?

nothing....

then I tried this as dlanor advised

ivtv-tune -teurope-west -c68 -d/dev/video0

and BINGO!  picture and sound :-)

so dlanor, you my friend, are a genius! A million thanks! :D

I had a fiddle to see if I could get other inputs working.
SVIDEO & RCA works too with the appropriate cable and setting

for svid
v4l2-ctl -i 1

for RCA
v4l2-ctl -i 2

both work as long as they are followed by 
ivtv-tune -teurope-west -c68 -d/dev/video0


I should note for anyone else who follows this:
my pvr-150 has svideo, rca and rf in .... and also an rf OUT. I think push on RF connections is a UK thing?
RCA seems to be the best quality....
also don't try alter the input settings with VLC open as it clearly locks it (on my set up anyway).

One last time...  dlanor thank you so much.  you've made me a happy man.:D
this issue was make or break for me and Ubuntu! 

Cheers

M


> **dlanor78 said:**
> This definitely sounds like a step forward.  Now I need to know how you're connecting the sat. box with the hauppauge card.  If you're using a coaxial cable (the kind you usually screw in) then you may need to change the channel on the hauppauge card to get it to work.  I don't use my card this way so I can't be sure, but you can try

```

ivtv-tune --channel=#

```

and put the channel where the # is.  Sounds like 68 would be the case here, but no guarantees.  

Or maybe the command

```

ivtv-tune -teurope-west -c68 -d/dev/video0

```

would be right (assuming that the UK is in Western Europe; geography was never my best subject in school ;-P).

Please see



for a little more info on how to use ivtv-tune.  

Someone else might have to jump in here if this is how you're connecting.

If you're using a rca connection (yellow, red, and white plugs) to connect then you need to change the card to use composite connection.  This is how I use my card, so when I want to watch tv on the computer I have to do the command

```

v4l2-ctl -i 2

```

That tells my card to use the Composite 1 input.  Using

```

v4l2-ctl -n

```

I see that my card also has a Composite 2 input.  To use that I would need to issue a

```

v4l2-ctl -i 4

```

command.  For s-video 1 it would be

```

v4l2-ctl -i 2

```

and for s-video 2 it would be

```

v4l2-ctl -i 3

```

The easiest thing to do here if possible would be to connect with rca composite or s-video.  If you use coax then you have to tune the card to a channel first which should be possible, but to me just complicates things just a bit more.

Also, on the off chance that my card is slightly different from yours (mine might be a mce edition of the hauppauge pvr 150) then in a terminal just run

```

v4l2-ctl -n

```

to see what inputs are available on your card and what number they are.  Here's what my card says on that command:

```

ioctl: VIDIOC_ENUMINPUT                 
        Input   : 0                     
        Name    : Tuner 1               
        Type    : 0x00000001            
        Audioset: 0x00000007            
        Tuner   : 0x00000000            
        Standard: 0x0000000000001000 ( NTSC )
        Status  : 0                          

        Input   : 1
        Name    : S-Video 1
        Type    : 0x00000002
        Audioset: 0x00000007
        Tuner   : 0x00000000
        Standard: 0x0000000000FFFFFF ( PAL NTSC SECAM )
        Status  : 0                                    

        Input   : 2
        Name    : Composite 1
        Type    : 0x00000002 
        Audioset: 0x00000007 
        Tuner   : 0x00000000 
        Standard: 0x0000000000FFFFFF ( PAL NTSC SECAM )
        Status  : 0                                    

        Input   : 3
        Name    : S-Video 2
        Type    : 0x00000002
        Audioset: 0x00000007
        Tuner   : 0x00000000
        Standard: 0x0000000000FFFFFF ( PAL NTSC SECAM )
        Status  : 0

        Input   : 4
        Name    : Composite 2
        Type    : 0x00000002
        Audioset: 0x00000007
        Tuner   : 0x00000000
        Standard: 0x0000000000FFFFFF ( PAL NTSC SECAM )
        Status  : 0

```

Wow, long post here but I'm trying to cover everything I can think of.  I'm still kind of a newbie, so please be patient while we both try to figure this all out.  Please keep us updated on your progress and I'll keep trying to help out.  I personally only have time to do this stuff on Saturday and Sunday but if you need help on other days hopefully someone else can jump in here.

---

