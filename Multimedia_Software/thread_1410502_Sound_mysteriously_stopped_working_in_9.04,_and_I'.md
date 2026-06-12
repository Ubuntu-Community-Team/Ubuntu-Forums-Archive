---
title: "Sound mysteriously stopped working in 9.04, and I've tried EVERYTHING"
date: 2010-02-18
forum: Multimedia Software
---

### Post by ferric84 on 2010-02-18
After months of everything working flawlessly, I turn my Thinkpad T61 on a few days ago to find I have absolutely no sound at all.  No login sounds, mp3s, test sounds, anything.  I didn't upgrade anything (that I can think of), change any settings, etc.  What I've done:

- Ensured Master and PCM are 100% and unmuted in alsamixer
- Upgraded ALSA (these instructions: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810))
- Uninstalled and reinstalled flashplugin-nonfree
- Ensured my user has permissions to "Use audio devices"
- Checked the sound settings in every program that has anything to do with sound
- Restarted a thousand times, every combination of killing pulseaudio, restarting alsa, checking every sound server for signs of life individually, etc.  Not a peep.

aplay -l gives me this:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


The only thing I can think of that *may* have something to do with it, was right around the time the sound stopped working, I was fooling around with my XP virtualbox machine trying to get my iPod working.  All this entailed though was dicking around in the USB settings of virtualbox, and adding my user to the "virtualbox" group.  I've gone into virtualbox and googled like crazy for anything related to no avail.

The only reason I know it's not hardware related is because I booted up the live CD, and confirmed that sound working fine in there.

What can I do??  Sound is one of those "you don't realize what you have until it's gone" things, and I'm suffering hard here.

---

