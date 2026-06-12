---
title: "Can I play multi-region DVDs?"
date: 2007-07-05
forum: Multimedia &amp; Video
---

### Post by QwUo173Hy on 2007-07-05
I'm in Ireland and want to order a DVD from the states. I have the Restricted codecs installed. Will that do the job?

---

### Post by Vajra Vrtti on 2007-07-05
I think so, but see the section **Setting DVD Region Codes** [here]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs").

---

### Post by ausmuso on 2007-07-05
I have never set a region on any of my DVD drives and I seem to be able to play DVDs from any region with MPlayer, VLC or Totem.

Have fun!

---

### Post by imagoarbour on 2007-07-05
I'm in Australia, I have several region 1 or 2 DVD which I got from Amazon. I've only been using Ubuntu since Monday, but I'll give them a whirl tonight and see how far I get since it's an issue I'll have to deal with soon.

Cheers,

---

### Post by QwUo173Hy on 2007-07-05
Thanks lads / ladies. I think I'll order it. The link Vajra Vrtti posted is also very helpful. Thanks again.

---

### Post by imagoarbour on 2007-07-05
Okay, I couldn't play region 2 DVD's so I followed the instructions provided by Vajra. I followed the instructions as far as the medibuntu part but I couldn't get the page for the download to come up, I got the dreaded '403 Forbidden' error. However I found this page,  using google and libdvdcss2 as the search: [http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/](http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/). From here I used/fluked this piece of code: 'sudo apt-get install libdvdcss2 w32codecs'. I'm not sure how but it's worked, for Kaffine anyway, I can confirm that my region 1 and 2 DVDs are now playing! I saved the log just in case.

---

### Post by GG_HTPC on 2007-07-05
403 Permission Denied can be overriden by executing a command with 'sudo' (executed as root) that's what you did to install the libcss

Have fun:KS

---

### Post by simtaalo on 2008-07-13
Edit

---

### Post by eldragon on 2008-07-13
there are 2 types of region protection schemes.

RPC1, is the one handled by the OS. as you may imagine, linux doesnt force any region on your player.

RPC2, is the one handled by the dvd-rom firmware. and thus, its OS independant. thats the one you need to get rid of.

there are several alternate firmwares that will make your dvdrom RPC1 instead of RPC2 (which is how manufacturers sell them). but they might brick your device, so be wary of what you are doing.

i would buy a cheap LG burner for which im sure i will be able to patch the firmware, and rip the content of the discs with it. making the newly created iso, region free.

heres a nice resource: [http://tdb.rpc1.org/](http://tdb.rpc1.org/)

---

