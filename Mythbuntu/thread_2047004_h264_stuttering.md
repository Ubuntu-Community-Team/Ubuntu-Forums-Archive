---
title: "h264 stuttering"
date: 2012-08-24
forum: Mythbuntu
---

### Post by kublikhan on 2012-08-24
I am trying to play an HD H.264 file on my Mythbuntu box. But VLC stutters and on mplayer the audio-video goes out of sync. The file plays fine on my windows box. My cpu is underpowered for software decoding(Athlon 3200). So I was hoping to use hardware decoding. I believe my video card comes with a H.264 decoder on it(NVidia Geforece 7600 GS). But thus far I have not been able to get HD H.264 files to play smoothly.

System specs:
Ubuntu 10.04.4 Lucid
NVidia Geforce 7600 GS
AMD Athlon 64 Processor 3200+
Video Driver: Proprietary driver - NVIDIA accelerated graphics driver (version current) [Recommended]
VLC version 1.1.13
mplayer version: 1.0rc4-4.4.3

Sample file trying to play:
Video: MPEG4 Video (H264) 1920x800 23.98fps [Undetermined (Video 1)]
Audio: Dolby AC3 48000Hz 6ch [English (Audio 1)]

[http://www.webupd8.org/2010/10/use-mplayer-with-vaapi-support-hardware.html](http://www.webupd8.org/2010/10/use-mplayer-with-vaapi-support-hardware.html)
I found the above website that has instructions for enabling hardware acceleration in MPlayer for Ubuntu 10.04. But it didn't work for me. The library it said to install is already installed. And the command to execute mplayer gave an error:
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3), -aid 0, -alang eng
[mkv] Track ID 3: subtitles (S_TEXT/UTF8), -sid 0, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1920x800  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Xlib:  extension "NV-GLX" missing on display ":0.0".
[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Video: no video

I also tried the link here: [http://ubuntuforums.org/showthread.php?t=1476992](http://ubuntuforums.org/showthread.php?t=1476992)
I added the repository "ppa:nvidia-vdpau/cutting-edge-multimedia" without error and did a "sudo apt-get update". it seemed to update ok, but my original problem remains: vlc stutters and mplayer out of sync. I am not sure what I should try next.

---

### Post by SeijiSensei on 2012-08-24
Your NVIDIA card doesn't support hardware decoding.  You need a 8xxx series or later adapter.  Given how [cheap]("http://www.newegg.com/Store/SubCategory.aspx?SubCategory=48&name=Desktop-Graphics-Cards&Order=PRICE") a decent NVIDIA card is these days, I'd upgrade the graphics card.

You still won't be able to watch the newer 10-bit H.264 format as the onboard graphics controllers do not yet support this.  But you'll be able to watch any 8-bit H.264 release.

---

### Post by kublikhan on 2012-08-25
Thanks for the info. I have some other video cards including a Geforce 8400, but they are PCI-Express, the motherboard is AGP. Most of the AGP cards for sale on newegg are older than the card currently in the system. They do have an AGP Radeon HD 3450 and a Radeon HD 4350 for sale. Do you think one of those cards would work for my needs? It seems it would be cheaper to buy a new video card then to upgrade the entire system. These guys seem to got it working ok: [http://ubuntuforums.org/showthread.php?t=1518160]("http://ubuntuforums.org/showthread.php?t=1518160")

---

### Post by SeijiSensei on 2012-08-25
I avoid ATI graphics hardware since ATI has a history of poor proprietary Linux drivers in comparison to NVIDIA.  However other people here have had better experiences with Radeons of late, so you might be okay.

---

### Post by nickrout on 2012-08-26
> **kublikhan said:**
> Thanks for the info. I have some other video cards including a Geforce 8400, but they are PCI-Express, the motherboard is AGP. Most of the AGP cards for sale on newegg are older than the card currently in the system. They do have an AGP Radeon HD 3450 and a Radeon HD 4350 for sale. Do you think one of those cards would work for my needs? It seems it would be cheaper to buy a new video card then to upgrade the entire system. These guys seem to got it working ok: [http://ubuntuforums.org/showthread.php?t=1518160]("http://ubuntuforums.org/showthread.php?t=1518160")

I don't think that there are any AGP based VDPAU compatible cards, so you are SOL on that front.

---

