---
title: "Realtek ALC880 9.04 audio artifacts"
date: 2009-04-28
forum: Multimedia Software
---

### Post by creess1 on 2009-04-28
This is on a fresh install of 9.04.  This is the first time i've ever used anything other than windows operating systems.  I'm a network engineer and have been building PC's for over 10 years.  So i know about hardware and microsoft operating systems, but know very little about linux. 

So I'm listening to a live stream from [http://www.mix961.com/cc-common/ondemand/player.html?world=st](http://www.mix961.com/cc-common/ondemand/player.html?world=st)

Took me about an hour before i figured out the to install "gstreamer0.10-plugins-bad" to get it to work.  I also tried VLC before that, but got the same artefacts in the audio playback, so i figured it wasn't the installed app and something wrong with the drivers on the OS.

Now the sound stream "works", but i get these hiss sounds when people talk etc.  like everyone has a lisp or something.  very annoying.

My motherboard is an MSI 915GM Speedster which uses the Intel 915GM northbridge with ICH6 southbridge: [http://us.msi.com/product/p_spec.asp?model=915GM_Speedster-FA4R](http://us.msi.com/product/p_spec.asp?model=915GM_Speedster-FA4R)

It says the onboard audio codec is "Realtek ALC880"  I tried looking for drivers on the website, but their all for windows OS's only.

Anyone have any suggestions?  Also note, i will be attempting to get ventrillo and world of warcraft working together today.  I've heard there is sometimes issues with getting multple sound sorces all working at the same time so i thought i'd mention that i would like this audio stream from this website, and wow and vent to all work simultaniously.

---

### Post by creess1 on 2009-04-28
woah second page already, and its only 10am.  

Any ideas from anyone to fix this?  i tried going into the audio properties and changing the playback to OSS or ALSA or Pulsaudio but they all do the same thing.  unless maybe i need to reboot the computer for changes to take effect, didnt try that. 

Any idea's?

---

### Post by bass0 on 2009-05-16
Bump.

Same problem, I think. The test tone for all the different sound servers is hissy, plus I get this error for one of the servers (ALSA analog):

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

Macbook 2,1 running a fresh install of Jaunty.

---

