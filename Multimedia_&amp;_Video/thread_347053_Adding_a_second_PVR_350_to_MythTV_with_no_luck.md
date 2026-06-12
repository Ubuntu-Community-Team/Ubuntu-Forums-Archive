---
title: "Adding a second PVR 350 to MythTV with no luck"
date: 2007-01-26
forum: Multimedia &amp; Video
---

### Post by jmoe74 on 2007-01-26
I have added a second pvr-350 to my mythbox. When I run the command:

*lspci | grep "Internext Compression"*

it shows that I have two tuner cards. When I run the command 

*ls /dev/video?*

it shows:

/dev/video0  /dev/video1

I can not get it to record from the second card either through myth or through mplayer my computer recognizes that there are two PVR-350 cards, but only one will record. how do I get the second card to record as well? I have googled til my fingers bled and there is hardly any documentation on this. I would be more than happy to post my process if someone would be kind enough to point me in the right direction. ](*,)

---

### Post by SyvanX on 2007-01-26
Have you added /dev/video1 as a second tuner in mythtv-setup?

You should then have to setup what listings it references just like your first card.  I think you should be able to link the same information to the new card.

---

