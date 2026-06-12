---
title: "alter lirc configuration"
date: 2009-02-06
forum: Multimedia Software
---

### Post by mthaddon on 2009-02-06
Hi Folks,

I have a Pinnacle PCTV mini remote. It seems to be detected and work (mostly) fine, but some of the buttons don't work. For instance, the Play/Pause button isn't recognised (this is based on using Mythbuntu's GUI for setting key mappings).

Looking in /etc/lircd/lircd.conf I see that it is working off /usr/share/lirc/remotes/pinnacle_systems/lircd.conf.pctv and looking in that file I see a bunch of mappings for actions to keycodes in the following format:

          Mute                     0xB53C
          Power                    0x2D2F
          Chan+Play                0x173F
          Chan-Stop                0xC63E
          Vol+FF                   0xF13B
          Vol-Rew                  0x643D

If I run "xev" from a console and then push the Play/Pause button I get the following:

KeyPress event, serial 34, synthetic NO, window 0x2e00001,
    root 0x13b, subw 0x0, time 182862165, (-171,59), root:(252,377),
    state 0x0, keycode 172 (keysym 0x1008ff14, XF86AudioPlay), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

I'm not really sure how to map that output to the format in lircd.conf.pctv. Anyone able to help out?

Cheers, Tom

---

