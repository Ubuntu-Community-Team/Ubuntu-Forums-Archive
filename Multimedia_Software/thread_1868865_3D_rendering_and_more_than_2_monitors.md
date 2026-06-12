---
title: "3D rendering and more than 2 monitors"
date: 2011-10-24
forum: Multimedia Software
---

### Post by oakdog8 on 2011-10-24
I just built a new computer and installed 11.10 with high hopes of a great desktop experience. I was planning on running 3 monitors and knew from past experience that nvidia had good linux support and configuration, so I got a GTS 450 and a motherboard with onboard video.

Well that was my first mistake. I searched long and hard and it seems there's no way to load two different graphics drivers no matter how many hacks are applied. That was disappointing, however I still had some cash so I got a second GTS 450.

However my troubles were not over. I was able to get all three monitors working with Xinerama and separate x sessions, but now there is no 3D rendering at all. Lame. Twinview works well with 2 monitors, but can't function on 3. Lame.

I found what looked like a working solution here: [http://ubuntuforums.org/showthread.php?t=884161&page=1](http://ubuntuforums.org/showthread.php?t=884161&page=1) , until I found that the xgl server he had installed is no longer available. I tried installing it manually from a package I found online but ran into trouble finding dependencies. 

Does anyone have any recent experience with this? Has anyone been able to get more than 2 monitors working with 3D graphics? I have to say it's pretty pathetic how difficult it is to get any more than 2 displays working, even in 2D. Clearly it's possible because there are options for two monitors like Twinview. Since twinview is for monitors on the same card, could I bridge my cards in SLI and still run all three monitors? What options do I have for 3D?

---

### Post by oakdog8 on 2011-10-26
Bump. Someone out there has to have been able to get 3+ monitors running with 3D in the past 2 years.

---

### Post by oakdog8 on 2011-10-28
Nobody? Anybody?

---

### Post by BicyclerBoy on 2011-10-28
3 separate X screens
or 2 in twinview & 1 extra separate X screen.
Can not use Xorg xinerama as this breaks openGL.

note: nVidia xinerama extension (auto loaded) is not the same as Xorg xinerama (deprecated).

Sadly, nVidia chooses to reserve real multi-monitor for mosaic on quadro or quadro-plex.

I'm no AMD fanboy but AMD multi-monitor eye-finity looks to p*%% all over nVidia.

---

### Post by oakdog8 on 2011-10-31
Why is that? I can't believe it is any more difficult that flipping a few booleans to allow more than two monitors in TwinView.

---

### Post by BicyclerBoy on 2011-10-31
Pro video cards (video & CAD) make them (& AMD)  a lot of money for basically the same hardware.
I guess the mosaic feature helps protect this market.

They would have to change the name from twinview to "nView" maybe..(like it is called in windows).

Judging by the problems people have with twinview/full-screen/composite/video-tearing...I would say the problem is significant.

Add to that..Xorg X server is nearing end-of-life to be replaced by wayland.
Ubuntu Unity is hell-bent on forcing composite managed/mangled desktops on the masses.

I think the Xorg X server does not allow multiple graphics drivers in the same X desktop.
I'm sure you can load multiple X servers/graphics drivers.

---

