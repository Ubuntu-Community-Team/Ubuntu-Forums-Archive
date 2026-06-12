---
title: "Which video player can leverage Intel HD Graphics 530 to render smooth 4K HEVC video?"
date: 2018-12-31
forum: Multimedia Software
---

### Post by holmessherlock on 2018-12-31
I am using GoPro Hero7 Black version to shoot 4K HEVC (H.265) video: [URL="https://i.stack.imgur.com/QcbBh.png"]https://i.stack.imgur.com/QcbBh.png
[/URL]
Below is the software and hardware configuration I am using:

 - VLC 3.0.4
 - Ubuntu 18.04 (Bionic Beaver), x86-64 bit
 - [Intel(R) Core(TM) i7-6820HQ CPU @ 2.70GHz]("https://ark.intel.com/products/88970/Intel-Core-i7-6820HQ-Processor-8M-Cache-up-to-3-60-GHz-")
 - [https://www.intel.com/content/www/us/en/support/products/88345/graphics-drivers/graphics-for-6th-generation-intel-processors/intel-hd-graphics-530.html]Intel®]("http://[url") HD Graphics 530[/url]

    ```
$ vainfo
    VAProfileHEVCMain               :    VAEntrypointVLD
    VAProfileHEVCMain               :    VAEntrypointEncSlice


    $ VDPAU_DRIVER=va_gl vdpauinfo
    HEVC_MAIN             --- not supported ---
    HEVC_MAIN_10       --- not supported ---
    HEVC_MAIN_STILL     --- not supported ---
    HEVC_MAIN_12        --- not supported ---
    HEVC_MAIN_444     --- not supported ---
```


From the specification, Intel HD Graphics 530 seems to be able to decode 4096x2304@60Hz video streams. However, `vdpauinfo` and `vainfo` do not seem to to agree with each other as far as HEVC decoding capability is concerned. The former says `HEVC_MAIN_*` is not supported while the later returns a valid entry point for `VAProfileHEVCMain` (if that means the capability is supported). The problem during play back in 

I tried a few other players as well, here're the results:


[LIST]
[*]Mplayer, mplayer2, smplayer => There's no gray frames, but it lowers frame rate to an extent such that 30 seconds of video almost takes thrice the recording time to play back.
[*]mpv => This gives the best result so far. The video plays almost flawlessly, minor choppiness experienced for a brief while once or twice.
[*]ffplay => Stands still at the first frame.
[*]VLC => The worst result, the video is lagging, shows gray frames in between and unacceptably choppy.
[/LIST]

**My questions are:**

 - VLC media player [doesn't seem to support]("https://wiki.videolan.org/VLC_GPU_Decoding") hardware accelerated HEVC (H.265) decoding on Linux. Is my understanding correct?
 - Is it possible to render smooth 4K HEVC video with my hardware configuration using any video player on Linux? 
 - If yes, is there any media player and driver combination on Ubuntu 18.04, 64 bit that can leverage the hardware decoding capability of the Intel HD Graphics 530 while rendering the video?

---

### Post by wildmanne39 on 2018-12-31
Please use the attachment facility by clicking on the paperclip or  use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

---

### Post by mc4man on 2019-01-01
Gave my skylake laptop with 4k screen to my son so can't compare as my haswell doesn't support hevc. 
So in general - 
I'd forget about libvdpau-va-gl1, just a hack to at this point provide some hwdec for mplayer with Intel.

As far as vlc, don't know. That page you linked is 2+ yrs. old. If it did support hevc on hevc capable chipsets then it would be thru vaapi. 
The default for vlc & hwdec is automatic, you could always try setting specifically to vaapi (X11) in Input & Codecs and also set to OpenGL in Video > Output

Overall best bet would be mpv. Have you tried other hevc vids not from the gopro? What is the bitrate, bit depth & format profile of your videos?
Are you outputting to a 4k monitor or scaling to a 1080p one?

When using mpv you could have verbose output  in terminal with -v , a lot of it would be nothing related but maybe something would show.. 
(you can always have a current (overwritten) log by using in ~/.config/mpv/mpv.conf a line of this, would be in home folder
log-file=mpv.log

Also when playing in mpv going shift+i will overlay some stats, are the issues dropped frames?

Is there a sample of a troublesome vid available?

---

### Post by SeijiSensei on 2019-01-01
SMPlayer can use mpv as well as mplayer.  Options > Preferences > General > Multimedia engine

---

