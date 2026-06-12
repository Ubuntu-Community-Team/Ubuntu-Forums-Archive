---
title: "Ipod classic not mounting under 9.04"
date: 2009-08-28
forum: Multimedia Software
---

### Post by pimparello on 2009-08-28
Hello there,

I have e new ipod classic 120g and I want to use it with ubuntu 9.04. gtkpod and amarok installed, I already used an older ipod here, but under 8.10. 

The problem is: Nautilus recocngzes the ipod under 8.10 (on another computer) without problem, I could transfer files as usual. But on my laptop with ubuntu 9.04 I just don't get the ipod mounted. Nautilus doesn't recognize it anyway and doing it by hand gives the following output:

$ sudo mount -t vfat /dev/sdd2 /media/ipod
mount: only root can do that

What should I do? I heard that maybe upgrading the apple firmware using win and itunes might help, but I wonder whether I would loose all the files on the pod then?

How can I avoid that? Anyway: How can I avoid using running around searching a win-machine?

Thanks for your help!

edit: output lsusb:

Bus 001 Device 007: ID 05ac:1261 Apple, Inc. iPod Classic

edit2:
libgpod4 and libgpod-common are installed

---

### Post by pimparello on 2009-08-28
Does anyone know if the ipod classic will work under 9.10?


I have also installed this: [https://launchpad.net/~cconway/+archive/ppa](https://launchpad.net/~cconway/+archive/ppa)

and changed libgpod.
But it's still not working.

---

### Post by pedro_orange on 2009-08-28
Hey, I have a 120GB iPod classic, and yes I can confirm it works fine.

I use GTKPod for copying items to my iPod.

> $ sudo mount -t vfat /dev/sdd2 /media/ipod
mount: only root can do that

Have you tried adding an item to your /etc/fstab?

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

> What should I do? I heard that maybe upgrading the apple firmware using win and itunes might help, but I wonder whether I would loose all the files on the pod then?

I believe you can choose settings that will not automatically sync your iPod with the Windows machine when you plug it in. Perhaps turn that off before you try and upgrade the firmware.

---

### Post by Briped on 2009-08-28
My Ipod classic mounted fine on 9.04 till about 1 week ago. Then suddenly one day I couldn't transfer my podcasts, even if the Ipod appeared to be mounted. I messed about with it. Tried 3 different installations of 9.04 - still no good. Then I tried vista and Itunes. This worked fine, so I decided to reset my Ipod to factory settings: all files vanished. This was not a big problem, as I have them all on my HD, but the problem is that vista needed to be online while doing this, and Apple might have worked some magic to create further problems for non-windows users. Result = Now my Ipod won't mount at all! Not even using a live CD 8.10 or 9.04. My advice is:

Don't reset to factory settings using Itunes.

Anybody wants to buy a fairly new Ipod classic 120GB? 

My conclusion so far... An ubuntu update must have created some havoc, and I aggravated the problem resetting the device. I am hoping Canonical support has a solution to this problem, and will report back if I get it solved.

Britta

---

### Post by pimparello on 2009-08-29
@pedro_orange

I would like to use gtkpod, too. But first I would need to mount the ipod anyway. I think, the problem lies there, which software I use for transfer seems like a secondary question to me. Gtkpod now indeed offers the option to create a mountpoint for an ipod classic 120g, but it can't find one though it's connected and lsusb detects the device.

That's the problem...

(Under 8.10 gtkpod didn't offer to create a mountpoint for the 4th gen ipod, so I just used the one offered for g3 160g - and it worked fine. The big problem is that I don't have access to this machine anymore.)

I really wonder why it works under 8.10 and not under 9.04? 

AFAIK updating the firmware will in every case destroy the data on the ipod.

Please help!

---

### Post by bikerman2299 on 2009-09-10
Have you tried making your mount point, and adding it to fstab? I put my Gen 4 80gig under /media and it mounts up fine.

---

