---
title: "HD Video Stutter Issues"
date: 2011-08-13
forum: Multimedia Software
---

### Post by Beacon11 on 2011-08-13
Hello all.

I've seen numerous posts regarding this issue, but none of the proposed solutions (e.g. changing VLC output to OpenGL or disabling compiz) work.

I'm running an up-to-date Ubuntu 10.04 installation, with proprietary ATI drivers for a Radeon HD 5850 (XFX Black edition, overclocked). I also have a dual core Intel E8500 processor. I dual-boot with Windows 7 for games and, until now, blurays (which play wonderfully well). I recently discovered makemkv, and have been experimenting playing my blurays in Linux. However, neither VLC or Totem will play the HD content to my satisfaction (i.e. video stutters horribly while the audio is fine). Makemkv creates a .mkv file (as you probably guessed). I don't know much about this format, but Ubuntu gives me the following details:

Video:
Dimensions: 1920 x 1080
Codec: H264
Framerate: 24 frames per second
Bitrate: N/A

Audio:
Codec: Dolby Digital (AC-3)
Channels: Surround 5.1
Sample rate: 48000 Hz
Bitrate: 640 kbps


As I said, playing this bluray works great in Windows, so I'm certain my hardware is good enough. Why can't I get this to play well in Linux? Is it a driver issue? Codec issue? Should I use ffmpeg and convert this file to something else in which VLC on Linux would rejoice? VLC in Windows plays this .mkv file perfectly.

Thanks for your help; this really isn't my strong suit.

---

### Post by Beacon11 on 2011-09-07
Bump-- does no one else have these issues? Are the ATI drivers lacking sufficient hardware acceleration?

---

### Post by papibe on 2011-09-07
In order to use video hardware acceleration on an ATI card you need to install an additional library (besides the proprietary driver).

Although, I don't know the exact details, I'm going to try to point you in the right direction.

You need the VA API library for your card (usually referred as vaapi or libva). I don't know the exact name of the ATI package. For Nvidia cards it is called vdpau-va-driver.

In my understanding 10.04 it is not ready 'as is' to use vaapi. Its VLC version doesn't include support for vaapi, and the vaapi library is not even available. If you were using 11.04 neither of that would be a problem.

If you want to stay in 10.04, it may be some options. There are ppa's to update you to the latest Xorg framework, ppa's for the latest VLC version, and (I think) ppa's for the vaapi library.

Again, please take this this with a grain of salt. You would need to do more research about the topic.

Here's some interesting links:
[LIST]
[*][Arch's wiki on the ATI Catalyst (video acceleration section).]("https://wiki.archlinux.org/index.php/ATI_Catalyst#Video_acceleration")
[*][Reference to vaapi for ATI on an Nvidia tutorial.]("http://ubuntuforums.org/showthread.php?t=1037625")
[/LIST]
It's all I can think right now (I'm sort of a Nvidia kind of guy),
Regards.

I hope someone will provide more accurate information.

---

### Post by Beacon11 on 2011-09-07
Thank you Papibe, that's exactly what I needed and gives me a great direction to go. I'm not at all stuck with 10.04, I just didn't have a reason to upgrade until now. I'll look into this and post back.

---

