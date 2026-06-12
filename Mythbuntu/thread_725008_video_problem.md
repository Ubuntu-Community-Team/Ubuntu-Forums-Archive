---
title: "video problem"
date: 2008-03-15
forum: Mythbuntu
---

### Post by ceb0 on 2008-03-15
Hi

The last version of myth didn't work for me at all, with the new one I finally get a picture.  To start with I encountered the pink screen bug which I solved by updating my nvidia drivers.  Now I have a different and much stranger problem which I can't seem to find any reference to.

The picture is split in half with a large black band running down the middle.  The two sides of the picture are transposed , the left half is on the right side and the right half is on the left - it's not a pleasant viewing experience.  Do you remember ancient television sets with a 'horizontal control' button you sometimes had to fiddle around with?  It's like I need a horizontal control button.  As the icing on the cake, all channels seem to have a kind of strobe effect going on as well.  I've not  seen any settings in mythtv that seem to relate to it.  I'm set to Pal for New Zealand but have tried different variations of pal to see if it has any effect - nope.

TVtime is fine, a nice clear picture with no more quality complaints  than you might expect with an indoor aerial.

The card is a Hauppauge HVR-900 usb with the em28xx driver.  It's just analogue tv not DVB-T (thats a whole other problem).  I've got mythtv 0.21 on an up-to-date gutsy.  My video card is an onboard nvidia 6150.

Please help as this is slowly driving me mad.


A day later ...

After more digging around I managed to solve this by changing the recording preferences to 720x576, the default had been 420x756 (I think).  This was configured in mythfrontend.  Now I just had a tinny audio problem, and the random lockups to sort out and all will be well.

---

