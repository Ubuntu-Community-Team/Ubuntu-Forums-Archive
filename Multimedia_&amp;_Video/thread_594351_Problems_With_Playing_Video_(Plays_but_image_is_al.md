---
title: "Problems With Playing Video (Plays but image is all...crap.)"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by Mr_Congeniality on 2007-10-27
I installed some codecs so I could play some video files, but I can't watch them.  Example included.

Using NVidia video card, by the way.

[[IMG]http://img141.imageshack.us/img141/3582/issuescz3.th.png[/IMG]](http://img141.imageshack.us/my.php?image=issuescz3.png)

---

### Post by fain on 2007-10-27
Yup had this same friggen problem. What i did was use the envy program to install my nvidia drivers for me. It cleans up whatever is the cause. There is a known bug with the 100.14.19 driver that causes this. [https://bugs.launchpad.net/ubuntu/+bug/155618]("https://bugs.launchpad.net/ubuntu/+bug/155618")

theres a few posts on the nvidia forums about it saying that they know what it is and will be fixed in an upcoming release....

just curious what chipset are u using?

---

### Post by williammanda on 2007-10-28
I'm a 64 bit user, core 2 duo, and I have the same problem with the video as the first user. I use mythtv and xine. If I start mythtv then goto xine then I get the "garbled" messed up screen too. This is what I did to overcome the problem. I installed Envy and uninstalled Nvidia then re-installed the driver and I used xine -V XShm to start xine. This is the info I got from xine:

The image looks strange, it is shifted, cropped or shows weird lines!
This points to a problem with the Xv extension, which is used by xine to display the video image. To verify this, try running xine with the XShm video output plugin:
   xine -V XShm
If that works fine, you just proved, that the Xv extension is buggy. xine will remember the last used video output plugin, so the setting will stay at XShm. You could simply continue using this, but XShm is a lot slower than Xv, so read on and see if you can get it working. Usually you should look for updated versions of the X driver module that belongs to your graphics card.
Other possibilites are limitations in either your X driver module or your graphics hardware. If your card could somehow be running out of ressources (graphics RAM perhaps) and displays an incorrect Xv overlay because of that, try reducing the display resolution and/or colour depth.
Consult the next question for more details on Xv. 

Now everything works ok.
Thanks

---

### Post by fain on 2007-10-28
yes it does have to do with Xv. something weird happened to me last night i started up mythtv and boom pink screen of death when it was working before? So used envy to install the driver again and it worked again??? Theres something writing some where that is causing this. i wish i knew more about the video subsystem so i could try and debug this.

---

### Post by williammanda on 2007-10-28
Well I still have the problem. I found this post on the Nvidia site:

Just now, I was experiencing the problem. Before finding this thread, and using totem to watch videos. I went into the Multimedia Systems Selector in Gnome, and on the video tab, I left the output plugin set to XV, but I changed the device from Default to "NV05 Video Blitter" and the problem went away for me.

If I set it to "NV17 Video Texture", it comes back for me. I suspect it is the XvmcUsesTextures option in my xorg.conf. I turned it off, but haven't restarted my X session yet.

[http://www.nvnews.net/vbulletin/showthread.php?t=98852&page=3](http://www.nvnews.net/vbulletin/showthread.php?t=98852&page=3)

I made this change and haven't had a problem yet.

---

### Post by bananaman on 2007-10-28
Im having the exact same problem except i found the problem goes away when i completely disable compiz desktop effects... this is odd because it used to work fine when i had just installed Gutsy... 

What I want to know is if this is an issue with my nvidia driver or with compiz... so i know where to look for an answer... could this have been caused by an update? Cause im telling you it used to work fine...

---

### Post by williammanda on 2007-10-29
From what I have found this is a problem with Nvidia, refer to the link posted in the earlier thread. I already had compiz disabled but still had the problem.
Thanks

---

### Post by williammanda on 2007-10-29
> **williammanda said:**
> Well I still have the problem. I found this post on the Nvidia site:

Just now, I was experiencing the problem. Before finding this thread, and using totem to watch videos. I went into the Multimedia Systems Selector in Gnome, and on the video tab, I left the output plugin set to XV, but I changed the device from Default to "NV05 Video Blitter" and the problem went away for me.

If I set it to "NV17 Video Texture", it comes back for me. I suspect it is the XvmcUsesTextures option in my xorg.conf. I turned it off, but haven't restarted my X session yet.

[http://www.nvnews.net/vbulletin/showthread.php?t=98852&page=3](http://www.nvnews.net/vbulletin/showthread.php?t=98852&page=3)

I made this change and haven't had a problem yet.

This fix causes Xine to have problems with playback. Xine will freeze up, which sometimes requires a reboot.
Thanks

---

### Post by williammanda on 2007-10-29
I just wanted to post the same problem on another post:
[http://ubuntuforums.org/showthread.php?p=3665081#post3665081](http://ubuntuforums.org/showthread.php?p=3665081#post3665081)

Thanks

---

### Post by williammanda on 2007-10-29
One user went back to version 100.14.11. Does anyone know how to do this using Envy or another way that wouldn't be to involved with the command line?
Thanks

---

### Post by williammanda on 2007-11-05
I tried the downgrade see this post:
[http://ubuntuforums.org/showthread.php?t=597618&page=3](http://ubuntuforums.org/showthread.php?t=597618&page=3)

---

