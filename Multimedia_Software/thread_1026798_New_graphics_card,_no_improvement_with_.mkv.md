---
title: "New graphics card, no improvement with .mkv"
date: 2008-12-31
forum: Multimedia Software
---

### Post by Skeorx13 on 2008-12-31
I recently purchased a 9600 gt to replace my 7600 gt because the new one is HDCP ready and the old one is not. I figured it should help out quite a bit with .mkv files so I can watch full 1080p. 720p was skipping rarely but it happened once in a while and I also wanted to clear that up. But upon putting in the new card which has more ram and a higher clock the graphics quality actually went down a little. I tried installing the proprietary drivers downloaded directly from nvidia's site for linux but it took me about 3 hours to get the damn things to compile. Then when I did it wouldn't even recognize the card (it only listed up to series 8 geforce for some reason) and wouldn't let me go beyond 800x600 resolution. So I rebuilt xserver and reverted to the open source drivers to get my resolution back to 1920x1080. With the 7600 I was running the proprietary drivers when I did the install of 8.04. I didn't really do anything, it just asked if I wanted to use them and installed them. But now I can't figure out how to turn them back on. I check the proprietary drivers section and it says none are installed. 

One issue did pop in my head though. My mobo is pci-express 1.0, and the card is 2.0. Could this be an issue? But regardless the new card is way better so I should at least see a slight improvement rather than the opposite shouldn't I?

system runs: 
Pentium D (830)
Intel D945PVSLKR mobo
3 GB ddr2 667 (2x1gb, 2x512)
52" LCD samsung HDTV, full 1080p, dvi to hdmi.

---

### Post by shirilover on 2008-12-31
Your graphics card is not an isuue, as there is no hardware acceleration of h.264 video streams in linux. All decoding is done by your processor.

---

### Post by Skeorx13 on 2009-01-02
Is this a graphics driver issue or something fundamental about linux that prevents it?

---

### Post by shirilover on 2009-01-02
It's a driver issue.

---

### Post by Skeorx13 on 2009-01-03
I was poking around and found some snippets about h.264 decoding in Linux. They mentioned VDPAU. Would this do anything for the mkv files? And how would one go about implementing this? Do any of the video players in linux actually use VDPAU yet? I believe it just came out a few months ago so I'm guessing not many do.

---

### Post by steeleyuk on 2009-01-03
There's a highly experimental patch for mplayer around. I think someone has patched xine as well but again, its highly experimental. There's reports of it not working on some configurations but thats to be expected really.

---

### Post by pietjanjaap on 2009-01-03
Look at this:
[http://ubuntuforums.org/showthread.php?t=1006435&highlight=mkv](http://ubuntuforums.org/showthread.php?t=1006435&highlight=mkv)

Maybe this helps.

---

### Post by jespdj on 2009-01-03
Try the newest nVidia drivers (version 180 beta). nVidia included support for VDPAU in those drivers, which should make playing HD-video content under Linux much better.

---

### Post by Skeorx13 on 2009-01-03
Is there a simple way to install the beta drivers? I tried downloading the drivers from nvidia's website and followed their directions. Installing/compiling the 177 drivers took me several hours just to find the right run level and figuring out the exact way it wants me to shut down the xserver for the effin' thing to compile. Then it wouldn't even work properly.

---

### Post by Skeorx13 on 2009-01-15
Ok, well I upgraded ubuntu to version 8.10 in the hopes it would do something. It did. It recognized that I had an nvidia card and asked to download and install the 177 drivers. I have them working now. The media files will play at the same performance as the 7600gt but the 1080p mkv files still lag just like the 7600gt. I would like to try out the 180.22 driver that is available from nvidia but the repositories in synaptic don't have it available yet for some reason. 

Also a big issue I've come across, VLC sound no longer works for mkv files but will for everything else. My master sound no longer allows me to increase or decrease volume. I can only do it through mplayer or through vlc on non-mkv files (or my tuner, of course). mplayer, when playing 1080p files, throws an endless loop of errors: too many video packets in the buffer. I uninstalled and reinstalled vlc and tried again but got the same results. I also noticed when I right click on a video file there are two options for "open with vlc player". One does nothing. I uninstalled vlc again and checked again. Now there is one option for "open with vlc player" that does nothing and vlc is not installed (I double checked in synaptic to be sure). What is with the phantom player option???

---

### Post by webaake on 2009-01-15
I have a 7600GS and have alwyas had stuttering x264 (mkv) video playback - unusable.

UNTIL Nvidia 180.xx !! No stuttering anymore!

Here are som pretty straight forward instructions for installing;

[http://technowizah.com/2006/11/debian-how-to-nvidia-drivers.html](http://technowizah.com/2006/11/debian-how-to-nvidia-drivers.html)

---

