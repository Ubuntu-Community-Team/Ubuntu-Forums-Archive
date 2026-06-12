---
title: "Logitech digital ext speakers work in 12.04 but not 12.10"
date: 2013-02-10
forum: Multimedia Software
---

### Post by ZootNerper on 2013-02-10
Hi Folks,

I have a pair of Logitech Digital external speakers that run off the USB port. I am running Ubuntu.

Under a fresh install of 12.04 they can be selected in "sound settings" and work perfectly. However, under a fresh install of 12.10, with all updates, they do not.

Under 12.10, they appear in "sounds settings" and can be selected, but they do not work, except when pressing the sound volume buttons on the units which brings up a popup showing the volume going up or down or mute/unmute.

Anyone have any ideas please?

-- Zoot

---

### Post by ZootNerper on 2013-02-10
My appologies. I searched the two trouble searching guides but found nothing about digital speakers and thought they were of no use to me, but the first one had a link to using the alsomixer and this is the solution.

For those who may want to know. I did this:

1. Ran alsamixer in a terminal
2. Hit F6 and used the arrow keys to select the "usb audio" option
3. The volume on the slider was at zero. I moved it up to 100 and all works.

My appologies again.

-- Zoot

---

