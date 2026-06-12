---
title: "VDPAU and Flash videos"
date: 2013-04-13
forum: Multimedia Software
---

### Post by M3m3nt0 on 2013-04-13
Hi all!!

I'm here asking you if there is a way to get VDPAU works with flash videos (like youtube) in Firefox...

I'm  using Ubuntu 12.04 x64 on a Atom + Nvidia ION equipped motherboard and I've  activated the Experimental proprietary Nvidia drivers (310.40); using  Gnome MPlayer VDPAU works fine and I can watch 1080p movies without  problems...

When I try to watch a video from Youtube and I look  at the video's info I get "*accelerated video rendering*" but "*software  video decoding*"...
In Windows 7, instead, HD flash videos plays smoothly (even 1080p); infact i can see in the video info "*accelerated video rendering*" and "*accelerated video decoding*".


Any suggestion is higly appreciated!:)



(p.s: sorry for my bad english!!)

---

### Post by M3m3nt0 on 2013-04-15
Bump...

the same happens with a laptop equipped with Nvidia 8200M G (integrated) and Ubuntu 13.04 (32bit) with Nvidia drivers 313...

any suggestion?

---

### Post by M3m3nt0 on 2013-04-21
...no one could give me any hint?:(

---

### Post by brainwash on 2013-04-21
> **M3m3nt0 said:**
> ...no one could give me any hint?:(

Alright, here's a hint: EnableLinuxHWVideoDecode

---

### Post by monkeybrain2012 on 2013-04-21
If you only need vdpau for youtube and a few sites there is a better solution, which is not to use flash at all. There are two greasemonkey scripts which play flash videos in some popular sites (Youtube, Vimeo and Dailymotion etc) with mplayer which uses vdpau.  Install the gecko-mediaplayer plugin for Firefox (may not work well in Chrome but perfect in FF) and open gnome-mplayer, go to Edit > Preference and change the video output to vdpau

Here are the greasemonkey scripts.

[http://linterna-magica.nongnu.org/](http://linterna-magica.nongnu.org/)
[http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)

You only need one. In my experience Viewtube gives you more control (it doesn't load video automatically)  but LM works for more sites, LM uses regular expressions to detect flash objects so it works for many sites which are not even explicitly supported, the downside is sometimes you may encounter sites that freeze your browser (because they are too busy?) and these sites need to be excluded (from greasemonkey's settings)

In view of all the flash problems I think these scripts should get more exposures for Linux users.

Also, there is a standalone Youtube viewer that comes with Smplayer (so  can configure to use vdpau from Smplayer). Install the latest version   from the developer's  ppa

[https://launchpad.net/~rvm/+archive/smplayer]("https://launchpad.net/%7Ervm/+archive/smplayer")

---

### Post by pqwoerituytrueiwoq on 2013-04-21
this is what i use for that
[http://pastebin.com/RY4GqL6b](http://pastebin.com/RY4GqL6b) - saved to [FONT=courier new]/usr/local/bin/video[/FONT]
i pause the video and click the launcher on my panel that runs this command (only works on youtube after you change the playback quality)
```
video smplayer "-fullscreen -close-at-end -minigui"
```
this works on all flash videos that do not use DRM

@[**[COLOR=#000000]brainwash[/COLOR]**]("http://ubuntuforums.org/member.php?u=1579891") that is very unstable and has even locked my entire system up

---

### Post by M3m3nt0 on 2013-04-25
> **brainwash said:**
> Alright, here's a hint: EnableLinuxHWVideoDecode

Thanks, I've already tried this trick...but no luck :( it freezes my system (like **pqwoerituytrueiwoq**) 


I would add another "clue" that will (probably) help identify the problem: on Windows 7 if I use Internet Explorer I have no problem (accelerated rendering & decoding); instead if I use Firefox flash videos are laggy (accelerated rendering but only software decoding)...:confused: I've observed this behaviour either on my Atom (N330)+ION motherboard either on an AMD(C50)+Radeon HD 6250 netbook.

At this point I'm asking...Firefox problem?:(

---

### Post by M3m3nt0 on 2013-06-23
Update:

Using XBMC (and the YouTube plugin) all the flash videos run smoothly also at 1080p!!
Now I assume is a Firefox problem...or am I wrong?

any suggestions on which tests to perform?

---

### Post by SeijiSensei on 2013-06-23
> **M3m3nt0 said:**
> Now I assume is a Firefox problem...or am I wrong?

I'd blame Adobe, myself.  Now that I'm using an i5 I no longer need hardware acceleration so I can switch it off in flashplayer and not have human smurfs. In general that works fine. I've also thought about trying to use the [gecko-mediaplayer]("https://launchpad.net/ubuntu/+source/gecko-mediaplayer") plugin for Firefox from the repositories to play Flash videos but haven't gotten around to that option.  Maybe you can give it a try and report back.

---

