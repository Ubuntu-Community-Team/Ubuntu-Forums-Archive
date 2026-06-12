---
title: "Horizontal rendering lines during fast movement when playing DVDs"
date: 2009-03-17
forum: Multimedia Software
---

### Post by simonfogliato on 2009-03-17
Problem:
I need help when playing DVDs! I have followed the Medibuntu instructions to the letter by adding the repository + key and installing libdvdcss2. I can play any DVD just fine but during play whenever there is movement I can see these strange horizontal render lines like the decoder can’t seem to keep up with play. They are very close together, almost half a millimeter. It wouldn’t really bother me so much if I weren’t such a movie buff.

Things I have tried:
I have tested this on multiple PC’s like my laptop with a built in nvidia card and my desktop with an nvidia 8600GTSoc PC-Express card. I have also tested this on Ubuntu 64 as well as x86 and with various players like MPlayer, VLC, etc. So I am 100% sure that this is a software issue related to the DVD decoder.

My only other option I can think of is to go to the Canonical store and buy PowerDVD Linux because the free decoder from Medibuntu is not fast enough?

All I ask is that my Ubuntu play crystal clear smooth DVDs just like my Windows PC. Help!?

---

### Post by xc3RnbFO8P on 2009-03-17
Did you install [Medbuntu]("https://help.ubuntu.com/community/Medibuntu") codec?

---

### Post by simonfogliato on 2009-03-17
I installed the following:
[LIST]
[*]sudo apt-get install libdvdcss2
[/LIST]

Do I also need to install the codec for Playing Non-Native Media Formats? Isn't libdvdcss2 all you need???

---

### Post by mc4man on 2009-03-17
Those may be interlacing artifacts. Most dvd's are progressive but many that come from tv sources are interlaced. (and some film based dvd's are poorly done and will show interlacing artifacts.

Try enabling 'deinterlace' in your player (some players have multiple deinterlace choices, some have only 1 default.

I did notice that with a 7800gs card that playback of progressive sources was not as good in 8.10 with the nvidia 177 drivers as it was in 8.04

Switching to the 180.29 driver resolved that

---

### Post by lovinglinux on 2009-03-17
I think this is not a DVD related issue. This kind of lines appear when you play any type of video, but only when there is lots of movement. It is known nvidia card problem, that can be fixed with newer drivers.

Try disabling compiz to see if the problem persists. If not, then is the same problem a lot people have. Check [this thread]("http://ubuntuforums.org/showthread.php?t=942339"), there are several possible workarounds suggested. The only one that worked for me is turning off compiz. But the best solution is to upgrade the video driver if you can.

---

### Post by simonfogliato on 2009-03-18
My issue has been SOLVED! I did exactly what you guys said and just used the latest nvidia driver and bingo it was crystal clear! This was one of those things where I overcomplicated things.

libdvdcss2 + latest nvidia driver = perfect dvd play

Thank you very much for all your help...

---

### Post by simonfogliato on 2009-04-12
Okay the lines are back so I still require your help! I was so impressed with Intrepid that I installed Jaunty to try it out and as soon as I did I noticed that the lines were back. I did exactly the same things as I did before to get the DVD to play but now with Jaunty I have the lines!

The following were my steps:
1) Install Jaunty
2) Did a full OS update
3) Installed libdvdcss2, etc for Jaunty
4) Installed Mplayer
R) Playing DVD showed the lines
5) Activated the latest NVIDIA driver v180 as per recommended
R) Playing DVD still showed the lines

I have attached and image to better understand what I am talking about. I know it is possible to get this to work because I did it in Intrepid and I am repeating my steps with Jaunty without success.

---

### Post by simonfogliato on 2009-04-14
Eureka!!! I have finally solved my stupid line problem and learned a few things about DVDs... Ubuntu/Video Drivers/libdvdcss2 were all working just fine, the only issue was **interlacing**.

I could type an essay on the topic now but to better explain interlacing please read:
       - [http://tldp.org/HOWTO/DVD-Playback-HOWTO/usage.html](http://tldp.org/HOWTO/DVD-Playback-HOWTO/usage.html)

The solution is **deinterlacing**, it is the process of converting source material that contains alternating half-pictures to a computer screen that displays a full picture at a time. Aka fixing interlaced DVD video. The following link explains everything you need to know on how to fix the problem and apply your custom deinterlacing technique.
       - [http://tldp.org/HOWTO/DVD-Playback-HOWTO/usage.html](http://tldp.org/HOWTO/DVD-Playback-HOWTO/usage.html)

Most all players support deinterlacing to correct your interlaced video. For example open up a DVD using VLC media player and select - "Video > Deinterlace > Linear". Bingo problem solved...

---

