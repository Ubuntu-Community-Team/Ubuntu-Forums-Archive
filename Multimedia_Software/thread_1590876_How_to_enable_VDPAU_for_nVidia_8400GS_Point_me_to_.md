---
title: "How to enable VDPAU for nVidia 8400GS? Point me to a post?"
date: 2010-10-08
forum: Multimedia Software
---

### Post by locoHost on 2010-10-08
I installed libvdpau and then I installed the nvidia vdpau software. I was following some steps from another post. When I run XBMC and hit 'O' I can see that the gcpu is still not doing any work (0 - 6%), the two computer cpus are doing all the work. They run at 30%'ish on 720p content and that renders smooth. No prob there. However, the cpus jump up to 50%+ (both cpus) on 1080p content and they can't keep the frame rate steady. It jumps around significantly so of course the movie stutters. No, the network is not the issue. Its completely wired gigabit end to end. Plus I'm running the video from the local hard drive and it doesn't change.

So... the solution is to get VDPAU working and so far I haven't found the right instructions. Can someone point me to some clear steps?

Thanks a lot for your help! :)

Mark

---

### Post by Yellow Pasque on 2010-10-08
Have you changed the render method to VDPAU in XBMC's video settings?

---

### Post by locoHost on 2010-10-08
> **Temüjin said:**
> Have you changed the render method to VDPAU in XBMC's video settings?

Yeah I have. I just looked at the xbmc.log. Here it is...

```
14:45:09 T:3078961024 M:803958784  NOTICE: DVDPlayer: Opening: smb://SPOCK/movies-usb4/Centurion (2010) 1080p/Centurion (2010) 1080p.mkv
14:45:09 T:3078961024 M:803958784 WARNING: CDVDMessageQueue(player)::Put MSGQ_NOT_INITIALIZED
14:45:09 T:2847861616 M:803823616  NOTICE: Creating InputStream
14:45:10 T:2847861616 M:803696640  NOTICE: Creating Demuxer
14:45:10 T:2847861616 M:793088000  NOTICE: Opening video stream: 0 source: 256
14:45:10 T:2847861616 M:793088000  NOTICE: Creating video codec with codec id: 28
14:45:10 T:2847861616 M:792961024  NOTICE: CDVDVideoCodecFFmpeg::Open() Creating VDPAU(1920x816)
14:45:10 T:2847861616 M:792961024  NOTICE: (VDPAU) unable to get handle to libvdpau
14:45:10 T:2847861616 M:792961024  NOTICE: CDVDVideoCodecFFmpeg::Open() Failed to get VDPAU device
14:45:10 T:2847861616 M:792961024  NOTICE:  (VDPAU) ~CVDPAU
14:45:10 T:2847861616 M:792961024  NOTICE: CDVDVideoCodecFFmpeg::Open() Using codec: H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
14:45:10 T:2847861616 M:792961024  NOTICE: Creating video thread
14:45:10 T:2847861616 M:792961024  NOTICE: Opening audio stream: 1 source: 256
14:45:10 T:2847861616 M:792961024  NOTICE: Finding audio codec for: 86021
14:45:10 T:2822683504 M:792961024  NOTICE: running thread: video_thread
14:45:10 T:2847861616 M:792821760  NOTICE: Creating audio thread
14:45:10 T:2847861616 M:792821760  NOTICE: Opening Subtitle stream: 2 source: 256
14:45:10 T:2814290800 M:792821760  NOTICE: running thread: CDVDPlayerAudio::Process()
14:45:10 T:2814290800 M:787861504  NOTICE: Creating audio device with codec id: 86021, channels: 2, sample rate: 48000, no pass-through
14:45:10 T:2822683504 M:781012992  NOTICE:  fps: 23.976025, pwidth: 1920, pheight: 816, dwidth: 1920, dheight: 816
14:45:10 T:2822683504 M:781012992  NOTICE: Display resolution DESKTOP : 1920x1080 @ 50.00 - Full Screen (12)
14:45:12 T:3078961024 M:766455808  NOTICE: Using GL_TEXTURE_2D
14:45:12 T:3078961024 M:766455808  NOTICE: GL: Selecting Single Pass YUV 2 RGB shader
14:45:12 T:3078961024 M:765599744  NOTICE: GL: NPOT texture support detected
14:45:19 T:2822683504 M:778919936 WARNING: Decode - avcodec_decode_video didn't consume the full packet. size: 70641, consumed: 0
14:45:19 T:2822683504 M:778919936 WARNING: Decode - avcodec_decode_video didn't consume the full packet. size: 71035, consumed: 0
14:45:21 T:2822683504 M:778895360 WARNING: Decode - avcodec_decode_video didn't consume the full packet. size: 79643, consumed: 0
14:45:21 T:2822683504 M:778895360 WARNING: Decode - avcodec_decode_video didn't consume the full packet. size: 52665, consumed: 0
14:45:21 T:2822683504 M:778895360 WARNING: Decode - avcodec_decode_video didn't consume the full packet. size: 50052, consumed: 0
14:45:21 T:2822683504 M:778895360 WARNING: Decode - avcodec_decode_video didn't consume the full packet. size: 63096, consumed: 0
14:45:23 T:2822683504 M:778862592 WARNING: Decode - avcodec_decode_video didn't consume the full packet. size: 68382, consumed: 0
14:45:24 T:2822683504 M:778928128 WARNING: Decode - avcodec_decode_video didn't consume the full packet. size: 59945, consumed: 0
14:45:24 T:2822683504 M:778928128 WARNING: Decode - avcodec_decode_video didn't consume the full packet. size: 61108, consumed: 0
14:45:24 T:2822683504 M:778928128 WARNING: Decode - avcodec_decode_video didn't consume the full packet. size: 60546, consumed: 0
14:46:29 T:2822683504 M:779710464 WARNING: Decode - avcodec_decode_video didn't consume the full packet. size: 42394, consumed: 0
14:46:30 T:2822683504 M:779456512 WARNING: Decode - avcodec_decode_video didn't consume the full packet. size: 43548, consumed: 0
14:46:30 T:2822683504 M:779456512 WARNING: Decode - avcodec_decode_video didn't consume the full packet. size: 44022, consumed: 0
14:46:34 T:2822683504 M:779329536 WARNING: Decode - avcodec_decode_video didn't consume the full packet. size: 34786, consumed: 0
14:46:34 T:2822683504 M:779329536 WARNING: Decode - avcodec_decode_video didn't consume the full packet. size: 44974, consumed: 0
14:46:38 T:2822683504 M:779304960 WARNING: Decode - avcodec_decode_video didn't consume the full packet. size: 50147, consumed: 0
14:46:42 T:2822683504 M:779350016 WARNING: Decode - avcodec_decode_video didn't consume the full packet. size: 50047, consumed: 0
```

There is a lot more in the log file but it will blow the post limit. This has the section where the movie begins to play. I see an issue with the VDPAU driver loading. I thought this was included with the NVidia hardware drivers? Do also have to install libvdpau?

---

### Post by gordintoronto on 2010-10-08
From the VDPAU wiki: "The libvdpau standalone VDPAU library is distributed by NVIDIA independently of their proprietary Linux graphics driver in an effort to help the adoption of VDPAU by those outside of NVIDIA. This open source library package contains a wrapper library and a debugging library allowing other manufacturers to implement VDPAU support into their device drivers."

Do you know what version of the driver you are using?

---

### Post by locoHost on 2010-10-10
Turns out I needed to install **libvdpau1**. That did it! That got both of the cpus down to 3 to 9 percent usage while playing 1080p content. Put a "PureVideo" (VDPAU) NVidia card in any old 3ghz P4 and it will play full HD content! Why would you ever put any video card other than NVidia in your Ubuntu machine?!?! 

Thank you very much for the replies guys! :)

---

