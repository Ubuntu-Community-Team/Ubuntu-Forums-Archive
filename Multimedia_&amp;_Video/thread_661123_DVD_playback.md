---
title: "DVD playback"
date: 2008-01-07
forum: Multimedia &amp; Video
---

### Post by Dodelijk on 2008-01-07
Hello All, 


Having a real problem  getting DVD playback to work in Gutsy. 

I have tried: 

using: 
```
sudo apt-get install ubuntu-restricted-extras
```

I have installed **Gstreamer** and related extras. 

i have installed **libdvdcss2**

But i can not play DVDs. 

in **Totem** i get the following message: 
```

Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc

```

**Mplayer**  will play the first part of the disk (the part you can't skip past ) and then it stops playback. 

And **Gxine** will play but the screen is scrambled and the only way to unscramble it is to open a menu so that it partially covers the screen. 

Another peculiarity is that once I have tried to play a DVD I can not eject the disk unless i first unmount the DVD drive with: 

```

umount /media/cdrom0 

```

Is there anything I can do? 

Thanks.....

---

### Post by reckless2k2 on 2008-01-07
[http://easylinux.info/wiki/Ubuntu:Gutsy#How_To_Add_DVD_Playback_Capability](http://easylinux.info/wiki/Ubuntu:Gutsy#How_To_Add_DVD_Playback_Capability)

make sure to thank me. hahaha

---

### Post by SunnyRabbiera on 2008-01-07
you may want to replace totem-gstreamer with totem-xine, it works better

---

### Post by Dodelijk on 2008-01-07
reckless2k2: Thanks(is that ok :lolflag:) I had tried those instructions before but they didn't work. I just retried them and gxine works. Great!

SunnyRabbiera: What how do I do what you suggested? 

Thank you both for your help

---

### Post by reckless2k2 on 2008-01-07
no problem. enjoy your DVD. haha

---

### Post by SunnyRabbiera on 2008-01-07
> **Dodelijk said:**
> reckless2k2: Thanks(is that ok :lolflag:) I had tried those instructions before but they didn't work. I just retried them and gxine works. Great!

SunnyRabbiera: What how do I do what you suggested? 

Thank you both for your help

well by default ubuntu comes with totem gstreamer, to replace it go into the package manager (synaptic, not add/remove) and search for totem xine.
synaptic is easy, to use it go to system, then administration then to "synaptic package manager"
after that type in your password and once its loaded use the search feature to look for what I suggested.
after it finds the package just click on the box next to "totem-xine" and select "mark for installation"

now it may want you to uninstall totem gstreamer, but really its better this way.
if you need more help use this page as reference:
[http://monkeyblog.org/ubuntu/installing/#installing_with_synaptic]("http://monkeyblog.org/ubuntu/installing/#installing_with_synaptic")

---

### Post by njwiley on 2008-01-08
My commercial DVD playback breaks when I allow update manager to upgrade libdvdcss2 from 1.2.5 to 1.2.9. Is anybody else running into this or is it just me?

---

### Post by ubu-for on 2008-01-08
> **Dodelijk said:**
> I just retried them and gxine works.

You can use VLC or Ogle to play your DVDs instead.

> **njwiley said:**
> My commercial DVD playback breaks when I allow update manager to upgrade libdvdcss2 from 1.2.5 to 1.2.9. Is anybody else running into this or is it just me?

Try an alternative DVD player (s.o.) or try libdvdcss2 from the [Medibuntu repositories](https://help.ubuntu.com/community/Medibuntu).

---

### Post by gregcss on 2008-01-08
nm

---

### Post by gregcss on 2008-01-08
I have VLC, Totem-xine and the restricted stuff installed and cant get DVD play back.

---

### Post by gregcss on 2008-01-09
Well, I got a DVD to play with Mplayer but no sound. Thats because I dont have the audio cable connected from the DVD-RW to the system boards. Whoops.

---

