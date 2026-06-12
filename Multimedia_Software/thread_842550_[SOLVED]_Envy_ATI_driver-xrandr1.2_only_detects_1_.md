---
title: "[SOLVED] Envy ATI driver-xrandr1.2 only detects 1 monitor and other issues"
date: 2008-06-27
forum: Multimedia Software
---

### Post by ZabiGG on 2008-06-27
Hi everyone ;)

I've been fiddling with this issue for days and tried every howto under the sun, but I can't get my two monitors (JVC LT-40X776 + Dell 2001FP) to play nice because of different  aspect ratios (16:9 vs 4:3). 

EDIT: Catalyst detects both monitors but won't let me set two different resolutions.

The LT-40X776 is connected via DVI (DVI-0 based on what I could find in ati  documentation) and the 2001 FP is connected via VGA (VGA-0). xrandr only detects one, i.e. I have to unplug one for it to detect a "main monitor," but it always fails to detect both at once. With the recent changes to xorg, it appears traditional dual screen configurations just crash the system and trigger a low graphics mode startup. Of course, I can't read the messages since the text is in 2pt size. (I'd love to change that, but 2 days worth of research have given me zip, and changes to the greeter XML file don't resize the error messages).

EDIT: _**The issue below is solved using the newest ATI driver.**_ Completely purged everything and started from scratch using the cchtml wiki, but was careful to follow 64-bit instructions instead of normal dpgk step. Had to cd .. at some points not specified in the guide for everything to work, though.

[I]I'm using one graphic card, an ATI HD2600Pro on pci bus 1:0:0, which xorg refuses to detect correctly because the envy driver won't initialize properly. 

(aticonfig --initial -f gives me this error:
me@my-desktop:~$ aticonfig --initial -f
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-3
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.)

After sifting through about 50 web pages about this error, I still can't solve that problem, so I gave up since I do have an acceptable image on at least one of my monitors.
[/I]   
fglrxinfo gives me this:

me@my-desktop:/etc/X11$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2600 Pro
OpenGL version string: 1.4 (2.1.7415 Release)

_**Solved:**_ Whenever I try to reset the driver, everything gets all messed up, so I'd rather not play with it. I've tried the open source ati driver, the radeonhd driver, the envy driver, and even tried to compile the most recent ati driver which won't work because of a badly programmed redirection script. I've purged the system of everything and reinstalled the envy driver which is supposed to be compatible with xrandr... no joy.

_**Still unsolved:**_ What I'd like to achieve is simple: 

I want the same image on both screens, but in a "native resolution" for each (1680x1050 for the JVC flat panel TV and 1280x1024 for the Dell flat panel monitor)

Here are the relevant sections of my latest xorg configuration attempt which, of course, just sends me into low-graphics mode and resets everything to vesa 800x600, on the Dell monitor only.

Section "Device"
    Identifier    "0 Configured Video Device"
    Option        "VideoOverlay"    "on"
    Option        "OpenGLOverlay"    "off"
    Driver        "fglrx"
    BusID            "PCI:1:0:0"
       Screen    0
    Option         "DDCMode" "True"
    Option         "MonitorLayout" "TMDS1"

EndSection

Section "Device"
    Identifier    "1 Configured Video Device"
    Option        "VideoOverlay"    "on"
    Option        "OpenGLOverlay"    "off"
    Driver        "fglrx"
    BusID            "PCI:1:0:0"
       Screen    1
    Option         "DDCMode" "True"
    Option         "MonitorLayout" "CRT1" ### the monitor is a flat-panel LCD , but that's
                                                                how xrandr detects it on the VGA-0 output
EndSection

Section "Monitor"
    Identifier    "TMDS1"
EndSection

Section "Monitor"
    Identifier    "CRT1"
EndSection

Section "Screen"
    Identifier    "Screen 0"
    Monitor       "TMDS1"
    Device        "0 Configured Video Device"
    Defaultdepth    24
        Modes         "1680x1050" "1280x960" "1152x864"
EndSection

Section "Screen"
    Identifier    "Screen 1"
    Monitor       "CRT1"
    Device        "1 Configured Video Device"
    Defaultdepth    24
        Modes         "1280x1024" "1024x768"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        0 "Screen 0"
        Screen        1 "Screen 1" RightOf "Screen 0"
    InputDevice     "stylus"    "SendCoreEvents"
    InputDevice     "cursor"    "SendCoreEvents"
    InputDevice     "eraser"    "SendCoreEvents"
    InputDevice    "pad"
    Option         "Xinerama"     "false"
EndSection

I don't mind doing the necessary research, but I'm nothing if not stumped at this point.
Could someone at least point me in the right direction to solve these issues? Sorry this is so long winded.

Thanks in advance,

Z.

---

### Post by ZabiGG on 2008-06-28
The system font size is solved by cheating in the xorg.conf file.

Instead of entering the actual DisplaySize value (which should be 850 495) under the Monitor section, I entered the smallest resolution values of my system (320 200), figuring the aspect ratio would at least be correct.

It worked. After a complete system restart the system font size is now legible.

So now, all that remains is being able to "clone" the monitors, but using two different resolutions. Unplugging each and reconfiguring individually works, but reverts back to the Dell monitor as default with an oversized display as soon as both monitors are connected. Catalyst 8.6 still won't let me define individual resolutions for the monitors, except in big desktop mode, which I don't want.

xrandr still just detects the default monitor, and does not list the outputs as explained here:
[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

It just gives me the Screen 0 line + resolution list below

Of course, I've reset xorg.conf to defaults (relevant sections here):

Section "ServerLayout"
    Identifier       "Default Layout"
    Screen      0   "aticonfig-Screen[0]-0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "pad"
    Option            "AIGLX" "on"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    DisplaySize 320 200
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


What I really don't understand is how Catalyst properly detects both monitors and models while xserver sees only one generic monitor...

Anyone?

---

### Post by ZabiGG on 2008-06-28
BTW

aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

is easily solved: aticonfig commands require good ol' sudo

---

### Post by markbuntu on 2008-06-28
Have you tried reconfiguring x from a terminal with both monitors plugged in and turned on?

 sudo dpkg-reconfigure -phigh xserver-xorg

and then running:

aticonfig -f

You can type aticonfig --help and it will give you a list of options. You can use aticonfig directly to set the resolution of the second monitor. Catalyst Control Center does not have all the options aticonfig is capable of. You should probably try this first.

---

### Post by ZabiGG on 2008-06-29
Yup, reconfigured the xserver a number of times. 

I've been trying to figure out aticonfig for a few hours now. Here are my findings:

- although the monitor is connected to VGA, aticonfig detects it (crt1) on DVI-1
- the HDTV is what is actually connected via DVI (with a DVI-to-HDMI jack) and is also reported on DVI-1, as tmds1
- when I disconnect the VGA and restart, my HDTV screen remains black upon startup, but when I connect the VGA and restart, HDTV image returns... which leads me to believe the issue is with the HD2600 card. I roamed through the ATI knowledge base and found zip about that problem (might be as simple as a dip switch, but I'll need to get my hands on the actual drawings and specs to verify that)
- I enabled SurroundView in my bios, which changed my pci to 2:0:0 instead of 1:0:0
- I tried pluging the VGA on the onboard graphics card (I had re-enabled in the bios) and the HDTV on DVI. Result was no display on either.
- I tried HDMI-HDMI (there is an HDMI port in my ati card), which doesn't work due to HTPC compliance from what I could gather.

So I tried reconfiguring with aticonfig --initial -dual=head
Set up the resolutions I wanted on both screens, which were individual X sessions
Every setting was entered via aticonfig (whose help file is really not helpful...lol)

The result was nice, and I rather liked it.

But that setup led to 
- CTRL-ALT-Backspace crashing my system
- Being unable to use compiz

So I gave up and returned aticonfig to --initial -f, and...

- The image on the TV is perfect
- The image on the monitor is too big and requires mouse panning
- CTRL-ALT-Backspace now works fine
- Compiz works fine
- Catalyst segfaults

The aticonfig help file specifies that clone mode provides for setting different resolutions. I tried setting it in normal mode and in dual-head mode using desktop-layout, but Xorg just ignores it (less /var/log/Xorg.0.log confirmed that). I tried adding a paired mode with this result

me@my-desktop:~$ sudo aticonfig --add-pairmode=1680x1050+1280x1024
[sudo] password for me: 
FGLRX_AddPairMode failed when try to add mode : 1680x1050+1280x1024

At this point, I guess I'd have much less trouble changing video cards :p 

I'm just about ready to give up too, so I guess I'll have to live with panning on the monitor or with a scrunched down image on the HDTV. Or with changing the resolution each time I use either. 

I'm sure I haven't yet explored all the configuration options in aticonfig, but that help file is REALLY unclear.

---

### Post by markbuntu on 2008-06-29
Have you tried switching the dvi plugs. For some reason I think the ati driver needs the tv to be the secondary monitor (screen1), not the primary(screen0). 

And yes, the --help file is pretty cryptic and incomplete.

---

### Post by ZabiGG on 2008-06-29
Nice suggestion Mark, thanks. But the card has one VGA out (blue) and one DVI out (white) only, so that would mean converting VGA into HDMI which is rather contrary to the purpose. I could use Supervideo also, but then why would I use an HDTV? (lol)

Is there any software way to work around this? My Dell monitor is considered default and reported as the primary display.

less /var/log/Xorg.0.log attached.

A few things strike me as odd:

- PCI:*(2:0:0) ATI Technologies Inc unknown chipset (0x9589) rev 0, Mem @ 0xd0000000/28, 0xfdde0000/16, I/O @ 0xee00/8 -- the chipset and card are detected correctly later in the file

- (WW) fglrx: No matching Device section for instance (BusID PCI:1:5:0) found -- that would be normal for now, since it's the basic onboard X1200 video card and nothing's connected to it right now

- (--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR2 -- from my computer specs (64-bit AM5100-E5302A, Acer Aspire, Phenom 9500, 8 GB RAM, 800 GB SATA) my card is supposed to be 512MB

- (WW) fglrx(0): board is an unknown third party board, chipset is supported -- but it is listed properly a few lines above

- Dell monitor reported as display 1, JVC HDTV as display 2

but then, there's this
(II) fglrx(0): Primary Controller - DFP on internal TMDS
(II) fglrx(0): Secondary Controller - CRT on primary DAC

- (WW) fglrx(0): Probed monitor is 890x500 mm, using Displaysize 320x200 mm -- I guess it probes the secondary display instead of the primary because of the controllers?

- Warning: LookupDrawable()/SecurityLookupDrawable() are deprecated.  Please convert your driver/module to use dixLookupDrawable(). -- researched that and found nothing informative


From what I could find on the web, the X1200 card is not too shabby, although only 128MB. Luckily, I have a few spare partitions set aside for VMs, so I'll try a test install with the VGA plugged into that one to see how that goes. 

It also appears I read aticonfig wrong and that my DVI is I, not 1, which explains the dual analog-digital outputs. Although listed as a separate display in the log, I have this strange feeling the HDTV is merely TV-out, which would mean there's no way to clone to different resolutions and refresh rates without changing tv geometry and losing pixels.

The more i find out, the more lost I feel (lol). The ideal and seemingly simple solution would be to switch controllers. Is there any way this could be achieved?

I'll keep on researching, but your help is appreciated, thanks.

Cheers,

Z.

---

### Post by markbuntu on 2008-06-29
You really need to disable the on board video in the bios. If fglrx can find it, it will try to use it and become confused. That could be your problem because I am sure other people have not had so much difficulty in setting up that card with a tv and a monitor.

---

### Post by ZabiGG on 2008-06-29
Did already. Replugged everything, at least the HDTV works by itself without the VGA plugged in now. I will try a test install on another partition sometime this week to see how that works.

Thanks again for your help.

Z.

---

### Post by ZabiGG on 2008-07-01
The plot thickens...

After a test install on another partition, it appears the dual-head configuration (two different X screens) using aticonfig breaks the ALT key somehow. Trying to switch between application windows confirmed it. Surfing the web to see if anyone else has experienced this...

---

### Post by alibro on 2008-07-01
You have done well getting two screens to work at all with an ATI card. After struggling for a couple of days I gave up and installed an Nvidia card. I'm not sure how easy it is to set up a wide screen monitor but using sudo nvidia-settings I have no trouble changing resolution or refresh rate.

Cheers
Alibro

---

### Post by ZabiGG on 2008-07-01
At this point, I am seriously considering getting an NVidia card too! lol... and there are no two ways about it --  ATI is the problem. There are some posts on the phoronix forum from people who have similar problems.

The only "suitable" solution I've found for now is to set both screens to 1440x1050 and live with the distortion without (at least) having to pan the mouse on the smaller monitor.

Even with a fresh install on the HDTV exclusively (in safe graphics mode, otherwise I only got a black screen after the splash page), setting it as the primary display, aticonfig still considers the smaller screen as primary. I figure the card considers VGA the primary display as default even if the monitor was only hot plugged after a number of setting adjustments and reboots. Since xorg considers that the DVI is the primary display from the install, any settings other than --initial -f with aticonfig just scr**w up X.

And that card is so weird that xrandr still doesn't see any port on it other than the one the main display is plugged in...

I'll keep looking! :)

Z.

---

### Post by markbuntu on 2008-07-01
I had absolutely no difficulties at all getting two monitors to work with my HD3650 card using both i386 and amd64 Ubuntu8.04 (I use both). The primary is a 24inch widescreen LCD and the secondary is a standard 19 inch LCD.

I had no need to do a clean install. I just plugged the card in and plugged the monitors into it and then disabled the on board video and enabled the new card in the bios and booted up, logged in, got the restricted driver, set up the displays with Catalyst Control Center, and did a ctrl-alt-backspace to reset x. Voila, monster extended desktop.

Since then I have updated the driver twice to 8.5 and then 8.6 and have had aboslutely no problems at all at any time. This is with both i386 hardy and amd64 hardy.

With my old 200m on board I had nothing but problems, Envy became a nightmare. Since it didn't support 2 monitors I had every excuse to get a new video card and it has been smooth sailing ever since.

Finding the right directions to follow is critical to success.
I get my drivers from here:


[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat85-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat85-inst.html)

I install them using Method 2 from here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

And I tweak them with directions from here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

It works every time.

---

### Post by ZabiGG on 2008-07-01
I did the same thing, Mark ;) But from what I could gather all over the Web, the HD2600 Pro is probably the buggiest card of them all (lol), and you have to be twice as careful with it because it comes in AGP and PCI ex flavours, too (mine is PCI ex). When I use the 8.6 driver in clone mode, it works if I'm not picky about the resolution on the second screen. It just really doesn't like dual-head mode or xrandr.

Thanks for all your help, though ;)

Z.

---

### Post by ZabiGG on 2008-07-03
Issue solved:

xrandr works
dual-head works
compiz works on both screens
no more glitching when I watch a video

;)

How?

Three simple steps:

1) purchased nvidia 8800 GT card
2) installed newest driver
3) configured using nvidia-settings

All in all, it took a huge 30 minutes after a week of trying to solve problems. 

Conclusion: ATI HD2600 Pro can only be used with a clone configuration of same resolution, period. 

It's a shame, though.

Now I'll have to start a new thread to figure out how to solve the single issue I have with the new NVidia card: HDTV overscanning.

I read creating a custom edid file could solve this, cause bad edid detection clearly is the problem (compared with the edid data the ati card read).

Just need to learn how to understand and edit Hex ;) 

Pointers anyone?

Cheers,

Z.

---

