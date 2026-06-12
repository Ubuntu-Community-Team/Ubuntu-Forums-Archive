---
title: "Problems with master volume on board audio"
date: 2008-04-17
forum: Multimedia &amp; Video
---

### Post by dldseneviratne on 2008-04-17
I'm using Ubuntu 8.04 beta and when I try to control the volume from my mutimedia keybord, the volume change is displayed on screen but it doesn't get effected to the sound output. I had the same problem with Ubuntu 7.10 and I thought 8.04 will work fine. But no luck with that. I'm using an onboard 5.1 channel support audio device on a Gygabyte motherboard.

I also cant hear anything from the rear speakers. I only want to use 4 channels and MIC. I tried searching everywhere for a solution and thought of creating a new post.

My audio system is properly configured and works well with Windows XP. Any help on this would be greatly appreciated.

Thank you,

---

### Post by kpkeerthi on 2008-04-17
Go to System > Preferences > Sound and select Master volume

---

### Post by dldseneviratne on 2008-04-17
Thank you, that fixed my volume control keyboard buttons. How can I enable 4 channels?

---

### Post by kpkeerthi on 2008-04-17
Type ```
alsamixer
``` in a terminal window. Enable front & rear channels by selecting appropriate mixer sliders.

> Use left & right arrow keys to navigate
> Press M to toggle mute/unmuted
> Use up & down arrow to adjust volume levels
> Press 'Esc' to quit

---

### Post by dldseneviratne on 2008-04-18
Thanks. ;) :KS

---

### Post by kpkeerthi on 2008-04-18
So did it work?

---

