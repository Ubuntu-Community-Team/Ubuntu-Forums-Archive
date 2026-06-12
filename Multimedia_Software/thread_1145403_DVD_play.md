---
title: "DVD play"
date: 2009-05-01
forum: Multimedia Software
---

### Post by Silvercloaks on 2009-05-01
Hi!

   So I'm really new to Linux and Ubuntu, I've dabbled a bit in the past but this is the first time I've built a system entirely based on linux.

  Anyways, I've made a TV DVR machine to stream TV and stuff, all that's been fine and good.  I'm using VLC, and have tried a few other players, but VLC seems to be the best at handling subtitles and video for me.

   My only issue has been that I CANNOT get any of my retail DVDs to play in linux.  I've attempted to install LibDvd but that hasn't gotten far.  I'm not all that great at understanding how to install packages manually unless the instructions are crystal clear.  And so far, no matter what I do - I can't get libdvd to install...

   Anyone else out there able to help me?  It would be great to get DVDs play with closed captioning support on my linux box.

:popcorn:

Silvercloak

---

### Post by logos34 on 2009-05-01
follow this:

[https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs](https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs)

---

### Post by Silvercloaks on 2009-05-01
> **logos34 said:**
> follow this:

[https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs](https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs)

THANK YOU!!! That's awesome, I'll check it out when I get home.

Incidentally, I did this last weekend;

 ./configure --host=i586-mingw32msvc --target=i586-mingw32msvc \
  --build=i386-linux

straight from the install text file and it didn't work... I just kept getting errors.  I totally don't understand how this works.  Was I supposed to unzip the libdvdcss file somewhere else?  I just made a directory in my home directory and worked inside there, but nothing worked.  I finally just gave up.

Silvercloak

---

### Post by logos34 on 2009-05-01
could be any number of things...most likely you're missing some development libs, maybe  build-essential was all you needed, dunno.  never tried compiling libdvdcss frm source, personally

normally you do something like

tar xzvf source-1.x.x.tar.gz

cd source-1.x.x

.configure
make
sudo make install

---

### Post by Silvercloaks on 2009-05-01
> **logos34 said:**
> could be any number of things...most likely you're missing some development libs, maybe  build-essential was all you needed, dunno.  never tried compiling libdvdcss frm source, personally

normally you do something like

tar xzvf source-1.x.x.tar.gz

cd source-1.x.x

.configure
make
sudo make install


Thank you thank you thank you, your link to that webpage was JUST what I needed.  One last challenge regarding DVD's now... Does anyone know how to get Closed Captioning running?  I'm trying VLC, Mplayer, Movie Player and gxine and none of them do the job.  Unless I'm looking in the wrong place.

Help?

Silvercloaks

---

