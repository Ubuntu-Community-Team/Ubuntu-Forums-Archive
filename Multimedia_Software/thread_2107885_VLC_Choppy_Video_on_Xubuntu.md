---
title: "VLC Choppy Video on Xubuntu"
date: 2013-01-23
forum: Multimedia Software
---

### Post by John Jason Jordan on 2013-01-23
I have used VLC without problem for years on Ubuntu 10.04 Gnome, but I recently did a fresh install on the same computer of Xubuntu 12.04. Now I get choppy video in VLC, although audio is fine. The same videos play perfectly in Totem, but I prefer VLC. I also get slow response in VLC to clicking on menu items - like VLC is sucking up all the RAM/CPU power. But top says it is using only 4% CPU and about 50 MB RAM. In fact, nothing is using much RAM or CPU.

I deleted the vlc config file in ~/.config and restarted VLC, but no joy. I also reinstalled via Synaptic, but the video is still choppy. My good friend Mr. Google came up with a few similar complaints, but they were all on Windows, and none of them had a solution.

I need VLC for foreign movies, because Totem sucks at figuring out subtitles and odd video formats.

Can anybody help? Any suggestions welcome!

---

### Post by Toz on 2013-01-23
> Any suggestions welcome!Does [this]("http://blog.riswan.com/2012/05/how-to-fix-slow-choppy-video-playback.html") link help?

---

### Post by John Jason Jordan on 2013-01-23
> **Toz said:**
> Does [this]("http://blog.riswan.com/2012/05/how-to-fix-slow-choppy-video-playback.html") link help?

Thanks for the link. I played with all the settings changes mentioned in the link, but nothing made any difference. 

It is strange that the same video plays perfectly in Totem. And I never had choppy video with VLC on Ubuntu/Gnome 10.4. So the problem has to be a change in either Ubuntu/Xfce 12.04 or VLC 2.0.5 Twoflower. I don't know what version of VLC I had in 10.4, but it was whatever was current at that time. The computer is the same, so it can't be lack of adequate hardware.

I could play with more of the settings in VLC besides the ones mentioned in the link, but I have no idea what most of them do. And there are lots of them. The possible permutations would take forever to try. 

Since my original post I tried the Parole media player that came with Xubuntu 12.04. It also has choppy video, although not quite as bad as VLC. Yet Totem is smooth. 

Still baffled. I need more suggestions.

---

### Post by SeijiSensei on 2013-01-23
Install **smplayer** from the repositories. It was designed by its developer to simplify subtitle viewing when using mplayer.  It gives you complete control over things like whether to use an .srt file, whether to get the subs from a remote location, as well as using subs that are included in a container like Matroska (.mkv).  It also lets you choose the fonts and location for both plain and SSA/A** subtitles.

I really don't know why smplayer isn't the default player on most distributions.  It's one of the first things I add to any new installation of Ubuntu.

There's a Windows version as well at the developer's site, [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/).

---

### Post by John Jason Jordan on 2013-01-23
> **SeijiSensei said:**
> Install **smplayer** from the repositories. It was designed by its developer to simplify subtitle viewing when using mplayer.  It gives you complete control over things like whether to use an .srt file, whether to get the subs from a remote location, as well as using subs that are included in a container like Matroska (.mkv).  It also lets you choose the fonts and location for both plain and SSA/A** subtitles.

OK, I installed smplayer. I used Synaptic, which popped up a pile of dependencies, one of which was mplayer (of course). When I tried to play a video in smplayer it popped up a message that it couldn't tell what version of mplayer I wanted it to use. But the video was playing in spite of the error message. Strange.

Unfortunately, smplayer/mplayer also gives me choppy video. Maybe that's not really unfortunate because now we have three players that deliver choppy video (VLC, Parole, and Smplayer) and one that gives me smooth video (Totem).

Now all I need to do is figure out what Totem has that the others do not. Some video setting? A dependency or add-on?

---

### Post by monkeybrain2012 on 2013-01-23
> **John Jason Jordan said:**
> OK, I installed smplayer. I used Synaptic, which popped up a pile of dependencies, one of which was mplayer (of course). When I tried to play a video in smplayer it popped up a message that it couldn't tell what version of mplayer I wanted it to use. But the video was playing in spite of the error message. Strange.


Choose the newest version of mplayer in the popup. Also, I recommend the MOTU ppa for updated version of mplayer (actually mplayer2 is better in my opinion and it is also in the ppa) and rvm's ppa for the updated version of Smplayer (e.g the Youtube viewer in the repo's version doesn't work)

[https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily)
[https://launchpad.net/~rvm/+archive/ppa/](https://launchpad.net/~rvm/+archive/ppa/)

There seems to be some kind of performance regression in VLC since 2.15, it still works well on my system but 2.13 was smoother.

---

### Post by Yellow Pasque on 2013-01-23
I find it odd that Totem plays smoothly while Parole doesn't (since they both use gstreamer for playing).
What video card/driver does your setup use? Attach the relevant output from
```
sudo lspci -v
```

---

### Post by papibe on 2013-01-23
Hi John Jason Jordan.

If you are trying to play HD video, besides the settings linked by Toz, you need to install the proper vaapi libraries so VLC can actually use the video acceleration capabilities of your graphic card.

Just a thought.
Regards.

---

### Post by John Jason Jordan on 2013-01-23
> **papibe said:**
> If you are trying to play HD video, besides the settings linked by Toz, you need to install the proper vaapi libraries so VLC can actually use the video acceleration capabilities of your graphic card.

Indirectly, that got me to a solution.

First I installed the vaapi libraries. If anything, that made things worse. But after installing the libraries I noticed a checkbox in Preferences > Input and Codecs Settings for Use GPU accelerated coding. It was checked.

It finally dawned on me that VLC works fine on my Fedora 16 laptop, so I launched it and looked at the Preferences settings. The VLC on the laptop is 1.1.13 The Luggage. In the same Preferences > Input and Codecs section it shows a checkbox for "Use GPU acceleration (experimental). The box was not checked.

So I went back to the VLC 2.0.5 on the Xubuntu desktop and unchecked the box for GPU acceleration. After saving the setting and restarting VLC videos now play much better. It is not absolutely perfect, but good enough for me. 

It appears that "Use GPU acceleration" maybe should still be labeled "experimental." :)

And for the record, the desktop uses the GeForce 6150 on the motherboard. Another difference between the previous Ubuntu 10.04/Gnome and the new 12.04/Xfce is that the new installation is using nouveau, where on the older installation I had insalled the nVidia proprietary drivers.

---

### Post by SeijiSensei on 2013-01-24
NVIDIA cards prior to the GeForce 8xxx series have onboard H.264 decoding using VDPAU.  The 6150 doesn't have that, so you should see the same video performance using either driver.

---

