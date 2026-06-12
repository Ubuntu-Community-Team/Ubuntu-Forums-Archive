---
title: "What is using my sound card?"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by Mimsy on 2007-05-28
> mimsy@mimsy-laptop:~$ cat /dev/urandom >> /dev/dsp
bash: /dev/dsp: Device or resource busy

According to the tutorial I was reading at the time, the above message means that an application is using my sound card, which in turn makes it impossible for me to have any other application do so.This is frustrating, since I am trying to play a game, and I want the game to have sound.

What puzzles me is, if something is using mysoundcard, it's an application or process that I have not started and am not aware of. I went straight from boot to the game (running it in Wine), and it has no sound. Weird.

Help, please?

/Mimsy

---

### Post by SoggyCornflake on 2007-05-28
> **Mimsy said:**
> \What puzzles me is, if something is using mysoundcard, it's an application or process that I have not started and am not aware of. I went straight from boot to the game (running it in Wine), and it has no sound. Weird.

Help, please?

/Mimsy

You might be getting this message if you didn't set up your sound correctly in wine.  When you used **winecfg** to setup your wine environment, did you setup the sound that matched the sound your system is using?

 When I tried  using wine, I had to choose **ALSA** since I have an **ALSA** sound setup.  I think **winecfg** defaults to **OSS**

---

### Post by Mimsy on 2007-05-28
Oh, that's a good point. Let me go see what my sound set-up on the rest of the system is, and I'll get back to you :)

EDIT:
Well, don't I feel stupid now... that fixed it. Thanks!

EDIT2: Skinny soy caramel? When do I get a chocolate mocha?

---

