---
title: "HD Video Playback is Choppy!"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by quadomatic on 2007-06-25
I was wondering if I could get some help. I've been able to play HD videos just fine in windows using ffdshow/combined community codec project. They play smooth and everything.

But in Ubuntu I can't get HD mkv videos to play smooth. In VLC they play very choppily. It's the same problem with MPlayer. Can someone tell me what to do? Is it a problem with my video card driver? I'm using an ATI X850 PRO.

---

### Post by revpfil on 2008-04-22
I've been having the same problem. Specifically, VLC gives me:

```
 [00000388] ffmpeg decoder error: more than 5 seconds of late video -> dropping frame (computer too slow ?)
```

On feisty I was able to play 1080 hd video without a problem, but Hardy 64 I'm getting maximal cpu use and dropped frames.

My system:
Athlon X2 64 4600+
2GB ddr2
NVidia HDA
NVidia GeForce 9600gt w/proprietary beta drivers

---

### Post by quixotic-cynic on 2008-05-07
Same problem - Toshiba Satellite Pro A120 running Hardy. It definitely got worse over the upgrade - my pc could just about cope before.

---

### Post by telepathetic on 2008-05-15
word-- same problem here on my core 2 duo 3G ram 3100X toshiba laptop.. any help!?

---

### Post by markbuntu on 2008-05-16
If you are running compiz you might try switching to metacity or turning compiz off before playing videos. Compiz seems to control a lot of the restricted video driver resources. If google earth also does this then you should for sure try switching to metacity before playing the videos.

---

### Post by Trollslayer on 2008-05-17
> **markbuntu said:**
> If you are running compiz you might try switching to metacity or turning compiz off before playing videos. Compiz seems to control a lot of the restricted video driver resources. If google earth also does this then you should for sure try switching to metacity before playing the videos.

I get exactly the same - 7.10 was fine with HD, 8.04 is very slow with SD.
No Compiz - Mplayer, VLC and Xine give the same resutls.
This is with the ATI restricted driver in both cases.

---

### Post by +Eric on 2008-05-18
I'm having the same issue with an nividia card. Nothing helps, metacity.... nothing.

Ugh, this is a huge problem for me....

---

### Post by olavjunior on 2008-05-18
I can't play 1080 either. 
nvidia geforceGo 7200
dualCore 1,7 gHz

Is my system to slow?

---

### Post by Vashu on 2008-05-19
Same here. With both compiz on and off. Same video on windows plays like it should even on less powerfull hardware.

---

### Post by chewearn on 2008-05-19
Previously, I have investigated the problem with attempting to play 1080p h264 mkv file using vlc.


1. I believe ffmpeg is not installed by default.
Install it.
```
sudo apt-get install ffmpeg
```If your computer is fast enough, the video should be less choppy or might work.

I have AMD X2 3800+ and it is **not** fast enough.  Another Core2Duo 2GHz is almost ok, but still not good enough.


2. The ffmpeg in the repo is outdated.
This is unfortunate.  There was an attempt to update it for Hardy, but it didn't make it on time.

Solution:
Compile from source (might not be for the faint hearted):
[https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg)

I have not tried this in Hardy, not sure if the steps are still the same.  I did the compile in Gutsy and it worked.

With the AMD X2 3800+, after compile, it was still not working.  With Core2Duo 2GHz, it works perfectly.


3. Multi-core decoding is not working
Why ffdshow is super in Windows is because full dual cores are used.  Unfortunately, I have not been able to make ffmpeg do the same in ubuntu.  There might be a setting somewhere for this, but I give up before finding out.


4. Use less processing at the expense of video quality
There is a setting in vlc under  (you need to check "Advanced options" in the lower right to be able to see this option):
Settings > Preferences > Input / Codecs > Other Codecs > Ffmpeg > Skip the loop filter for H.264 decoding

Set that to none.


.

---

