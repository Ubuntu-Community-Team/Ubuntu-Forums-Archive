---
title: "Twinview - Only OpenGL games open on wrong screen"
date: 2009-12-15
forum: Multimedia Software
---

### Post by boomernang on 2009-12-15
Hi, I am running Ubuntu 9.10 64bit and have nvidia drivers 185.18.36 (recommended distro)

I have a lcd tv 23 inch(1920x1080) as my primary screen and a 21" lcd screen as my secondary. Twinview works awesome and everything is fine, except - 
When i execute say warsow for example(fullscreen openGL), it opens up on my 21" lcd, not my primary screen.

This is a minor issue because it doesn't lag or anything, runs fine actually! It's just that it opens on the wrong screen!

This does not happen with movies or anything else.

Here is my xorg.conf - [http://pastebin.com/f281f650a](http://pastebin.com/f281f650a)

Someone mentioned I could change the "Order" in nvidia-settings but I'm not sure what that refers to; I have ticked "Make this my primary screen" for the 23" tv. That's all I can see that is relative.

Any ideas? Thanks for your time

---

### Post by boomernang on 2009-12-15
Just found out some more information from IRC that is very helpful. Nearly solved - 

Here is how the conversation went:

#nvidia on freenode

boomernang: here is my xorg.conf 
chibi-wing: you have to add in a metamode to do that
chibi-wing: something like "DFP-0: 1920x1080 +0+0, DFP-1: nvidia-auto-select +1920+0; DFP-0: 1920x1080 +0+0, DFP-1: NULL"
chibi-wing: don't remember the correct syntax
boomernang: I guess the real question is "how" does it choose the secondary screen at the moment for full screen opengl. or "why"?
chibi-wing: well DFP-0 is set to only be at 1920x1080
_chibi-wing:_ so if the game is set to a res that's not 1920x1080
chibi-wing: then it can't go on DFP-0

((DFP-0 is my main screen))

So that makes perfect sense, now I need to find out the correct syntax for that metamode in xorg.conf

---

