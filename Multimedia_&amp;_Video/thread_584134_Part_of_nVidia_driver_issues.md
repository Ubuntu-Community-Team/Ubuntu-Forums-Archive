---
title: "Part of nVidia driver issues??"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by electronbee on 2007-10-20
Any ways, after deciding to wait and hold off with my nVidia 8600GTS I have discovered that for some odd reason Gutsy is not properly identifying my display hardware. Specifically, my monitor. DPMS should report the name of my monitor and applicable h/v sync rates, right? Feisty was able to identify my monitor. However, Gutsy is going with the default monitor and the boot screen is all off centered with artifacts at the top of the screen. But, this only happens AFTER the Ubuntu splash screen with the progress bar. The login screen is the one with the issue. Which is weird. 

Also, nvidia-glx-new doesn't work in Feisty and the restricted drivers do not work in Gutsy. I have tried every tip and suggestion on this forum, the web, and even with Envy. I try it and BAM, I get messed up login screen.

Any ways, here is what my screen looks like if I try the restricted drivers or nvidia-glx-new in Feisty:

[IMG]http://farm3.static.flickr.com/2122/1660805221_3770b84478.jpg?v=0[/IMG]

Any idears anyone?

---

### Post by ozite on 2007-10-20
I had the same problem with 8400 GS. I don't think the 8400 and above are supported in the nvidia-glx-new. I installed the newest Nvidia 100.14.19 and after some xorg.conf tweaking it works as good as it did before.

---

### Post by electronbee on 2007-10-20
ozite:

Can you pretty please tell us what you did? Especially as far as xorg.conf goes. I am a total newb on this. But, before I go and uninstall my nvidia-glx-new I'd like to know what I need to add and take out. 

Also, I assume I'll have to put nv in the restricted modules?

At least I am learning a lot on how to bring back X after a crash. :D

eb

---

