---
title: "No sound from Realtek ALC899 on Asus board"
date: 2010-03-04
forum: Multimedia Software
---

### Post by Botruckle on 2010-03-04
Just built a new system with an Asus P6X58D Premium board, but can't get sound out of it. Running the 64bit version of Ubuntu 9.10. 

I've read dozens of other posts that are also having issues with the Realtek ALC889 and related family of audio hardware. I actually got it working for a while, then it mysteriously quit and hasn't worked since. (I also have a Radeon HD 5850 that has the option of HDMI audio, but my speakers can't physically connect to it.)

I have installed the latest driver from Realtek in Taiwan, but no difference. I have selected the output device as Internal Audio Analog Stereo, have the speakers connected to the right port in back (and tested the speakers with my laptop - they work). I have tried various other options in Sound Preferences for hardware and Output, but no luck. 

One post suggested modifying /etc/modprobe.d/alsa-base.conf and adding these lines but there was no change in sound after restarting.
   alias snd-card-0 snd-hda-intel
   options snd-hda-intel model=auto

I've tried uninstalling and reinstalling the audio driver and tried other versions of the driver, as well as other modifications of the alsa-base.conf file.

Any suggestions as to next steps, or info that you would like?

---

### Post by mörgæs on 2010-03-06
9.10 has so many sound problems that I think you should try 10.04 as a first step:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

It is only in alpha, but on all machines where I have installed it the sound (and everything else) just worked. I guess we have a really good release coming up here.

---

### Post by Botruckle on 2010-03-07
Well, I'm chagrined. The tipoff for me was that I had it working and then it stopped. Apparently in Sound Preferences, even if the volume is adjusted manually, mute can still be checked (and it was). Sound works fine with the tweak I added in the first post to the alsa-base.conf file. The really good news is that even in this version of Ubuntu, the sound can be made to work.

---

### Post by Botruckle on 2010-03-10
Also, since games were lacking sound even after un-muting, I found a thread about purging PulseAudio and doing this fixed the sound in games also. 

I ran this line then restarted the computer, and it seemed to do the trick
**sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio**

Someone else in the thread said to run these lines:
[B]sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge gstreamer0.10-pulseaudio vlc-plugin-pulse pulseaudio[/B]

Here is the thread link:
[http://ubuntuforums.org/showthread.php?t=1368141](http://ubuntuforums.org/showthread.php?t=1368141)

---

### Post by Tagard on 2010-03-18
I've been having the same problem on an ALC663 on an Asus board. I've actually had the sound work for a couple of days before having it subsequently fail a couple of reboots later. It's like it decides that it's time to take a vacation and I am left trying every last trick I can find on the forums to get it going again.

I'm so frustrated at this point that I'm considering loading the 10.04 alpha.

---

### Post by mörgæs on 2010-03-19
> **Tagard said:**
> 
I'm so frustrated at this point that I'm considering loading the 10.04 alpha.

By all means, please do! It is in beta now, but the address above still works. Try a live boot first, though.

---

### Post by Tagard on 2010-03-22
Thanks Mörgæs, I tried 10.4 as you suggested and I've got sound again :)

---

### Post by mörgæs on 2010-03-23
You are welcome. 
A detail: The new Ubuntu is called 10.04 and not 10.4. The names indicate year and month of the release.

---

