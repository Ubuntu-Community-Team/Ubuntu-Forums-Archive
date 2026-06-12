---
title: "Solved: Dell 1501 amd64 won't Shutdown after fglrx install."
date: 2007-10-04
forum: Multimedia &amp; Video
---

### Post by sqlpython on 2007-10-04
After I installed ATI fglrx on my Del 1501 amd64 it would not Reboot/Shutdown/Logout.. 
I am running Feisty 7.04 AMD64 kenel..
Here is my fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8)

Here is what I did to fix the Problem. I hope it helps someone else.

******************
** These 3 steps correct/allow per KDE GUI Logout/Reboot/Shutdown

# Kubuntu 7.04 amd64 w/ ATI fglrx Installed
# Now Won't Shutdown w/ KDE GUI Log Out
# The fix 3 Steps
#
1.. Modify GRUB's menu.lst
#
/boot/grub/menu.lst
add to kernel line acpi=force
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=a8862269-c6ee-4525-bb66-94f53824fdc1 ro quiet splash acpi=force
#
2.. Change KDE Session Manager
#
Also K > Settings > KDE Components > Session Manager
Change [Default Shutdown Option] to (X) Turn Off Computer
#
3.. Modify kdmrc
# /etc/kd3/kdm/kdmrc
# ADD to Section
#[X-*-Core]
TerminateServer=true
************************
Th-The Th-The Th-The That's All Folks! (C) Looney Tunes

---

