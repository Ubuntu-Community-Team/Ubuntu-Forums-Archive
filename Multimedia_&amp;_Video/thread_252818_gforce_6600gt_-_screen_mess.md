---
title: "gforce 6600gt - screen mess"
date: 2006-09-07
forum: Multimedia &amp; Video
---

### Post by guest5 on 2006-09-07
hello all.  fresh install (friends pc) with nvidia 6600gt and all i can see are rows of different colored rectangles.  teere is nothing to read on this display.

do i have to put in a different card to download the drivers and then put the nvidia card back in the machine? or an override key combination or something?

at first i thought might be a corrupt iso torrent i download, so i torrented the live disk (x86) only to have a duplicate issue.  so it isn't the iso file i burned.

thanks in advance.

---

### Post by tseliot on 2006-09-07
boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

The Xserver should work fine

---

### Post by guest5 on 2006-09-07
thank you for the prompt responce.  i will not be able to get to his pc till later, but will give this a shot as soon as i can.

thanks again

---

### Post by guest5 on 2006-09-08
finally got to the pc.  i went through the screens selecting the defaults and came up with the same issue.  so i modified one or two settings and it froze at the kubuntu loading screen after saying ok to the first load up screen.

here is a psuedo list of the settings available:

(this is an x86 pc)

no vesa, but NV, selected nv.
(correctly identifies the nvidia gforce 6600 card)
please enter the card's bus identifier (?)
enter amount of video ram (128) {i had left this blank the first time}
auto detect keyboard
enter xkb rule set (xorg is the default)
keyboard (pci101)
type of mouse 1)impps/2 or 2)explorerps/2 (mouse is a razor)
configure xserver-org (defaults)
write default to configuration file (y)
monitor autodetect (y)
monitor size (simple)
samsung 955DF

---

### Post by tseliot on 2006-09-08
> **guest5 said:**
> finally got to the pc.  i went through the screens selecting the defaults and came up with the same issue.  so i modified one or two settings and it froze at the kubuntu loading screen after saying ok to the first load up screen.

here is a psuedo list of the settings available:

(this is an x86 pc)

no vesa, but NV, selected nv.
(correctly identifies the nvidia gforce 6600 card)
please enter the card's bus identifier (?)
enter amount of video ram (128) {i had left this blank the first time}
auto detect keyboard
enter xkb rule set (xorg is the default)
keyboard (pci101)
type of mouse 1)impps/2 or 2)explorerps/2 (mouse is a razor)
configure xserver-org (defaults)
write default to configuration file (y)
monitor autodetect (y)
monitor size (simple)
samsung 955DF
Wasn't vesa available in the list of drivers???

---

### Post by guest5 on 2006-09-08
no 'vessa' in the list:

i810
imstt
mga
neomagic
newport
nv


that's the list.  thanks for looking into this w/for me.

---

### Post by tseliot on 2006-09-08
> **guest5 said:**
> no 'vessa' in the list:

i810
imstt
mga
neomagic
newport
nv


that's the list.  thanks for looking into this w/for me.

Are you sure that you can't scroll down the list with your keyboard arrows?

---

### Post by guest5 on 2006-09-08
man o man, what am i thinking, i didn't even try to scroll down.  fighting the brainwashing by micro$oft i guess.  nothing indicating a possible scroll, so i didn't think for myself.  i have to break out.  breaking out, lol.

thank you so much, booted right up proper.  thank you again.
g5

---

