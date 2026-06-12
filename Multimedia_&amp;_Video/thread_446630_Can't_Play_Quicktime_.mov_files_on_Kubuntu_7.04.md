---
title: "Can't Play Quicktime .mov files on Kubuntu 7.04"
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by charlie. on 2007-05-17
I can't play Quicktime .mov files on Kubuntu 7.04. Opening the file loads Kaffeine, which does not throw any errors or anything, but the file won't play - the clicking the play button causes the progress indicator to light up (become enabled) and then become disabled again, as if the file was valid but had zero length.

I'm running a stock-standard Kubuntu 7.04 installation.

Any ideas?

---

### Post by charlie. on 2007-05-17
It seems to work in VLC... strange.

---

### Post by charlie. on 2007-05-21
Only some files work. Others have sound, but only show the first video frame. Some spawn several VLC windows - most containing solid white and one containing the actual video.

The ones that work are cool. The ones that spawn child windows are usable, but odd. The ones that only have sound are useless.

Any ideas?

---

### Post by 6StringKng on 2007-05-21
install VLC Media Player, works for me...

---

### Post by charlie. on 2007-05-22
Duh. That's why I said it worked in VLC.

Unfortunately, not all of the files work - only some.

Currently, I'm experimenting with ffmpeg2theora to try to convert the mov's to ogg's. If I can get the quality right, this solution may just work.

I'd still appreciate a solution that did not require format conversion, however.

---

### Post by RomeReactor on 2007-05-22
Hi. Probably your problem comes from not having the required codecs; to install them from Konsole:
```
sudo apt-get install libxine1-ffmpeg libxine-extracodecs
```
or look for those codecs through Adept.

---

### Post by charlie. on 2007-05-22
Thanks, but it did not work. I'm not surprised because libxine1-ffmpeg was already installed and libxine-extracodecs is a "transitional package to ensure clean upgrades". Neither packages actually added anything.

Back to the drawing board...

---

### Post by RomeReactor on 2007-05-22
Try adding the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories (if you don't have them yet) and installing the **w32codecs**.

---

### Post by charlie. on 2007-05-22
Thanks for the suggestion. I did not know about Medibuntu - which is quite cool!
(It's about time something like Medibuntu happened - a pity about the 403 errors, though.)

Sadly, installing w32codecs did not help despite the coolness of Medibuntu.

---

### Post by RomeReactor on 2007-05-22
It's been a while since I used Kaffeine, but I believe there's an option to select which backend to use (or was that Kmplayer?); if there *is* such an option, make sure you're using Xine. Sorry if I'm mistaken.

---

### Post by vange on 2008-06-26
This is still an issue on Kubuntu 8.04 64-bit. Most movies from railscasts.com doesn't work, mainly the title screen is showing, and the sound is fine.

Did you solve your problems?

---

### Post by jacoblyles on 2008-06-26
> **vange said:**
> This is still an issue on Kubuntu 8.04 64-bit. Most movies from railscasts.com doesn't work, mainly the title screen is showing, and the sound is fine.

Did you solve your problems?

Hi, I also cannot get railscasts to work in Ubuntu 8.04 64-bit. Have you solved your problem yet? 

Thanks.

---

### Post by vange on 2008-06-30
I just watch the "alternative download for iPod & Apple TV", that is the m4v-files.

---

