---
title: "ATI reverts to Mesa after Log Out"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by TheMaxxus on 2007-08-16
I have setup the official ATI driver and fglrxinfo gives:

[INDENT]maxxus@maxxus-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6747 (8.40.4)[/INDENT]

After a Log Out fglrxinfo gives:

[INDENT]maxxus@maxxus-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)[/INDENT]

If I use the ALT+CTRL+Backspace to restart the gdm, and thus avoid using the Log Out funtion and log back in the driver doesn't revert.  The restart button on the case works too, but I have to wait for the system to boot back up.

---

### Post by Paul133 on 2007-08-17
The same thing has happened to me. System -> Administration -> Restricted Drivers Manager reports that the restricted ATI driver is enabled and in use but fglrxinfo gives me the mesa driver. Furthermore, my /etc/X11/xorg.conf file reports

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card""

```

where it used to list my ATI graphic card name. Very weird, but I still have acceleration, including Compiz Fusion, so I'm not complaining. THe only difference I've noticed is the change in my xorg.conf and in fglrxinfo.

---

### Post by TheMaxxus on 2007-08-21
Unfortunatly, I don't still have acceleration.  I just reinstalled the OS and installed the ATI driver to see if starting clean would fix the problem but it doesn't.  What happens only during Log Off that would affect my video driver?

---

### Post by TheMaxxus on 2007-08-21
Okay the answer to my problem is that the new xorg uses AIGLX by default with the proprietary drivers don't support yet.  So, if you add this to your xorg.conf it will fix the problem:

[INDENT]Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection[/INDENT]

---

### Post by lhardyl on 2008-02-18
Hmm tried the server flag thing but that didnt work :(

---

