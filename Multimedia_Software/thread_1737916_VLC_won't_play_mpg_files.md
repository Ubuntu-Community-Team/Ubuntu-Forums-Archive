---
title: "VLC won't play mpg files"
date: 2011-04-24
forum: Multimedia Software
---

### Post by forficula on 2011-04-24
VLC will play most other formats, but not mpg/mpeg - just shows the first frame and slider moves, but no sound or video.  I can play mpg files using other players such as Kaffeine, Xine and Banshee, so I can play all types of file with no real problem, but I keep hearing VLC is the best, but won't do all for me.  Banshee will play everything, as will Kaffeinw.  Totem plays most OK (not generally as good as other players, but, though it palys mpg files, the slider goes all the way to the right, so there is no control available.  Thanks. David.

---

### Post by handy on 2011-04-25
I take it you have installed the Restricted Formats:

[https://help.ubuntu.com/community/RestrictedFormats/#Playing%20Restricted%20Formats](https://help.ubuntu.com/community/RestrictedFormats/#Playing%20Restricted%20Formats)

If so it should work.

You could try un-installing & reinstalling VLC, on the off-chance that it resolves a misconfiguration that has somehow occurred in the background.

---

### Post by forficula on 2011-04-25
Yes, I have done that already - other players play mpg, I just can't get VLC to do so.  Thanks, David

---

### Post by handy on 2011-04-25
Have you installed libdvdcss2 ?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by forficula on 2011-04-26
Unfortunately, that makes no difference, but thanks for the suggestion.  D.

---

### Post by andrew.46 on 2011-04-26
Can you post one of the troublesome files somewhere?

---

### Post by K_45 on 2011-04-26
Doesn't VLC depend on its modules, not gstreamer?  Run

```
vlc *file*
```

 in the terminal with file being the file and post the output. What drivers are you running?

---

