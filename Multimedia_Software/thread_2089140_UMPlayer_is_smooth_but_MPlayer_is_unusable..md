---
title: "UMPlayer is smooth but MPlayer is unusable."
date: 2012-11-28
forum: Multimedia Software
---

### Post by rock4christ on 2012-11-28
When I run UMPlayer(using vdpau for video output) everything is smooth, but MPlayer has little hiccups before slowing to a few fps while audio continues, even when i set it to use vdpau. Any way I can get MPlayer up to UMPlayer's performance?

---

### Post by andrew.46 on 2012-11-28
Seems a little odd as UMPlayer is simply a frontend for MPlayer. Can you give the MPlayer terminal output?

---

### Post by SeijiSensei on 2012-11-28
SMPlayer, from which UMPlayer is derived, lets you see the mplayer command line it generates under Options > View Logs.  Anything like that in UMPlayer?  For instance, playing a H.264-encoded subtitled video in the MKV container generates this whole command line for mplayer:

```
/usr/bin/mplayer -noquiet -nofs -nomouseinput -lavdopts threads=4 -sub-fuzziness 1 -identify -slave -vo gl:yuv=2:force-pbo -ao pulse -nokeepaspect -framedrop -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 109052063 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-force-style PlayResX=512,PlayResY=320,Name=Default,Fontname=Arial,Fontsize=16,PrimaryColour=&H00ffffff,BackColour=&H00000000,OutlineColour=&H00000000,Bold=0,Italic=0,Alignment=2,BorderStyle=1,Outline=1,Shadow=2,MarginL=20,MarginR=20,MarginV=8 -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 16 -subfont-text-scale 16 -subcp UTF-8 -vid 0 -aid 0 -subpos 100 -volume 40 -nocache -osdlevel 0 -vf-add screenshot -slices -channels 6 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 somefile.mkv
```

While most of these options concern the subtitle stylings, things like "-framedrop", "threads" and "-double" for double buffering all affect performance.  The "force-pbo" option for the gl driver also plays a role on NVIDIA and ATI cards.

I just dumped the proprietary NVIDIA driver because the most recent update resulted in poor font rendering on my display, so I'm not using vdpau any longer.  (I have a fast quad-core machine which has no trouble decoding even high-res material in the CPU.)  Try a couple of other video drivers like gl or xv.  Any better?

Are you sure you're using the correct codecs for h264 material?  With vdpau, you should see a "-vc ffh264vdpau" in the list of command-line parameters.  If you are running mplayer from the prompt, try adding that option and see if it helps.  You can check to see what codecs are installed by running "mplayer -vc help | grep vdpau".  You should have all of these:

```

ffmpeg12vdpau ffmpeg    working   FFmpeg MPEG-1/2 (VDPAU)  [mpegvideo_vdpau]
ffwmv3vdpau ffmpeg    problems  FFmpeg WMV3/WMV9 (VDPAU)  [wmv3_vdpau]
ffvc1vdpau  ffmpeg    problems  FFmpeg WVC1 (VDPAU)  [vc1_vdpau]
ffh264vdpau ffmpeg    working   FFmpeg H.264 (VDPAU)  [h264_vdpau]
ffodivxvdpau ffmpeg    working   FFmpeg MPEG-4,DIVX-4/5 (VDPAU) [mpeg4_vdpau]

```

The "problem" children like WMV3/9 require installing some Windows .dll files which I have not bothered with since I never watch anything in those formats.

---

