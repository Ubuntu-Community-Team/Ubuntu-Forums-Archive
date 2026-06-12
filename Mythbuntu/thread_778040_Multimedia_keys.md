---
title: "Multimedia keys"
date: 2008-05-01
forum: Mythbuntu
---

### Post by whein on 2008-05-01
I followed the instructions from [https://help.ubuntu.com/community/XfceMultimediaKeys?highlight=%28XfceMultimediaKeys%29#124759292487597227](https://help.ubuntu.com/community/XfceMultimediaKeys?highlight=%28XfceMultimediaKeys%29#124759292487597227)
and now some of my keys on my keyboard don't work...  Specifically I've noticed the 'e', 'm' and Enter/Return keys so far...  HELP!!!  :(

How do I reset it back to goodness?  I can ssh into the machine so I can do *some* stuff that requires typing into the command line, but not typing into text boxes (figured that out when I couldn't use the enter key for password dialogs...)

-Will

my .Xmodmap file:
```
keycode 26 = XF86Video
keycode 27 = XF86AudioRecord
keycode 28 = XF86Launch0
keycode 31 = XF86Pictures
keycode 32 = XF86Launch1
keycode 33 = XF86AudioPlay
keycode 36 = XF86Launch2
keycode 41 = XF86Forward
keycode 56 = XF86Back
keycode 58 = XF86Music
keycode 99 = XF86RockerUp
keycode 105 = XF86RockerDown
keycode 144 = XF86AudioNext
keycode 153 = XF86AudioPrev
keycode 160 = XF86AudioMute
keycode 162 = XF86AudioPause
keycode 164 = XF86AudioStop
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 178 = XF86MyComputer

```

---

### Post by whein on 2008-05-02
Ok, I managed to revert it by SSHing in and renaming the .Xmodmap file something else, then rebooting.  Turns out some of the keys the multimedia keyboard used for "media" keys sent the same keycodes as existing keys.  So when I remapped those key codes... grr.  Ah well, that's what I get for going with a no-name brand.  Actually, the name of the company apparently changed between when I placed the order and when it arrived...  Same product as the picture though.  Other than that minor quirk I like it.

As a help to others who find this thread, you can look at the existing mapping by using ```
xmodmap -pke
``` _before_ you mess around.  :)
-Will

---

