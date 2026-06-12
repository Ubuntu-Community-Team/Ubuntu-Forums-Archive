---
title: "which live cd for remote maintenance?"
date: 2009-06-25
forum: Mythbuntu
---

### Post by mathog on 2009-06-25
My Mythtv system has only TV-OUT attached, no high res display, keyboard, or mouse. ssh from a remote machine is the only way to administer anything.  Unfortunately mythtv-setup seems to be exceedingly picky about the sort of display it expects.  So far:

1.  knoppix:  mythtv-setup starts but when in the foreground uses horrible and very hard to read colors.  Click elsewhere on the desktop (outside of mythtv-setup) then mythtv-setup is shown in its normal colors.  Only when it is in the foreground, ie, able to accept input, is it unreadable.

2.  slax:  mythtv-setup will not start, it wants some display extension which isn't present (if memory serves, Xrandr).

3.  mandriva 2009.0 one:  like knoppix

When there was a display directly attached mythtv-setup worked properly with Mythbuntu 8.10.

Other X11 programs (xterm, nedit) work fine with all 3 of the live CDs, it is just mythtv-setup which is so very sensitive about the X11 server.  The graphics card on the remote system is an ATI Radeon 9200SE.

What live CD actually works with mythtv-setup over an ssh connection???

---

