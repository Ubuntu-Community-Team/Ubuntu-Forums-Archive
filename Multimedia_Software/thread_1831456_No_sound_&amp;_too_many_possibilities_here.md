---
title: "No sound &amp; too many possibilities here"
date: 2011-08-23
forum: Multimedia Software
---

### Post by savafan on 2011-08-23
First let me say that I have spent many hours looking through threads to find a similar problem that I am having, & yes, there are many but I cannot seem to find the correct fix.

I have a HP laptop model HP G72 Notebook PC, Processor Intel(R) Core(TM) i3 CPU M 350 @2.27GHz & the Sound devices are Intel(R) Display Audio & Realtek High Definition Audio.

This machine came loaded with Windows7 & I have successfully dual booted it with Ubuntu Lucid 10.04.3.

The problem I am having is that I cannot get the sound to work at all in Ubuntu. No opening sounds or anything else that I have tried. No Web sounds, no CD sounds... All sounds work fine on the Windows side, but nothing I have tried so far seem to work with Ubuntu & I have tried many options from many threads.

Any help at all from anybody?

---

### Post by handy on 2011-08-23
So you have been through this thread:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by lidex on 2011-08-24
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

