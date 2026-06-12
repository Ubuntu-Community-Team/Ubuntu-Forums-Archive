---
title: "Firefox, mplayer, crash"
date: 2008-06-24
forum: Multimedia Software
---

### Post by paul.reloaded on 2008-06-24
Hi.
When I visit [www.ct24.cz](www.ct24.cz) I can watch video on the page. But when I try to click on some link pointing to other video, firefox crashes with:

The program 'firefox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 29359 error_code 3 request_code 10 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7fc3767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7fc381e]
#2 /usr/lib/libX11.so.6 [0xb6b1e518]
#3 /usr/lib/libX11.so.6(XFreeCursor+0x25) [0xb6afa8f5]
#4 /usr/lib/libqt-mt.so.3(_ZN11QCursorDataD1Ev+0x3f) [0xb5571389]
#5 /usr/lib/libqt-mt.so.3(_ZN7QCursorD1Ev+0x5a) [0xb557158e]
#6 /usr/lib/libqt-mt.so.3 [0xb55715d5]
#7 /lib/tls/i686/cmov/libc.so.6(exit+0xd4) [0xb7d60084]
#8 /usr/lib/libgdk-x11-2.0.so.0 [0xb6704637]
#9 /usr/lib/libX11.so.6(_XError+0xfe) [0xb6b1773e]
#10 /usr/lib/libX11.so.6 [0xb6b1ee5c]
#11 /usr/lib/libX11.so.6(_XReply+0x15a) [0xb6b1f21a]
#12 /usr/lib/libXext.so.6(DPMSCapable+0x99) [0xb65662c9]
#13 /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so(_Z12DPMSReenableP16nsPluginInstance                                                                  +0x6e) [0xaf8671fe]
#14 /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so(_ZN16nsPluginInstance8shutdownEv+0x                                                                  78c) [0xaf86402c]
#15 /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so(_ZN16nsPluginInstance4shutEv+0x58)                                                                   [0xaf864248]
#16 /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so(NPP_Destroy+0x33) [0xaf8669e3]
#17 /usr/lib/xulrunner-1.9/libxul.so [0xb777a129]
#18 /usr/lib/xulrunner-1.9/libxul.so [0xb7326155]
#19 /usr/lib/xulrunner-1.9/libxul.so [0xb7326568]

Does anybody encoutered this?
I have last firefox from repos (3rc2, Kubuntu Hardy).
Thanks.

---

### Post by wolfen69 on 2008-06-24
i see you have mplayer plugin. that's good. but you should remove totem-mozilla first, as they can conflict with each other.```
sudo apt-get remove totem-mozilla
```

---

### Post by paul.reloaded on 2008-06-24
totem-mozilla is not installed (no package with 'totem' in name).

---

