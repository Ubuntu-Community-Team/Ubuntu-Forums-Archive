---
title: "TVT3 Dual TV Tuner"
date: 2011-08-24
forum: Multimedia Software
---

### Post by expphoto on 2011-08-24
Okay, I've Googled myself silly and I cannot find a dang thing on how to install.

I've got a Dell Dimension 4700 with the Emuzed TVT3 Dual TV Tuner, and I've dual booted with Mythbuntu for use with MythTV. Though I have been unable to find any way to install the capture card.

I have gone into the settings (and even after reading the wiki), I'm not 100% sure what to select. Not to mention, where it says probed, it shows failed to load.

Anyone have any advice?

---

### Post by bance on 2011-08-24
Is this card a dvb card ?

Have you checked the video for linux (V4L) website for support ?

Have you got it to work with another application E.G. mplayer first ?

Does your system recognise the card ?

---

### Post by expphoto on 2011-08-26
> **bance said:**
> Is this card a dvb card ?

Have you checked the video for linux (V4L) website for support ?

Have you got it to work with another application E.G. mplayer first ?

Does your system recognise the card ?

That's what I'm kind of curious about. V4L has nothing listed that I found helpful. I can't tell if it recognizes it, I'm pretty sure no, since when I go to add a capture card, nothing shows up. :-/

What's a good application to use to configure the card?

---

### Post by thewolfman on 2011-08-27
Install the "Medibuntu repo" if you haven't already:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then install the package "linux-firmware-nonfree" and also "dvb-apps" if it is a DVB device. I would also install "kaffeine".

Hope this helps.

Regards thewolfman:P

---

### Post by expphoto on 2011-08-27
> **thewolfman said:**
> Install the "Medibuntu repo" if you haven't already:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then install the package "linux-firmware-nonfree" and also "dvb-apps" if it is a DVB device. I would also install "kaffeine".

Hope this helps.

Regards thewolfman:P

Thanks :-D 

Haha. Argh. Why does it have to be so confusing? Im tempted to just buy a tuner that's plug and play. Just sucks. There are no straightforward and definitive configuration tools that I see. And the wikis are confusing.

---

