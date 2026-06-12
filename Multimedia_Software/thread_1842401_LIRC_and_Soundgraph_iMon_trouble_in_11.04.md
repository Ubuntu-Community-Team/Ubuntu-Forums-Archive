---
title: "LIRC and Soundgraph iMon trouble in 11.04"
date: 2011-09-11
forum: Multimedia Software
---

### Post by selectedusername on 2011-09-11
Hi guys,

I'm currently having some trouble with my iMon Pad VFD/IR setup. After initial installation of LIRC from the package repositories some of the buttons on my remote works (eg. volume up/down). I can not, however, get all buttons to work on the remote. In irw the answer is ^[[D, ^[[B, ^[[C and ^[[D when I press on the "PAD" suggesting that I'm using the remote control as a keyboard. None of the other buttons are working. How can I get the remote to work with MythTV and remap the buttons to suit my setup?

I'm runing lirc 0.8.7 and kernel 2.6.38-11.

Please let me know I you need more information to be able to help!

Thanks in advance
/Thomas

---

### Post by cyberwizzard on 2011-11-06
I have the same issue in 11.10.

Using 'showkey' I can see that the remote buttons are actually mapped but it seems they no longer are assigned to the key codes like KEY_PAGEUP or KEY_PREVIOUS; only a small subset of keys on the remote work...

Is there a key mapping table somewhere? (hopefully outside the kernel module?)

---

### Post by jwhiteIT on 2012-07-16
I see this is an older post, I have the same thing on 12.04.  Just wondering of you solved it?

---

### Post by wildmanne39 on 2012-07-17
Hi, this is an old thread so it is being closed, please start a new thread.
Thanks

---

