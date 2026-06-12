---
title: "Jaunty Skype Video problems"
date: 2009-05-16
forum: Multimedia Software
---

### Post by ptipton on 2009-05-16
When I first installed Jaunty Skype worked perfectly out of the box with my logitech webcam but now I have video problems in that I cant see either the callers or my own video (just blank window) but the caller can see me. If I go to options and hit the Test button in the video section nothing happens.

I have tried staring Skype with
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
and
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

But in both cases the same problem exits.

Not sure what has changed since it was working correctly about the only thing I've doe is install a few programs and then delete some of them.

Any help much appreciated.

---

### Post by ptipton on 2009-05-18
Have resolved the problem it was caused by Cairo-Dock 2 when I remove this skype video works fine again. Will post in Cairo-Dock forums

---

### Post by fabounet on 2009-05-19
this is a know Qt4 issue
you have to set XLIB_SKIP_ARGB_VISUALS before launching a Qt4-based program :
for instance :
```
export XLIB_SKIP_ARGB_VISUALS=1 && skype
```
you can add it into the skype launcher in your dock.

---

### Post by bn127 on 2009-05-30
> **fabounet said:**
> this is a know Qt4 issue
you have to set XLIB_SKIP_ARGB_VISUALS before launching a Qt4-based program :
for instance :
```
export XLIB_SKIP_ARGB_VISUALS=1 && skype
```
you can add it into the skype launcher in your dock.
Thank you a lot. After adding the code to the dock launcher I got Skype working 100%!

Bn127

---

### Post by hihihi on 2009-06-16
that works for mee too, thx a lot,
and suddenly qt4-apps have shadows as well :)

---

### Post by Radhavictory on 2009-06-21
Awesome dude! Thanks a lot! Pure & simple!
Oh yeah and just in case there is any confusion for anybody, the

"skype" in the "command to launch on click" window must be replaced by
export XLIB_SKIP_ARGB_VISUALS=1 && skype

---

### Post by gryall on 2009-07-10
I am having the same problem as above (I can't view my own or other peopels webcams, whilst they can view mine fine. Other progams display my webcam fine.)

I have tried all of the above soulotions and none of them have worked. Anyone got any other Ideas?

---

### Post by fballem on 2009-07-10
> **Radhavictory said:**
> Awesome dude! Thanks a lot! Pure & simple!
Oh yeah and just in case there is any confusion for anybody, the

"skype" in the "command to launch on click" window must be replaced by
export XLIB_SKIP_ARGB_VISUALS=1 && skype

Tried this and got the error shown in the screenshot below. Any ideas?

Thanks,

---

### Post by oscarmeyer51 on 2009-11-17
You can also see this thread for an additional solution.

[http://ubuntuforums.org/showthread.php?p=8338722#post8338722](http://ubuntuforums.org/showthread.php?p=8338722#post8338722)

---

### Post by OM NOM NOM on 2010-06-06
Thank you thank you THANK YOU! This worked out great - that issues was driving me absolutely CRAZY

---

### Post by WimVD09 on 2011-01-11
> **Radhavictory said:**
> Awesome dude! Thanks a lot! Pure & simple!
Oh yeah and just in case there is any confusion for anybody, the

"skype" in the "command to launch on click" window must be replaced by
export XLIB_SKIP_ARGB_VISUALS=1 && skype

Hey, not entirely sure what you mean by add to the command to launch on click window, how do i get to that? step by step would be greatly appreciated, I am new to ubuntu and its fun-ness.

---

