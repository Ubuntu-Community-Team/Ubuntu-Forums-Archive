---
title: "Lost Amarok MP3 support. Was working before. xine-check result inside."
date: 2008-03-25
forum: Multimedia &amp; Video
---

### Post by Hauk on 2008-03-25
Hi,

I've been lurking here for a while, basically using this place as a knowledge-base of information, which has proved great.

I'm using Ubuntu Gutsy Gibbon 7.10. i386.

The hardware side of things.

AMD A64 3200+
ASUS A8N-SLi Deluxe Motherboard.
1GB RAM
XFX GeForce 7800 GTX

I've been trying to get Flash working in Firefox 2.0.0.6, and I followed [this]("https://wiki.ubuntu.com/PulseAudio") guide for installing pulseAudio to try and get flash working. I followed it because it was linked from an article on trying to get flash working in firefox.

Anywho, long story short, after installing PulseAudio, I lost sound support in amarok. I have sound working for .avi movies in Totem, but not in VLC.

In System -> Preferences -> Sound, I have my C-Media USB Headset as the Device listed under Default Mixer Tracks.

Sound Events: Sound Playback: USB Audio. The test works.

Music and Movies: Sound Playback: USB Audio: The test works.

Audio Conferencing: Sound Playback: USB Audio: The test works.

Audio Conferencing: Sound Capture: USB Audio: Error(I'll deal with this later)

I ran the xine-check and got the following:

```
hauk@hauk-desktop:~$ xine-check
Please be patient, this script may take a while to run...
[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.22-14-generic)
[ good ] intel compatible processor, checking MTRR support
[ hint ] you have MTRR support but it's unused.
         It seems like your X server didn't set any MTRR ranges for the
         graphics card. Maybe upgrading your X server helps...
         You don't have a PCI graphics card, do you? AFAIK, MTRR only
         helps with AGP cards.
         press <enter> to continue...

[ good ] found the player at /usr/bin/xine
[ good ] /usr/bin/xine is in your PATH
[ hint ] No xine-config found. Assuming xine from Debian package
         The xine-config script can be used to determine some file locations
         used by xine-lib, but you don't have such a script on your system.
         However, it looks like you installed xine from the Debian packages.
         So I'll just guess that you are using the standard locations.
         If you want me to be sure about those file locations, you can install
         the 'libxine-dev' package, which contains xine-config. However, this
         package is not really needed to run xine...
         press <enter> to continue...

[ good ] plugin directory /usr/lib/xine/plugins exists.
[OUCH!!] There are no input plugins.
         xine needs at least one input plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no demux plugins.
         xine needs at least one demux plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no decoder plugins.
         xine needs at least one decoder plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no video_out plugins.
         xine needs at least one video_out plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no audio_out plugins.
         xine needs at least one audio_out plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[ good ] skin directory /usr/share/xine/skins exists.
[ good ] found logo in /usr/share/xine/skins
[ good ] I even found some skins.
[ good ] /dev/cdrom points to /dev/hda
[ good ] /dev/dvd points to /dev/hda
[ good ] DMA is enabled for your DVD drive
[ good ] found xvinfo: X-Video Extension version 2.2
[ good ] your Xv extension supports YV12 overlays (improves MPEG performance)
[ good ] your Xv extension supports YUY2 overlays
[ good ] Xv ports:  YUY2 YV12 UYVY I420 YUY2 YV12 UYVY I420

``` 

I re-installed the xine-engine. No luck.

I've pretty much run out of idea's at this stage. I had Amarok's MP3 playback running perfectly until up until this. :(

And sorry if this sounds really noobish, I tried to provide as much info as possible.

Thanks for the replies,

Hauk

---

