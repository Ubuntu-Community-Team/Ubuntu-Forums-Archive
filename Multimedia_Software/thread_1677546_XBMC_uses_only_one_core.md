---
title: "XBMC uses only one core"
date: 2011-01-28
forum: Multimedia Software
---

### Post by beew on 2011-01-28
I was watching a movie clip in XBMC on a dual core machine and noticed that most of the time one cpu is working at 80-90% while the other is hovering around 10% . Is there a way to make it  distribute the load more evenly?

Also, as a related question, how do I find out whether mplayer is using both cores even though I have set number of threads for decoding in smplayer to be 2? The top command only shows the total usage.

---

### Post by beew on 2011-01-29
Hello? Any idea?
 
I found out that in my machine that uses vdpau XMBC does use both cores and playback is smooth. But on other machines without vdpau it uses only one core and stutters horribly for some high definition clip even though vlc and mplayer both handle them well (Here is another thing I don't understand, I think vlc is supposed to be able to use only one core but playback is smooth and system monitor shows that both cpus are about working equally)

---

### Post by beew on 2011-02-03
Bump!

---

### Post by beew on 2011-02-09
Bump!! I think XBMC supports multithreaded decoding, am I wrong?

---

### Post by P4man on 2011-02-09
AFAIK, XBMC uses FFmpeg for software decoding, and is limited to single thread decoding. That might be different if you can use VDPAU or VAAPI accelerated decoding. There are some experimental builds of XBMC that use ffmpeg-mt to support multithreaded cpu decoding, but you will have to google for that, and I dont know how up to date they are.

Frankly though, you really really want VDPAU to play HD content. I just build a XBMC box around some ancient single core athlon 64 with a geforce 8400, and it plays anything I throw at it without the cpu even exceeding 800 MHz coolnquiet state. CPU load is reported as 30-40%.. but at 800 MHz rather than its nominal 2700Mhz.

---

### Post by beew on 2011-02-09
> **P4man said:**
> AFAIK, XBMC uses FFmpeg for software decoding, and is limited to single thread decoding. That might be different if you can use VDPAU or VAAPI accelerated decoding. There are some experimental builds of XBMC that use ffmpeg-mt to support multithreaded cpu decoding, but you will have to google for that, and I dont know how up to date they are.

Frankly though, you really really want VDPAU to play HD content. I just build a XBMC box around some ancient single core athlon 64 with a geforce 8400, and it plays anything I throw at it without the cpu even exceeding 800 MHz coolnquiet state. CPU load is reported as 30-40%.. but at 800 MHz rather than its nominal 2700Mhz.

Yes, with vdpau xmbc plays high definition smoothly and uses both cores. I was asking because I would be interested in also using it in computers that don't have a Nvidia card. But it performs quite horribly in other machines. That is what I don't get. I think vlc also uses only one core, while playback is not always smooth, most time it is good enough, only xmbc stutter horribly Maybe  I need to adjust some settings?(I uses a ppa version of mplayer that uses multicore, it has the best performance on any machine without question, and it uses vdpau as well if it is available. Since I have mplayer doing the job already why would I care about xmbc you may ask. Well I think it is always good to have options, and it would not be befitting for a mature OS like Linux to have only one working option for something as basic as playing videos )

As an aside, I know that ffmpeg-mt has been around for quite sometimes. I don't understand why all Linux players (and definitely the Ubuntu version in the official repositories) are still stuck with single core ffmpeg. With high definition videos becoming more common and most computers today having at least dual core multithreading should be made the default. I uses the multicore version in mplayer,  I don't find it buggy in any way, but even a little buggy is better than not being able to watch most hd content at all.

---

### Post by P4man on 2011-02-09
I think you should ask that on the XBMC forum, but I dont think XBMC uses any installed standalone mplayer, it has one integrated. You'll need to compile your own XBMC to use another version, or find a git/svn repo somewhere that does it for you.

---

### Post by P4man on 2011-02-09
> **beew said:**
> As an aside, I know that ffmpeg-mt has been around for quite sometimes. I don't understand why all Linux players (and definitely the Ubuntu version in the official repositories) are still stuck with single core ffmpeg. With high definition videos becoming more common and most computers today having at least dual core multithreading should be made the default. I uses the multicore version in mplayer,  I don't find it buggy in any way, but even a little buggy is better than not being able to watch most hd content at all.

ffmpeg-mt will be merged in to ffmpeg. But if you consider how crucial ffmpeg is to a TON of apps, they cant afford it to be a "bit buggy".  Besides, GPU decode is the way forward anyway.

---

### Post by beew on 2011-02-09
> **P4man said:**
> ffmpeg-mt will be merged in to ffmpeg. But if you consider how crucial ffmpeg is to a TON of apps, they cant afford it to be a "bit buggy".  Besides, GPU decode is the way forward anyway.


I could be wrong but I think the only working GPU decoding is basically vdpau and a handful of Intel cards. I don't know about ATI, judging from forum posts they seem to have lots of problems with ATI cards.

---

### Post by P4man on 2011-02-09
GPU decode works on all ~5 year old videocards on windows. But AMD/ATI doesnt want to port their UVD decode engine to linux for some reason. On linux GPU decode works just fine on nvidia (VDPAU), Intel and even VIA (VAAPI). On AMD, no such luck.  In short, its only AMD+Linux where it doesnt work currently, that doesnt change the fact GPU decode is the best and most sensible way to do it.

---

### Post by beew on 2011-02-09
> **P4man said:**
> GPU decode works on all ~5 year old videocards on windows. But AMD/ATI doesnt want to port their UVD decode engine to linux for some reason. On linux GPU decode works just fine on nvidia (VDPAU), Intel and even VIA (VAAPI). On AMD, no such luck.  In short, its only AMD+Linux where it doesnt work currently, that doesnt change the fact GPU decode is the best and most sensible way to do it.


I can be wrong, but I think GPU decoding only works on a few Intel Cards (definitely not ~ 5 year old cards on Linux in my experience, so some old machines play 720p easily in Windows XP but it fries the cpu even playing 480p in Linux) I don't disagree that GPU decoding is the most sensible way to go, but it just strikes me as too precarious to put all the eggs in one basket. So much depends on the good will of graphic card manufactures. I think VDPAU is a gift from Nvidia to the Linux community, but to use VDPAU you still need the Nvidia proprietary drivers and it is out of the hand of the Linux community. It would be nice if there is a software alternative too (even not as ideal).

---

### Post by Redsandro on 2011-03-08
This is relevant to my interests.

My Media Center under control of a **Core 2 Duo 6300** running at **1.86GHz** on **Ubuntu 10.04.2 LTS** with a **GeForce 7600 GS** plays most HD (1080p) movies just fine. But some of the bigger ones choke half of the time, with the processor peaking at 50% all the time.

I do have the proprietary nVidia driver installed so I guess the card either doesn't support it or is not fast enough.

I'm pretty sure if I could use both cores, there wouldn't be a problem. **VLC**, **Gnome Mplayer** and **Totem** also choke.

Is there a player out there that does this out of the box? Without me needing to build and compile stuff?

Maybe this is the solution to play heavy movies in XBMC through an external player:
[http://wiki.xbmc.org/index.php?title=HOW-TO_use_an_External_Player_for_media_playback](http://wiki.xbmc.org/index.php?title=HOW-TO_use_an_External_Player_for_media_playback)

---

### Post by beew on 2011-03-08
> **Redsandro said:**
> This is relevant to my interests.

My Media Center under control of a **Core 2 Duo 6300** running at **1.86GHz** on **Ubuntu 10.04.2 LTS** with a **GeForce 7600 GS** plays most HD (1080p) movies just fine. But some of the bigger ones choke half of the time, with the processor peaking at 50% all the time.

I do have the proprietary nVidia driver installed so I guess the card either doesn't support it or is not fast enough.

I'm pretty sure if I could use both cores, there wouldn't be a problem. **VLC**, **Gnome Mplayer** and **Totem** also choke.

Is there a player out there that does this out of the box? Without me needing to build and compile stuff?

Maybe this is the solution to play heavy movies in XBMC through an external player:
[http://wiki.xbmc.org/index.php?title=HOW-TO_use_an_External_Player_for_media_playback](http://wiki.xbmc.org/index.php?title=HOW-TO_use_an_External_Player_for_media_playback)


Actually XBMC does use both cores  and it uses very little CPU on my machine that has vdpau. It is only on other machines (no Nvidia card or vdpau) that it doesn't. In fact it works flawlessly with vdpau on my laptop, but  on machines that don't have it, it chokes on videos that vlc and mplayer handle easily.

Try install mplayer from this ppa
[https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc") It is a multi-core built and works well with vdpau or without. I don't use coreavc, if you don't use coreavc just don't install dshowserver.

P.S. In my experience Totem is complete garbage, uninstalled it as soon as I set up my Ubuntu box. I don't know why it is used as the default.

---

### Post by Redsandro on 2011-03-09
Yes, VDPAU is master, that's established. :) But for people like me and TS it doesn't work, so we need a different solution. :)

Thanks for thinking with us, but I don't (want to) use (commercial) CoreAVC. TS mentioned his mplayer does multicore rendering. But I don't know how to set it up.

Also, I never 'really' use Totem, I always install a bunch of players and usually end up using VLC (apart from XBMC). But why is Totem crap? If I click something for a quick preview, Totem always plays it.

---

### Post by beew on 2011-03-09
No, you don't have to use coreavc if you don't want to. I don't, but I install from Rips' ppa because it is a nice build. There is a mplayer daily build ppa, I can't remember what it is now, try google but I am not sure if it is multi-threaded. A lot of people use the rvm ppa for mplayer, it is multi-threaded but it seems that it has not been  updated for quite a while and it is not avaliable for Maverick.

VLC is nice but it is single core

Totem chokes on videos that vlc and mplayer plays easily, it is very basic. I aslo don't like the interface (there may be builds that support multithread or vdpau, but I don't know)

---

### Post by P4man on 2011-03-10
> **beew said:**
> I can be wrong, but I think GPU decoding only works on a few Intel Cards (definitely not ~ 5 year old cards on Linux in my experience,

Not to nitpick, but using XBMC accelerated decode works fine on my intel X3100 laptop which is 4 years old. It struggles with very high bitrate x264 with DTS audio, but plays most 1080p vids I have (which are 10Mbit or below) with ease and very low CPU usage.  It  should also work on GMA 3000's which are indeed 5 years old.

> so some old machines play 720p easily in Windows XP but it fries the cpu even playing 480p in Linux)


Oh yes, quite a lot of them. All AMD/ATI based ones ;). For nVidia and Intel you have to go back ~5 years to find one that doesnt work properly with XMBC.

BTW, about the discrepancy between windows and linux; I just (re)build an XBMC machine for a neighbor. Based on a single core 2.6 GHz AMD64 and a Geforce GT440 (only low profile card I could find in stock). 

Using XBMC Live (ubuntu), it played my 1080p test video's with IIRC ~20-30% CPU load at 800 MHz. Unfortunately, I couldnt get HDMI audio to work (*) on xbmc live, so I finally installed windows. That same 1080p video, using the same XBMC version now requires ~50% CPU load at 2.7 GHz !? Even sitting in the interface the cpu will rarely drop below 2 GHz in windows where it never exceeds 1 GHz on ubuntu.

(*) interestingly, nVidia doesnt offer a certified linux driver for the GT440. There is one for the 420,430,450,460 etc, but not the 440. Not sure that has anything to do with it, video and VDPAU worked fine with the latest drivers, but HDMI audio did not, while that works fine with a GT420 I have in a different box.

---

### Post by Redsandro on 2011-03-10
Ah thanks **beew**! I misunderstood that part, I will check it out when I get home. Do you know if it´s possible to have the normal ´stable´ version from the repo´s and the mt build at the same time?

Nice **P4man**. If you have a lucky hardware combination, Linux performs quite well! Especially some older Windows games perform even better on my Linux machine (through wine).
But recently I don´t really get what makes a processor fast anymore. You mention this single core 2.6 GHz AMD that does a very good job. I have a single core Pentium 4 m 2.0 GHz that chokes on nearly everything except browsing with only a few tabs open. It´s hard (for me) to compare these days. :P

I was recently shopping for a laptop and I purposely narrowed my choice to laptops that were [on the list]("http://www.ubuntu.com/certification/release/10.10/laptops").

---

### Post by Yellow Pasque on 2011-03-10
> **Redsandro said:**
> My Media Center under control of a **Core 2 Duo 6300** running at **1.86GHz** on **Ubuntu 10.04.2 LTS** with a **GeForce 7600 GS** plays most HD (1080p) movies just fine. But some of the bigger ones choke half of the time, with the processor peaking at 50% all the time.


If you have a PCI-E slot, it would be easier just to get a card that supports vdpau (GT220/GT240/GT430). The 7600GS is a bit too old.

---

### Post by Redsandro on 2011-03-12
On the one hand you're right. On the other hand, I have a cpu core sitting there, already paid for, doing nothing. Software is available, just not mainstream yet.

---

### Post by Redsandro on 2011-03-15
Wow, it's very easy to get **mplayer-mt** indeed!

[SIZE="4"]**Get mplayer-mt**[/SIZE]

```
sudo apt-add-repository ppa:ripps818/coreavc
sudo apt-get update
sudo apt-get upgrade
```

**mplayer** gets updated to **mt** version. [SIZE="1"]CoreAVS has like **beew** said nothing to do with it.[/SIZE] It's easy indeed! :)

Note: **This works for MPlayer. Gnome MPlayer does not use MPlayer**. Use a different GUI to experience the improvement, such as **KMPlayer** or **SMPlayer**.

[SIZE="4"]**Add mplayer-mt to XBMC**[/SIZE]

To set this up for XBMC, copy the coreplayer config to your home [SIZE="1"](or not, but system-wide settings are always destroyed after an update)[/SIZE] and edit:

```
cp /usr/share/xbmc/system/playercorefactory.xml ~/.xbmc/userdata
gedit ~/.xbmc/userdata/playercorefactory.xml
```

Find:
```
  <players>
    <!-- These are compiled-in as re-ordering them would break scripts
    The following aliases may also be used:
      audiodefaultplayer, videodefaultplayer, videodefaultdvdplayer
    <player name="DVDPlayer" audio="true" video="true" />
    <player name="DVDPlayer" /> placeholder for MPlayer
    <player name="PAPlayer" audio="true" />
    -->
  </players>
```

Replace:
```
  <players>
    <!-- These are compiled-in as re-ordering them would break scripts
    The following aliases may also be used:
      audiodefaultplayer, videodefaultplayer, videodefaultdvdplayer
    <player name="DVDPlayer" audio="true" video="true" />
    <player name="DVDPlayer" /> placeholder for MPlayer
    <player name="PAPlayer" audio="true" />
    -->
    
    <player name="mplayer-mt" type="ExternalPlayer" audio="false" video="true">
      <filename>/usr/bin/mplayer</filename>
      <args>-fs "{1}"</args>
      <hidexbmc>false</hidexbmc>
    </player>
  </players>
```


Now in XBMC you can:

**Right Click > Play On... > mplayer-mt**

:popcorn:

[SIZE="4"]**Make mplayer-mt XBMC's default player for 1080p content**[/SIZE]

And take it one step further, if your 1080p hd files structurally stutter with the default player:

Find:
```
  </rules>
```
Replace:
```
    <!-- Use external player for highest definition video -->
    <rule filetypes="mkv|mp4" player="videodefaultplayer">
      <rule filename=".*1080.*" player="mplayer-mt" />
    </rule>
  </rules>
```

This makes every file named ***1080*.mkv** [SIZE="1"](e.g. "Elephants Dream.1080p.mkv")[/SIZE] automatically use the external mplayer-mt, while everything else keeps doing business as usual.

Ofcourse this messes up your XBMC (remote) controls during playback, but hey bow down to mplayer configuration for that. :)

Works with Lucid 10.04 LTS.

---

