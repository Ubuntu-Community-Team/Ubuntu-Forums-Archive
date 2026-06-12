---
title: "totem+compiz cube video while rotation or preview"
date: 2010-03-14
forum: Multimedia Software
---

### Post by Frudo on 2010-03-14
Hi there , 
I spend hours to figure out this one , but no luck. I am fairly new to ubuntu and digging problems or settings to figure out myself. This is with totem player video playback. 
i use ubuntu 9.10 , 64 bit , compiz effects works fine with my onboard ati rodeon express X1150 vosro 1000 laptop. 
Here is the deal. 
I realized i can not see the playing video , say enabling transparency while rotating the cube or in previews as i group the active windows with totem. As you rotate the cube other desktops the video is black, if you move the cube up-downwards its cutting the video into kind of half. or like chopping it from corners according to the angle you are looking at. or as if there is a delay if you move it around.gradually if you only rotate the cube facing right in front of you looking straight to it like focused you can see the video. same in expo view. Its as if like when you move the totem player screen , video inside is not fixedto the frame  and does not move with the player window itself. ](*,), went through the settings there is nothing. This is for totem only though. 
To test i pulled up vlc , 2 simultaneous players , started playing , rotate cube everything is normal. Can see 2 live playing even from absurd angles or inside transparent cube. Expo view OK, previews OK ?
As i said this is only in totem , and i changed “gstreamer-properties” too, no luck. 
I see vlc has an overlay video setting +skip frames setting enabled on my player not applicable in totem?. i want to use totem because of its simplicity , 5+1 surround sound output (dont know the right output setting in vlc for my home theater)  
This is really hard to describe but please have a look at this link for video fix 
[http://www.ubuntugeek.com/fix-for-video-playback-problem-in-compiz-fusion.html](http://www.ubuntugeek.com/fix-for-video-playback-problem-in-compiz-fusion.html)

Also irrelevant but can someone help me with the name of this effect. 
I have enabled edge scrolling under touch pad prop., i can scroll both vertical and horizontal. Now pull up 2 windows , place 1 in front , one kind of at  background  but bigger size.   hold down ALT key , scroll down up from your touch pad. You see active window being transparent and disappear completely and lets you see the inactive at the back ground. ? ;)

Thanks Frudo

---

### Post by Yellow Pasque on 2010-03-14
Some things to try - 
Updated video drivers: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
Updated gstreamer: [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

---

### Post by Frudo on 2010-03-14
> **Temüjin said:**
> Some things to try - 
Updated video drivers: [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
Updated gstreamer: [https://launchpad.net/~gstreamer-developers/+archive/ppa]("https://launchpad.net/%7Egstreamer-developers/+archive/ppa")

I am thinking if it was a vga problem , it should be doing it in vlc too. Am i right ?
for gstreamer it can be the problem to search for yes,  i sure will have a look at your links 
T 
Thanks

---

