---
title: "Odd sound problems"
date: 2009-07-08
forum: Multimedia Software
---

### Post by litlfrog on 2009-07-08
I've done a new install of Ubuntu 9.04 and sound is behaving differently on this machine than it was on my old one. I'm using the same little desktop stereo speakers I did on my old system. We've got voicemails that are automatically e-mailed to an account as .wav files; even with the volume cranked all the way up, they're barely audible. I also noticed that unlike on my other desktop, changing the master volume doesn't seem to do anything. I can change the volume by sliding the PCM and Headphone volume bars, but the master volume bar doesn't seem to do anything. If I listen to something on YouTube, for instance, it's audible but the sound is kind of tinny and distorted. The system uses onboard audio; here's the output of aplay -l.

> **** List of PLAYBACK Hardware Devices ****
card 0: nForce [NVidia nForce], device 0: Intel ICH [NVidia nForce]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: nForce [NVidia nForce], device 2: Intel ICH - IEC958 [NVidia nForce - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I've never worked with sound issues on Linux before and I'm afraid I don't know where to begin troubleshooting this problem.

---

### Post by litlfrog on 2009-07-08
bump

---

### Post by litlfrog on 2009-07-09
Anything? I know the speakers work properly with Linux, because they were hooked up to the last computer a couple of days ago. I suppose it could be something going on with the onboard sound, I don't know how I'd test that. While the sound is audible on everything except wav files, it's kind of distorted, like the levels are too high despite being hard to hear.

---

### Post by Yellow Pasque on 2009-07-09
Check the obvious stuff (volume levels):
```
alsamixer
pavucontrol  #you may need to install this package
```

---

### Post by litlfrog on 2009-07-11
OK, haven't heard of pavucontrol before. On the Output Devices and Input Devices tabs, what's listed is NVidia Nforce; the levels are set at 75% and changing them doesn't affect what I hear. When sound is playing, the output level graph seems to be moving appropriately.

---

### Post by litlfrog on 2009-07-11
In alsamixer, I have to nearly peg the PCM and Headphones bars to the top to be able to hear anything. I'm really suspicious about that headphones bar, and the fact that changing or even muting the master volume bar does squat.

---

### Post by litlfrog on 2009-07-12
Bump. This is really frustrating--I know that both the sound card and the speakers work, but I'm not able to do part of my job because of this. I need to listen to voicemails that come in as .wav files, and as it stands I'm not getting enough volume to hear them even if I crank everything up as high as it will go.

---

### Post by igorzwx on 2009-07-12
Why do you bump?

Think!

The reason is Pulse

**Audio Noise in Ubuntu**
[http://ubuntuforums.org/showthread.php?t=1035892](http://ubuntuforums.org/showthread.php?t=1035892)

---

### Post by litlfrog on 2009-07-12
So . . . I'm inferring from the link that you posted that you believe I should remove pulseaudio and install OSS4?

---

### Post by igorzwx on 2009-07-12
I do not believe in anything anymore.
I feel betrayed and disullusioned.
I has been busy with this for months.
And nobody told me the truth.
The only GOOGLE helps.

---

### Post by litlfrog on 2009-07-12
Thank you for your surreal lack of help.

---

### Post by litlfrog on 2009-07-12
I installed OSS and now have no sound at all. So, not really an improvement there. *sigh* uninstalling.

---

### Post by igorzwx on 2009-07-12
Could you please tell exactly what you did?

You cannot install OSS4 when ALSA modules are loaded.

You should first blacklist them.
Then reboot.

I made the same mistake, by the way.

Read this:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

do not forget to purge the failed installation

---

### Post by litlfrog on 2009-07-12
> **igorzwx said:**
> Could you please tell exactly what you did?

You cannot install OSS4 when ALSA modules are loaded.

You should first blacklist them.
Then reboot.

I made the same mistake, by the way.

Read this:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

do not forget to purge the failed installation

More sincerely this time: THANK YOU! This fixed the problem. The link to the ubuntu.com community advice was more thorough than that provided from the OSS code site. I tried to shut down ALSA modules when I did the first install, but kept getting an error that it was in use by a process. The processes listed were lib-something or other, and I didn't know whether it would be safe to shut them down. The install seemed to work, but I guess some ALSA things were in use. I followed the steps in that link and sound is working much better.

---

### Post by igorzwx on 2009-07-12
Whe you change to OSS4, you have to fix playback of players, etc.
Some work. It should be done carefully.
I seems that I have already managed to fix everything.
USB audio deviced are not supported at all, no need fix them.
You can ask me by e-mail.
On one box Ekiga is not tested yet.
We can test it together.

---

