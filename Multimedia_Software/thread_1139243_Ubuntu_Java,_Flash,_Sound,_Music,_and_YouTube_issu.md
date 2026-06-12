---
title: "Ubuntu Java, Flash, Sound, Music, and YouTube issues."
date: 2009-04-26
forum: Multimedia Software
---

### Post by Paulgarner on 2009-04-26
I am using the newest version of Ubuntu (I think it is 9.0.4). I just switched from windows. I play Runescape to blow time. Runescape uses Sun Java to run. You can see Runescape at [www.Runescape.com]("http://www.Runescape.com"). There is a standard detail (bad detail), and HD version of Runescape. I can run SD with some glitches, but it works. But if I rune HD, all I get is a white screen. I have been working on this for days trying various things I have read in other's threads. Also, I cannot play music or get audio from anything BUT Runescape (in SD mode). So no music or videos. I can see Youtube videos, but I cannot hear them. Music is completely impossible using Rythembox Music Player. I have tried most of the common fixes and the closest I have come is where I rebooted and I got sound for about 30 minutes, with glitchy video and sound (it would crack or warp the audio/video), but eventually it stopped working again. I am at desparation now!

---

### Post by Paulgarner on 2009-04-26
Please help me!

---

### Post by acimmarusti on 2009-04-26
Open up a terminal and then type:

```

sudo apt-get install ubuntu-restricted-extras

```

This should give you java, flash and a bunch of codecs for mp3, video and dvd playback. Therefore this should solve all your problems

---

### Post by Paulgarner on 2009-04-26
I already have tried that! No go! Any other ideas?

---

### Post by acimmarusti on 2009-04-26
what do you mean no go?

did the command fail to get the packages from the repository? 

were you able to install the packages, yet it still doesn't work?

you could try getting the packages manually using synaptic. Search for flashplayer-plugin, sun-java6, gstreamer mp3 plugin to name but a few.

---

### Post by Paulgarner on 2009-04-26
I already had it fully updated. When I used the command it was already there.

---

### Post by Paulgarner on 2009-04-27
Bump

---

### Post by unf on 2009-04-27
[http://ubuntuforums.org/showthread.php?p=7157485](http://ubuntuforums.org/showthread.php?p=7157485) 

same?

---

### Post by Paulgarner on 2009-04-27
Similar, but I don't get sound.

---

### Post by waj1122 on 2009-04-27
> **acimmarusti said:**
> Open up a terminal and then type:

```

sudo apt-get install ubuntu-restricted-extras

```

This should give you java, flash and a bunch of codecs for mp3, video and dvd playback. Therefore this should solve all your problems

Thank you very much for this, it worked for me. What I don't understand is that everything worked in 8.10 out of the box but not in 9.04 as far as the sound goes for me. Personally, I think they took 1 step forward and 2 steps back with this release. There are things that I like but there are also a lot of things I don't (trouble with sound just being one of them).

Bill

---

### Post by unf on 2009-04-27
> **Paulgarner said:**
> Similar, but I don't get sound.

Did you read the hole thing. I dont get sound ether sometimes.

---

### Post by Paulgarner on 2009-04-27
I mean, I get visual, yet no sound. Anyways. Do you recommend I down-grade from 9.0.4 a step?

---

### Post by psyke83 on 2009-04-27
Install the package "pavucontrol". When it's installed, open the PulseAudio Volume Control application.

Now, try to play sound in an application. Basically, if the application shows up on the list and plays sound, it's working fine. Any other possibility indicates that PulseAudio isn't working properly, or the application that doesn't use PulseAudio will block PulseAudio (and hence other applications that are trying to output audio via PulseAudio).

For a more in-depth guide, see: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by hcuriel on 2009-04-29
I saw what could be your solution, linked within the April 27 post in [http://businerdss.blogspot.com/](http://businerdss.blogspot.com/)

Regards,

---

### Post by kozjegyzo on 2009-04-29
> **hcuriel said:**
> I saw what could be your solution, linked within the April 27 post in [http://businerdss.blogspot.com/](http://businerdss.blogspot.com/)

Regards,


Yep the above mentioned dose work!
Here is the direct link:
[http://bugfixbug.wordpress.com/2009/04/25/ubuntu-flash-does-not-work/](http://bugfixbug.wordpress.com/2009/04/25/ubuntu-flash-does-not-work/)
Do the steps and you are on your way to sound and video.
The Adobe direct download worked for me after getting rid of the unwanted packages.
Although I still don't get any sound out of meebo ([www.meebo.com](www.meebo.com)), and that uses flash as well. If anybody has a solution please share.

Peace

---

### Post by BugFixBug on 2009-04-30
> **kozjegyzo said:**
> Yep the above mentioned dose work!
Here is the direct link:
[http://bugfixbug.wordpress.com/2009/04/25/ubuntu-flash-does-not-work/](http://bugfixbug.wordpress.com/2009/04/25/ubuntu-flash-does-not-work/)
Do the steps and you are on your way to sound and video.
The Adobe direct download worked for me after getting rid of the unwanted packages.
Although I still don't get any sound out of meebo ([www.meebo.com](www.meebo.com)), and that uses flash as well. If anybody has a solution please share.

Peace

do you have this package:
flashplugin-nonfree-extrasound

dont know if it will help you

---

### Post by kozjegyzo on 2009-04-30
> **BugFixBug said:**
> do you have this package:
flashplugin-nonfree-extrasound

dont know if it will help you

Awesome it works :D
THX Bugfix!

---

### Post by Benjabba on 2009-05-07
I am running 9.04, Dell inspiron 1545 with the ATI video card option.  fresh install.  I  ran in  terminal
 
 sudo apt-get install ubuntu-restricted-extras  

Which went well, all done no errors.  I have sound, everything works, so far.

  When I go to system/administration/hardware drivers I can activate my "ATI/AMD proprietary FGLRX graphics driver.  I have done so and can see no difference either way.

  The interesting thing with runescape is that I also get a partial whitescreen both ways when I try to run it which also freezes the program.  It seems to be the part of the screen that has an adblock tab, but I took the adblock off runescape.

  So I have two questions, why does my ATI card not do anything?

  What is going on to lock out runescape specifically and freeze the program?

---

### Post by replambe on 2009-06-06
> **acimmarusti said:**
> Open up a terminal and then type:

```

sudo apt-get install ubuntu-restricted-extras

```This should give you java, flash and a bunch of codecs for mp3, video and dvd playback. Therefore this should solve all your problems


I uninstalled all flash and then installed the restricted extras and it worked great. :)

---

### Post by cwrb on 2009-06-07
> **acimmarusti said:**
> Open up a terminal and then type:

```

sudo apt-get install ubuntu-restricted-extras

```

This should give you java, flash and a bunch of codecs for mp3, video and dvd playback. Therefore this should solve all your problems
I triied it on my newly installed 9.04 Jaunty Jackalope and got "couldn't find package ubuntu-restricted-extras".
what next?

---

### Post by Kanibal234 on 2009-07-05
I am having the same problem.

But none of this helps.

Help please !!

Thank you.

<b>NOTE:</b>
I cannot hear anything even on system. ( with default configuration )
I can hear music on Totem player. ( if i change sound to PnP OSS )

i have attached a screenshot of audio config.

---

### Post by Kanibal234 on 2009-07-06
someone help?

---

