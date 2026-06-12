---
title: "wireless connection keeps on resetting with lucid"
date: 2010-06-11
forum: Networking &amp; Wireless
---

### Post by weyl on 2010-06-11
[SIZE=3]Hi, I'm using Ubuntu 10.04 LTS on a laptop, and am experiencing a similar problem to bug #6417-essentially my wireless connection resets randomly at any given time- the difference being that I am using a more recent os version and different network manager. I tried to patch the file using the old patch associated with the problem using the steps provided in the forum entry here:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/64173](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/64173)

and had the savvy to change the network manager text to 0.8, but I had  a hunk fail entry:

weyl@weyl-laptop:~/network-manager-0.8$ patch p1 <reconnect-timeout.diff
patching file p1
Hunk #1 FAILED at 1.
1 out of 1 hunk FAILED -- saving rejects to file p1.rej
patching file p1
Hunk #1 FAILED at 430.
1 out of 1 hunk FAILED -- saving rejects to file p1.rej
patching file p1
Hunk #1 FAILED at 85.
1 out of 1 hunk FAILED -- saving rejects to file p1.rej
patching file p1
Hunk #1 FAILED at 588.
Hunk #2 FAILED at 623.
2 out of 2 hunks FAILED -- saving rejects to file p1.rej
patching file p1
Hunk #1 FAILED at 2261.
Hunk #2 FAILED at 2312.
2 out of 2 hunks FAILED -- saving rejects to file p1.rej
patching file p1
Hunk #1 FAILED at 407.
Hunk #2 FAILED at 458.
Hunk #3 FAILED at 470.
3 out of 3 hunks FAILED -- saving rejects to file p1.rej
weyl@weyl-laptop:~/network-manager-0.8$ patch  <reconnect-timeout.diff
patching file 16_undefined_macros.patch
Hunk #1 FAILED at 1.
1 out of 1 hunk FAILED -- saving rejects to file 16_undefined_macros.patch.rej
patching file NetworkManager.c
Hunk #1 FAILED at 430.
1 out of 1 hunk FAILED -- saving rejects to file NetworkManager.c.rej
patching file NetworkManagerMain.h
Hunk #1 FAILED at 85.
1 out of 1 hunk FAILED -- saving rejects to file NetworkManagerMain.h.rej
patching file nm-dbus-nm.c
Hunk #1 FAILED at 588.
Hunk #2 FAILED at 623.
2 out of 2 hunks FAILED -- saving rejects to file nm-dbus-nm.c.rej
patching file nm-device-802-11-wireless.c
Hunk #1 FAILED at 2261.
Hunk #2 FAILED at 2312.
2 out of 2 hunks FAILED -- saving rejects to file nm-device-802-11-wireless.c.rej
patching file nm-tool.c
Hunk #1 FAILED at 407.
Hunk #2 FAILED at 458.
Hunk #3 FAILED at 470.
3 out of 3 hunks FAILED -- saving rejects to file nm-tool.c.rej
weyl@weyl-laptop:~/network-manager-0.8$ patch --ignore-whitespace <reconnect-timeout.diff
patching file 16_undefined_macros.patch
Hunk #1 FAILED at 1.
1 out of 1 hunk FAILED -- saving rejects to file 16_undefined_macros.patch.rej
patching file NetworkManager.c
Hunk #1 FAILED at 430.
1 out of 1 hunk FAILED -- saving rejects to file NetworkManager.c.rej
patching file NetworkManagerMain.h
Hunk #1 FAILED at 85.
1 out of 1 hunk FAILED -- saving rejects to file NetworkManagerMain.h.rej
patching file nm-dbus-nm.c
Hunk #1 FAILED at 588.
Hunk #2 FAILED at 623.
2 out of 2 hunks FAILED -- saving rejects to file nm-dbus-nm.c.rej
patching file nm-device-802-11-wireless.c
Hunk #1 FAILED at 2261.
Hunk #2 FAILED at 2312.
2 out of 2 hunks FAILED -- saving rejects to file nm-device-802-11-wireless.c.rej
patching file nm-tool.c
Hunk #1 succeeded at 406 with fuzz 2 (offset -1 lines).
Hunk #2 FAILED at 476.
Hunk #3 FAILED at 488.
2 out of 3 hunks FAILED -- saving rejects to file nm-tool.c.rej
weyl@weyl-laptop:~/network-manager-0.8$ patch  <reconnect-timeout01.diffpatching file NetworkManager.c
Hunk #1 FAILED at 430.
1 out of 1 hunk FAILED -- saving rejects to file NetworkManager.c.rej
patching file NetworkManagerMain.h
Hunk #1 FAILED at 85.
1 out of 1 hunk FAILED -- saving rejects to file NetworkManagerMain.h.rej
patching file nm-dbus-nm.c
Hunk #1 FAILED at 588.
Hunk #2 FAILED at 623.
2 out of 2 hunks FAILED -- saving rejects to file nm-dbus-nm.c.rej
patching file nm-device-802-11-wireless.c
Hunk #1 FAILED at 2261.
Hunk #2 FAILED at 2312.
2 out of 2 hunks FAILED -- saving rejects to file nm-device-802-11-wireless.c.rej
patching file nm-tool.c
Hunk #1 FAILED at 407.
Hunk #2 FAILED at 458.
Hunk #3 FAILED at 470.
3 out of 3 hunks FAILED -- saving rejects to file nm-tool.c.rej
weyl@weyl-laptop:~/network-manager-0.8$ patch  <reconnect-timeout02.diff
patching file 16_undefined_macros.patch

I researched this and found out the problem lies in the fact that the patch is for older software (either in network manager or the os).

Is there any chance that there is a patch out there for Ubuntu 10.04 with the recent Network Manager? Or, does someone have a completely new approach?

As you can tell I am new to linux and shell commands. 





[/SIZE]

---

