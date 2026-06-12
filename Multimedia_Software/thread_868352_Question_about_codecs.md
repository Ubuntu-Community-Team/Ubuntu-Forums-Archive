---
title: "Question about codecs"
date: 2008-07-23
forum: Multimedia Software
---

### Post by Moonfrost on 2008-07-23
Do codecs come pre-installed now? I transferred my music from a backup disc and then watched some videos and everything worked out of the box! I'm using Ubuntu Hardy Heron 8.04.1 64bit version and all the .mp3 and .ogg files play perfectly on Amarok, I tried some .mpg files and they all work too...just a question out of curiosity.

---

### Post by cozmicharlie on 2008-07-23
No - you have to install them.  Many of the codecs have licenses so they can't come pre-installed.  It's not hard though.  Follow the instructions here [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683).  It looks like more complicated than it really is.  The basic steps are:

Enable the medibuntu repository
Install the codecs.
Install the players

It is all explained on the thread.  Post back though if you have any problems or don't understand something.

Enjoy

---

### Post by rockstarrem on 2008-07-23
An easier way to install the codecs you need would to add the media you want to Rhythmbox and Rhythmbox will detect you need to codecs and will open a Synaptic and ask you to install them (this can include mp3, wav, mov, etc).

---

### Post by Moonfrost on 2008-07-23
Seems none of you understand my question, what I said is I tried all my media files and they worked without asking me for codecs!! I know I usually have to install them but so far I tried different media files and they all work, I don't know why.

---

### Post by overdrank on 2008-07-23
> **Moonfrost said:**
> Seems none of you understand my question, what I said is I tried all my media files and they worked without asking me for codecs!! I know I usually have to install them but so far I tried different media files and they all work, I don't know why.

If this is a fresh install of Hardy 64bit  did you have a existing home partition?

---

### Post by Moonfrost on 2008-07-23
> **overdrank said:**
> If this is a fresh install of Hardy 64bit  did you have a existing home partition?

No, but I forgot to mention I installed Amarok with Xine engine and usually it requires a bunch of other stuff so I installed everything, didn't check if any of those were codecs. The thing is all the audio and video files I have tried so far work. Yes, this is a fresh install of Hardy Heron and no  I didn't have a previous home partition since I haven't used Linux in around 4 months and I was using Windows only, I formatted the hard drive (backed up my stuff of course) and then I did a fresh install of it.

---

### Post by cozmicharlie on 2008-07-24
> **Moonfrost said:**
> No, but I forgot to mention I installed Amarok with Xine engine and usually it requires a bunch of other stuff so I installed everything, didn't check if any of those were codecs. The thing is all the audio and video files I have tried so far work. Yes, this is a fresh install of Hardy Heron and no  I didn't have a previous home partition since I haven't used Linux in around 4 months and I was using Windows only, I formatted the hard drive (backed up my stuff of course) and then I did a fresh install of it.


During the process of installing everything you must have installed the libxine packages.  These contain plug ins that have the codecs for xine.  You can check in Synaptic to see which are installed.

---

### Post by Carl H on 2008-07-24
I did a fresh install of Hardy recently, and upon (accidentally!) double clicking on an mp3 file, I was presented with a pop-up dialogue informing me that I needed to install some extra codecs and did I want to do that now. I clicked 'Yes', and it just did everything for me.

---

