---
title: "How to install H265 in ubuntu?"
date: 2015-04-07
forum: Multimedia Software
---

### Post by remmas-sido on 2015-04-07
Hello guys 
I'm using Ubuntu 12.04, and I'm wondering how to install H265. that's all

---

### Post by FakeOutdoorsman on 2015-04-07
For encoding? Decoding? Playback?

---

### Post by dino99 on 2015-04-08
[https://viewsby.wordpress.com/2015/01/12/vlc-player-install-h-265-hevc-codec-on-ubuntu-linux/](https://viewsby.wordpress.com/2015/01/12/vlc-player-install-h-265-hevc-codec-on-ubuntu-linux/)

---

### Post by remmas-sido on 2015-04-08
> **FakeOutdoorsman said:**
> For encoding? Decoding? Playback?
Playback

---

### Post by mc4man on 2015-04-08
Add this ppa, update your sources
[https://launchpad.net/~strukturag/+archive/ubuntu/libde265](https://launchpad.net/~strukturag/+archive/ubuntu/libde265)

For totem or other gst players  install - gstreamer0.10-libde265
For vlc install - vlc-plugin-libde265

should then handle many h.265 files

---

### Post by SeijiSensei on 2015-04-09
I see Doug modestly refrained from suggesting that you use his [mplayer build]("https://launchpad.net/~mc3man/+archive/ubuntu/mplayer-test") which also includes a codec for H.265/HEVC.
```
$ mplayer -vc help | grep hevc
ffhevc      ffmpeg    working   FFmpeg HEVC / H.265  [hevc]

```
You can add his PPA, then install mplayer and smplayer, a full-featured GUI interface for mplayer.
```
sudo add-apt-repository ppa:mc3man/mplayer-test
sudo apt-get update
sudo apt-get install mplayer smplayer

```

---

### Post by tristan16 on 2015-07-08
What do I need to install to *encode *H.265/HEVC? After installing this plugin, VLC still tells me the LibAV/FFMpeg (libavcodec) is missing the encoder[COLOR=#000000] HPEG-H Part2/HEVC (H.265)[/COLOR].

---

### Post by mc4man on 2015-07-08
> **tristan16 said:**
> What do I need to install to *encode *H.265/HEVC? After installing this plugin, VLC still tells me the LibAV/FFMpeg (libavcodec) is missing the encoder[COLOR=#000000] HPEG-H Part2/HEVC (H.265)[/COLOR].

If for some reason you want vlc to convert to hevc than read here - 
[http://ubuntuforums.org/showthread.php?t=2141949](http://ubuntuforums.org/showthread.php?t=2141949)

---

### Post by mc4man on 2015-07-09
> **mc4man said:**
> If for some reason you want vlc to convert to hevc than read here - 
[http://ubuntuforums.org/showthread.php?t=2141949](http://ubuntuforums.org/showthread.php?t=2141949)

I wouldn't bother with vlc to convert, especialy thru it's built-in profiles (who ever named, set up the h264 & h265 profiles was clearly not paying any attention at all..
Just use an enabled ffmpeg - small sample of fairly extreme reduction here,  10:1, (orig 39MB)  - looks ok for such, could be better probably.. 
[http://www.datafilehost.com/d/efe3b1fa](http://www.datafilehost.com/d/efe3b1fa)

---

### Post by tristan16 on 2015-07-10
> **mc4man said:**
> If for some reason you want vlc to convert to hevc than read here - 
[http://ubuntuforums.org/showthread.php?t=2141949](http://ubuntuforums.org/showthread.php?t=2141949)

I'll just stick with H.264 then. I try to avoid building from source code so I don't break something.

> **mc4man said:**
> I wouldn't bother with vlc to convert, especialy thru it's built-in profiles (who ever named, set up the h264 & h265 profiles was clearly not paying any attention at all..
Just use an enabled ffmpeg - small sample of fairly extreme reduction here,  10:1, (orig 39MB)  - looks ok for such, could be better probably.. 
[http://www.datafilehost.com/d/efe3b1fa](http://www.datafilehost.com/d/efe3b1fa)

You make it sound like it's bad to use VLC for converting. I've used VLC for all of my conversion ever since I started using it to play DVDs on Windows XP. True, the profile names are incorrect, but I customize the settings anyway.

---

### Post by mc4man on 2015-07-10
> **tristan16 said:**
> I'll just stick with H.264 then. 

You make it sound like it's bad to use VLC for converting. 
No, this thread & your query where about h.265. For that,  yes, vlc is not that good.

---

### Post by puttux on 2016-01-10
> **SeijiSensei said:**
> I see Doug modestly refrained from suggesting that you use his [mplayer build]("https://launchpad.net/~mc3man/+archive/ubuntu/mplayer-test") which also includes a codec for H.265/HEVC.
```
$ mplayer -vc help | grep hevc
ffhevc      ffmpeg    working   FFmpeg HEVC / H.265  [hevc]

```
You can add his PPA, then install mplayer and smplayer, a full-featured GUI interface for mplayer.
```
sudo add-apt-repository ppa:mc3man/mplayer-test
sudo apt-get update
sudo apt-get install mplayer smplayer

```

Thanks a lot.

---

