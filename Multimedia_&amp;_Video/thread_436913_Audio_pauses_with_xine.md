---
title: "Audio pauses with xine"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by Road King on 2007-05-08
Rhythmbox plays audio from my iTunes library on Vista /sda1 
just fine.  That includes both mp3 and m4a files.

Totem-gstreamer plays DVDs fine (with its known limitations),
but has regular audio pauses every 2-4 seconds playing music
files.  Not a biggie since I don't use Totem for playing music.
It also plays the audio smoothly through the totem-mozilla 
plug-in in the CBS News video teaser before the main video, 
which it fails to play.  And it plays CNN videos fine.

Totem-xine (with chapter menus, etc) AND gxine have erratic 
audio pauses, about 1 per second, on both DVDs AND music files.
Totem-xine also has the same audio pauses playing CNN and
CBS News videos through the totem-mozilla plug-in.

Fox News (which never plays video) and MSNBC videos are Flash 
and not affected by xine.  ABC News video page doesn't even
load completely regardless of what player or plugin is used.

I'd like to have totem-xine working for the DVD menus.

I have installed and purged totem-xine, totem-gstreamer, 
totem-mozilla, and totem, autocleaned then reinstalled them.
I also purged linux-sound-base, alsa-base, and alsa-utils 
(which took out gdm and ubuntu-desktop), and reinstalled 
them all, per the Comprehensive Sound Problem Solutions Guide.
And I deleted ~/.xine to make sure the problem wasn't there.
None of these helped.

Relevant hardware is:
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: Dell Unknown device 0175
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at ec00 [size=256]
        I/O ports at e8c0 [size=64]
        Memory at dffffa00 (32-bit, non-prefetchable) [size=512]
        Memory at dffff900 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Unknown device 0175
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ffa0 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03) (prog-if 01 [AHCI 1.0])
        Subsystem: Dell Unknown device 0175
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
        I/O ports at fe00 [size=8]
        I/O ports at fe10 [size=4]
        I/O ports at fe20 [size=8]
        I/O ports at fe30 [size=4]
        I/O ports at fea0 [size=16]
        Memory at dffffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
        Subsystem: Dell Unknown device 0175
        Flags: medium devsel, IRQ 10
        I/O ports at e8a0 [size=32]

There is both a DVD drive and DVD-RW drive installed on 
the IDE controller and the problem occurs on both.  The 
hard drive is SATA.  This doesn't seem like it would be an 
issue, since the audio doesn't pause when the DVD is 
played from Totem-gstreamer, and the same audio 
pausing in Totem-xine is happening when playing music 
off the hard drive or streaming from the Internet.

Installed are:
libdvdplay0
libdvdnav4
libdvdread3
libdvdcss2

Gstreamer install includes:
libgstreamer0.10-0
libgstreamer-plugins-base0.10-0
gstreamer0.10-alsa
gstreamer0.10-esd
gstreamer0.10-gnomevfs
gstreamer0.10-x
gstreamer0.10-ffmpeg
gstreamer-plugins-base
gstreamer-plugins-good
gstreamer-plugins-ugly
gstreamer-plugins-ugly-multiverse
gstreamer-plugins-bad
gstreamer-plugins-bad-multiverse
gstreamer0.10-tools
gstreamer-tools

Xine install includes:
libxine1
libdmx1
libxineerama1
libxine1-console
libxine1-kde
libxine1-gnome
libxine1-plugins
libxine1-ffmpeg
libxine1-extracodecs
gxine

Suggestions welcome!

---

