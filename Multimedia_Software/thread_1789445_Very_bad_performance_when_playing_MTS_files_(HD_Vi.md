---
title: "Very bad performance when playing MTS files (HD Video) in Ubuntu 11.04"
date: 2011-06-23
forum: Multimedia Software
---

### Post by bustosjr1 on 2011-06-23
Hello,

First of all, congratulations for this forum, is excellent for those new users in Ubuntu like me.

My problem is that my computer plays MTS videos very bad (the videos get freeze, etc) in Ubuntu 11.04. I tested many players, but I didn't get good performance during the playback in any of them.

However, in the same computer, I use K-Lite Codec Pack in Windows XP and MTS videos are fine!

Is there any way to play MTS videos in Ubuntu very well?

Performance is excellent in both operating systems (XP and Ubuntu 11.04).

Thank you so much!

---

### Post by e79 on 2011-06-23
Hi and welcome to Ubuntu Forums !

I would simply try VLC media player, it usually can read just about everything you throw at it.  

Open the Ubuntu Software Center and search for 'VLC'

Let us know if that helps.

---

### Post by dFlyer on 2011-06-23
Have you install ubuntu-restricted-extras?

---

### Post by beew on 2011-06-24
After installing the codecs you should try mplayer2. It is the best player available IMO, (if you have the codecs) it is way better than VLC and normal mplayer in hd playback (I mean way better)  Curently you can install it from this ppa.

[https://launchpad.net/~ripps818/+archive/ppa]("https://launchpad.net/%7Eripps818/+archive/ppa")

Or if you are using 11.04 you can use also
[https://code.launchpad.net/~ed10vi86/+archive/tst]("https://code.launchpad.net/%7Eed10vi86/+archive/tst") 
It is the same mplayer (actually mplayer2) build from ripps' ppa.

As far as I know all other mplayer ppas only offer mplayer instead of mplayer2, if you are not using vdpau the performance is way way inferior to mplayer2 (with vdpau performance is comparable if you install the right version, say from the mplayer-mt ppa)

---

### Post by bustosjr1 on 2011-06-24
Hi again,

Thank you very much for all the replies.

I am trying to play MTS videos with VLC, Mplayer (SMPlayer), Kaffeine, Totem and Xine. I noticed that SMPlayer plays the videos smoother, but still freezes many times.

VLC plays MTS videos smoothly in the first two seconds, then video freezes many times (the same happens with VLC in Windows XP, but not with K-Lite Codeck Pack (using Media Player Classic).

So I think it's impossible to get the same performance with MTS videos in Ubuntu like in Windows XP with K-Lite Codec Pack.

By the way, I installed ubuntu-restricted-extras, ffmpeg, etc, and I installed MPlayer and SMPlayer from Synaptics.

I'm afraid I will have to convert MTS videos to another format, but I would like to play this format as I do in Windows XP without freeze...

Thank you very much for your help!

P.D.: Sorry for my bad English, I am Spanish ;)

---

### Post by bustosjr1 on 2011-07-01
Please, I need more help. Can anyone tell me any program to convert MTS files without loose quality?

---

### Post by vanadium on 2011-07-01
Unfortunately, indeed, there might, depending on your hardware, be performance problems playing HD video under linux.

If you want to convert in order to have smooth playback, you will need to downscale them. A 1080 HD video will still look nice when rescaled at 720p. Handbrake is easy to use and will do a good job in converting your video. Take into account that recompression will take many hours (I need 6 - 7 hours for 2 hours of video).

HD video is in an advanced codec, H264, that requires a lot of processing power. You could recode to mpeg2 without rescaling. HD mpeg2 video requires a lot less resources to play back, so there is a chance that that would play smoothly on your system. However, resulting files will be very big if you want to avoid visual compression artifacts.

---

