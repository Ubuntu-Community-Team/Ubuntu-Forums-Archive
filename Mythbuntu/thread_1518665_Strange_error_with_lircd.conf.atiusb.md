---
title: "Strange error with lircd.conf.atiusb"
date: 2010-06-26
forum: Mythbuntu
---

### Post by WhiteHairedGeek on 2010-06-26
I had installed Mythbuntu 10.04 with using an ATI Remote Wonder through the Install Process and everything worked fine.

I then added in IR Blaster support for the Hauppauge HD-PVR which also worked fine once I had followed the instructions on the MythTV Wiki. Part of those instructions required me to rebuild the lirc_atiusb driver, which I did successfully.

But with the HD-PVR working, the ATI Remote Wonder stopped working. If I removed the HD-PVR IR Blaster, then the ATI Remote Wonder worked fine by itself.

Finally, after a few days of bashing my head against the keyboard, I tried opening up the /usr/share/lirc/extras/more_remotes/atiusb/lircd.conf.atiusb file with gedit instead of with vi.

Lo, and behold I got the following error: "Could not open the file lircd.conf.atiusb, gedit has not been able to determine the character encoding. Please check that you are not trying to open a binary file."

However, I could open it fine in vi and proceeded to extract the remote definition that I needed and created a new file combining just that portion as well as the HD-PVR blaster portion and made the resulting file my lircd.conf.

After a restart of lirc, both the ATI Remote and the HD-PVR blaster started working.

So, I think there may be some stray binary characters in the lircd.conf.atiusb file in the Mythbuntu 10.04 distribution that screws up lirc when you have multiple include files specified in the lircd.conf file. And gedit happens to notice them, but vi does not.

Can someone else try and confirm this from a fresh install?

---

