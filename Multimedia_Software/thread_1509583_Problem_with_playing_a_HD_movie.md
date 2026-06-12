---
title: "Problem with playing a HD movie?"
date: 2010-06-14
forum: Multimedia Software
---

### Post by gabe17 on 2010-06-14
Hi! I use Ubuntu 10.04. I need to play a full HD (1080p) video on my pc:
CPU: AMD Athlon X2 7750 BE
MB: ASUS M3A32-MVP 
RAM: 2x1GB KINGSTON 1066MHz 
VGA: ASUS 8800GS 

I think my PC should be able to play it, but the video is really not fluent. What should be wrong? Power less hardware? Wrong codecs? Thanks for help.

---

### Post by wednesday allfather on 2010-06-14
Few questions

Your monitor is HD?

What format is the video?

What are you using to play the video?

Is it choppy or grainy when you playback?

---

### Post by gabe17 on 2010-06-14
Yes, my monitor is FULL HD. It is .mkv format. I played it with Movie player (default in ubuntu) and I also tried to play it with Rhytmnbox. Don't know, how do you mean "choppy", but I would use the word "snatchy"...f.e. it has very low fps...simply, it's not fluent, even though the video is FULL HD and has about 25GB.

---

### Post by wednesday allfather on 2010-06-14
I had problems with stock movie player playing mkv files a while back, but I haven't been using it.  Try to install VLC and play the video thru that.

---

### Post by gabe17 on 2010-06-14
So I tried the VLC, but in this player it is not only snatchy, but it is also very grainy. I don't think the problem will be in the player.

---

### Post by wesleybishop on 2010-06-14
check the thread [http://ubuntuforums.org/showthread.php?t=502854](http://ubuntuforums.org/showthread.php?t=502854) hope it helps

---

### Post by cchhrriiss121212 on 2010-06-14
You just need to install a few things so that you can use hardware acceleration from your graphics card. It is called vdpau and is available [here]("http://ubuntuforums.org/showthread.php?t=1037625"). You will then be able to watch 1080p video with only ~10% of your cpu power.

Once you've added the ppa, install smplayer from synaptic and select vdapu as the video output under preferences.

---

### Post by gabe17 on 2010-06-14
cchhrriiss121212: That sounds really good, I hope it will go, because unfortunately it doesn't.

I've done the following steps: 
(1): I added the next PPA to the software sources (System->Administration->System sources->Other software)
[http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu)
(2): I downloaded and installed mplayer and smplayer throught Synaptic
(3): I changed video output to vdapu

But now if I open the file throught Smplayer, it writes: *Mplayer has finished unexpectedly. Exit code: 1.*
Have I done something wrong?

---

### Post by cchhrriiss121212 on 2010-06-14
Could you open the file in a terminal like this:
```
mplayer -vo vdpau -vc ffh264vdpau path/to/file
```
Then post the output of the errors

---

### Post by gabe17 on 2010-06-15
I've tried, only the sound goes, the video doesn't. 

```
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...

```

---

### Post by cchhrriiss121212 on 2010-06-15
Could you post the complete output?

---

### Post by gabe17 on 2010-06-15
Of course :)

```

MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/Video/video.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "Video", -vid 0
[mkv] Track ID 2: audio (A_DTS) "English 5.1 [DTS-MA] (Master Audio)", -aid 0, -alang eng
[mkv] Track ID 3: audio (A_AC3) "Czech 5.1 [AC3] (coreAC3)", -aid 1, -alang cze
[mkv] Track ID 4: audio (A_AC3) "Slovak 5.1 [AC3] (coreAC3)", -aid 2, -alang slo
[mkv] Track ID 5: subtitles (S_TEXT/UTF8) "English", -sid 0, -slang eng
[mkv] Track ID 6: subtitles (S_TEXT/UTF8) "English (forced)", -sid 1, -slang eng
[mkv] Track ID 7: subtitles (S_TEXT/UTF8) "Czech", -sid 2, -slang cze
[mkv] Track ID 8: subtitles (S_TEXT/UTF8) "Czech (forced)", -sid 3, -slang cze
[mkv] Track ID 9: subtitles (S_TEXT/UTF8) "Slovak", -sid 4, -slang slo
[mkv] Track ID 10: subtitles (S_TEXT/UTF8) "Slovak (forced)", -sid 5, -slang slo
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[vdpau] Could not open dynamic library libvdpau.so.1
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [libdca] DTS decoding with libdca
Stream with high frequencies VQ coding
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [dts] afm: libdca (DTS-libdca)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   1.2 (01.2) of 9701.7 ( 2:41:41.6)  3.1% 

```

---

### Post by cchhrriiss121212 on 2010-06-15
First thing would be to check you have libvdpau installed in synaptic package manager, then try adding yourself to the video group in System>Users & Groups, reboot and after that try using xine instead of mplayer.

---

### Post by gabe17 on 2010-06-16
So I installed the libvdpau. If I run the video throught the command line using: ```
mplayer -vo vdpau -vc ffh264vdpau
```, it is really much better, but not 100% smooth (but much much better). I just can't understand why if I run it in other player, for example with smplayer, or gnome player, VLC or XINE, the video is awful. It's possible to be watched only across the command line runned mplayer, and as I mentioned, always not 100% smooth. The effect with decreasing the CPU usage is really good, my CPU is used only at 10-20% when playing the video. So what should I try next? Any ideas to play the video really as it should be?

---

### Post by wesleybishop on 2010-06-16
have you tried coreavc

---

### Post by wesleybishop on 2010-06-16
Also check this forum out [http://forums.whirlpool.net.au/forum-replies-archive.cfm/900615.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/900615.html) he had the same problem as you and he solved it by downloading every codec and player he could find lol

---

### Post by cchhrriiss121212 on 2010-06-16
Smplayer is just a GUI for mplayer so you should get the same output that you are getting from that mplayer terminal command. xine is the only other player to support vdpau, so using vlc or totem will not look any good. 
If that still is not smooth enough, then disable or remove compiz from your system.

---

