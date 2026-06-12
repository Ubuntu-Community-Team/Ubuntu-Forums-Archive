---
title: "Playing Audio Backwards?"
date: 2009-02-13
forum: Multimedia Software
---

### Post by Drubie on 2009-02-13
Good Morning,

I have a rather off-the-walls question:
How can I play an audio file backwards?  Can I use vlc to do this, or totem?

I wanted to learn how to play this song for guitar backwards, and am having trouble reading the music backwards - I need to hear it.

Thanks for your help guys!

---

### Post by prshah on 2009-02-13
> **Drubie said:**
> How can I play an audio file backwards?  

You can open the file in [Audacity]("apt://audacity") and use Effect-Reverse. Then, when you play it, it will play backwards; you can save it under another file name for future use.

---

### Post by andrew.46 on 2009-02-14
Hi,

If you are comfortable with the commandline SoX will do this:

```
$ play filename.mp3 reverse
```

Obviously substituting your own filename :-).

Andrew

---

