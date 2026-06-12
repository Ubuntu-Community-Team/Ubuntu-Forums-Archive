---
title: "Twinview, Tremulous... incorrect display"
date: 2006-11-14
forum: Multimedia &amp; Video
---

### Post by encompass on 2006-11-14
[SOLVED]
In tremulous with my dual monitor setup I have the game in the middle of the two screens.
Before, when I had twin view, setup with dapper and breezy, I did not get this problem.  It choose display number 1.  Any ideas?

Figured it out... I just added the proper single screen resolution to my twinviews meta resolution list.  That made everything work like a champ.

---

### Post by skiingdomo on 2008-02-25
care to post a link on how to do this?

Thanks

---

### Post by ad_267 on 2008-03-01
Yeah, I'm having the same problem with my games after updating my nvidia driver then reverting back because I was having problems. Could you post exactly what you did thanks?

---

### Post by ad_267 on 2008-03-01
I've got it working now

I changed this line in my xorg.conf file:
```
Option         "metamodes" "CRT-0: 1280x1024_60 +0+0, CRT-1: 1024x768_60 +1280+256; CRT-0: 1280x1024 +0+0, CRT-1: nvidia-auto-select +1280+0; CRT-0: 1280x960 +0+0, CRT-1: nvidia-auto-select +1280+0; CRT-0: 1152x864 +0+0, CRT-1: nvidia-auto-select +1152+0; CRT-0: 1024x768 +0+0, CRT-1: nvidia-auto-select +1024+0; CRT-0: 832x624 +0+0, CRT-1: nvidia-auto-select +832+0; CRT-0: 800x600 +0+0, CRT-1: nvidia-auto-select +800+0; CRT-0: 640x480 +0+0, CRT-1: nvidia-auto-select +640+0"
```

To this:
```
Option         "metamodes" "CRT-0: 1280x1024_60 +0+0, CRT-1: 1024x768_60 +1280+256; CRT-0: 1280x1024_60 +0+0, CRT-1: NULL; CRT-0: 1024x768_60 +0+0, CRT-1: NULL; CRT-0: 800x600_60 +0+0, CRT-1: NULL"
```

I got rid of a all of the modes except the first and then added options for using the first display only at different resolutions and disabling the second display.

---

### Post by CiaoCiao on 2008-03-01
Mind posting your complete xorg.conf for me to have a peek at?

I tried your line copied into my xorg.conf but my second monitor is always disabled with your line of code.

---

### Post by ad_267 on 2008-03-01
I've attached my xorg.conf. How you change yours will depend on the name of your monitors and  the resolutions and refresh rates. I used the previous metamodes and just removed ones I thought I wouldn't need and added extra ones with the second monitor set to NULL.

---

### Post by CiaoCiao on 2008-03-02
I'm still pear shaped on this bloody problem.  Anywhere in my xorg.conf I put NULL, restart GDM and the second monitor goes blank...

Here is what works.

```
    Option         "metamodes" "CRT-0: 1024x768_60 +0+0, CRT-1: 1024x768_60 +1024+256; CRT-0: 1024x768 +0+0, CRT-1: nvidia-auto-select +1024+0"
```

here's what makes the monitor go blank after a restart of GDM...

```
Option         "metamodes" "CRT-0: 1024x768_60 +0+0, CRT-1: 1024x768_60 +1024+256; CRT-0: 1024x768 +0+0, CRT-1: nvidia-auto-select +1024+0; CRT-0: 1024x768_60 +0+0, CRT-1: NULL"
```

I am open to suggestions, comments and/or cattle prods..

I really hope that I am doing something really dumb, 'cause that would be easy to fix...

---

### Post by ad_267 on 2008-03-03
I'm very new to ubuntu and linux so I can't help you sorry, I just guessed and got lucky. It might be a good idea to start a new so more people take notice.

---

