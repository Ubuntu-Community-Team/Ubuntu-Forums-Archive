---
title: "OSS stopped working"
date: 2008-06-03
forum: Multimedia Software
---

### Post by Zeikcied on 2008-06-03
I noticed a few months ago that the MPlayer plug-in for Firefox stopped outputting audio when using the OSS setting.  I switched to ALSA, and everything was fine.

I have since run into a problem with a program that uses OSS, and has no option to use any other program for the sound.  OSS still doesn't work, even after the upgrade to Hardy.

I was able to get the program working by using the aoss command, but I'd rather have OSS working than have to go to the command line to open a program.

How can I fix OSS?

EDIT: When looking around in Adept, I found a package called oss-compat, which I guess is a package that enables compatibility with OSS.  After I installed that, everything is fine.  Did Ubuntu discontinue OSS support?

---

