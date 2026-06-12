---
title: "Flickery compiz with opensource radeon driver"
date: 2010-09-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ljrmorgan on 2010-09-06
Hi,

I've just upgraded from Lucid to Maverick and my screen has started flickering when I switch desktops or use the cube plugin. The display only flickers during the change of desktops, not after.

Everything worked under lucid, and I did a straight update, I haven't changed any settings since then. I also haven't done any partial upgrades or anything like that.

I have an ATI X800XL PCIe card using the open source radeon drivers. I've got something resembling a screen shot, attached below.

Is anyone else having similar problems? Any suggestions about where the problem lies/where to file bugs/how to fix this?

Thanks,

Louis

---

### Post by ranch hand on 2010-09-06
You can probably fix it easily by waiting for the Final Release in October.  May work out before that.

Keep update/upgrading.

---

### Post by 23meg on 2010-09-06
> **ranch hand said:**
> You can probably fix it easily by waiting for the Final Release in October.  May work out before that.

Keep update/upgrading.

That's a really unhelpful reply. The OP is clearly asking how they can troubleshoot and help fix the problem (which is the main point of running Maverick in the first place), and you're doing the exact opposite of what is to be expected in a testing assistance forum: advising them to passively wait for the final release, where it may or may not be fixed.

[QUOTE=ljrmorgan]Is anyone else having similar problems? Any suggestions about where the problem lies/where to file bugs/how to fix this?[/QUOTE]

[https://wiki.ubuntu.com/X/Debugging](https://wiki.ubuntu.com/X/Debugging) is a good place to start with X driver related issues in general. Also do a bug search at [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/) for your graphics adapter model and relevant keywords to see if there's an existing bug report. You can also get further help at the #ubuntu-bugs and #ubuntu-x channels on irc.freenode net.

---

### Post by andrewthomas on 2010-09-06
Are you using the xorg-edgers ppa?

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

I have both a radeon 3870 and a 2600 and they both work flawlessly.

---

### Post by ljrmorgan on 2010-09-06
> **andrewthomas said:**
> Are you using the xorg-edgers ppa?

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

I have both a radeon 3870 and a 2600 and they both work flawlessly.

Thanks for the tip, I added the PPA and upgraded everything and the flicker was gone after a restart.

Marking as solved.

---

### Post by andrewthomas on 2010-09-06
glad to be of help.

---

