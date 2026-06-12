---
title: "ISO format DVD playback"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by Shiva-Shinken on 2007-11-07
I have a DVD image (ISO) without any encryption sitting in a shared windows folder.  I can access the image and start it in different players with no problems (VLC, MPlayer etc...) but cannot use the chapter selection, fast-forwarding, etc.  To make thing worse, VLC will play the DVD for about 3-4 minutes and abruptly stop.  Trying to play it again just starts the DVD at the beginning.  Any input?

Jixy

---

### Post by ohzopants on 2007-11-07
This might be due to the fact that it is streaming the file.  Try copying it to a local directory and see if the problem persists.  Alternatively you could try mounting the image and playing it from the mounted directory:
```

sudo mkdir /media/iso
sudo mount -t iso9660 -o loop /path/to/iso/file.iso /media/iso

```

---

### Post by Shiva-Shinken on 2007-11-07
Woops, I neglected to mention that I did mount it and run it from the mounted directory.  I do not think it is a streaming issue.

J

---

### Post by ohzopants on 2007-11-07
Do any dvds work? Could it be that image in particular that is no good?

---

### Post by Shiva-Shinken on 2007-11-07
No, the image is fine, as I can play it just fine both from the PC it is on, and other networked computers (Windows XP and Vista) just fine.  On those machines, everything plays normally, menu shows up fine, and can scroll chapters and fast-forward etc.  It is on the Ubuntu machine that I am having issues :(

J

---

### Post by disturbed1 on 2007-11-07
Open it with VLC. You can drag and drop it on VLC, or use a correct mounting script.

A video DVD needs to be mounted as udf instead of iso9660.

Once mounted, you can point mplayer or VLC to that directory. But, I've always found it easiest to just open the image with VLC without mounting it.

---

### Post by Shiva-Shinken on 2007-11-08
> **disturbed1 said:**
> 

A video DVD needs to be mounted as udf instead of iso9660.




Any instructions on how to mount as udf instead of iso9660?  Can I just replace iso9660 in the following commands with udf?  

```
sudo mkdir /media/iso
sudo mount -t iso9660 -o loop /path/to/iso/file.iso /media/iso
```

Apologize for noobish question, just trying to learn Linux for the first time :)

J

---

### Post by disturbed1 on 2007-11-08
just change the -t option from iso9660 to udf.

sudo mount -t udf -o loop yourfile.iso /media/iso

sudo - give root access. Only root can use the mount command.

mount - to logically attach a file system

-t - define the type of file system you are attempting to attach

udf - Universal Disc Format. The type of file system used for DVD-VIDEO (1.02). Though DVD-VIDEO does use an iso9660 standard subset of the secondary volume descriptor, mounting with only the iso9660 code page will not properly allow access to the DVD-VIDEO files. This can be seen when mounting as type iso9660 in that all files will be lower case, which improper for DVD-VIDEO. 

-o the options given

loop - creates a virtual node. Useful for encrypting file systems, and injecting files (disc images) as a virtual file system.

yourfile.iso - the actual name of the iso/img file you wish to mount. THE nAmE is CaSE SENsitVe :)

/media/iso - the actual path where the file will be mounted to. This directory needs to already exist. It doesn't have to be in /media/*. I usually just keep a folder in /media called DVD. Makes it easy for me. It should most likely be an empty directory. I don't know if mounting it you /usr/bin would damage any files, but I sure wouldn't want to be the one to test this out ;)


Did you try VLC yet? Mplayer does not do menus that well, Totem does not do menus at all. VLC has supported both commercial and homebrew authored menus with any issues for me. I'm sure there's a few disc menus VLC will choke on, but for the most part it is fool proof.

---

### Post by Shiva-Shinken on 2007-11-09
Since the DVD is in a windows shared PC, will the "/path/to/iso/file.iso" actually say smb://path/to/iso/file.iso ?

J

---

### Post by mommebu on 2007-11-21
While in earlier versions of ubuntu totem-xine was able to play iso files it seems to fail now if you load the image from the menu, however from terminal it worked for me using:
totem-xine dvd://absolute/path/to/your/iso/file.iso &
This is without mounting the image, don't know if it will work with a windows file server though...

Strange that the newer version lost the feature from the menu though...

---

### Post by Dive4Life on 2008-01-10
I was wondering. if I mount an ISO DVD this way, can I use Handbrake on that mounted ISO file?  Once mounted, how do you unmount it?  Whats the script for that.

---

### Post by diafygi on 2008-05-20
> **Dive4Life said:**
> I was wondering. if I mount an ISO DVD this way, can I use Handbrake on that mounted ISO file?  Once mounted, how do you unmount it?  Whats the script for that.

I just use the gui interface [gMount-iso]("https://launchpad.net/gmount-iso/") for mounting iso images.

EDIT: You can also unmount using this interface.

---

