---
title: "dpkg-reconfigure xserver-xorg"
date: 2010-02-15
forum: Multimedia Software
---

### Post by makria on 2010-02-15
I'm learning a lot from getting an old machine up and running on Ubuntu (more than I had planned in fact).

I installed Breezy (Ubuntu) and had to sort out video issues, I found the following command line very helpful: dpkg-reconfigure xserver-xorg 

Now I'm trying to get Karmic working (Kubuntu) on the machine and again have to sort fix video problems, but I find the above command no longer works.

I read on other posts this dpkg command for xserver is no longer available, and the one it is replaced with (in recovery mode) I certainly can't see.

Now it appears I'm left with nothing.

It seems the more modern Ubuntus are more intent on snatching defeat from the jaws of victory than previous releases! 

The dpkg option might not be the most friendly but at least it was the a level above editing the config files manually (which it seems I'm now going to try to have to do)

:-(

Are there any other tools to help configure the X server stuff.

E.g. when I did it on Breezy I had to limit...

* video to 800x600
* colour depth to 16 (I think)
* set the video card memory to 16384

Regards,
Mark.

---

### Post by Yellow Pasque on 2010-02-15
What video issues do you have? Post /var/log/Xorg.0.log

---

