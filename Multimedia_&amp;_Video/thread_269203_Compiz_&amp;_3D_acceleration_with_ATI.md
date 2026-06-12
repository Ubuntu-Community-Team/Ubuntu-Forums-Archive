---
title: "Compiz &amp; 3D acceleration with ATI"
date: 2006-10-01
forum: Multimedia &amp; Video
---

### Post by mats-palats on 2006-10-01
HELP!

I installed Ubuntu Dapper about a week ago being a second time Linux-newbie. The installation went rather smoothly except for some screen issues. The main reason I installed Linux again (tried it for several years ago) was that I saw a video of Compiz in action. Bla bla bla, yada, yada, yada...

I have since the installation tried to install Compiz and all the preconfiguration that had to be done. With NO luck.
One of these days the 3D acceleration was working (I guess), since 'glxgears' was spinning nicely. Now they don't. I've been trying several howto's and tried installing Beryl, flglrx, glx and whatever names they have. Now I'm tired of it...

Can anyone help me with this? I only want Compiz to run. I don't care (for now) what window manager or setup it will take.

Computer hardware:
Acer (Laptop) Aspire 9504WSMi
Pentium M 760 2GHz
17"WXGA
**ATI mobility radeon x700 PCI express 256Mb VRAM**
yada yada yada

I have installed the latest ATI drivers (8.29.06) and here's my [xorg.conf]("http://www.ubuntuforums.org/attachment.php?attachmentid=16644&stc=1&d=1159717646")

```
glxinfo | grep rendering
``` gives me a big NO

Is this information sufficient?

Thankful for any help given!

---

### Post by tseliot on 2006-10-01
Do you use XGL?

BTW I don't know if that driver works with Compiz

---

### Post by mats-palats on 2006-10-01
Uhm... well, I don't really know. I've been trying to install xgl but I don't know if I'm using it. :confused: 

This is what Synaptic says about it:

```
xserver-xgl:
  Depends: libc6 (>=2.4-1) but 2.3.6-0ubuntu20 will be installed
```

---

### Post by junglepeanut on 2006-10-01
The driver works.

OK, so now I am wondering if you have xserver-xgl installed and the comment is for the upgrade, or it is not installed at all and you just need to install it? If it is the case that it is not already installed, it should work OK with your older one, that is what I am doing right now.

Next have you installed the beryl packages? They are in serious flux but that would probably be the best way. I like the Beryl (quinstorm) packages, in fact I don't know if I ever used any other version of compiz though. 

What kind of error are you experiencing? I mean is it working half-way etc? Does it draw windowless borders? Not start at all? If so what command are you using to start it, as it has gone through many changes and depending on what you have upgraded so far it may be a different command? 

If this does not fix the problem. Would you please post on the beryl forum where somebody who knows something (I'm just a user) maybe able to help. Or give more info to me about what is happening and I will continue to try.

---

### Post by mats-palats on 2006-10-01
Well, xserver-xgl seems to be installed, but in Synaptic there is a little star next to the package (don't know what it means). And when I try to upgrade it, it gives me the above message with libc6.

The Beryl packages seem to be installed too. But I haven't tried Beryl... First I want the 3D acceleration to work.

I'm sorry if I seem a little stupid, but I am very confused from all this. ;)

Edit:
I think I will make a complete reinstallation and start from scratch. Then I won't be confused about what I did and didn't do. :KS

---

### Post by junglepeanut on 2006-10-02
Just occurred to me, did you rebuild your ...I think it is the headers but it may be the kernel. Actually now that I think about it I think it is the kernel. Just double check the wiki for installing the driver.

I am just saying this as a couple of updates ago I could not get things to work and it was just because I forgot that crucial step since we are not using the normal apt-get/aptitude/synaptic methods for driver install.

Hope this helps.

Jp

---

### Post by mats-palats on 2006-10-02
Thank you for helping me guys.

I reinstalled the whole system (Ubuntu) and followed [this]("http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome") howto #2 and everything worked just fine. Except for some bugs ofcourse. So perhaps you were right about the kernel. Almost sounds like it.

---

