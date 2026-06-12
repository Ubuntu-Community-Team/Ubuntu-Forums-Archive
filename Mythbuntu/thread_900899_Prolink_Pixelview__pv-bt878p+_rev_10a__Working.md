---
title: "Prolink Pixelview  pv-bt878p+ rev 10a:  Working?"
date: 2008-08-25
forum: Mythbuntu
---

### Post by antifaithstl on 2008-08-25
Wondering if anyone has got this card working.  In the backend setup it's detected as ***Unknown Generic.  I set it as a V4L card, but all I get is snow.  I also have a Hauppauge PVR-150 that's working great, so I'd love to have 2 cards working (any decent Mythbox needs 2 working cards!)  I set the bttv module to load at startup just to make sure.

So if anyone has gotten this model working I'd love to know what the settings should be set to.  

Here's my dmesg | grep BTTV:

> [   30.657649] bttv: driver version 0.9.17 loaded
[   30.657654] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   31.842457] bttv: Bt8xx card found (0).
[   31.842805] bttv0: Bt878 (rev 17) at 0000:01:08.0, irq: 16, latency: 32, mmio: 0xf7fff000
[   31.843695] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   31.843730] bttv0: gpio: en=00000000, out=00000000 in=002fffff [init]
[   31.856811] bttv0: tuner type unset
[   31.856813] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   31.857364] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   31.857904] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   31.858463] bttv0: registered device video1
[   31.858483] bttv0: registered device vbi1


Here's the relivent sudo lshw:
> e=bttv
        *-multimedia:1 UNCLAIMED
             description: Multimedia controller
             product: Bt878 Audio Capture
             vendor: Brooktree Corporation
             physical id: 8.1
             bus info: pci@0000:01:08.1
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: vpd pm cap_list
             configuration: latency=32 maxlatency=255 mingnt=4

And my lspci:
> 01:08.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:08.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)



Thanks for the help.

EDIT:
W00T!!!  Got it working!  No thanks to YOU GUYS!  (just kidding, I know the post got a lot of looks)
Here's what I did.
After a rediculous amount of googleing, I found this page:
[http://mysettopbox.tv/phpBB2/viewtopic.php?t=11874&highlight=options+bttv+modprobe+conf]("http://mysettopbox.tv/phpBB2/viewtopic.php?t=11874&highlight=options+bttv+modprobe+conf")
A guy w/ the same card.  I couldn't find the right BTTV module settings to ID the card, since the auto-detect didn't work.  He found that the settings that need to be passed to BTTV are:
> card=37 tuner=6
I wrote this in /etc/module.d/bttv
Rebooted & ran the backend setup again.  POOF!  It's working.
Unfourtunetly, this card is one of those cheapies that make you run a 1/8 in. audio cable from the back of the card to the line-in of your sound card.
Does anyone know a way to bypass this?  I doubt it, but maybe there's a way.

---

### Post by antifaithstl on 2008-08-26
bump!

---

### Post by pingeee on 2008-09-24
Hi, 

  I am new to Linux. I just installed Ubuntu 8.4.01 and I have problem detection my bt878p+ too.

   I did probing on dmesg | grep BTTV,sudo lshw,lspci like you did and my system is very similar to yours.

   When you said (quote) "I wrote this in /etc/module.d/bttv", specifically how did you do it? Did you open an existing bttv file and add the parameter or you just create a new txt file titled bttv? I check my etc folder I did not see module.d at all. Should I add all these myself?

    Also, I am in Asia, may I know which tuner type is more appropriate?

Thank you.

---

### Post by Joundill on 2010-02-07
Sorry about posting in such an old thread, but there's a mistake here that could cause problems for newer users.

antifaithstl said that he edited "/etc/module.d/bttv" in fact, what he meant to say was "/etc/modprobe.d/bttv". This is an existing file obtainable via apt.

If you have the same card, the solution is:

```
sudo apt-get install bttv
sudo gedit /etc/modprobe.d/bttv
```

This installs bttv, then opens /etc/modprobe.d/bttv for editing.

Next change the text from "card=X tuner=X", where the Xs will be numbers, assigned by installing bttv, to "card=37 tuner=6"

I hope this helps.

Joundill

---

