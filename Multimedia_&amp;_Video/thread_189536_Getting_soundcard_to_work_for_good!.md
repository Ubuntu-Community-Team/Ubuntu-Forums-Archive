---
title: "Getting soundcard to work for good?!?"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by hfwarner3 on 2006-06-05
I have put edubuntu 6.06 on a IBM 300PL Desktop with an integrated CS4235 sound card.  After install, the sound card did not work.  I logged in with root rights and ran the following:

sudo modprobe snd-cs4236

I logged out and logged back in as one of my kids and BINGO we have sound!  All is good.

But they shut the PC down for the night and this morning there is no sound again.  I repeated the process and it works again.

I tried editting the /etc/modules file to add the crystal sound card, but it is telling me that I can't since I am not owner of the file (root is).

How do I make this fix stick for good?

Thanks!

---

### Post by EReckase on 2006-06-05
sudo gedit /etc/modules will do it.

You have to sudo to edit the file as root. ;)

---

