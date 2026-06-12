---
title: "Solution for DVD Playback/Gutsy or Hardy"
date: 2008-05-03
forum: Multimedia Software
---

### Post by Jammerdelray on 2008-05-03
So your getting No Video or Audio or when you do it is choppy, here is the fix taken from: [http://lifehacker.com/350015/enable-dvd-playback-in-ubuntu-in-two-commands]("http://lifehacker.com/350015/enable-dvd-playback-in-ubuntu-in-two-commands")

Step 1- Install VLC Media Player in Synaptic Package Manager.

Step 2- In Terminal do the following and press enter after each.

#sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3 

#sudo /usr/share/doc/libdvdread3/install-css.sh

Also install gstreamer plugin through Synaptic.

Now restart and now you should have decent dvd playback.



Enjoy

---

### Post by vishzilla on 2008-05-03
I prefer medibuntu repo + vlc to play DVDs

---

### Post by sourcerer24 on 2008-05-09
> **Jammerdelray said:**
> So your getting No Video or Audio or when you do it is choppy, here is the fix taken from: [http://lifehacker.com/350015/enable-dvd-playback-in-ubuntu-in-two-commands]("http://lifehacker.com/350015/enable-dvd-playback-in-ubuntu-in-two-commands")

Step 1- Install VLC Media Player in Synaptic Package Manager.

Step 2- In Terminal do the following and press enter after each.

#sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3 

#sudo /usr/share/doc/libdvdread3/install-css.sh

Also install gstreamer plugin through Synaptic.

Now restart and now you should have decent dvd playback.



Enjoy

I tried to do this and I still cant play dvds on Hardy. I get "could not read form resource" error on totem. VLC just doesn't do anything. Am I missing something?

---

### Post by ahildoer on 2008-07-21
> **sourcerer24 said:**
> I tried to do this and I still cant play dvds on Hardy. I get "could not read form resource" error on totem. VLC just doesn't do anything. Am I missing something?

Here is the complete solution documented on my site: [http://www.hildoersystems.com/index.php/home/62]("http://www.hildoersystems.com/index.php/home/62")

---

### Post by merlyn on 2008-07-22
Hi all,

I experienced no problems with DVD playback under Gutsy, as all the packages mentioned here had been installed on my system.

Unfortunately since upgrading to Hardy, I can no longer hear the vocal track when playing DVD's.

I suspect that this has something to do with Pulse Audio.

Any suggestions would be most welcome.

Cheers.

---

