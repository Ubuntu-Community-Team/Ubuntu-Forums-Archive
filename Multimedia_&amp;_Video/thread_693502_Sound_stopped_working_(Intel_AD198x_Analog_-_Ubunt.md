---
title: "Sound stopped working (Intel AD198x Analog - Ubuntu 7.10)"
date: 2008-02-11
forum: Multimedia &amp; Video
---

### Post by dacovale on 2008-02-11
Somehow, my sound went awol on me during the night. Yesterday I got to bed, and the sound worked. (I know, I used the laptop to play some music)
This morning... no sound.

I've read through [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and haven't managed to get my sound working.

```
aplay -l
```

gives

```
**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: Intel [HDA Intel], enhet 0: AD198x Analog [AD198x Analog]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
```

(my locale is swedish)

and 

```
grep 'audio' /etc/group
```

gives

```
audio:x:29:niklas
```

and niklas is my username.

I've checked with ```
alsamixer
```

and everything seems unmuted. I have also tried to purge and reinstall alsa as per the above mentioned threads instructions.

The programs doesn't complain. They simply act as if I'm deaf and they're really working. 

Now, I'm fresh out of ideas. Help?

---

### Post by dacovale on 2008-02-11
Somehow, booting into Vista and unmuting the sound there helped me. Now, that makes me wonder; **What did I miss? What other controls for the sound are there?** I can't really accept having to boot into Vista to solve my Linux music problems.

---

### Post by now switched to linux on 2008-02-11
i dont know much abt linux 
but i had problem that sound doesnt came after my ubuntu installation.
what the temp solution i found was starting my ubuntu on battery
so whenever i start ubuntu from battery than i got sound and when on ac power it doesnt
hope this help u somehow:confused:

---

### Post by dacovale on 2008-02-11
nah, that doesn't help me. I started on batteries the first time around, but on subsequent boots, I was on AC power. (I must have rebooted half a dozen times before I gave up and tried from Vista)

but thanks for trying :)

---

