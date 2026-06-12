---
title: "video playback banding"
date: 2008-01-14
forum: Multimedia &amp; Video
---

### Post by ckamc on 2008-01-14
During video playback of certain video's, whether they be h264 encoded or xvid, I would get some that would display a lot of banding during movement.

I changed various settings (codec, video output, media players) and I still get the same reaction

I run a 8600GTS and using the 169.07 drivers via envy install. I do notice that in my restricted drivers section that it says my card is in use but there is no checkmark for enabled.

Could it be this old LCD TV(2+ year old viewsonic running at 1280x720 @60hz)?

---

### Post by ckamc on 2008-01-15
bump

now all my video's have banding issues in full screen.

---

### Post by RomeReactor on 2008-01-15
Hi. Is your system under considerable load? check 'System->Administration->System Monitor' and see if something is consuming too much RAM or CPU cycles. Try installing some libraries:
```
sudo apt-get install ubuntu-restricted-extras
```

As for H264 videos, what player are you using? Totem usually has some trouble playing those videos smoothly; try installing Mplayer and use it for them:
```
sudo apt-get install mplayer
```

Also, if your willing (read [this first]("https://help.ubuntu.com/community/RestrictedFormats")) add the [Medibuntu respositories]("https://help.ubuntu.com/community/Medibuntu"):
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
Then:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
And lastly:
```
sudo apt-get install w32codecs
```

---

### Post by ckamc on 2008-01-15
Thank you, looks like it was just codec install....

---

### Post by ckamc on 2008-01-15
well the problem came back

I loaded a regular avi file that i noticed a lot of banding in for testing last night after installing codec's correctly (even made the directories that i was even missing)

however, today after 10hrs of sleep i went to watch a tv ripped show and I got banding again.

both in xine, mplayer, and smplayer

in xine i even changed the directory that it looked for codec and yet it displayed a lot of banding during playback....

video output is set to xv and config file displays the following
> 
[default]
fs=yes
zoom=yes
monitoraspect="16:9"

[gnome-mplayer]
vo=xv
vf=eq2
ao=jack
monitoraspect="16:9"I am a bit lost now. unsure how to go about things now.

I went thru and created teh codec directory that was not implaced along with the binary codec package from mplayer's site into both the codecs and win32 folers and yet now i am back to the same problem.

anyway to debug the issue?

---

