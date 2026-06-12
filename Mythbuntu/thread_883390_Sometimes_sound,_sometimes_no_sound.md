---
title: "Sometimes sound, sometimes no sound"
date: 2008-08-07
forum: Mythbuntu
---

### Post by mythms on 2008-08-07
I am passing sound over hdmi from ATI Radeon HD 2400 to hd tv. (Actually SD signal from PVR-3500).  Sometimes the sound works, sometimes it doesn't.  If I 'Esc' back to the menu and return to 'Watch TV' several times in a row.  Sound will eventually come on.

Ideas?

---

### Post by mythms on 2008-08-07
Can ssh into my myth machine and execute the following to turn on the sound:

%> amixer -c 0 sset IEC958 on

The following will turn it back off:

%> amixer -c 0 sset IEC958 off

Anyone know how to issue the 'on' command above when the 'Watch TV' button is pushed?

---

