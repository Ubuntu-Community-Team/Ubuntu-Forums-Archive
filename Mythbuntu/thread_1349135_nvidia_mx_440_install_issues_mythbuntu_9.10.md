---
title: "nvidia mx 440 install issues mythbuntu 9.10"
date: 2009-12-07
forum: Mythbuntu
---

### Post by compudude86 on 2009-12-07
hello,
I installed mythbuntu on my computer, via livecd, and for some reason it wont function with my nvidia mx440 dvi-tvout card. I have my sanyo vizon 26 inch tv hooked to the DVI of the card with my HDMI-DVI converter, and on the HDMI port specified for such conversion. I got it to display by using open source driver, but it is horribly overscanned, missing a few inches on each side. when I reinstall with nvidia driver, the screen flickers rapidly after reboot and then goes to terminal, no X. any advice?

---

### Post by SiHa on 2009-12-09
> **compudude86 said:**
> hello,
I installed mythbuntu on my computer, via livecd, and for some reason it wont function with my nvidia mx440 dvi-tvout card. I have my sanyo vizon 26 inch tv hooked to the DVI of the card with my HDMI-DVI converter, and on the HDMI port specified for such conversion. I got it to display by using open source driver, but it is horribly overscanned, missing a few inches on each side. when I reinstall with nvidia driver, the screen flickers rapidly after reboot and then goes to terminal, no X. any advice?

Have a look at [[COLOR="Blue"]_this_[/COLOR]](http://ubuntuforums.org/showthread.php?t=1335114&highlight=flickering) thread, seems you might have the same problem.

BTW, you will probably find you get overscan whatever driver you use, it's a 'feature' on most TV's - a hang-over from analogue days. You can either try and turn it off via the TV service menu, or use the screen setup wizard in the frontend (Settings -> TV Settings -> Appearance) to reduce the Mythtv GUI to within the visible portion of the screen.

Failing that, if you **really** want to see the whole desktop, you could try connecting with VGA if the set supports it, that shouldn't have overscan.

---

### Post by Entropy512 on 2009-12-09
The MX440 is in the category of what Nvidia calls "legacy" cards not supported by their current drivers.  Not sure how Ubuntu handles installation of the Nvidia "legacy" drivers.  For an MX440, you need the 96.43.14 drivers.

The MX440 is an ANCIENT card.

---

