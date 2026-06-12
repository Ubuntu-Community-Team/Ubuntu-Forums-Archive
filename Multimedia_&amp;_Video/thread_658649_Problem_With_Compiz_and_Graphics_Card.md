---
title: "Problem With Compiz and Graphics Card"
date: 2008-01-04
forum: Multimedia &amp; Video
---

### Post by ademel on 2008-01-04
Hi. When I try to run compiz, it tells me "Desktop Effects Could Not Be Enabled." I have a Sony Vaio VGN-CR190 laptop and the graphics card I am using is:

VGA Compatible Controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
PCI ID: 8086:2a02

As per advice elsewhere on the forum, I am running the fglrx drivers and have enabled xserver-xgl. However, this still has not made compiz work. When I type compiz into terminal, this is what I get:

Checking for Xgl: present.
Checking for nVidia: not present.
Checking for Xgl: present.
Enabling Xgl with fglrx ATi drivers. . .
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: no manageable screens found on display :1.0

Unfortunately, I am a complete linux newbie and don't really know what to make of this. Ideas? Any help is greatly appreciated.

---

### Post by Yellow Pasque on 2008-01-05
fglrx is for ATI video cards, not intel integrated video. Uninstall it before doing anything else.

---

### Post by moeFinley on 2008-01-06
I have the same graphics card and when I try to run Compiz I'm told the I have a blacklist PCIID and it aborts?

---

### Post by Yellow Pasque on 2008-01-06
> **moeFinley said:**
> I have the same graphics card and when I try to run Compiz I'm told the I have a blacklist PCIID and it aborts?

The last I heard, Intel's X3k-series video controllers had problems with Compiz, which is why they're blacklisted. You can try to remove that restriction by doing a sudo gedit usr/compiz/bin and putting a '#' in front of this line: T="$T 8086:2972" # i965 (x3000)  It's line number 61 in my file.

---

