---
title: "DXVA enabled media player"
date: 2010-01-10
forum: Multimedia Software
---

### Post by Sorceror71 on 2010-01-10
I'm new to Ubuntu and I was wondering if there were any media players that were dxva enabled which is to say that the video is sent through the video card leaving the cpu mostly freed up. Doing this actually allows me to play HD 720p files whereas the playback on these files is rather choppy when being rendered using the cpu as per most media players.  Normally I use Media Player Classic - Home Theatre Edition under Windows XP which allows this dxva function.  Does any linux media player have this capability?

---

### Post by tikal808 on 2010-02-02
[DXVA]("http://en.wikipedia.org/wiki/DXVA") stands for DirectX Video Acceleration.  DirectX is Microsoft Windows API for interfacing with graphics cards. (GPU)

[VDPAU]("http://en.wikipedia.org/wiki/VDPAU") is the equivalent Video Acceleration API for GNU/Linux. Currently the video player named Mplayer supports VDPAU with NVIDIA graphics cards.  I have used [Mplayer's VDPAU]("https://launchpad.net/~nvidia-vdpau/+archive/ppa") from the command line with success to watch HiDef movies on a friends computer with a supported Nvidia graphics card.  ..But have been unable to do the same with the GUI.

On a separate note I'm really hoping that Intel will get the ball rolling faster with their implementation of VDPAU for Intel based GPU's like the one in my notebook computer.  I recently installed Windows on my notebook to test out DXVA with Media Player Classic HC, and it worked very well. I was able to play 1080p files with very low CPU usage.  But now that I'm back to Ubuntu on my notebook computer, I have no video acceleration abilities for h.264 video files. It's quite disappointing.  But on a brighter note, cheers to Nvidia for their VDPAU implementation.

---

