---
title: "Video Conversion problems"
date: 2010-10-23
forum: Multimedia Software
---

### Post by Oscareightyone on 2010-10-23
I have just recently switched to Ubuntu from windows xp. I can see why so many people use it. I also have an ipod classic. Using it with ubuntu is a nightmare. I can put movies on if they are in mpeg4 format, but mine are avi. I have tried every Linux video converter, but none work. I can post the error messages if you want.](*,)I have been trying all day!

---

### Post by coffee412 on 2010-10-23
> **Oscareightyone said:**
> I have just recently switched to Ubuntu from windows xp. I can see why so many people use it. I also have an ipod classic. Using it with ubuntu is a nightmare. I can put movies on if they are in mpeg4 format, but mine are avi. I have tried every Linux video converter, but none work. I can post the error messages if you want.](*,)I have been trying all day!

Just gotta love those ipods eh?

I use avidemux-gtk which is available thru the software center for install. Under the auto selection choose ipod and it should set up the correct video/audio codecs to use and then you can convert your movies and then move them over to the ipod.

have fun.

---

### Post by Oscareightyone on 2010-10-23
> **coffee412 said:**
> Just gotta love those ipods eh?

I use avidemux-gtk which is available thru the software center for install. Under the auto selection choose ipod and it should set up the correct video/audio codecs to use and then you can convert your movies and then move them over to the ipod.

have fun.
Thanks, I can see this working! But can you please tell me what settings to use to be ipod classic compatible? I can't work it out.

---

### Post by coffee412 on 2010-10-23
> **Oscareightyone said:**
> Thanks, I can see this working! But can you please tell me what settings to use to be ipod classic compatible? I can't work it out.

> **Video**

                     
[LIST]
[*]H.264 video, up to 1.5 Mbps, 640 by 480 pixels, 30 frames per  second, Low-Complexity version of the H.264 Baseline Profile with AAC-LC  audio up to 160 Kbps, 48kHz, stereo audio in .m4v, .mp4, and .mov file  formats; H.264 video, up to 2.5 Mbps, 640 by 480 pixels, 30 frames per  second, Baseline Profile up to Level 3.0 with AAC-LC audio up to 160  Kbps, 48kHz, stereo audio in .m4v, .mp4, and .mov file formats; MPEG-4  video, up to 2.5 Mbps, 640 by 480 pixels, 30 frames per second, Simple  Profile with AAC-LC audio up to 160 Kbps, 48kHz, stereo audio in .m4v,  .mp4, and .mov file formats
[/LIST]
[http://www.apple.com/ipodclassic/specs.html](http://www.apple.com/ipodclassic/specs.html)

Look in the menus under AUTO

Have at it! :P

---

### Post by bluekarasu on 2010-10-23
try Handbrake, easier than avidemux, faster, and the built-in profile are better.

---

### Post by Oscareightyone on 2010-10-23
Stupid me! I hadn't seen the auto menu! I had one other problem though...Sorry scratch that! all sorted!:biggrin:

---

### Post by Oscareightyone on 2010-10-24
Okay...I put the video on the ipod with gtkpod...I get sound but no video! HEEELLLLLP!

---

### Post by Oscareightyone on 2010-10-24
Handbrake didn't work. It's not GNOME compatible.

---

### Post by coffee412 on 2010-10-24
> **Oscareightyone said:**
> Okay...I put the video on the ipod with gtkpod...I get sound but no video! HEEELLLLLP!

Not a problem. If you have an existing video on the ipod that does play then download it off the ipod and load it in avidemux. There is a button in the top menus that gives you information on the video. Get the resolution and what codec its using (video and sound). Now load up your video and change it to match those.

Actually, Its only video your having a problem with so you just need the video info. Leave the sound setting at "copy". 

of course, If you dont have a video on it then get one that is known to work. 

There is nothing more frustrating than apple products on linux. Every darn ipod is different and some are just basically not supported. I hate them. But thats just me.
:)

---

### Post by Sin_fe on 2010-10-25
> Handbrake didn't work. It's not GNOME compatible.
Last edited by Oscareightyone; 8 Hours Ago at 03:27 AM.. 

Try with nightly builds

[http://forum.handbrake.fr/viewtopic.php?f=6&t=15901](http://forum.handbrake.fr/viewtopic.php?f=6&t=15901)

---

### Post by JohnAStebbins on 2010-10-25
> **Sin_fe said:**
> Try with nightly builds

[http://forum.handbrake.fr/viewtopic.php?f=6&t=15901](http://forum.handbrake.fr/viewtopic.php?f=6&t=15901)

... which will ultimately lead you here
[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

```

sudo add-apt-repository ppa:stebbins/handbrake-snapshots
sudo apt-get update
sudo apt-get install handbrake-gtk

```

---

