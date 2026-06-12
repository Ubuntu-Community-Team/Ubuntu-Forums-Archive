---
title: "playing dvd with totem"
date: 2007-06-15
forum: Multimedia &amp; Video
---

### Post by Chymera on 2007-06-15
i have recently installed ubuntu, and wanted to watch a video on it, so i stuck the dvd in the drive and started totem, it prompted me saying that it needed a few plugins, and if it should install them... I said yes...  but of course it didnt work after that either so i gave up on it...

Now the interesting part is that, every time i stick a dvd in the drive, after 1-2 minutes totem starts playing the dvd on its own, sound, subs, and all.... but if i close the window and open it again later,  guess what, i get prompted for the plugins :D , so i have to take the dvd out, put it again in, and wait another couple of minutes for it to get going on its own...

Inspite of the fact that i dont know very much about linux, I have a hunch that the plugins got installed but ubuntu forgot to make a note of the fact that they are there... I tried reinstalling the plugin but i got the same problem :(  how could i fix this?

---

### Post by frodon on 2007-06-15
Everything about the restricted drivers is explained here :
[https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29)

If it still don't work then maybe the problem is not related to the codec installation.

---

### Post by maher_79 on 2007-06-15
> **frodon said:**
> Everything about the restricted drivers is explained here :
[https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29)

If it still don't work then maybe the problem is not related to the codec installation.

I have this problem as well - can't play DVDs on Totem.  This is the pop up error i get when i try to play one.

```
Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it
```

Also, when i insert the DVD and let Tomtem starts on its own to play it, then it will give me the following pop up error:

```
Could not open location; You may not have permission to open the file.
```  I can however open the DVD ROM and look at the files.  So i don't know what the above message is referring too!!

I have libdvdread3, libxine1-ffmpeg, libdvdread2, and Ubuntu restricted extras package.
What is the difference between totem-gstreamer and totem-xin?

---

### Post by Chymera on 2007-06-16
thank you very much for your suggestion frodon, i have followed the steps on that link, but i still get the same  thing. The only improvement i noticed was that afterwards i could play .rm files. Which is indeed helpful, but not my main problem.

I have tried installing totem with xine backend, and the only thing thats different is the error message, it just says  "Totem could not play 'dvd:/'. 
There is no plugin to handle this movie"

instead of what maher just posted...

Since being able to watch dvds properly is very important if i am to change full-time to ubuntu (and thats what im trying to do), i even reinstalled the whole thing (ubuntu, i mean), and got the same problem again :(

I have tried using MPlayer, but when i click on open dvd i just get a black window which remains so until i close it (which takes about 2-3 minutes)..
Still, as long as i dont use xine, the dvd starts playing on its own after i insert it----

Any other sugestions?

---

### Post by linuxfan3 on 2007-06-16
Did you install the libdvdcss2 package?

---

### Post by maher_79 on 2007-06-16
> **linuxfan3 said:**
> Did you install the libdvdcss2 package?

Yes that doesn't help either - still same problem.
There are the packeges i have installed:  libdvdread3, libxine1-ffmpeg, libdvdcss2, and Ubuntu restricted extras package.

Thanks for the help!

---

### Post by Gremlinzzz on 2007-06-16
I was having the same problem with totem and regular mplayer.couldnt get em to play a dvd movie.I read about smplayer at this forum thought i would give it a try , works like a charm not only does it play the movie but also adds sub text for those who need it.i uninstalled totem alltogether.:D

---

### Post by maher_79 on 2007-06-16
> **Gremlinzzz said:**
> I was having the same problem with totem and regular mplayer.couldnt get em to play a dvd movie.I read about smplayer at this forum thought i would give it a try , works like a charm not only does it play the movie but also adds sub text for those who need it.i uninstalled totem alltogether.:D

I will give mplayer a try when i get home from work.  Hope this works for me too!

---

### Post by Gremlinzzz on 2007-06-16
Thats SMPLAYER  its new far as i know but works good this is the forum i learn about it 
[http://ubuntuforums.org/showthread.php?t=472149&highlight=smplayer](http://ubuntuforums.org/showthread.php?t=472149&highlight=smplayer)

---

### Post by Gen2ly on 2007-06-16
install gstreamer0.10-ffmpeg, xine may obstruct it so I'd remove it.  Also you'll want to edit Removable Drives and Media.  In multimedia set Video DVD Discs to:

totem dvd://

---

### Post by Gremlinzzz on 2007-06-16
Heres it web site with a picture of smplayer [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/)

---

### Post by chele on 2007-06-29
> **maher_79 said:**
> I have this problem as well - can't play DVDs on Totem.  ... when i insert the DVD and let Totem starts on its own to play it, then it will give me the following pop up error:

```
Could not open location; You may not have permission to open the file.
```  I can however open the DVD ROM and look at the files.  So i don't know what the above message is referring too!! ...  This sounds like the permissions error as indicated in [this bug report]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/10550"). A workaround may be to force Totem to run as root by putting "gksudo" in front of the command to play DVD's in gnome-volume-manger.

---

