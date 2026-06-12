---
title: "Cannot mount .iso files"
date: 2011-08-18
forum: Multimedia Software
---

### Post by jasperytlau on 2011-08-18
Hey guys, I'm sorry. Some of you might this is a stupid post but I have only started using Ubuntu a couple months ago and am loving it :) Hope some of you could tell me how to mount .iso files. I tried using Gmount and Furius ISO mount, even followed instructions on the internet but I still can't see the .iso images. It appears to be empty or unmounted. Please help and thank you so much for all of your time :) I just wanna watch some movies but they in .iso :(

---

### Post by Savio2010 on 2011-08-18
Right Click on the iso file and select Open with Achieve Mounter.

Hope it helps.

---

### Post by kyletstrand on 2011-08-18
Another more geeky way of mounting the .iso files is to go to your terminal, create a manual mount point and mount it manually:

```
sudo mkdir /media/mount
sudo mount -o loop [yourisofile].iso
```

Doing that will mount your .iso to /media/mount where you will be able to access all the files.  You can mount it elsewhere, I just like to have separate mount files that I use so I don't get any conflicting information.

You only need to create the mount point once, so after the first time, all you need to do is the second command. 

When you are finished with your .iso, to unmount it, you simply type the following command:

```
sudo umount /media/mount
```

Hope that helps!  If you have any other questions, please ask!

---

### Post by orange2k on 2011-08-18
You can also install Acetone ISO from the software center.
It works just like Daemon Tools or similair in Windows...:)

---

### Post by andrew.46 on 2011-08-19
Can I ask what sort of iso images you are trying to mount? I ask mostly because many people are mounting dvd movie iso images, and these will play directly using a modern copy of vlc and MPlayer...

---

