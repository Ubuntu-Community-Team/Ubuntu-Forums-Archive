---
title: "firefox mplayer-plugin + divx + alsa = out of sync playback"
date: 2007-05-15
forum: Multimedia &amp; Video
---

### Post by kpkeerthi on 2007-05-15
When playing divx videos from [www.stage6.com](www.stage6.com) in firefox (mplayer plugin), the audio goes out of sync when using alsa. oss works OK but I get crappy sound. Any help to fix this problem is highly appreciated.

---

### Post by schnupi on 2007-05-15
how did u get mplayer to work with stage6 videos in the first place? totem-xine/gstreamer only worked for me.. try totem instead 

the only problem is that it only buffers 7 seconds ahead which is really annoying. i just opened a threat about it today [http://ubuntuforums.org/showthread.php?p=2659773](http://ubuntuforums.org/showthread.php?p=2659773)

---

### Post by kpkeerthi on 2007-05-16
I don't prefer totem for the same reason you are having with streaming divx. Check out [http://ubuntuforums.org/showthread.php?t=396569](http://ubuntuforums.org/showthread.php?t=396569) to get mplayer work with stage 6.

**Anyone have suggestions to my actual problem? Thanks.**

---

### Post by ricrac on 2007-05-16
Download a known working (in-sync) file and test locally using 
  "mplayer -ao oss filename"
   and
  "mplayer -ao alsa filename"

Are there still sync errors using alsa?  
  If No, you should be able to get it working, try disabling esd or arts and repeat test locally.
  If Yes, try disabling esd or arts and repeat test locally.

Are there still sync errors using alsa?  
  If No,  use jack or pulse instead, or just use one app at a time, usually works ok when you're sitting for a long video.
  If Yes, download 3 or 4 livecds that include mplayer, boot up livecds and repeat tests locally.

Are there still sync errors using alsa?  
  If No on any livecd, you should be able to get it working, try to compare kernel and program versions, pertinent conf files, and programs running,  look for differences between your install and the working livecd.
  If Yes, continue

Is your sound card on the motherboard?
  If Yes, you may need a pci sound card $10-$20, well supported by alsa card.   Or you probably need a hardware upgrade.
  If No, if your sound card is cheap, you might try and replace it or..
You probably need a hardware upgrade.

An all in one motherboard with video and sound $50 cpu $50 mem$50 case/pwr $50 HD $50
A $250 system w/ubuntu 7.04 is fully capable of playing multiple divx streams simultaneously using firefox, mplayerplug-in, mplayer, alsa in constant sync over broadband.  


Most likely causes of sync problems are motherboard sound card and arts/esd.

---

