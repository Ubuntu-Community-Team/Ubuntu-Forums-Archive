---
title: "gnome-terminal-3.44.1; Edit--&gt;Select All selects only part of its output"
date: 2022-12-14
forum: MINT
---

### Post by MIJ-VI on 2022-12-14
EDIT: Sat. 17 Dec. 2022

I've ruled out gnome-terminal-3.44.1 as being the cause of the issue described in this post.

Using grml-rescueboot to boot into the linuxmint-20.3-cinnamon-64bit-edge.iso, I tested '20,3's gnome-terminal 3.36.2 by running dmesg in order to obtain a lengthy Terminal output and then choosing Edit-->Select All which did indeed select all of said output.

Next, I booted into the linuxmint-21-cinnamon-64bit.iso and tested the Edit-->Select All function of its gnome-terminal-3.44.1. Like all previous efforts indicated below, it only selected the final 20 lines or so of the output while leaving rest unselected.

So, I booted into my Linux Mint 21 Cinnamon install, downloaded gnome-terminal_3.36.2-1ubuntu1~20.04_amd64.deb and gnome-terminal-data_3.36.2-1ubuntu1~20.04_all.deb from Ubuntu's web site.

Then, after using Synaptic Package Manager to uninstall gnome-terminal-3.44.1 and doing a reboot, I used gdebi to install gnome-terminal_3.36.2 etc.

Finally, I once again ran dmesg followed by Edit-->Select All. The result? The* very same* problem occurred as many times before: Only the final 20 lines or so of the output were selected while leaving rest unselected.

gnome-terminal-3.44.1 ls not broken. Something else is at a deeper level. But what?

========

Hi.

For years the stock Terminal that came with Linux Mint Cinnamon allowed me to Edit-->Select All in order to copy the Terminal's entire output for pasting into a text file.

Does anyone here know how to fix gnome-terminal-3.44.1 so that Edit-->Select All works as it should?

gnome-terminal-3.44.1's Preferences offer neither clue nor remedy.

FTR, I tried mate-terminal. It has the same issue as gnome-terminal-3.44.1. Specifically: Edit-->Select All only selects part of the Terminal output instead of the whole thing. Something else is going on. But what?

Please note:

I'm posting to this forum because gnome-terminal-3.44.1 is part of the Ubuntu 22.04 LTS package base that Linux Mint 21 Cinnamon is built on.

Thank you.

---

