---
title: "missing x extensions"
date: 2008-06-29
forum: Multimedia Software
---

### Post by peterroots on 2008-06-29
Kubuntu8.04 with nvidia driver installed.
When I tried to set up a dual monitor the nvidia settings program reported I was lacking x extensions.
I get this
peter@Peter:~$ xrandr -q
Xlib:  extension "RANDR" missing on display ":0.0".
RandR extension missing

looking in adept I seem to have  libxrandr-dev libxrandr2 and x11proto-randr-dev installed. I tried installing libxcb-randr0 but this made no difference so I uninstalled it again.
running krandrtray loads the applet but it has a grayed out 'required x extensions not available.

I have set a virtual screen in my xorg.conf file under section screen subsection display

anyone any idea which x extensions I am missing, why, and where do I get them from?

---

