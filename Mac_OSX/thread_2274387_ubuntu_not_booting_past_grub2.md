---
title: "ubuntu not booting past grub2"
date: 2015-04-20
forum: Mac OSX
---

### Post by dhawk3122 on 2015-04-20
[COLOR=#111111][FONT=Ubuntu]I installed Ubuntu on my 2012 Macbook Air. Everything worked well, no issues with dual booting Yosemite and Ubuntu. Then I did a software update and could not longer boot into Ubuntu. Instead each boot gets stuck on the Grub2 black cli screen. I can boot into Ubuntu if I type exit then let the system reboot then type exit again. How can I fix this so the Grub correctly boots Ubuntu without this hassle?

This is what I see when I boot into my Ubuntu partition:

Gnu Grub Version 2.02-beta2[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Minimal Bash like editing is supported for the first word TAB list possible command completions. Anywhere else TAB lists Possible device or file completions.[/FONT][/COLOR]

---

### Post by dino99 on 2015-04-20
Looks like something is borked into the grub config; reinstall it
sudo apt-get install --reinstall grub-pc

---

### Post by oldfred on 2015-04-20
Moved to Apple sub-forum since a Mac.

Is system installed in UEFI boot mode? I thought Mac used UEFI, but not familiar with all the versions.
Then reinstall may not be grub-pc but grub-efi-amd64.

[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

---

### Post by dhawk3122 on 2015-04-20
[COLOR=#000000]grub-efi-amd64 is installed. I will reinstall it and see if that helps. [/COLOR]

---

