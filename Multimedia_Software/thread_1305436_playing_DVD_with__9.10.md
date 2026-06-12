---
title: "playing DVD with  9.10"
date: 2009-10-29
forum: Multimedia Software
---

### Post by numbness05 on 2009-10-29
Hi guys

I have just done a fresh install of Karmic 9.10 and have everything runnig smoothly after having installed the restricted extras package.
How ever I do have 1 issue remaining and thats that I can not seem to play a DVD. I have tried totem and VLC.
Normally speaking after having installed the restricted extras DVD should play right?? it certainly has in the past some one suggested sudo /usr/share/doc/libdvdread4/install-css.sh in terminal but this doesnt seem to work either.

Any ideas anyone please

Thanks!

---

### Post by alextor98682 on 2009-10-31
> **numbness05 said:**
> Hi guys

I have just done a fresh install of Karmic 9.10 and have everything runnig smoothly after having installed the restricted extras package.
How ever I do have 1 issue remaining and thats that I can not seem to play a DVD. I have tried totem and VLC.
Normally speaking after having installed the restricted extras DVD should play right?? it certainly has in the past some one suggested sudo /usr/share/doc/libdvdread4/install-css.sh in terminal but this doesnt seem to work either.

Any ideas anyone please

Thanks!


I ahve the same problem here... CDR mounts fine dvds wont even mount.

---

### Post by evworld on 2009-10-31
I had the same problem and ran this command and I can play DVD's now.
 
 
 
sudo /usr/share/doc/libdvdread4/install-css.sh

---

### Post by coffeecat on 2009-10-31
> **numbness05 said:**
> some one suggested sudo /usr/share/doc/libdvdread4/install-css.sh in terminal but this doesnt seem to work either.

Curious - that used to work. I'm in Jaunty at the moment, but when I'm next in Karmic I'll check to see if the script is still there. When you say it doesn't work, do you get a terminal error message? If so, what does it say?

Anyway, that script installs libdvdcss2 which you need to be able to read encrypted commercial DVDs. If you can't get the script to work, simply go to [http://www.medibuntu.org/](http://www.medibuntu.org/) . Either follow the instructions to add Medibuntu to your repository list and then install libdvdcss2 using Synaptic. Or go to the Packages tab and download the libdvdcss2 package directly. Make sure you get the 32-bit or 64-bit package appropriate to your install. To install, simply put the .deb package on your desktop, double-click on it and follow the prompts.

---

### Post by ssj6akshat on 2009-10-31
sudo /usr/share/doc/libdvdread4/install-css.sh
 its described somewhere, i can't remember where.

---

### Post by coffeecat on 2009-10-31
@**numbness05**, I'm now in Karmic and the /usr/share/doc/libdvdread4/install-css.sh is there, so it should work. What error message did you get when you tried to run it?


> **ssj6akshat said:**
> sudo /usr/share/doc/libdvdread4/install-css.sh
 its described somewhere, i can't remember where.

Check the OP's post again. They've already said this didn't work for them.

---

### Post by Mike'sHardLinux on 2009-10-31
I've had similar problems with Karmic. Sometimes, after I insert a DVD, the DVD will mount after a long time, and then it will play, but not usually. It seems to be a problem mounting the DVD. I have been googling around on this issue. I have run across a known bug or two, with some possible work-arounds, but nothing has fixed the issue, yet. I know it is not my drive, because I can pop in my Jaunty drive or a windows drive and DVDs play fine. I am still researching.....

---

### Post by e-nygma on 2009-10-31
You have to install [B]libdvdcss2[B] for DVD playback.

---

### Post by Mike'sHardLinux on 2009-10-31
> **e-nygma said:**
> You have to install [B]libdvdcss2[B] for DVD playback.

Ya, I am pretty sure that is common knowledge by now. That is not the problem in this case. The OP already stated that they did that.

---

### Post by e-nygma on 2009-10-31
Depending on your system, have you tried installing w32codecs or w64codecs?  Also try to install GStreamer fluendo MPEG2 demuxing plugin.  I just performed a clean install of Karmic and everything is working great so far...including DVD playback.  I hope this helps.

---

### Post by imaca on 2009-11-01
Not sure if this is same problem, but, on my system I have to reboot before playing a DVD.
If I put a DVD in *while* I'm logged in Xine tells me I don't have rights to it.
If it's already in the drive *before* I log in, it works fine.

---

