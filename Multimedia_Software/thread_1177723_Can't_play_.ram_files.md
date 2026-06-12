---
title: "Can't play .ram files"
date: 2009-06-03
forum: Multimedia Software
---

### Post by sideburns on 2009-06-03
My sister uses the latest version of Ubuntu, and keeps it updated.  Today, she tried downloading and playing a .ram file and got nothing.  Checking, other audio files work.  I'm presuming she needs a codec, but need a pointer to getting it.

---

### Post by jerrrys on 2009-06-03
i use vlc media player. vlc plays everything, but guess what....no .ram support...

an internet search seems to indicate that RealPlayer supports .ram.  i know, heck of a way to go just to play .ram, but thats all i could find...

[http://filext.com/file-extension/RAM](http://filext.com/file-extension/RAM)

so there it is for what its worth...

---

### Post by hansdown on 2009-06-03
Hi sideburns.

This firefox addon should help.

[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

Thankyou to ugm6hr.

---

### Post by andrew.46 on 2009-06-03
Hi sideburns,

> **sideburns said:**
> My sister uses the latest version of Ubuntu, and keeps it updated.  Today, she tried downloading and playing a .ram file and got nothing.  Checking, other audio files work.  I'm presuming she needs a codec, but need a pointer to getting it.

MPlayer will play this type of file, or rather pointer to a file, with the -playlist option:

```
mplayer -playlist myfile.ram
```

If you download the .ram file itself and open it with a text editor you will see that it is a set of directions pointing to the *actual* media stream. The graphical frontend SMPlayer illustrates this option well and I attach a screenshot to demonstrate this.

All the best,

Andrew

---

### Post by sideburns on 2009-06-03
Thank you, handsdown, but how is that going to help if she can't play the file once she's downloaded it?  Looks like getting her RealPlayer is the best bet.

---

### Post by hansdown on 2009-06-03
Sorry, I missed that.

Realplayer should help.

---

