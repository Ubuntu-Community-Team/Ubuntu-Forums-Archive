---
title: "[SOLVED] Gimp Won't Load Windows Images"
date: 2007-08-30
forum: Multimedia Production
---

### Post by cubeist on 2007-08-30
Hey There, here is the problem
GIMP won't load JPEG images that were downloaded via the xd card reader in my laptop.  Ubuntu does not recognize the card reader so I boot into my vista side and import the photos and then transfer the files over.  It doesn't matter how I transfer them over, ie burn a cd, use a pen drive, or just mount the partition and drag and drop.  Whatever method renders the jpeg unloadable by the GIMP.

When I attempt to open a jpeg from the desktop, or directly from the gimp the computer starts using all the ram available plus all the cpu and almost 1gb of swap while it tries to open the file.  It does that for a minute, or sometimes two, and then displays a generic fault warning that it is unable to load the image. (no error number unfortunately)

So far I have verified the jpegs (with jpeginfo) and they are not corrupt or damaged or anything, they open fine in all other programs like f-spot or image viewer.  I have also tried taking pictures with the camera and importing into linux via a usb cable and those images open fine... so it is definitely something windows did to the files.

I have completely removed and re-installed gimp and jpeg libs with no success.  Oh, and the system monitor shows the app that is using all the resources to open the file is simply called "jpeg"

Any suggestions are greatly appreciated.

---

### Post by dabl on 2007-08-31
That's pretty weird.  Hmmm, 23 hours and no reply -- I guess I'm not the only one who thinks it's weird!  :-?

I'd start doing some experiments to try to "isolate" the problem to Vista, Ubuntu, Gimp, or some hardware thing. So, for example:

- will gimp open jpegs downloaded from the Internet, or saved on a CD made with some other computer?

- will gimp open anything at all?

- can Ubuntu (nautilus) see jpeg files (thumbnails) on that card, or on anything else like a CD?

- will jpegs saved on that xd card by Vista open on any other computer?

Hopefully, the results of checking these things will point you toward the "bad actor" in your little drama.  :popcorn:

---

### Post by cubeist on 2007-08-31
It is crazy weird!  Thanks for your feedback.  I did make a little process, I opened an image from f-spot into gimp (using the open with command) and let it do it's crazy cpu, ram, swap hog thing for as long as it wanted... about 5 minutes later gimp opened the jpeg but it was an astounding 486 MB! For some reason the gimp interpolated 100x the amount of data in the image (the original was about 4.86MB).  Unfortunately I still cannot open from the desktop or from gimp.  As to your isolating techniques...

> **dabl said:**
> That's pretty weird.  Hmmm, 23 hours and no reply -- I guess I'm not the only one who thinks it's weird!  :-?

I'd start doing some experiments to try to "isolate" the problem to Vista, Ubuntu, Gimp, or some hardware thing. So, for example:

1. - will gimp open jpegs downloaded from the Internet, or saved on a CD made with some other computer?

2. - will gimp open anything at all?

3. - can Ubuntu (nautilus) see jpeg files (thumbnails) on that card, or on anything else like a CD?

4. - will jpegs saved on that xd card by Vista open on any other computer?

1. and 2. Yup, no problems at all... it opens all types of images almost instantly

3. yup. nautilus doesn't have a problem with them at all

4. again, yes.  rules out anything wrong with xd card or camera.

So, now that it is narrowed down a bit I will try a batch converting program in vista and convert all the jpegs to another format (probably png) and transfer them back to linux.  This way I can determine if it is a jpeg only issue or just vista.  Right now my best guess is that vista encoded some sort of exif data while importing that the gimp doesn't like.  I think I will also try gimp for windows and see if they open in vista.

I will post back later with results... any more suggestions are welcome!
:confused:

---

### Post by raijinsetsu on 2007-08-31
I would say something in your GIMP install is whacked... From the sound of it, the jpeg library is at fault. Can you open the jpegs in other programs on linux?

And the 438mb size is (most likely) the amount of memory used to store the image pixel by pixel, as this is the way it's stored in memory.

---

### Post by MerlinsLair on 2007-09-03
Hi,

Just came across this thread while researching a solution for an issue I'm having and did a little testing of my own.

I'm using XP Pro on one HD and Ubuntu 7.04 on a second HD. Both are in the same machine. Can access the windoze drive from Ubuntu and grab any image(s), files, etc. with no problems.

Tried opening an image from the windows drive through The GIMP on my Ubuntu drive. No issues in doing so. Was also able to edit the image and save it back to my windoze drive.

Maybe it is something to do with Vista if not any of the suggestions already mentioned?

---

### Post by cubeist on 2007-09-06
I fixed it!! :)

Unfortunately I still don't know what caused the problem, only that it was something windows vista did to the files that gimp didn't like.  Anyway, the fix was relatively easy.  I tried a couple different image converters to change the format but none of them liked the images either (extremely long conversion for a 5MB JPG, about 5 mins).  Just when I was about to quit I tried the built-in gthumb program and converted all the .JPG's to .jpeg's and now everything works dandy in the gimp.

Thanks for your replies, I hope this helps someone else in the future!

---

