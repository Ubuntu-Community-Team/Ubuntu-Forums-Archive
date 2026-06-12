---
title: "Adjusting Resolution for an another monitor."
date: 2009-01-21
forum: Multimedia Software
---

### Post by Kamex on 2009-01-21
I have a mac mini that has Windows, Linux, and Mac OS X on it. I have two monitors I use with the machine, but not at the same time. One is an ordinary LCD computer monitor that has a max resolution of 1920x1200 and is connected via DVI. The other is an LCD TV with a max resolution of 1920x1080 and is connected through an adapter that allows be to plug its VGA cable into my DVI slot.

Windows and Mac OS X behave normally. When I switched to the TV, they correctly displayed the TV's lower resolution of 1920x1080 and did not try to run in 1920x1200. Ubuntu, however, seems to have made up its mind that my monitor will always be a 1920x1200 monitor, because upon starting X, I get an error by my TV saying it can't display this mode. The thing is, when I first installed Ubuntu, it was with the monitor, and it had no problem detecting my monitor. In addition, I have noticed that the live CD, or a USB Flash installation of Ubuntu also has no problem detecting new monitors. Is there any way to make it do this automatically every time it starts on my installation (Done via WUBI)? If not, is there at least a way to manually reset the configuration so that it will detect the proper settings again like it does on first boot? I would not mind having to do it manually from the command line each time, as long as I can actually do it.

Trying to find the answer myself, I set up my Ubuntu environment to be inpendentant of X by removing gdm and usplash. From the command line, I tried the following:

sudo dexconf - This seemed to be what I was looking for according to a Google search, but it didn't seem to do anything.
sudo mv xorg.conf xorg.conf.old. I still get the same error from my TV doing this. I moved the old config file back afterwards.
sudo dpkg-reconfigure xserver-xorg - I was asked questions that didn't seem to be related to resolution. After answering the questions, the problem remained.

I could reinstall Ubuntu from scratch to work with the TV. I wouldn't mind the black bars on the top and bottom when I use my monitor, but I need to take the thing to a Linux computer club thing once a month, and I need to use a cheap CRT there. If I cannot reconfigure X for a different monitor, I would be unable to use Linux while there.

Any ideas?

---

