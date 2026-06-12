---
title: "Creative X-fi card doesn't work even in 8.10"
date: 2008-11-01
forum: Multimedia Software
---

### Post by macuser2000 on 2008-11-01
I'm trying to get my sound card working. I'm running ubuntu 8.10 AMD64. Does anyone know how to install it on there?

---

### Post by DeltaUK on 2008-11-08
bump

---

### Post by m.afifi on 2008-11-08
Download this file, [http://support.creative.com/downloads/download.aspx?nDownloadId=10792](http://support.creative.com/downloads/download.aspx?nDownloadId=10792)

Make sure you can compile kernel modules.

```

sudo apt-get install gcc
sudo apt-get install kernel-package

```

Expand the tar.gz file you've downloaded, change into the new directory

```

make
sudo make install

```

Reboot, and you should get sound.

---

### Post by VipeR_11 on 2008-11-08
i have the same problem :(

when i type

 "make"

in root terminal i receive:

" No targets specified and no makefile found"

What i am doing wrong??

Sorry i am noob with ubuntu :confused:

edit: maybe i know what i am doing wrong!!! i thing I am not properly in the direcotry!!! How we change into a directory? (told you noob :s )

---

### Post by VipeR_11 on 2008-11-08
Ok i found how to change direcotory lol that was the problem!!!

But still no sound after reboot i have the alsa X-FI added to my sound list pressing test and no sound i fi move from autodetect to manually select the X-Fi alsa i am getting this:

    audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample !  
    gconfaudiosink: Could not open audio device for playback.


:( :confused:

Any help here???

---

### Post by macuser2000 on 2008-11-08
Have it installed already, I've posted this thread before I've found out of the new driver

---

