---
title: "White Screen instead of desktop in 10.10 (Radeon 7500 card)"
date: 2010-10-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ubanksy on 2010-10-03
I have upgraded an IBM T41 laptop from UNR 10.04 to 10.10 beta. Upgrade ran fine.

After rebooting, I see the splash screen, and eventually the screen goes white. It does this over a few transitions, most likely in the time between X starting and having the desktop loading (I have auto logon enabled).

Once it is all white, I can Ctrl-Alt-F1 to the terminal. Since then I have disabled auto login but same result. I have also removed Unity (I use UNR and the T41 doesn't have a 3d graphics card), and have the same white screen.

Only after removing xserver-xorg-video-radeon, can I get to the Ubuntu Desktop (in 16 colour glory).

The Thinkpad T41 has a Radeon Mobility 7500 in it, and ran fine in UNR 10.04 (which is also a different kernel).

There was no xorg.conf in use (although I have added one during testing and forced the radeon driver to load) and I reviewed xorg log but didn't see anything.

Any ideas on how to get X working properly again?

[This was originally wrongly posted to "Installation & Upgrades" forum, moving conversation to here]

---

### Post by tanari on 2010-10-04
the same with radeon 5750

I don't know how to make correct bugreport...

---

### Post by ubanksy on 2010-10-04
Apparently this is a known issue with a resolution - I just can't find it (in forums or in launchpad).  I was told in my original post that if I "check the Maverick Development forum and do a search on ATI, you will find a post dealing with radeon-driver problems that also contains a fix." however my search skills didn't return a resolution.  

I'll update this if I work it out.

---

### Post by VMC on 2010-10-04
What I did to fix my rather old ATI was to add "radeon.modeset=0" on the linux line.

From grub menu, push 'e' then find "linux" line , and add at the end of the line.

Also, I added "xforcevesa", but that was unneeded to fix my "white screen"

---

### Post by crjackson on 2010-10-04
Have a look at this [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/643118") and try some of the workarounds.  Perhaps you can help to squash [this bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/643118").

---

### Post by ubanksy on 2010-10-05
> **VMC said:**
> What I did to fix my rather old ATI was to add "radeon.modeset=0" on the linux line.

From grub menu, push 'e' then find "linux" line , and add at the end of the line.



Thanks!  This worked for me.  My line had "radeon.modeset=1", so I changed it to "radeon.modeset=0" and pressed Ctrl-X and it booted fine.  I couldn't work out how to save these changes on that screen, so I edited /etc/default/grub to look like this

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.modeset=0"
```

and then ran 

```
sudo update-grub
```

It's looking great now - thanks again.

---

### Post by tormod on 2010-10-05
Please report these issues in separate bug reports. The easiest way is
```
ubuntu-bug xserver-xorg-video-ati
```
(for ATI cards). Then add in the bug report that it works fine without KMS (radeon.modeset=0 kernel option disables Kernel ModeSetting). It **should** work out of the box without having to add such options, and one day this option will go away, so you better make sure it will be fixed properly.

---

### Post by ubanksy on 2010-10-05
OK have done.  Bug [#655099]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/655099") created

---

