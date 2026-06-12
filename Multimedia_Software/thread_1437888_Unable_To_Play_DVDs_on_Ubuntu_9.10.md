---
title: "Unable To Play DVDs on Ubuntu 9.10"
date: 2010-03-24
forum: Multimedia Software
---

### Post by hodgie2005 on 2010-03-24
Every time I insert a video DVD in my DVD drive in Ubuntu 9.10 the CD/DVD Drive in the File Browser disappears. Any ideas as to why this may be happening? Thanks so much in advance!

P.S. I am able to view files on a DVD that is not a video DVD when I insert it.

---

### Post by coolcaseley67 on 2010-03-24
Hi

-make sure you are up to date 

- It's like you have no  preferred app too play DVDs .

- to set a preferred app  go to System , preferences , preferred  applications 

- Have you install codecs or a media player that can play DVDs ?

- if not install vlc player see [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html) 



hope it helps

---

### Post by 2hot6ft2 on 2010-03-24
Like already mentioned you need to define a player, my choice is VLC Player.
You need the codecs to decode the dvd and since the next question you'll have is how to play web videos like youtube.... let's just cut to the end and install it all at once so you can play pretty much everything. What do you think?

I could spend a half hour saying go here click this open that  yada yada yada instead do this.

Open a terminal
Applications > Accessories > Terminal
and run these one at a time and your password wont be shown when you type it in just type it in and hit enter.
This first one enables the medibuntu repository for restricted codecs and such
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then for all the multimedia, mp3's java, divx web player, flash and dvd playback
```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 gecko-mediaplayer vlc
```

And you're done.
VLC Player will be in Applications > Sound and Video > VLC

The forum search works if you use it. This question is asked just about every day.

---

