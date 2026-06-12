---
title: "Sound issues.... well kind of??"
date: 2008-04-28
forum: Multimedia Software
---

### Post by msjones on 2008-04-28
Hi,

I have a fresh install of hardy running on my HP6710b Laptop. My sound is working fine, for single applications.

For example if I have been watching a video on youtube and then load up rythmbox I will not be able to listen to any music in my play list until I close down both applications and reload them. After this music plays fine, but if I want to pause a song to watch another video online, or even a video file in VLC I have to close applications down again and reopen them to get sound from the file I want to view.

Is there anyway to sort this problem?

Thanks

---

### Post by fatihsanli58 on 2008-04-28
same here. fresh hardy installation. I reproduced the problem. it is exactly as you mention. not solved yet. I keep searching.

---

### Post by fatihsanli58 on 2008-04-28
hi there I found the solution on launchpad(if you are already did not find it). Here are the steps you should follow:
1. sudo apt-get install --reinstall pulseaudio 
2. sudo apt-get install libflashsupport
3.change everything to pulseaudio in "system->preferences->audio settings".
that is it. it works for me. i hope it works for you too.

---

### Post by elfgoh on 2008-04-28
> **fatihsanli58 said:**
> hi there I found the solution on launchpad(if you are already did not find it). Here are the steps you should follow:
1. sudo apt-get install --reinstall pulseaudio 
2. sudo apt-get install libflashsupport
3.change everything to pulseaudio in "system->preferences->audio settings".
that is it. it works for me. i hope it works for you too.

I have a fresh upgrade frm Gutsy. Think step 2 is the fixer. Fyi, for step 3, i change all to autodetect or alsa. Still works.

Cheers

---

### Post by msjones on 2008-04-29
Excellent, all is working OK now.... thanks alot guys!

---

### Post by eamonireland on 2008-04-29
I tried this and now have no sound at all - nothing

---

### Post by msjones on 2008-04-29
Have you done the pulseaudio reinstall?

Do as above again, set all selection in sound preferences to autodetect and then reboot.

I had no sound before I rebooted.

Let us know

---

### Post by eamonireland on 2008-04-29
[This thread]("http://ubuntuforums.org/showthread.php?t=616845") worked for me in sorting out my sound problems. It seems a bit complex, but basically you need to find out your sound card model and then use it to identify the command you need to add to alsa-base.

For me, I needed to 

sudo gedit **/etc/modprobe.d/alsa-base**

and add the following line

options snd-hda-intel model=dell-3stack

And the world is perfect again!

---

### Post by ryth on 2008-04-29
> **fatihsanli58 said:**
> hi there I found the solution on launchpad(if you are already did not find it). Here are the steps you should follow:
1. sudo apt-get install --reinstall pulseaudio 
2. sudo apt-get install libflashsupport
3.change everything to pulseaudio in "system->preferences->audio settings".
that is it. it works for me. i hope it works for you too.

This worked perfectly for me.  I was having the issue that only one application at a time was able to access the sound card.  Upon re-installing pulse and switching all my settings from Alsa to Pulse it works great.

---

### Post by yonasz on 2008-07-13
> **fatihsanli58 said:**
> hi there I found the solution on launchpad(if you are already did not find it). Here are the steps you should follow:
1. sudo apt-get install --reinstall pulseaudio 
2. sudo apt-get install libflashsupport
3.change everything to pulseaudio in "system->preferences->audio settings".
that is it. it works for me. i hope it works for you too.
This worked perfect for me. 
Tnx

---

