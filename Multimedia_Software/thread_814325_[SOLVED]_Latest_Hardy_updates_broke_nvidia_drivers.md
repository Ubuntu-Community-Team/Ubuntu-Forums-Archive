---
title: "[SOLVED] Latest Hardy updates broke nvidia drivers?"
date: 2008-05-31
forum: Multimedia Software
---

### Post by DemonicKyle on 2008-05-31
All:

So I come back home after a week off, and there are a ton of updates to install on Heron.  There are some kernel updates (2.6.24-17-386), and nvidia driver updates.  Not paying much attention, I just said to install them, and rebooted as it suggested.

Aaaaand now I can't get into my desktop.  I get No Signal to my monitor.  I can Ctrl-Alt-F into some terminals to do work, but that's it.  

[LIST]
[*]Tried booting with a different kernel version in Grub, same thing.  
[*]Tried uninstalling/reinstalling Nvidia drivers with EnvyNG, no change.  
[*]Put 'nv nvidia_new' in DISABLED_MODULES in linux-restricted-modules-common.  Didn't help.[/LIST]

I've been scouring these forums for a few hours, but so far, I haven't found anything that'll help.

Any suggestions?  I'm all ears.

Thanks all,

-DK

P.S.:  Oh, in case it's important - I've got an Nvidia GeForce 4 MX 440 APG 8x.

---

### Post by superbiskit on 2008-05-31
Something to check: 
Do all your versions of, e.g., linux-restricted-modules, linux-ubuntu-modules, etc. match (completely!) with your new kernel modules?

I am having the same problem, since Thu, 29 May. following an upgrade that included the kernel. Elsewhere in the fora it was suggested that sometimes the upgrades to the kernel get put up on the archive before the version of the supporting packages.

A month or so ago, the same sort of failure made me back off of using a 2.6.24 kernel (back to 2.6.22).  Now that seems not to help and I'll need to wait for Monday before I can see whether I can resurect my 2.6.22 environment.

---

### Post by DemonicKyle on 2008-05-31
Thanks for your response!

> Do all your versions of, e.g., linux-restricted-modules, linux-ubuntu-modules, etc. match (completely!) with your new kernel modules?

Not exactly sure how to check that - viewing the files didn't reveal version numbers, kernel or otherwise.  I've used Ubuntu for a while now, but system level stuff is still a little hard to wrap my head around.

Any other ideas?

-DK

---

### Post by DemonicKyle on 2008-05-31
Solved!  This thread helped a little bit:

[http://ubuntuforums.org/showthread.php?t=813026](http://ubuntuforums.org/showthread.php?t=813026)

Basically, I went to Nvidia website, downloaded the latest driver for my card.  Then, booted to Recovery Mode, ran the installer.

Said 'yes' a bunch of times to make it do it's thing, it compiled a new kernel binding, and boom - install done.

Typed in 'init 3', and now here I am in my desktop.  

These forums rock.

-DK

---

