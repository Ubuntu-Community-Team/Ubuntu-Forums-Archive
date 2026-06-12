---
title: "Forcing GPU video engine processing"
date: 2021-12-26
forum: Multimedia Software
---

### Post by gdesilva on 2021-12-26
Hi,

I am running Lubuntu 20.04 with a nVidia Geforce GT710 card (nvidia 470.86 driver)

I notice that when I play some mp4 video files on Vlc, both the GPU utilisation and the video engine utilisation on the nvidia card go up - resulting in a low CPU utilisation on the machine.

However, if I use mkv format of the same file on Vlc only the GPU utilisation goes up and video engine utilisation stays at 0%. When this happens, the CPU utilisation hovers around 150% and results in high video jitter and loss of audio/video sync.

I also notice that when I play a video on Brave (with hardware acceleration on) while the GPU utilisation goes up the video engine utilisation stays at 0 utilisation and CPU utilisation hovering around 40%.

The question is how do I off load all video processing on to the GPU to free up CPU utilisation as I am running an old Pentium Duo CPU.

Many thanks.

---

### Post by csae2608 on 2022-01-02
maybe the GT 710 cannot decode newer format very well like VP9, Av1 and similar which are increasingly used on Youtube and similar.
If you downloaded an Mp4 from there, chances are high that they are encoded in those format and therefore the GPU would offload the work onto the CPU, and therefore you have high CPU utilisation.

you can check which codec the mp4 uses with the app 

> mediainfo


another way to playback newer mp4 on older systems is to transcode them to files that the graphics card can process easily, with tools like 
> handbrake

here you can check the decoding/encoding capabilities of your graphics card and others from Nvidia

[URL="https://developer.nvidia.com/video-encode-and-decode-gpu-support-matrix-new"]https://developer.nvidia.com/video-encode-and-decode-gpu-support-matrix-new


[/URL]

EDIT: actually the GT 710 is missing in the matrix outlined above by Nvidia, you can find it here on WiKipedia

[https://en.wikipedia.org/wiki/Nvidia_NVDEC](https://en.wikipedia.org/wiki/Nvidia_NVDEC)

---

