---
title: "no video for Real video Intrepid 8.10"
date: 2009-03-29
forum: Multimedia Software
---

### Post by bob12564 on 2009-03-29
I cannot get video for a Real stream using any media player.  I just did a clean install of Intrepid and I followed the sticky media guide for installing video support.  I get sound but no video.

I installed the ubuntu-restricted-extras and gecko-media-player which also installs MPlayer.  I found an internet page with samples of all types of videos and they all seem to play OK.  Quicktime streams seem to work and Flash seems to work.  DIVX, wmv, mpeg2, etc. all seem to play fine.  The only problem is Real.

I also installed VLC to try that and it won't play the file either.  I also tried downloading the stream file and running from the desktop to avoid problems with internet connection.  That didn't help.  I found a command on these forums that displays the MPLayer capabilities for Real.  It shows:

 mplayer -vc help | grep -i real
rv3040      realvid   working   Linux RealPlayer 10 RV30/40 decoder  [drvc.so]
rv3040win   realvid   working   Win32 RealPlayer 10 RV30/40 decoder  [drvc.dll]
rv40        realvid   working   Linux RealPlayer 9 RV40 decoder  [drv4.so.6.0]
rv40win     realvid   working   Win32 RealPlayer 9 RV40 decoder  [drv43260.dll]
rv40mac     realvid   working   Mac OS X RealPlayer 9 RV40 decoder  [drvc.bundle/Contents/MacOS/drvc]
rv30        realvid   working   Linux RealPlayer 8 RV30 decoder  [drv3.so.6.0]
rv30win     realvid   working   Win32 RealPlayer 8 RV30 decoder  [drv33260.dll]
rv30mac     realvid   working   Mac OS X RealPlayer 9 RV30 decoder  [drvc.bundle/Contents/MacOS/drvc]
rv20        realvid   working   Linux RealPlayer 8 RV20 decoder  [drv2.so.6.0]
rv20winrp10 realvid   working   Win32 RealPlayer 10 RV20 decoder  [drv2.dll]
rv20win     realvid   working   Win32 RealPlayer 8 RV20 decoder  [drv23260.dll]
rv20mac     realvid   working   Mac OS X RealPlayer 9 RV20 decoder  [drv2.bundle/Contents/MacOS/drv2]
fraps       vfw       working   FRAPS: Realtime Video Capture  [frapsvid.dll]

So it looks like I should have MPlayer codecs to play the stream/file.  The video clip is RV30 as far as I can tell.

I'm still a noob at this so any help is appreciated.

Thanks.

---

