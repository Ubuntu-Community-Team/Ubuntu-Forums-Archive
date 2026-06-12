---
title: "Videos won't play after nvidia driver install"
date: 2010-05-09
forum: Multimedia Software
---

### Post by The Flying Penguin on 2010-05-09
I have an Asus ul30vt with the Intel 4500MHD/Nvidia G210M hybrid graphics. I finally found a way to get the Nvidia card to work. I followed these instructions [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1361466&page=2](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1361466&page=2) and now my nvidia card is working.

Now though I can't play a single video through the movie player that comes with Lucid 64bit or VLC. I have tried various movies in different formats and different resolutions, both hd and sd. Every video just shows a black screen with sound in the background.

What could be causing this?

EDIT: I set the output on vlc to X11 and now my videos play but 720p is p little choppy sometimes and 1080p is completely unplayable. Using the Intel card 720p was perfect and 1080p wasn't nearly as choppy but still not really watchable. So something must be messed up because this card should play a lot better than the Intel.

---

### Post by cchhrriiss121212 on 2010-05-10
Nvidia cards make use of hardware acceleration by using vdpau video output, which is installed by default on lucid. Whether it will work on your hybrid card or not is something I don't know but it is worth a try. Just install smplayer from the repos and select vdpau output under video preferences.

---

### Post by The Flying Penguin on 2010-05-19
It took me a bit to post back but I tried what you said and the video runs even worse than with the X11 setting in VLC.

I'm using an official driver. You would think that it would allow me to play 1080p just as I can in Win 7.

I don't know what I did but now when I try to play 1080p in VLC using X11, the video will play great for sometimes up to maybe 30 or 40 seconds and then the screen will get all blotchy for a few seconds. If I rewind I can then play back the part I missed due to the blotchiness. So what is the deal here? Is this a buffering issue or something?

Any help would be appreciated. If I don't solve this I'm just going to go back to the Intel driver.

---

### Post by karl3 on 2010-05-19
go to terminal and start```
gstreamer-properties
```

click on "video" tab, and under "default output", "plugin" select "x window system (no xv)".

worked for me :)

---

### Post by The Flying Penguin on 2010-05-21
I set gs-streamer properties to x window system (no xv) but am still having problems. If SMPlayer is set to vdpau then when I launch my video I get an error message stating "MPlayer has finished unexpectedly. Exit code:1".

VLC doesn't seem to have a vdpau option and I saw no improvement when using my previous video output settings.

What video player are you using and what output settings have you selected?

Can anyone share their video settings with me?

---

### Post by joshedmonds on 2010-05-22
> **cchhrriiss121212 said:**
> Nvidia cards make use of hardware acceleration by using vdpau video output, which is installed by default on lucid.
I found that contrary to advice above, package 'libvdpau1' is NOT installed by default. HTH

---

### Post by The Flying Penguin on 2010-05-22
Thank you so much for your help guys!

I love how every new post was a piece of the puzzle and now I have smooth 1080p playback.

So now I have libvdpau1 installed from the package manager, gstreamer's video output plugin is set to "X Window System (No xv)", and I have SMPlayer set to vdpau. Now 720p and 1080p .mkvs play perfectly.

Interestingly, when playing Appleseed Ex Machina, my first cpu core never goes above 14% and my second never above 10%. Average I would say would be about 3-8% per core. I tried playing a 720p without acceleration and my cores were working from 50-75% per core (the video played pretty decent though with minimal choppiness) and with vdpau they don't go beyond 20%. I know its odd the 720p still uses more cpu power than the 1080p with vdpau but it must just be the way the .mkvs are encoded or the movie itself.

Anyway, thank you again guys! Now I don't have to boot into Windows to watch 1080p. I think I can confidently say that gaming, DVD Decrypter, and the software I'm using to convert all my WMA lossless to .flac, are now the only three reasons I need to boot into Windows anymore, not counting a couple games and MS Publisher that I run in Virtual Box. I see that its possible to use DVD Decrypter in Wine with some work and I'm nearing the end of my music conversion process so maybe I'll only have one reason soon.

---

### Post by dineshdharme on 2010-08-27
karl3's advice :
go to terminal and start

gstreamer-properties

click on "video" tab, and under "default output", "plugin" select "x window system (no xv)".

worked for me as well.
Thank you very much.

---

