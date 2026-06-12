---
title: "Problem mounting DVD movie ISO's from mkisofs / k3b on OS X"
date: 2008-05-13
forum: Multimedia Software
---

### Post by deviantintegral on 2008-05-13
Hi,

I have a bunch of VIDEO_TS folders which I now want to convert into .ISO images. I can successfully create an image with mkisofs / genisoimage and k3b, and it mounts fine with loopback and plays with VLC.

```
mkisofs -dvd-video -o IMAGE.iso -r -udf -V VOLNAME DVD_FOLDER/
```

However, when I mount this images on OS X (10.5.2), the image shows no contents. I can mount images on both systems if I create them on OS X using:

```
hdiutil makehybrid -udf -udf-volume-name VOLNAME -o IMAGE.iso DVD_FOLDER
```

Is there some flag I need to set to get the images to work properly on OS X?

Thanks!
--Andrew

---

### Post by mc4man on 2008-05-13
don't have a mac so don't know but maybe look in genisoimage help, there is some mac, apple, hfs stuff

---

### Post by zeronothing on 2008-05-13
you could try this application to compile the iso. I like to use this program acetoneiso. there [website]("http://acetoneiso.netsons.org/index.php") has .deb packages available for ubuntu hardy heron. so install is very simple. have at it.

---

### Post by deviantintegral on 2008-05-14
Thanks for the suggestion of Acetone. I was able to successfully create an image which would mount, but playing with DVD Player wouldn't work, and VLC would crash! My guess is that it wasn't doing the proper setup for a DVD video, but the way it uses fuse to make ISO's is neat :)

Coming at this from another angle - is there a way to verify a DVD video image to know that it meets the DVD spec and should play properly? Perhaps that will tell me where the problem lies.

--Andrew

---

### Post by bulletxt on 2008-05-16
> **deviantintegral said:**
> Thanks for the suggestion of Acetone. I was able to successfully create an image which would mount, but playing with DVD Player wouldn't work, and VLC would crash! My guess is that it wasn't doing the proper setup for a DVD video, but the way it uses fuse to make ISO's is neat :)

Coming at this from another angle - is there a way to verify a DVD video image to know that it meets the DVD spec and should play properly? Perhaps that will tell me where the problem lies.

--Andrew

Hi, i'm one of AcetoneISO's developers. We're rewriting from scratch almost everything and the next release will include a lot of new stuff including burning functions. I will personally implement creating correct ISO of DVD Video folders.

---

### Post by mc4man on 2008-05-16
> creating correct ISO of DVD Video folders. What is it that these couple of apps (including apparently yours) are doing 'incorrectly' in terms of dvd video? Any iso creator that I've ever used always produced images that were compatible in any Os and/or ultimately standalones.

---

### Post by bulletxt on 2008-05-16
> **mc4man said:**
> What is it that these couple of apps (including apparently yours) are doing 'incorrectly' in terms of dvd video? Any iso creator that I've ever used always produced images that were compatible in any Os and/or ultimately standalones.


currently ISOs are created as standard Rock Ridge and Joliet format as ISO9660 filesystem. for a dvd video compatible 100% with dvd players, the -dvd-video option must pass to create a UDF file system structure. of course you need to prepare a DVD-Video compliant directory tree.

---

### Post by mc4man on 2008-05-16
> Hi, i'm one of AcetoneISO's developers. We're rewriting from scratch almost everything and the next release will include a lot of new stuff including burning functions. I will personally implement creating correct ISO of DVD Video folders.
looking foward to that, seems like it will be a good thing, particulary for people who want to use linux only apps. One of the few progs. I carried from windows is Imgburn, atm there is no linux app that even comes close in terms of creating, burning, options and displayed info.

---

### Post by deviantintegral on 2008-05-16
Apparently using hdiutil doesn't always work with all standalone players, for anyone else reading this thread. I haven't had any problems, but YMMV.

Toast has been able to create images which work in everything I've tried so far. But it's proprietary, doesn't work on Linux, and is much slower because the image has to be read and written to over the network in my case :(

Perhaps the problems with mkisofs aren't related to DVD video at all; I'll try making some data-only UDF images and see if I can get them to mount properly.

Anyone tried Nero for Linux? Does it let you make DVD images?

--Andrew

---

### Post by mc4man on 2008-05-16
> Anyone tried Nero for Linux? Does it let you make DVD images?
i dl'ed the demo (was curious if it included the cdspeed tools, it doesn't).
you could certainly use it to create an iso and either stop there or burn. Personally I wouldn't pay for nero, it was never the best choice in windows and there would be no reason to expect otherwise in linux.

---

### Post by alegallo on 2008-06-19
I guess it is a genisoimage bug in version 1.1.6-1ubuntu6, which ships with hardy and replaces mkisofs

A solution has been found here:

[http://ubuntuforums.org/showthread.php?p=5217002#post5217002](http://ubuntuforums.org/showthread.php?p=5217002#post5217002)

Hope it helps ;)

---

### Post by deviantintegral on 2008-06-19
Thanks! Installing the latest cdrkit from source allowed an image to mount fine.

---

