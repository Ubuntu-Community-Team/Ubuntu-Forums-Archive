---
title: "[SOLVED] My sound just stopped working"
date: 2008-11-12
forum: Multimedia Software
---

### Post by RiazM on 2008-11-12
aplay -l gives me:
```
**** List of PLAYBACK Hardware Devices ****
card 0: M5455 [ALi M5455], device 0: Intel ICH [ALi M5455]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: M5455 [ALi M5455], device 2: Intel ICH - IEC958 [ALi M5455 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and nothing is muted in alsamixer, when I press test sound in sound preferences the thing comes up but nothing happens. I am on 8.10. If I reboot into Windows I can get sound. Anyone know where I should start to debug this thing?

---

### Post by douham on 2008-11-12
> **RiazM said:**
> aplay -l gives me:
```
**** List of PLAYBACK Hardware Devices ****
card 0: M5455 [ALi M5455], device 0: Intel ICH [ALi M5455]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: M5455 [ALi M5455], device 2: Intel ICH - IEC958 [ALi M5455 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and nothing is muted in alsamixer, when I press test sound in sound preferences the thing comes up but nothing happens. If I reboot into Windows I can get sound. Anyone know where I should start to debug this thing?

What version of Ubuntu are you using? Have you tried using Lord Raidens guide? [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by RiazM on 2008-11-12
I am on 8.10, I used the guide so much as to check that my drivers were installed and sound wasn't muted. I also don't think it's a user privilege problem.

---

### Post by RiazM on 2008-11-12
running this command as quoted [here]("http://ubuntuforums.org/showpost.php?p=5131958&postcount=2")

produced the warning

```
cat: /proc/asound/card0/codec#*: No such file or directory

```

---

### Post by RiazM on 2008-11-12
Well, ok it started working after I did sudo alsa reload then went into alsamixer, there was alot more levels to adjust, so i unmuted as many as I could and it started to work.

Wierd.

---

### Post by douham on 2008-11-12
Hi RiazaM, your thread title is "my sound just stopped working," does this mean that it was working when you first installed? . A few weeks ago, I followed a thread to killall pulse, etc and that killed my Intrepid sound. 
You have already done some research, have you changed your sound settings already. Try code: alsamixer and make sure Master and PCM are at full.

Sorry, but thats 'bout all I can help you with

---

### Post by RiazM on 2008-11-12
yeah it was working, then it stopped today when I booted.
But it works again now. Previously when I ran alsamixer there was only a master volume level, but now it's fine. I had better close this thread.

---

