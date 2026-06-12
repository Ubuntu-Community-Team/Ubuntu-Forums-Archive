---
title: "720p/1080p audio sync problem (SMPlayer, VLC)"
date: 2008-07-24
forum: Multimedia Software
---

### Post by Zarok on 2008-07-24
Greetings

I have the following issue with my new Ubuntu 8.04 installation.

While trying to watch any .mkv container 720p/1080p videos, the audio on SMPlayer is maybe about .5 seconds off sync, not much but enough to be visible and very annoying. I've noticed that the audio syncronisation option on it does nothing to skew the audio anywhere, so I can't fix it with that either. 

I've tried it with several 1080p and 720p files, so it's not an off sync movie issue. There's something wrong with SMPlayer and I can't figure out what. I've tried switching the audio decoder it uses to ALSA from Pulse etc, no help. Totem doesn't even play the file, and if I use native mplayer without the SMPlayer extension, it goes horribly OOS FAST. The audio codec SMPlayer is using for it according to the file info is a52. I tried using ffac3 but it had the same slight audio skew to it, and the audio channels were messed up.

With VLC Player the problem isn't audio sync, that works fine. With VLC the issue is that it only uses 1 of my 2 CPU cores for the video processing, thus lacking the computing power for smooth video playback(I've checked this by having a terminal open with top running - cpu usage won't go over 52% or smth, while with smplayer it goes up to 65% and plays everything smooth while VLC has nasty frame drops). And file seeking is broke.

So. Any good ideas if VLC can be enabled to use both CPU cores to avoid really annoying file freezes/frame drops, or any ideas how I could get that annoying sync skew fixed on SMP? SMP works fine with non-mkv video, so I'm guessing the codecs are the issue, but why/how is beyond me.

Edit:

I also tried with Xine, same synch issue as SMPlayer, which really leads me to believe that the issue has to be codec-related to the A52 codec. Oh and I forgot to mention, the audio "card" I use is an integrated Realtek chip on a MSI p775 Platinum-motherboard.

---

### Post by shirilover on 2008-07-24
Taken from the MPlayer man page:

	

+ and &#8722;      Adjust audio delay by +/&#8722; 0.1 seconds.

---

### Post by Zarok on 2008-07-25
Like I said on my first post, messing with mplayer's audio skew settings helps nothing, cause I believe its a codec issue not a problem with the player itself. No matter how much I mess about with the plusses and minuses you mentioned, it'll go straight off sync in a matter of seconds if I get it even remotely right. I was thinking about trying CoreAVC for Linux if that'd help, as long as I get it installed somehow...

---

### Post by rvm4000 on 2008-07-25
Did you try the framedrop option? That makes mplayer to skip some frames from time to time to keep audio sync.

---

### Post by Zarok on 2008-07-27
> **rvm4000 said:**
> Did you try the framedrop option? That makes mplayer to skip some frames from time to time to keep audio sync.
Yep, doesn't help. The files are also off sync as soon as I start them, they don't go gradually off. I also tried fixing sync again with the +- buttons and noticed if I sync it up to one scene and watch for maybe a minute more, then it is hugely off. Like if the audio is too fast, and I ---- for a bit, then a minute later the audio is behind alot. 

I know its not the files that mess it up, cause I've tried like 4 different files that I know are in sync(work in VLC excluding cpu-related freezes & work 100% in windows and for other people), smplayer works fine with divx/xvid, so its just mkv-related. I can always just watch 720p on VLC, but it doesn't have enough CPU power for 1080p, so this problem is pretty annoying. :/

---

### Post by rvm4000 on 2008-07-28
I've just remembered that some versions of mplayer contain a bug which makes -framedrop not to work, if used with -correct-pts (which is enabled by default).

The workaround is to pass -no-correct-pts (or -nocorrect-pts, I'm not sure) to mplayer. You can do it in smplayer in Preferences -> Advanced -> Options for mplayer -> Options.

[http://lists.mplayerhq.hu/pipermail/mplayer-users/2008-February/071685.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2008-February/071685.html)

---

### Post by Zarok on 2008-07-28
> **rvm4000 said:**
> I've just remembered that some versions of mplayer contain a bug which makes -framedrop not to work, if used with -correct-pts (which is enabled by default).

The workaround is to pass -no-correct-pts (or -nocorrect-pts, I'm not sure) to mplayer. You can do it in smplayer in Preferences -> Advanced -> Options for mplayer -> Options.

[http://lists.mplayerhq.hu/pipermail/mplayer-users/2008-February/071685.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2008-February/071685.html)


Aaaand that's another nogo. -nocorrect-pts caused nothing to play at all so I figure that's a wrong syntax, while -no-correct-pts didn't help the issue at all. :( This is getting pretty incredibly frustrating.

---

### Post by rvm4000 on 2008-07-28
Mmmm, could you provide a sample or a link to a small video which exhibits this problem?

---

### Post by Zarok on 2008-07-28
> **rvm4000 said:**
> Mmmm, could you provide a sample or a link to a small video which exhibits this problem?

Its basically any 720p/1080p video I've tested. I've tried including but not limited to:
10 episodes of Sarah Connor Chronicles tvrip
300 1080p rip
Batman Begins 1080p rip
Mythbusters Shark week 720p tvrip
Bunch of random movie samples including
Zodiac
Matrix Revolutions
etc.
All of those rips are fine in windows and aren't "nuked", so the videos are allright. I can't really supply a sample, cause I have nowhere to upload anything and I can't find any legal 720p mkvs anywhere :P All movie trailers etc are .mov, which aren't the issue.


Edit: Eh.. now I'm getting paranoid if its all video/audio or something.. Maybe it's some other delay issue rather than the players or codecs... I'm pretty sure Xvids are in sync tho and I'm not blind, but still. Making me paranoid :P Just feels like all mkv video starts playback like ,1 - .2 seconds earlier than audio and that messes it up and framedrops change nothing, but still. Its really bizarre. And pisses me off :/ Its like every time I pause/fast forward it feels like video starts playing slightly before the audio, same with when I start the file. Urgh.

---

### Post by wu-stix on 2008-07-28
I had the same problem.  Tried to change all the setting and nothing worked.  It really pissed me off because it took 3 days to download the movie.  In the end I just went to blockbuster and rented it on blu-ray.

---

### Post by rvm4000 on 2008-07-28
I've only got one 720p mkv video.

First, my computer is not fast enough to play HD videos. I had to scale it to 768x432. I also had to enable the options "Allow frame drop" and "Skip the loop filter" in Preferences -> Performance to be able to play it.

And yes, it seems the audio has to be delayed about -200 ms to be completely sync'd with the video. (This can be done in the menu Audio).

If this problem is something generalized then it should be reported to the mplayer developers so they can fix it.

---

### Post by Zarok on 2008-07-28
> **wu-stix said:**
> I had the same problem.  Tried to change all the setting and nothing worked.  It really pissed me off because it took 3 days to download the movie.  In the end I just went to blockbuster and rented it on blu-ray.

Hm, what's your setup? Maybe there's something in common...
I use the basic a52 audio codec & FFH264 video players offer to download when they need codecs, gstreamer pack or something. Hardware etc setup is:
Intel core 2 duo e6400
2gb DDR2 533mhz ram
Gainward GF7900 Golden Sample using the Nvidia-gtk-new driver, hooked up to a Mirai 42" HDTV I had to setup manually in xorg.conf cause the driver didn't recognize the resolutions right,
Realtek integrated audio chip on a MSI P775 Platinum mobo
Ubuntu 8.10
Mplayer I used the default version from the repositories with apt-get mplayer, currently I have mplayer 2:1.0rc2-0 ubuntu13+medibuntu1 installed, also tried with Xine 0.99.3. VLC that works (I think atleast) is 0.86.

---

### Post by wu-stix on 2008-07-29
I have the Phenom 2.5Ghz, with Asus m3a78-eh-hdmi mobo, 3Gb ram, I use the hdmi and this has caused quite a bit of headache but its good now.  I used movieplayer and downloaded all the codecs I could find.    My tv is a 1080p Hitatchi plasma.  I have the ati accelerated graphics driver. Maybe this is a 64-bit problem, kind of like the flashplayer problem.

---

### Post by Zarok on 2008-08-02
> **wu-stix said:**
> I have the Phenom 2.5Ghz, with Asus m3a78-eh-hdmi mobo, 3Gb ram, I use the hdmi and this has caused quite a bit of headache but its good now.  I used movieplayer and downloaded all the codecs I could find.    My tv is a 1080p Hitatchi plasma.  I have the ati accelerated graphics driver. Maybe this is a 64-bit problem, kind of like the flashplayer problem.
I actually don't have the 64bit ubu distro installed cus I was concerned about random compatibility etc issues so... :/

---

