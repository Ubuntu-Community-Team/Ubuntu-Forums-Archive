---
title: "nVidia drivers for ASUS V8200T"
date: 2013-04-10
forum: Multimedia Software
---

### Post by MrProsser on 2013-04-10
I have recently installed lubuntu 12.10 on an old desktop computer that I have but it has been some time since I have used a Linux distro, so I am a bit rusty. The integrated graphics card was pretty terrible so I popped in an ASUS V8200T2 into it, which I believe is based on the GeForce3 Ti200. I tried installing the nVidia drivers based on this guide:
[http://falkvinge.net/2013/02/15/how-to-install-nvidia-drivers-in-ubuntu-12-10-quantal/](http://falkvinge.net/2013/02/15/how-to-install-nvidia-drivers-in-ubuntu-12-10-quantal/)

and while I have video there seems to be a few problems. First, the desktop is strange. The font is very small and the icons are huge:
[ATTACH=CONFIG]241184[/ATTACH]

When I try to open the nVidia X Server settings I get the message:
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

but when I run nvidia-xconfig I get this:
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

but the X server settings still give me the same error after this.

Additionally, when I try to use glxgears I get the error:
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't get an RGB, Double-buffered visual


I am really not sure where to start with debugging this problem, I have no experience dealing with these drivers at all. I know this is rather random but some help would be appreciated.

---

### Post by MrProsser on 2013-04-10
Annnnd I just realized I really should have put this in the Multimedia and Video forum. Should I repost this, or can it just be moved by an admin?

---

### Post by papibe on 2013-04-10
Thread moved to **Multimedia & Video** ;)

---

