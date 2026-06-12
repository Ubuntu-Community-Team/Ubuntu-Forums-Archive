---
title: "Eternal sound problems"
date: 2007-01-14
forum: Multimedia &amp; Video
---

### Post by juan_kerr on 2007-01-14
Hello,

Here's my situation. I, like many others have recently decided to switch to Linux. I have spent the best part of the last 6 weeks installing, reinstalling, messing stuff up and then fixing it. I have been switching between Ubuntu and Kubuntu, 32 and 64 bit versions. 

I am currently on Kubuntu 64 bit version and I am trying to get sound out of my onboard Nvidia CK804 (Realtek 850) equipment, via optical SPIDIF to my AV reciever. When I first installed it I had no sound. However this was quickly remedied using tweaks found after hours of trawling the net for the same problem in 32 bit Ubuntu. 

Turns out all I needed to do was to ensure AC97 playback was set to zero volume and ensure that IEC958 playback and capture switches were activated in ALSA mixer. 

Under Ubuntu 32 bit this worked and gave me ONLY stereo output over optical i.e. stereo PCM. I could never get AC3 to work for some reason. All codecs were in. This must have been a system issue as I went through practically all media players and they were all the same, even retail DVDs. This was the final problem I needed solved.

So then I buggered something up and ended up deciding to go back to Kubuntu 64 bit version (the 32 bit won't install for some reason). I did the same as I did under Ubuntu and I had sound, stero PCM. However, I then installed codecs and media players using Automatix and since then I have no sound at all. I have tried checking and double checking  setting under    ALSA, tried uninstalling ALSA and reinstalling and none of these worked. 

I have tried numerous changes to .asoundrc and had no success. As a final attempt I decided to download the Realtek audio driver for Linux and ran this. This has no buggered up my sound system as I get an error in my my sound settings in the system settings:

libasound.so.2: cannot open shared object file: No such file or directory

I have no idea how to fix this. 

So then I decided that I would try the AC'97 driver from the Asus (my MB) website for Linux. I have downloaded this and I have no idea what to do with it. I haven't compiled anything yet.  The readme says:

For driver installation, please follow below steps. 

Step 1. unzip source code
        tar xfvj alcsound.tar.bz2

Step 2. Turn on sound support (soundcore module, default turn on)

Step 3. Complied source code
	a. ./configure
	b. make
	c. make install
	d. ./snddevices

Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
 	(Please refer to the attached modules.conf)

Step 5. reboot your machine


Tried this and I don't really know what it did, if anything. I'm still without sound and my sound settings are still missing in the system manager, same error as above. 



I have gone through the comprehensive sound solutions part of this forum and tried a few things, but still nothing. 

I am really impressed my both versions of Ubuntu and I'm really starting to get the hang of it now, but this is really starting to wear me down. All I want is sound and then preferably full AC3 so I can watch AC3 encoded files and DVDs.

Can anyone help me at all?  Please. 

Sorry for the length of this.

---

