---
title: "View .CR2 Raw Photos Without GIMP"
date: 2012-08-03
forum: Multimedia Software
---

### Post by refringe on 2012-08-03
Hi everyone,

I'm looking for a way I can view .CR2 raw photos without opening GIMP. It seams overkill to open a full-featured editing program just to view a photo. I'm looking for a program that will allow me to quickly view the photo and maybe cycle through them using the directional keys... Something like Image Viewer.

Or maybe there's an update for Image Viewer that will allow it to open .CR2 files. Right now when I try to open a .CR2 file in Image Viewer it just displays a transparent background.

Screenshot:
[http://www.dropmocks.com/mBkGJr](http://www.dropmocks.com/mBkGJr)

Possible?

[SIZE="1"][COLOR="Gray"]DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"[/COLOR][/SIZE]

---

### Post by Rallg on 2012-08-03
Yes. It can be done. My own camera is a Canon S100, and I save in raw (*.CR2) format. But I wish to give a long explanation, to avoid confusion:

First, understand that I am in Ubuntu 12.10 (development, Quantal Quetzal) so I may have some codecs installed that you don't yet have in 12.04 or earlier.

Your *.CR2 file contains a raw image AND a processed thumbnail, which is much bigger than a mere icon. I can open my *.CR2 files in Shotwell, which is the default image viewer. But I'm looking at the thumbnail, not the raw file. If all I want to do is see what the photo is, that's good enough. But not for editing!

If I want to look at the raw file and maybe do some essential color manipulations, without using GIMP, I have several choices. The easiest to use is "ufraw" HOWEVER current production versions have a problem interpreting raw files from certain cameras (such as my S100). I was able to get non-production source code from the programmer and compile it myself. Looks great.

There are a variety of other raw-capable programs available via Synaptic package manager. Use "raw" to search for them. Most rely on the same underlying codec, the main difference being the GUI. If your *.CR2 photos look odd in one of the programs, then the chance is good that it will look odd in all of them, until the development version of the codec is released. But most Canon camera files do not have this issue.

Now, here's the catch: Do you have Canon's own DPP (digital photo pro) program, or can you download it from the Canon web site? If you do, then I suggest you use it. It will run in WINE, but there is a trick to installing it (search forums for the trick). DPP has the advantage that corrections for Canon lens distortions and vignetting are included automatically. Then, you can export the file as TIFF for another program. If you open your *.CR2 directly in a non-Canon program, then the distortion and vignetting may be uncorrected, or only corrected via a "user database" which is not authoritative.

When you look at a camera-made JPEG file, or at the thumbnail for a *.CR2 file, you are seeing the result AFTER Canon's own software makes corrections. You will also see the corrections in DPP. But if you open the raw file in non-Canon software, it may look distorted; the software is not wrong, it is simply not applying corrections.

---

