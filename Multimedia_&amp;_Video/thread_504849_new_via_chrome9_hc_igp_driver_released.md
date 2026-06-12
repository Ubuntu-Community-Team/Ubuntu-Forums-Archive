---
title: "new via chrome9 hc igp driver released?"
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by bandofmercy on 2007-07-19
after buying this laptop (everex stepnote something or other--specifically because it was CHEAP) several months ago it looks as though support for the video card has finally been released--using ubuntu in 800x600 since then has been nearly impossible:
[http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=164](http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=164)
(scroll to the bottom)

can anyone help me figger out how to install this driver?  i've read the documentation but dont have a very good handle on it and am afraid i might mess everything up... it isn't on synaptic, is it?

---

### Post by overdrank on 2007-07-19
> **bandofmercy said:**
> after buying this laptop (everex stepnote something or other--specifically because it was CHEAP) several months ago it looks as though support for the video card has finally been released--using ubuntu in 800x600 since then has been nearly impossible:
[http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=164](http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=164)
(scroll to the bottom)

can anyone help me figger out how to install this driver?  i've read the documentation but dont have a very good handle on it and am afraid i might mess everything up... it isn't on synaptic, is it?

Hi they are tgz files and if you extract the file there is a installation file within. I have only compiled like that twice and it is time consuming, If you would like to attempt installing I would say backup your data so that if all goes wrong you will at least save that. I would suggest this link to maybe help you with your quest
[http://www.monkeyblog.org/ubuntu/installing/#source](http://www.monkeyblog.org/ubuntu/installing/#source)
Good luck! :popcorn:

---

### Post by bandofmercy on 2007-07-19
compiling the driver i should be okay with... here is the part i am having trouble with (from the instructions):
```
3. Prepare kernel source for VIA display driver (DRM) or rebuild kernel (AGP). 
   *The sample is default kernel in Fedora Core Linux 5.
       ...[different distributions are listed, i used debian...]
   *The sample is default kernel in Debian Linux 4.0.
       # cd /usr/src/
       # tar jxvf kernel-source-2.6.18.tar.bz2
       # cd kernel-source-2.6.18
       # cp /boot/config-2.6.18-4-486 .config
   Note: Depending on your system used, it may take 10 or 15 minutes to finish.
   Note: Mandriva Linux 2007.0 will have the kernel source tree in /usr/src/ 
         folder when installing the kernel source rpm package 
         "kernel-source-2.6.17.5mdv-1-1mdv2007.0".
```

i tried ignoring this but got a warning about missing the kernel something or other so i stopped.  i went back, this time following the debian directions and going into /usr/src/linux-headers-2.6.20-generic (per my uname -r) because there was no tar file-- but maybe this isn't where i should be for ubuntu?

so anyhows then i went into my /boot folder and got ready to copy config-2.6.20.16-generic into the new file "configure" in my /usr/src/linux-headers-2.... folder when i thought... perhaps this "linux-headers" means i am in the wrong place altogether... or i at least have to change something in one of the driver's install files?  or change the kernel name in one of those?

my first preference would be for someone to just post a whole long tutorial that explains everything for me... go!

---

### Post by bandofmercy on 2007-07-19
here is the releasenotes.txt file which contains the instructions... i don't really know what to make of it though except that it might have something to do with this:

[https://wiki.ubuntu.com/KernelSourceDriver?highlight=%28KERNEL%29%7C%28SOURCE%29](https://wiki.ubuntu.com/KernelSourceDriver?highlight=%28KERNEL%29%7C%28SOURCE%29)

---

### Post by bandofmercy on 2007-07-23
wahhhhh help me wahhhh i'm a big baby

---

### Post by hessajee on 2007-08-12
Hi.

I'm new to Ubuntu, and after searching have found this thread which relates to my problem. Now I'm using Ubuntu 7.04 (Feisty Fawn) and am trying to install the drivers in the link also mentioned above:

[http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=164]("http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=164")

Now in the PDF, it mentions that I need some dependency packages, however when I looked in the Synaptic Package Manager for:

mesa-6.5.2.orig.tar.gz
mesa_6.5.2-3ubuntu7.diff.gz

I could not find it. I've searched and found all the others and installed them, and now I'm stuck as to how to progress.

Hopefully someone can help out, as I just want to have better resolution than 800 x 640. Otherwise it looks like I'll have to get rid of this system or buy a graphics card (which I don't want to do as I only use it for browsing and working).

Thanks.

---

### Post by hessajee on 2007-08-12
OK, I've managed to find the files elsewhere and install manually.

Now I'm stuck on doing part (d). I've tried to put "EXTRAVERSION= -15-generic" in the same line as vi /usr/src/linux/Makefile as well as whilst I was in the Makefile, however I don't know how to complete it afterwards.

Can someone help me out here please? Thanks.

---

### Post by will peavy on 2007-08-15
Have you had any luck? I've got an Everex Stepnote and am having the same issue

---

### Post by bandofmercy on 2007-08-16
no, everybody just ignores me... i figure that it will be integrated into a future version's kernel and i'll just have to wait until then...

---

### Post by jdx on 2007-08-21
Yes, that VIA video driver README.pdf is poorly written.
The INSTRUCTIONs do mention mesa, but don't say where to find
Get those two mesa archives from here:


[http://launchpadlibrarian.net/7079188/mesa_6.5.2.orig.tar.gz](http://launchpadlibrarian.net/7079188/mesa_6.5.2.orig.tar.gz)
and
[http://launchpadlibrarian.net/7079189/mesa_6.5.2-3ubuntu7.diff.gz](http://launchpadlibrarian.net/7079189/mesa_6.5.2-3ubuntu7.diff.gz)


It is not Ubuntu's fault that VIA's (or my) instructions are cursory, so:
 - be patient
 - persist
 - read the Fancy manual

---

