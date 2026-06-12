---
title: "movie player &amp; wmv files"
date: 2009-03-22
forum: Multimedia Software
---

### Post by xrayjohn on 2009-03-22
I can't get wmv files to play. If I understand what I read, I needed to run: sudo apt-get install ubuntu-restricted-extras

Is there something else I am supposed to do? 'Cause that didn't work. The kicker is, I had this working before but had to reinstall Ubuntu after a fatal crash that resulted from using the terminal server client and a VPN...  I was really liking Linux prior to that... Right now I hate it.

Thanks for the help.

---

### Post by mc4man on 2009-03-22
Never used ubuntu-restricted-extras so don't know exactly what it does or doesn't install.
You'd want w32codecs installed for many wmv types
[http://packages.medibuntu.org/](http://packages.medibuntu.org/)

pick your ver. of ubuntu, ect.

---

### Post by andrew.46 on 2009-03-24
Hi,

If you are keen you can test the capabilities of your version of MPlayer as follows:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -vc help | grep -i wmv[/COLOR]**
ffwmv1      ffmpeg    working   FFmpeg WMV1/WMV7  [wmv1]
ffwmv2      ffmpeg    working   FFmpeg WMV2/WMV8  [wmv2]
ffwmv3      ffmpeg    problems  FFmpeg WMV3/WMV9  [wmv3]
ffwmv3vdpau ffmpeg    problems  FFmpeg WMV3/WMV9 (VDPAU)  [wmv3_vdpau]
wmv9dmo     dmo       working   Windows Media Video 9 DMO  [wmv9dmod.dll]
wmvdmo      dmo       working   Windows Media Video DMO  [wmvdmod.dll]
wmv8        dshow     working   Windows Media Video 8  [wmv8ds32.ax]
wmv7        dshow     working   Windows Media Video 7  [wmvds32.ax]
wmvadmo     dmo       working   Windows Media Video Adv DMO  [wmvadvd.dll]
wmvvc1dmo   dmo       working   Windows Media Video (VC-1) Advanced Profile  [wvc1dmod.dll]


```

All the best,

Andrew

---

