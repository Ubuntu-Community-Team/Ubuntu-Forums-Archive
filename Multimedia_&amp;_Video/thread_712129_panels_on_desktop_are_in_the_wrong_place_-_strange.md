---
title: "panels on desktop are in the wrong place - strange!?"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by waldorf on 2008-03-01
Please look at the screenshot attached.

This is the 1440 x 900 external monitor attached to an inspiron 600m laptop (1024x768) with an ati video card. I believe its a Radeon 9000 mobility, but in the xorg.conf it identifies it as a Radeon R250 [Mobility FireGL 9000]. This is a fresh install, no tweaking etc.

I cannot get the panels to expand to the full 1440 and they refuse to be placed at the bottom. So the bottom panel cuts through the middle of the screen and over windows.

Not sure what is going on and would greatly appreciate any help.

Thanks in advance

---

### Post by Glaxed on 2008-03-01
Try going to System --> Preferences --> Screen Resolution and put your setting there.

---

### Post by waldorf on 2008-03-01
Thanks for the quick response, but 1440x900 is not a choice in those settings. It only goes up to 1024x768.

---

### Post by Glaxed on 2008-03-01
:(, has this always been a problem? I was gonna suggest reconfiguring X.

---

### Post by waldorf on 2008-03-01
> **Glaxed said:**
> :(, has this always been a problem? I was gonna suggest reconfiguring X.

This is a fresh install so its the first time I tried it. How would I reconfigure X - ie which lines would I change and how would I change them?

Thanks again

---

### Post by Glaxed on 2008-03-02
Boot into the recovery kernel;
```

dpkg-reconfigure xserver-xorg

```

---

### Post by waldorf on 2008-03-04
Thanks Glaxed - I think that does it!

---

