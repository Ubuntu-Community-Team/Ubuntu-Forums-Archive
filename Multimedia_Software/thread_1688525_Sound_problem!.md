---
title: "Sound problem!"
date: 2011-02-15
forum: Multimedia Software
---

### Post by zeelandia on 2011-02-15
Greetings.

Pardon my ignorance, but I am having problems with my sound.

When I first installed Ubuntu (10.10 Maverick Meerkat), I had a problem with a crackling / distortion / machine-gun-like sound. I am running a really old audio card (CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator]) by Santa Cruz Turtle I believe from Dell.

I found this site here ( [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/428619](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/428619) ) that offered a solution by changing the [default.pa]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/428619/+attachment/1778178/+files/default.pa")          and [daemon.conf]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/428619/+attachment/1778177/+files/daemon.conf")         which I did so. Nothing was fixed. I tried stopping some pulse driver test ( instructions I can no longer find) and it did not run. Later, something seemed to have crashed and my sound was miraculously fixed. However, I could adjust the sound within the program, I could not adjust the sound through the top tab of the Ubuntu main window.

Currently, my situation is worst. The sound no longer works. Exception is that sound works whenhen I boot up my computer, I hear the Ubuntu theme sound (sounds African drums) and when I watch Youtube (Flash based) videos and media. However, when I open a MP3 or video, I hear nothing what so ever.

Anyone have a genius fix?

---

### Post by tommcd on 2011-02-15
> **zeelandia said:**
>  The sound no longer works. Exception is that sound works when I boot up my computer, I hear the Ubuntu theme sound (sounds African drums) and when I watch Youtube (Flash based) videos and media. However, when I open a MP3 or video, I hear nothing what so ever.

The fact that you have sound in flash videos and when Ubuntu boots up indicates that your sound card is working.

For mp3 files and other media, have you installed the multimedia codecs that are required to play patent protected media?
Try opening any media that has no sound in Totem (which is Movie Player in the: applications > sound and video menu). If there are codecs missing, then Totem will prompt you to install them.
You could just install the *ubuntu-restricted-extras* package, which installs every restricted codec, plus a lot of other stuff that I would never need or want. I prefer to only install what I need though. Using Totem to find the codecs you need is easy; and it only installs what I need.
Hope this helps.
And welcome to the Ubuntu forums!

---

### Post by zeelandia on 2011-02-16
Thanks for the tips.

I was actually able to play MP3s prior to trying to fix the distortion. When I open the files in Movie Player, they seem to play but no sound comes out. It's as if the volume has been reduced to 0 when MP3s are played. In Movie Player, when I click on the sound icon to adjust the sound, nothing happens. It's as if it is a dead icon. Before I messed around with it, it was working just fine.

Is there a way to reinstall the sound software? If so, how do I go about doing it?

---

### Post by tommcd on 2011-02-16
> **zeelandia said:**
> Before I messed around with it, it was working just fine.

What exactly did you do when you "messed around with it"? Please post the specific things you did.
If you undo what you have done you should get your sound working again.
In the future, before you "mess around with things", make sure you have an exit strategy to undo what you have done in case it does not work.

---

