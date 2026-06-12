---
title: "How to reinstall aiglx"
date: 2007-02-21
forum: Multimedia &amp; Video
---

### Post by AlMadrid on 2007-02-21
I have a Toshiba Satellite A50 with a Intel video card and Kubuntu Edgy. I know that Edgy comes with aixgl installed but I have unistall it or disable it following a wrong tutorial. I want to reinstall it but I don't know how to do it.

When I start with Kubuntu Live, aiglx works perfect, and so did it when I first installed Kubuntu Edgy.

Please help me. Thanks!

---

### Post by fishwithapipe on 2007-02-22
find the lines

Section "Extensions"
        Option      "Composite" "False"
EndSection

in /etc/X11/xorg.conf and delete or comment them out then restart the X server ctrl-alt-backspace.
goodluck, happy beryling ;)

---

### Post by AlMadrid on 2007-02-22
There aren't those lines in xorg.conf.

I don't think it's a problem about xorg.conf because I have tried to copy xorg.conf after start with Live Kubuntu (in which aiglx works perfect) and use it in my Kubuntu Edgy but nothing changes.

---

### Post by MasterOfDisaster on 2007-02-22
AIGLX is enabled by default in Edgy, as it is included in X Windows.  Unless you have uninstalled X, AIGLX is still installed.  Perhaps you are refering to Compiz/Beryl, the actual applications for a composite desktop?

---

### Post by AlMadrid on 2007-02-23
I am not referering to Compiz/Beryl, just aiglx. When I try to run a program that needs aiglx the following message appears:

"couldn't find matching glx visual"

---

### Post by AlMadrid on 2007-02-27
I answer myself. The problem was that I was installed the nvidia driver for aiglx. I have uninstalled from adept and everything is alright again.

---

