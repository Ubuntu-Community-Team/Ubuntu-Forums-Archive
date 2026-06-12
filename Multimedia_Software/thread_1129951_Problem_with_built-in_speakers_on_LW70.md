---
title: "Problem with built-in speakers on LW70"
date: 2009-04-19
forum: Multimedia Software
---

### Post by SciB6y on 2009-04-19
I have a LG LW70 laptop and have just installed Jaunty jackalope (9.04 RC1) and first of all, on this machine you must blacklist the "pcspkr" driver to have it not crash whenever the computer wants to beep (like when you press backspace once too many in a dialog or in a terminal window).

Secondly, just like in 8.10, the internal speakers do not work out of the box, but sound works in the headphones output. The fix that used to work was to add "options snd-hda-intel model=minimal" to the alsa-base-file. But that file is now a alsa-base.conf and has a lot of code in it and adding that line to this file does not seem to work.

Has anyone got any ideas why the "model=minimal" doesn't seem to have any effect? Is there another configuration-file I should put driver options into? Because it doesn't seem to matter which option I add, it makes no difference.

---

### Post by chrisewcs on 2009-05-09
edit
/etc/modprobe.d/alsa-base.conf
# Prevent abnormal drivers from grabbing index 0
options snd-hda-intel model=minimal

and also edit
/etc/init.d/alsa-utils
before
# Required for HDA Intel (hda-intel):
    unmute_and_set_level "Front" "80%"
after
# Required for HDA Intel (hda-intel):
    unmute_and_set_level "Front" "70%"
and
before
# HDA-Intel w/ "Digital" capture mixer (See Ubuntu #193823)
    unmute_and_set_level "Digital" "80%"
after
# HDA-Intel w/ "Digital" capture mixer (See Ubuntu #193823)
    unmute_and_set_level "Digital" "70%"
reboot

hope this helps you

Chris on LG LW70
it helps me fine :razz:

---

