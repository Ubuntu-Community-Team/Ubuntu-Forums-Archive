---
title: "Remmina won't connect completely without sudo"
date: 2013-03-25
forum: Networking &amp; Wireless
---

### Post by QuaintRealist on 2013-03-25
I've had this problem since 12.04.  Currently running 13.04 nightly with same issue.  Remmina is current (correct) version for Ubuntu, connecting to Windows 2008 server.  Gnome remote desktop works (and has worked since 11.04), but lacks functionality.

Remmina runs and works correctly if started from command line with sudo.  When run from launcher or run from command line without sudo, it connects and authenticates, but hangs at "configuring your desktop" screen on windows server.

I've tried purge/reinstall under 12.04 and 13.04 without success.  Frankly, I thought it was a 12.04 issue (could not use 12.10 due to video driver issues on my lenovo X100e).

Web searches for similar issue found one instance of the same problem.  The advice was to check for correct/current build of Remmina.

Thank you in advance for any help!

---

### Post by QuaintRealist on 2013-03-25
Not sure if it adds anything, but attaching a copy of the terminal output with (successful) Remmina session using sudo

Remmina plugin VNC (type=Protocol) registered.
Remmina plugin VNCI (type=Protocol) registered.
Remmina plugin RDP (type=Protocol) registered.
Remmina plugin RDPF (type=File) registered.
Remmina plugin RDPS (type=Preference) registered.
Remmina plugin SFTP (type=Protocol) registered.
Remmina plugin SSH (type=Protocol) registered.

(remmina:2553): IBUS-WARNING **: The owner of /home/**(user name is here)**/.config/ibus/bus is not root!

hope this is of help

---

### Post by QuaintRealist on 2013-03-26
Last shameful self-bump, then I'll let this die in peace.

I presume there have to be permission issues involved, since sudo works.  I'd be more than willing to make adjustments with chmod to try to get this to work correctly, but don't want to fly blind with permissions on any sort of remote protocol.  I'm hoping for some insight into which file(s) might be causing the hang.  If this is a one-off problem with no broadly applicable solution then, well, I understand.

Any suggestions?

---

### Post by steeldriver on 2013-03-26
I don't know what to suggest - it works without sudo for me from 12.04 to a Win7 box, the only thing I can think is that maybe if you used 'sudo' one time something in your ~/.remmina dir (or perhaps the dir itself) has got screwed up (root) ownership / permissions which is then preventing new non-sudo sessions from starting - kind of like the remmina equivalent of the root-owned .Xauthority issue that comes up a lot

```

steeldriver@lap-t61p:~$ ls -al ~/.remmina
total 24
drwx------  2 steeldriver steeldriver 4096 Mar 26 20:34 .
drwxr-xr-x 54 steeldriver steeldriver 4096 Mar 24 16:10 ..
-rw-rw-r--  1 steeldriver steeldriver  388 Sep 18  2012 1347941048650.remmina
-rw-rw-r--  1 steeldriver steeldriver  372 Mar 26 20:33 1360849076676.remmina
-rw-rw-r--  1 steeldriver steeldriver  380 Feb 20 19:14 1361405580852.remmina
-rw-rw-r--  1 steeldriver steeldriver 1013 Mar 26 20:34 remmina.pref
steeldriver@lap-t61p:~$

```

---

### Post by QuaintRealist on 2013-03-26
Thanks for the reply, steeldriver.  Posting the output from this side.

total 16
drwx------  2 pete pete 4096 Mar 26 19:14 .
drwxr-xr-x 25 pete pete 4096 Mar 26 20:07 ..
-rw-r--r--  1 root root  443 Mar 26 15:46 1364221633496.remmina
-rw-r--r--  1 root root 1429 Mar 26 19:14 remmina.pref

This problem occurred long before I tried running remmina with sudo, and occurred with stock 12.04 build, but I note that two files have different permissions than yours.  Would you suggest chmod permissions on either?

---

