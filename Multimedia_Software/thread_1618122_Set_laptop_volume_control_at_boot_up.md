---
title: "Set laptop volume control at boot up?"
date: 2010-11-10
forum: Multimedia Software
---

### Post by mango42 on 2010-11-10
I appreciate this topic has been covered before but could some kind programmer tell me how to set at least my headphone/lineout socket precisely to -15dB at boot up, please? If I knew how to make **amixer** commands permanent, I wouldn't be re-raising the issue :)

The Gnome GUI volume control is fine in normal circumstances but to set it accurately requires a bit too much fiddling, IMO - now if someone were to adjust the programming so a dB readout *accompanies* slider movement, rather than as a pop-up *after* adjusting the slider, 'twould be more ergonomic, IMO.

---

### Post by mango42 on 2010-11-12
Bump.

Do I ask impossible questions? ;-)

---

### Post by cchhrriiss121212 on 2010-11-12
alsamixer seems to work permanently for me.

---

### Post by mango42 on 2010-11-13
Thanks for the response, cchhrriiss, but with the version I have (AlsaMixer v1.0.20) the machine (T43 thinkpad) it still randomly resets to mute on boot.

There must be a dot.file somewhere...

---

### Post by cchhrriiss121212 on 2010-11-13
When you say randomly resets do you mean it mutes occasionally on boot? Or every time?
Either way you could try running a simple post boot script (I haven't used this with any recent Ubuntus but you could try this out):
```
sudo gedit /etc/gdm/PostLogin/Default
```
Then just paste in your preferred amixer commands.

---

