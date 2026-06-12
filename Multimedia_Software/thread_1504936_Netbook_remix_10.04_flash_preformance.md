---
title: "Netbook remix 10.04 flash preformance"
date: 2010-06-08
forum: Multimedia Software
---

### Post by jeremyleroy96 on 2010-06-08
I installed Netbook remix on my dell inspiron mini (Intel Atom with 1gb of ram)

I have noticed that flash video lags (more so video then audio) 

Flash games such as farmville (my mom plays it not me) the performance is playable but not very satisfying as it is on windows

---

### Post by lovinglinux on 2010-06-08
See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by mikewhatever on 2010-06-08
Flash for Linux is greatly inferior to that for Windows, so no matter what you do, it's not going to be the same.

---

### Post by snowpine on 2010-06-09
Which model of Dell Mini do you have, and which video card? 

Some of the Minis (10 and 12 I believe) use the Intel GMA500 Poulsbo video card, which requires a special driver. More details here: [http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345) 

I have a Dell Mini 9 (which does **not** have the GMA 500 graphics) and I have had better luck downloading the video first, then watching it from my hard drive. The Atom with integrated graphics is just too slow for streaming flash on Linux, in my experience.

---

### Post by lovinglinux on 2010-06-09
> **snowpine said:**
> Which model of Dell Mini do you have, and which video card? 

Some of the Minis (10 and 12 I believe) use the Intel GMA500 Poulsbo video card, which requires a special driver. More details here: [http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345) 

I have a Dell Mini 9 (which does **not** have the GMA 500 graphics) and I have had better luck downloading the video first, then watching it from my hard drive. The Atom with integrated graphics is just too slow for streaming flash on Linux, in my experience.

You could also use [FlashVideoReplacer](http://flvideoreplacer-extension.blogspot.com).

---

### Post by jeremyleroy96 on 2010-06-09
I have a dell mini 10 (not to be confused with 10v) I will check out flash optimization. What is this driver you are recommending it wasn't in restricted drivers when i installed it.

And for checking my video card i have no clue :(

---

### Post by snowpine on 2010-06-09
> **jeremyleroy96 said:**
> I have a dell mini 10 (not to be confused with 10v) I will check out flash optimization. What is this driver you are recommending it wasn't in restricted drivers when i installed it.

And for checking my video card i have no clue :(

The following terminal command will tell you what kind of video card you have:

```
lspci -nn | grep VGA
```

Post the results back here, and I will try my best to help (assuming I know the answer ;)).

---

