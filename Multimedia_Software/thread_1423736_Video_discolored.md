---
title: "Video discolored"
date: 2010-03-07
forum: Multimedia Software
---

### Post by dobry_den on 2010-03-07
Hi! Whenever I play .avi files in any of my video players (vlc, totem, mplayer), I get a discolored output. I've just recently patched my system because of a flipped webcam image ([http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/](http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/)) and I don't know if that's the reason. I attached a picture of how it looks. Do you have any ideas what to do?

---

### Post by Rey117 on 2010-03-07
try pressing windows+M see what happens

---

### Post by dobry_den on 2010-03-07
It gets very whitish, i guess the colors are inverted. But it didn't help.

---

### Post by Rey117 on 2010-03-07
oh sorry it happened to me and It you might have done it to sorry I couldn't help.

---

### Post by dobry_den on 2010-03-14
ok so i rebooted the computer and the problem was gone. and now it's back again. it has appeared after i updated my system, and i suspect that it's this line in synaptic package manager that's responsible for all of it: libv4l-0 (0.6.4-1+hg20100220~kkv4l1) to 0.6.4-1+hg20100220~kkv4l2. now even the video on skype is like that. do you have any idea please?

---

### Post by no2498 on 2010-03-14
they say cheese is how we set the color now
but for me with 910 karmic the rgb is back wards 
i use the old v4l1 they put them both together v4l1 and v4l2

hope cheese works for you

---

### Post by benerivo on 2010-03-14
The hue is wrong. Try opening totem and changing the hue slider control (google for 'totem hue' for bug reports).

---

### Post by Uncle Spellbinder on 2010-03-14
This might help: [http://www.wiredrevolution.com/ubuntu/fix-blue-tinted-video-in-ubuntu](http://www.wiredrevolution.com/ubuntu/fix-blue-tinted-video-in-ubuntu)

In Totem, I've also found that *edit > Preferences > Display > Restore to Defaults* can help sometimes.

---

### Post by dobry_den on 2010-03-16
Thanks a lot guys. I tried "Restore to Defaults" in Totem (the sliding bar was all the way at the left) and it solved everything!

---

### Post by pickarooney on 2010-04-02
This has suddenly happened me again now, but affects SMPLAYER, VLC and TVTIME. Image is fine in totem (pity it's such a crap player). Adjusting the slider in totem does nothing to solve the problem in the other players. Uncle Spellbinder's link does nothing either.

Any suggestions?

---

### Post by pickarooney on 2010-04-02
Seems a particular video file has the power, when played, of screwing up my colours systemwide. Rebooting fixed it for now.

---

### Post by Chronon on 2010-04-02
> **pickarooney said:**
> Seems a particular video file has the power, when played, of screwing up my colours systemwide. Rebooting fixed it for now.

It might pose an odd corner-case.  It could be worth posting a bug report explaining this and offer to provide the video to developers for testing.

---

### Post by donato roque on 2011-07-19
This happened to me after a kernel upgrade. I use Nvidia card. There is an unusual tint (colors are off) affecting videos played on media players. It does not affect flash and therefore videos played on the browser are ok.

Please check your graphics driver. I can do that by going to 'Additional Hardware drivers'. Let it scan your system. Make sure the recommended driver is focused and activated. Let ubuntu download and install the recommended driver for you. 

Reboot.

Problem solved.

---

