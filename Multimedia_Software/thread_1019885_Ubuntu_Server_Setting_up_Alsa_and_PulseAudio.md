---
title: "Ubuntu Server: Setting up Alsa and PulseAudio"
date: 2008-12-23
forum: Multimedia Software
---

### Post by ash568 on 2008-12-23
Hello,

I have been trying to setup a very lightweight install of Ubuntu so choose to start with the server installer. All has gone very well have got the system working and am using OpenBox for my WM.

However when it comes to getting sound I have hit a wall and have been unable to get any where even after copious googling, mostly because the guides have made lots references to Gnome and of course not having it I have been unable to complete those steps.

So I have installed the pulse audio packages as well the GUI tools to go with it.

So with what I have done so far I am the following state.

I can bring up an instance of VLC or Mplayer and it begins playing.
I can then bring up pavumeter and it shows varying sound levels.
However no sound is coming out the speakers.

Also if it is any help before this latest install I was running the standard desktop package of Ubuntu and I had sound working.

Thank you in advance for any help and I do hope I have provided enough information.

---

### Post by markbuntu on 2008-12-23
In the PA volume control (pavucontrol) you need to see which sink those apps are using and change it to the one for your soundcard/speakers. You also need to check the alsamixer to make sure that it is set correctly and that the default asla sound card is pulseaudio.

There is a comprehensive guide to using alsa/pulseaudio here, (the gnome parts are not critical to your success):

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

You are very close to getting this working.

---

