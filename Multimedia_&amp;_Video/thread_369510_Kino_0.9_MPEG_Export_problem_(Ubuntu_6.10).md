---
title: "Kino 0.9 MPEG Export problem (Ubuntu 6.10)"
date: 2007-02-24
forum: Multimedia &amp; Video
---

### Post by guy.murray on 2007-02-24
Hi all,
    when I attempt to export my captured video to DVD using any of the MPEG options of the export option of Kino 0.9, I get the following error...

**Error writing to KINO/MJPEG audio filter**

Is this a known problem with Ununtu 6.10/Kino 0.9, or is it just me?

Either way, is there a solution?

Many thanks

Guy

---

### Post by Hathor on 2007-03-01
Hi,

I had the same problem.
In Synaptic, I've installed the "mjpegtools" package.
What you may need:
sudo apt-get install kino mjpegtools ffmpeg kinoplus toolame mpeg2dec a52dec
[http://planet.ubuntu-fr.org/index.php?q=mjpegtools]("http://planet.ubuntu-fr.org/index.php?q=mjpegtools")

I don't have the problem anymore but when I export to mpeg, I don't have the video but just the sound! I think I miss something in the list above. I will try later.
I hope that you will solve your problem.
Regards

---

### Post by guy.murray on 2007-03-01
Hi,
   thanks for responding.

Tried 

sudo apt-get install kino mjpegtools ffmpeg kinoplus toolame mpeg2dec a52dec

but got the following...

The following packages have unmet dependencies:
  mjpegtools: Depends: aalib1 (>= 1.2)
              Depends: slang1 (> 1.4.9dbs-4) but it is not installable

tried installing these libraries but just got told that they were replaced by libaa1 and libslang1 which were already at their latest version.

Also tried installing Kino 0.92 from source but got bogged down in dependency hell. Hopefully it will be packaged for apt-get soon.

Guy

---

### Post by Buscando El Sol on 2007-04-08
Hi!:

I have the same problem with the same libraries trying to install mjpegtools package, finally I realize that I have the package already installed. If you want to check that, you can type:

$ sudo apt-cache pkgnames mjp

the mjpegtools must be in the list if it's installed.

cheers

luis

---

