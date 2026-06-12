---
title: "[SOLVED] Nvidia doesn't keep resolution setting"
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by samjh on 2007-11-28
I've been using Gutsy since it was released, and previously used Feisty and Edgy as well.  In all that time, I've had very few problems with Nvidia, and what problems I came across were fixed by editing xorg.conf.

But this problem has me stumped.

Yesterday, I logged off the computer, and when I turned it back on later, my screen resolution had changed to 1280 x 1024 @ 75 Hz.

No biggie, I thought.  I fired up nvidia-settings, like I did when I first installed Gutsy, and changed the resolution and refresh rate settings to my chosen 1028x768 @ 85 Hz, then saved the configuration to xorg.conf.

That should have done the trick.

It did not!  For when I restarted my computer, the resolution had switched back to 1280x1024 @ 75 Hz.

After several more tries, I determined that whenever I log off (ie. just logging off, not restarting), my X server restarts.  This didn't happen in previous versions of Ubuntu, but it happened all the time with Gutsy so I didn't think much of it.  But every time my X server restarts, the resolution jerks to 1280x1024 @ 75 Hz.

Eventually I reinstalled Ubuntu, but the problem is still here.

Can someone please help?

---

### Post by samjh on 2007-11-28
OK, fixed it!

For other users who may be having this problem:

In the nvidia-settings window, go to X Server Display Configuration.  Choose your display resolution and refresh rate, then click Advanced.

Click on the left-most button in the "Meta" section.  Select auto-select, then click the Delete button.  Then select the meta-mode you really want (in my case, it was "1024x768_85 +0 +0"), then click Apply.  Click Save to X Configuration File, and then save your settings to xorg.conf.

The auto-select meta-mode was automatically choosing 1280x1024 for me.  The way to stop it is to remove it and force nvidia-settings to use the configuration of your own choice by following the directions I've supplied above.

Hope this helps anyone else who are or may face this problem in the future.

---

