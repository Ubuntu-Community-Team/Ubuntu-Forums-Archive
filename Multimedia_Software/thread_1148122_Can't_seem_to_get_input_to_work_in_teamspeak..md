---
title: "Can't seem to get input to work in teamspeak."
date: 2009-05-04
forum: Multimedia Software
---

### Post by Kristofer Gustafsson on 2009-05-04
Hey all, i use teamspeak to talk with friends and stuff and i use it quite often. It's something that i can sacrifice but i would like to make it work. 

If i go to preferences > sound > audio conferencing, capture. Then choose "HDA Intel ALC833 Analog (ALSA)" i can use sound recorder so on, it works. I can hear myself clearly. If i choose anything with OSS tho, i cant hear anything. I can use sound recorder and stuff, it works but teamspeak...

In teamspeak > settings > options. I can set sound driver, the default is oss /dev/dsp. I have tried to use /dev/dsp1 tho i dont even have that in /dev.. I tried /dev/adsp even tho i don't even know what that is :P

I read on some wiki page that teamspeak for linux is oss and there's no native support for alsa.. I think :P 

I'm sure this is a common question i have googled but there's so many pages around about different things its hard to find the right answer.

---

### Post by Yoghurt_LX on 2009-05-04
Had that weekend exactly the same problem. Nothing did work in TeamSpeak while everywhere else all worked fine. Even the assigned key didn't work in TeamSpeak when I pressed it to talk.

Did find out that the short cut from the menu calls "padsp teamspeak" which cause a no go.
Opening a Terminal and enter "teamspeak" should start TS and work fine.
Change the "padsp teamspeak" in the menu short cut to "teamspeak".

---

