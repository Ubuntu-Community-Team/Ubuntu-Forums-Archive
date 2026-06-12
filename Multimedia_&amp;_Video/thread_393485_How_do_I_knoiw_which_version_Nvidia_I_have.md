---
title: "How do I knoiw which version Nvidia I have?"
date: 2007-03-25
forum: Multimedia &amp; Video
---

### Post by glenn69 on 2007-03-25
I am using Xubuntu.

I am pretty sure that I have the nvidia driver running, but not positive.

How do I test that I do, in fact, have nvidia driver running, and how do i determine which version it is?

Thanks

---

### Post by glennzo on 2007-03-25
If Fedora, my primary distro, there is an NVidia control panel in the menu system. Applications > System Tools > NVidia Display Settings. This tells me the version of the NVidia driver that is installed. There's also
[COLOR="Blue"]/usr/bin/nvidia-settings
/usr/sbin/nvidia-config-display
/usr/sbin/nvidia-xconfig[/COLOR]

Maybe you have one or more of these?

Also, [COLOR="Red"]cat /etc/X11/xorg.conf | grep "Driver"[/COLOR] will show you all drivers used in xorg.conf. You should see '[COLOR="Blue"]nvidia[/COLOR]' listed.

---

### Post by glenn69 on 2007-03-25
I ran nvidia-settings and a box displays some nvidia stuff.  The only items diaplsyed are : Enable tool tips, Display status bar, slider text entries, Include X Display names in config file, and show "Really Quit" dialog.

I have seen a similar box in another version of linux and it diaplsyed the version number.  This box does not.

Any more suggestions?

---

### Post by johnc4510 on 2007-03-25
cat /proc/driver/nvidia/version

This will show what you what driver version you have installed. If no driver version showing, it's not installed.

Here is an example of mine:

johnc@Feisty:~$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006

driver version is 1.0-8776

---

### Post by glenn69 on 2007-03-26
Thanks, that was exactly what i needed to know.

---

