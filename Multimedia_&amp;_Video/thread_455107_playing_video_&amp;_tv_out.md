---
title: "playing video &amp; tv out"
date: 2007-05-26
forum: Multimedia &amp; Video
---

### Post by Dan23 on 2007-05-26
Hello everyone!

First of all I will say that I`m new to Linux and Ubuntu so please be gentle with me :)

my problem is this:
I have a radeon ati graphics card with a tv-out connection and I installed the fglrx driver. After doing so, I can now see my computer screen on my tv screen (big success).
Unfortunately when I play videos in players like xine or totem while on my computer screen I see the film. on my tv screen in the area where the film should be seen, I only see a black rectangle. my tv out works great It`s only that I can`t see films with it.
Do anybody has an idea on how I might fix this?

---

### Post by Kevf on 2007-05-26
I don't have a clue.... but I DO have a question for you. I've got a Radeon chipset also. Exactly which files did you install to get it working (it won't work for me)?  And how did you get the tv-out working?

Could you post the output of 

```
fglrxinfo
```

---

### Post by Dan23 on 2007-05-26
> **Kevf said:**
> I don't have a clue.... but I DO have a question for you. I've got a Radeon chipset also. Exactly which files did you install to get it working (it won't work for me)?  And how did you get the tv-out working?

Could you post the output of 

```
fglrxinfo
```

Well, I just used this step by step: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

here is the code you asked for:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X300/X550/X1050 Series
OpenGL version string: 2.0.6334 (8.34.8)

Anybody else know how can I fix my problem?

---

### Post by Dan23 on 2007-05-27
bump :popcorn:

---

### Post by beck24 on 2007-05-27
Bump again!
I was just about to post this same question... someone must know how to make video show up.  Please?

- Beck

---

### Post by HydroDiOxide on 2007-05-29
Could you also post the output of

```
cat /etc/X11/xorg.conf
```

This might help those who can't get tv-out to work with their x300 chipsets (like kevf)

ps: for your problem you might want to look into your overlay options

---

### Post by HobbitCy on 2007-05-30
dump

---

### Post by Dan23 on 2007-05-30
Well there is an happy end to this one.
I DL the Mplayer software and under preferences>video I chose:
"gl2 X11 (OpenGL) - multiple textures version" and It works great!

---

### Post by Kevf on 2007-05-31
I've tried this wiki

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

and again nothing.... still mesa

Strange thing is, I've got two xorg.conf's. One backup and one original.

---

