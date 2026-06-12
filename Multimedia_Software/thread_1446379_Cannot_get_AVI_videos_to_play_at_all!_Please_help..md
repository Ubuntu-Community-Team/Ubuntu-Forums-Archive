---
title: "Cannot get AVI videos to play at all! Please help..."
date: 2010-04-04
forum: Multimedia Software
---

### Post by veryannoyed on 2010-04-04
I cannot get AVI videos to play with the Totem movie player that comes bundled with Ubuntu 8.04 on the Dell Mini 9. I keep getting: "Could not determine type of stream." Randomly, one or two of the dozen or so videos on my SD card will work, but most will not. This is very frustrating because all the videos I download are always in AVI format. 

I tried used the synaptic package manager find an alternative player and tried MPlayer, but that didn't do anything. I'd just get a blank screen on everything. Using the tutorial in this forum, I got GNOME Mplayer, which also didn't work, but even a video that worked with Totem would only play audio with GNOME Mplayer. 

I looked in the repository for video codec updates but didn't see any. What do I do? Is there like a Winamp for Linux? This is a total bummer. I just want to play AVI files that are so commonly used for video.

:(

---

### Post by kblft on 2010-04-04
Make sure you have third party software enabled in Software Sources

And then try to install ubuntu restricted extras

Open terminal ( Applications -> Accessories -> Terminal ) and type :

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by veryannoyed on 2010-04-04
OK, I did both. What's supposed to happen? .AVIs aren't magically playing now. :???:

---

### Post by adam814 on 2010-04-04
As players go I'm partial to VLC.  Just a matter of personal preference though.

I'm guessing you're missing a codec somewhere.  Try this:
```
file /path/to/broken/avi/file
file /path/to/working/avi/file
``` Substitute the correct paths of course.

I'm guessing the video and/or audio codecs it lists won't match and that should give you a hint as to what you need to install to make it work.

If all else fails there's always adding the Medibuntu repository.  Their libraries ship with support for more formats.

---

### Post by veryannoyed on 2010-04-04
Well, I am an inexperienced Ubuntu user so...

I didn't really know what to do with the code you suggested. I typed: "file media/MCARD/The Office [405] Local Ad.avi" in the terminal and it didn't understand it. I'm not sure how I'm supposed to see the codecs. When I  right click on the file to its file properties, I can only see the codecs of the files I can play with Totem.

I  believe I just installed the Medibuntu repository using the sticky thread above, but I have no idea how to open it up and start using it. I don't see a shortcut anywhere. Sorry I'm so newbie.

---

### Post by kblft on 2010-04-04
The files are suppose to play if you installed all the codecs - are you still unable to play the files using the movie player?

If not - have you tried another player - vlc for instance
open terminal and type
```
sudo apt-get install vlc
```

---

### Post by adam814 on 2010-04-04
It didn't understand the file name because there were spaces in it.  To get the shell to interpret it properly you have to enclose that part in quotes like this:
```
file media/MCARD/"The Office [405] Local Ad.avi"
```

But if you've installed the Medibuntu repository correctly it should update your codecs on the next upgrade:
```
sudo apt-get update && sudo apt-get upgrade
```That will get them if you don't have them already.

---

