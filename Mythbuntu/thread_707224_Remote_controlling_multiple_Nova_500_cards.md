---
title: "Remote controlling multiple Nova 500 cards?"
date: 2008-02-25
forum: Mythbuntu
---

### Post by stevanbt on 2008-02-25
Hi,
I've recently re-built our mythtv box (using Mythbuntu this time).  I have installed a Hauppauge Nova 500 card and remote control - all is well.  I have another Nova 500 card (both cards used to exist happily in our old box, but I didn't bother installing the remote control).

Has anyone installed two Nova 500 cards AND managed to get the remote control to work?  If so were there any problems?  I can't make my mind up if it will or not... 

I know I could just install it and see, but I won't be happy if I break the box as it's running without any issues.

Thanks in advance, Steve.

---

### Post by Nikas on 2008-02-25
It should work. Just use one of the ir cables that comes with the cards. The cards will get two different inputs but you just have to use one.

I have two in my server but i'm using my home made serial receiver but there should be no problems with the built in.



[   38.058855] input: IR-receiver inside an USB DVB receiver as /class/input/input3
[   36.821024] input: IR-receiver inside an USB DVB receiver as /class/input/input2

Just use one of them with lirc.

---

