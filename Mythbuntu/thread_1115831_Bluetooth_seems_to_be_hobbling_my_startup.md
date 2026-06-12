---
title: "Bluetooth seems to be hobbling my startup"
date: 2009-04-04
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-04-04
Hi Folks

I'm running Mythbuntu 8.10, which mainly works OK when it's started. Trouble is, it often fails to boot properly. As far as I can tell, it is trying to do something with Bluetooth at the part of the startup procedure where it fails. I've posted some log files of this previously ([http://ubuntuforums.org/showthread.php?t=1070915](http://ubuntuforums.org/showthread.php?t=1070915)).

I have no Bluetooth kit and am not planning to use any in the foreseeable future. Should it be possible to solve this problem simply by disabling Bluetooth? If so, how can I do that?

Many thanks
NM

---

### Post by ajgreeny on 2009-04-04
Install bum (boot-up-manager) and then when you run that you can disable bluetooth.  Problem over.

You may also find that you can disable a few other things, but be careful or you could make more problems for yourself.  I stopped acpi-support, apmd, laptop-mode and hotkey-setup, but these are things I know I don't need or want,  (I have a desktop computer).

---

### Post by NautiusMaximus on 2009-04-05
Many thanks for that, that's exactly what I needed. I've installed BUM, disabled Bluetooth, and it seems to be starting up OK now.

I can't be absolutely sure I've fixed it, as it was only an intermittent problem in the first place, but I've just rebooted about half a dozen or so times and it got there every time (albeit rather slowly one time), so things are looking good so far.

---

### Post by ajgreeny on 2009-04-05
One other thing you can do which might make a small difference, is profile your boot-up.  At the grub menu, choose the ubuntu you want to boot and hit "e" then go to the kernel line and hit "e" again.  Add the word profile after the words "quiet splash" so you end up with "quiet splash profile".  Now press enter to accept the edit and then "b" to boot.  That boot up will be slow but subsequent boots may just be a bit faster.  The edit will only affect that boot up, not future ones, as you have not changed your menu.lst file.

---

