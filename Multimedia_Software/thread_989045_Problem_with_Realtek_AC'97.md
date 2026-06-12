---
title: "Problem with Realtek AC'97"
date: 2008-11-21
forum: Multimedia Software
---

### Post by celer2008 on 2008-11-21
Hi, i need help with my sound driver.
I have sound, i can play music and so forth, but it's all very quiet. The quality of the sound is also suspicious - sometimes there's a lot of crunchy sounds, because i have to turn my pc speakers to maximum volume to hear. I even checked out 'alsamixer', but that's maxed out too. 

Maybe the problem is that i've chosen the wrong output? Or is there a way to install something from Realtek?

Screencap of my sound preferences: [http://img167.imageshack.us/my.php?image=screenshotsoundpreferenjq1.png](http://img167.imageshack.us/my.php?image=screenshotsoundpreferenjq1.png)

---

### Post by psyke83 on 2008-11-21
> **celer2008 said:**
> Hi, i need help with my sound driver.
I have sound, i can play music and so forth, but it's all very quiet. The quality of the sound is also suspicious - sometimes there's a lot of crunchy sounds, because i have to turn my pc speakers to maximum volume to hear. I even checked out 'alsamixer', but that's maxed out too. 

Maybe the problem is that i've chosen the wrong output? Or is there a way to install something from Realtek?

Screencap of my sound preferences: [http://img167.imageshack.us/my.php?image=screenshotsoundpreferenjq1.png](http://img167.imageshack.us/my.php?image=screenshotsoundpreferenjq1.png)

Checking "alsamixer" will only check the PulseAudio mixer by default in Intrepid. You need to check your hardware device (especially the PCM mixer, which gets inexplicably muted for many users):

```
$ alsamixer -Dhw
```

Also check your PulseAudio configuration: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by celer2008 on 2008-11-21
> **psyke83 said:**
> ```
$ alsamixer -Dhw
```That did the trick. Thank you!

---

