---
title: "For those of you having problems with movies, use VLC"
date: 2008-10-22
forum: Multimedia Software
---

### Post by kaldor on 2008-10-22
Use "sudo apt-get install vlc" to get VLC media player.

I was unable to use my DVDs for months because of codecs/freezing etc. I downloaded VLC tonight, popped in a DVD, and it worked fine. 

Open VLC Media Player. Click File>Open Disc>OK

This should run your DVD, or any other media just fine.

Enjoy :)

---

### Post by brianpatrick on 2008-10-28
No luck with VLC

I installed VLC media player with Symaptic (and the help of the alternate /etc/apt/sources.list hack). What I am seeing is a mostly black screen with pea sized chunks of random colors and an occasional glimpse of the movie in the background. 

I have tried the openGL, openGl(GLX), xvideo, and x11 output modules as well as the theora, x264 and fake video codecs. All options appear to make no difference. 

Xine tells me that the source (Terminator I SE, retail box) seems encrypted. I have compiled libdvdcss from latest source (without csskeys.h) and installed it as root. 

Totem Movie Player 2.22.1 shows the video_tx.ifo part way through, but mangled and chopy as though it is refreshing 1 horizontal inch of the screen at a time. The audio is on for half a second then off for half a second. They it dies with a black screen and no sound. 

Ogle shows a black screen, most of the audio with occasional sharp chirps. 

Realplayer 11 tries to open /media/E2952/VIDEO_TS/video_ts.ifo and complains that it can't have capabilities to play this content. Update is useless as it is the latest. Helix player does exactly the same thing. 

On BBC Galapagos, VLC has 1/2 second audio, 1/2 second silent, and occasional glimpses of the title screen. 

I have an ASUS P5Q3 DELUXE/WIFI-AP CH1-11 LGA 775 Intel P45 mobo, q9550 quad core 2.83 ghz intel cpu, ddr3/4gb, msi ati r4850-512M video card with directx 10.1 and opengl 2.1, Syncmaster 305T, 30 inch, 2560x1600 lcd. 

I am running Ubuntu 8.04 64 bit workstation with almost everything installed with synaptic. I have the ati accelerated graphics driver installed with latest from ati.amd.com.

Any DVD movie player which works will be fine, hopefully at full screen. Any ideas?

Thanks,
    BrianP

---

