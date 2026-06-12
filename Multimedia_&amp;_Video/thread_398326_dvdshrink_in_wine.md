---
title: "dvdshrink in wine"
date: 2007-03-31
forum: Multimedia &amp; Video
---

### Post by mshale on 2007-03-31
Hi all, 
I just installed dvd shrink using wine.  I got to run the program, and it opens, but doesn't recognize my combo drive on my laptop.  Any suggestions??

---

### Post by tenn on 2007-03-31
Try running the command,
**winecfg** in the terminal, and than adding DVDShrink with add application button and than setting Window version to** Windows NT 4.0**

---

### Post by FrozenFOXX on 2007-04-02
I have to admit I'm having the same problem regardless of Windows setting (using 0.9.34 of Wine).

For me I gave up on getting it to recognize the drive (I even tried manually setting it...no dice) and just mount the disc manually to the /media/cdrom0/ mount point.  Then I just point the program to the directory instead of opening a disc and voila, it finds it.


Now personally I'm having big issues with getting a usable image as for some reason the last time I tried this I ended up with a DVD image that was bigger than the DVD itself (the original, actually).  How?  I don't know, trying to retest that now.

---

### Post by stchman on 2007-04-02
> **mshale said:**
> Hi all, 
I just installed dvd shrink using wine.  I got to run the program, and it opens, but doesn't recognize my combo drive on my laptop.  Any suggestions??

Yes, intsall k9copy.

sudo apt-get install k9copy

It does the exact same thing as DVDShrink.  Follow the steps on my webpage:

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

This will get CSS decryption up and going on Ubuntu.  After k9copy is done decrypting and compressing it will burn it to a DVD using k3b or just create a .iso.

---

### Post by williammanda on 2007-04-03
Is there a program that will mount a virtual drive to play an image or iso file? Once K9 makes the iso can it be played somehow?
Thanks

---

### Post by FrozenFOXX on 2007-04-03
You could mount the image onto a location.  I used to do this in Gentoo but cannot remember right offhand.  However I remember there is a way to mount a disk image like an ISO so it can be read.

---

### Post by pixeldotz on 2007-04-03
yes there is.

here's the command i use to mount iso's taken from another thread.

**Everything in Linux is a directory.**

**Applications -> Accessories -> Terminal**

```
sudo mkdir /media/iso
sudo mount -t iso9660 -o loop filename.iso /media/iso
df -h


```

now just point your file browser to /media/iso and your files from the dvd iso will be there. play them as you wish.

---

### Post by FrozenFOXX on 2007-04-03
Ah yeah, the loopback, thank you.

---

### Post by mshale on 2007-04-03
Ok, I tried to use k9copy, but it seems to give me an error, and an option to report a bug when it gets about 1/2 way through the dvd.  I popped in to Windows, and used dvd shrink, and it let me know that there was this new protection where the makers of dvds actually mess with the structure of the dvd table.  with dvdDecryptor to place dummy sectors and VTfix to fix those dummy sectors, I can get it copied.  

That may be wrong now that I think about it.  Sorry for the long post, but it seems that this is the problem:  I insert the dvd into my combodrive, and i get an option to play or view info of the dvd.  it's like it is an embedded program in the dvd itself.  If you want to see what i'm talking about, go rent The Holiday.  If anydvd is running when you put this dvd in, it causes anydvd to buggout and close, then windows doesn't even recognize a dvd in the drive.  

so both k9copy and windows ripping tools fail.  I guess that the authors have finally produced a dvd that just isn't coppyable.  :(

*update*  I will admit though, that k9copy was twice as fast as dvdshrink.  I do believe that k9copy is the superior program, but is still no match for that new protection.

---

### Post by yabbadabbadont on 2007-04-03
> **mshale said:**
> I guess that the authors have finally produced a dvd that just isn't coppyable.  :(

Use google to search for dvdfabdecrypter.  Unlike dvdshrink and dvddecrypter, it is still maintained and updated.  It can handle newer discs that the other two can't.  Just FYI.

---

### Post by stchman on 2007-04-03
> **mshale said:**
> Ok, I tried to use k9copy, but it seems to give me an error, and an option to report a bug when it gets about 1/2 way through the dvd.  I popped in to Windows, and used dvd shrink, and it let me know that there was this new protection where the makers of dvds actually mess with the structure of the dvd table.  with dvdDecryptor to place dummy sectors and VTfix to fix those dummy sectors, I can get it copied.  

That may be wrong now that I think about it.  Sorry for the long post, but it seems that this is the problem:  I insert the dvd into my combodrive, and i get an option to play or view info of the dvd.  it's like it is an embedded program in the dvd itself.  If you want to see what i'm talking about, go rent The Holiday.  If anydvd is running when you put this dvd in, it causes anydvd to buggout and close, then windows doesn't even recognize a dvd in the drive.  

so both k9copy and windows ripping tools fail.  I guess that the authors have finally produced a dvd that just isn't coppyable.  :(

*update*  I will admit though, that k9copy was twice as fast as dvdshrink.  I do believe that k9copy is the superior program, but is still no match for that new protection.

Go to k9copy website [http://k9copy.sourceforge.net/](http://k9copy.sourceforge.net/) and get the latest version.  If I remember right Ubuntu uses an older version.  You may have to build it though.

---

### Post by gtr225 on 2007-04-10
Hey I tried both K9copy and DVDshrink and even though k9 is faster I had a DVD that was overly compressed and the menus were heavily pixelated. Is there any way to get better compression out of k9copy? Even though DVDshrink is a lot slower, I've never had that problem with it.

---

