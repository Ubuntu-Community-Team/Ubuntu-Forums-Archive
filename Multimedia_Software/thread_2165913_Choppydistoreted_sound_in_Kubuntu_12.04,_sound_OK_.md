---
title: "Choppy/distoreted sound in Kubuntu 12.04, sound OK in Mint 13 (maya)"
date: 2013-08-06
forum: Multimedia Software
---

### Post by cackerso on 2013-08-06
My motherboard is a ECS Z77H2-a2x. In Mint 13, 32 bit, maya, the sound is fine. In Windows 7 64 bit the sound is fine. In Kubuntu 12.04 (64 bit) the sound is distorted and choppy.

aplay -l gives:
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0

I also did: wget -O alsa-info.sh [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) && chmod +x ./alsa-info.sh && ./alsa-info.sh

The info is at: Your ALSA information is located at [http://www.alsa-project.org/db/?f=8a750](http://www.alsa-project.org/db/?f=8a750) ... 1e6a126e30

I've tried a few fixes that I've found listed on the web/forums to no avail, including compling the latest driver from Realtek and installing it.

I think I need some expert help here.

---

### Post by speartip on 2013-08-07
I'm no expert on this, but if sound is fine on Mint 13, it should be the same in 12.04, as Mint is based on this.
Have you got the kubuntu-restricted-extras package installed?
If you have, then it could well be as simple as a settings problem.
Try booting into a live cd/usb session & see if the problem still persists.
Other than that, maybe someone else could offer a suggestion.

---

### Post by cackerso on 2013-08-08
Well that turned out to be interesting.  The sound is not distorted when running from the live CD as you suggested.  And the same thing happens with Mint KDE 15.  Installed, with no other software installed besides what comes with the initial installation, the sound is choppy in the same way as with Kubuntu 12.04.  But from the live CD of Mint KDE 15 (64bit), the sound is fine.  

I do have the Proprietary drivers and Multiverse packages installed.

But what settings problem would explain the sound distortion?

---

### Post by speartip on 2013-08-08
As a matter of interest, when you say "sound distortion" do you mean all sound? Music? Video?
And what application are you using to play the sound?

---

### Post by cackerso on 2013-08-08
Just about anything that plays a sound.  The chime when KDE finishes loading, any music I play, any games I play, any You tube video with sound.  It doesn't seem to be limited to any particular application.

---

### Post by speartip on 2013-08-09
Still sounds like a sound setting problem to me try typing alsamixer in a terminal & see what your levels are.
I have attached a picture of mine as a reference.

---

### Post by cackerso on 2013-08-09
It seems to me it would be easier if I just posted an image file of the result of running alsamixer, like you have but I have no idea how to do it.  At first pass it seems pretty similar to what you posted.

(Edit) Well I did manage to use Ksnapshot to make a jpeg of the alsamixer output.  But the file is 189.1 KiB and I haven't yet figured out how to post it here as a thumbnail.

(Edit) Does this work?

---

### Post by cackerso on 2013-08-12
Well speartip you were spot on.  The solution turned out to be pretty trivial.  I had to use alsamixer to set the "Master" volume at about 50% to cut the distortion.  I guess for my set up with the setting all the way up I was over driving something hence the distortion.  Thanks for the input.

---

### Post by cackerso on 2013-08-12
Well speartip you were spot on.  The solution turned out to be pretty trivial.  I had to use alsamixer to set the "Master" volume at about 50% to cut the distortion (more like you had it).  I guess for my set up with the setting all the way up I was over driving something hence the distortion.  Thanks for the input.

---

### Post by speartip on 2013-08-13
Glad to here you got it sorted.
It usually is the case that the issues that cause you the most grief have the simplest solutions.
It's just finding out what they are.

---

