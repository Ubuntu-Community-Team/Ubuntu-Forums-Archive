---
title: "complete noob, how do i get my sound to work? =("
date: 2010-10-31
forum: Multimedia Software
---

### Post by skatergirl on 2010-10-31
warning: Noob


This is the second time im giving Ubuntu a try. (first time didnt go so well lol)

Anyway i just installed it.

how do i get the sound to work?

what are the first thing to do?

---

### Post by gordintoronto on 2010-10-31
Welcome, Skater.

If you're trying to play MP3s, you probably need to run System/Administration/Synaptic Package Manager, click on Settings/repositories and make sure the "multiverse" is enabled, click on Close to exit that. You might have to click on reload.

Now select "Ubuntu Restricted Extras" Click on Install, then Apply.

For all sounds, the first thing to check is that sound is not muted, which happens frequently. Click on the speaker icon, near the right on the upper panel. Select "Sound preferences." What you see then depends on your hardware and what version of Ubuntu you are using.

If that's no help, you can try this: Open a Terminal (Program -> Accessories -> Terminal), then enter this command:

ubuntu-bug audio

If you try Google you'll find a confusing array of suggestions, most of them obsolete. Perhaps the best is at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) 
but be prepared to spend a little time reading.

---

### Post by 73ckn797 on 2010-10-31
If it just sound you need, click on the speaker icon at top panel and adjust the level up.

[gordintoronto]("http://ubuntuforums.org/member.php?u=507940")'s recommendations will also be needed such as ubuntu-restricted-extras.

Go here and there are other sound & video codecs you will likely need:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Follow the instructions related to your installation, 32 or 64. Or you can go to Applications/Accessories/Terminal and enter for a 32 bit Ubuntu:

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```Then:
```
sudo apt-get install libdvdcss
```And lastly:
```
sudo apt-get install w32codecs
```These will mostly be for video codecs.

---

### Post by skatergirl on 2010-11-02
Thanks guys!

Sound works now!


Working on fixing the other media stuff! :)

---

