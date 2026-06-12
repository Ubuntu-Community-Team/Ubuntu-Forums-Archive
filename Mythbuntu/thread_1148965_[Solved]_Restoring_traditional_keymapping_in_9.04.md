---
title: "[Solved]: Restoring traditional keymapping in 9.04"
date: 2009-05-04
forum: Mythbuntu
---

### Post by klc5555 on 2009-05-04
Upgrading (via clean install) my 7.10 master BE/FE to 9.04, I was surprised how smoothly the process went (after the usual inevitable Grub Error 2's).

But I used a Snapstream mini-Firefly as the remote on this machine in 7.10, which remote's extra keycodes would be loaded from a text file by xmodmap as a startup application in X. I was surprised to find this couldn't be done in 9.04: xmodmap keymappings are ignored by the X server.

It turns out this is a by-product of the new feature "input hotplugging" incorporated into current-ish versions of X.

For those who don't require "input hotplugging", this feature may be turned off by adding Option "AutoAddDevices"  "False" to the section "ServerFlags" in the /etc/X11/xorg.conf file, i.e.:

Section "ServerFlags"
  Option "AutoAddDevices" "False"
EndSection


After restarting X (logoff, or Control-Alt-Backspace if you've reenabled it) xmodmap should now work normally _from a terminal_ and should add keymaps from a standard text file.

However, at least on my 9.04 installation, the bare command "xmodmap /[path]/keys.txt" still will not function and add my keymappings when added to the startup programs in "Session and Startup", the way it used to in 7.10. The reenabled xmodmap in 9.04 seems to require a terminal.

But adding a terminal for xmodmap to the X startup programs is simple enough. Using the command:

xterm -e  xmodmap /[my path]/keys.txt  

instead of the bare xmodmap in "Sessions and Startup" works for me --the mappings autoload, and the mini-Firefly remote is enabled. 

Hope this helps someone.

Cheers!

---

