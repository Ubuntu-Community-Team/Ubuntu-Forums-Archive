---
title: "Dapper: Nvidia screen corruption after restarting X"
date: 2006-06-01
forum: Multimedia &amp; Video
---

### Post by nixt on 2006-06-01
Hi all

Clean dapper install, and grabbed nvidia-glx from the repos. The video acceleration is all fine.

The problem is when you attempt to kill X (ctrl+alt+backspace), or restart the machine (notice that both situations trigger a video mode change), the entire screen corrupts.. you can still make out the text, but artifacts are peppered all over the screen, and you just have to reboot. 

I'm using a 5700 Ultra with an LG LCD monitor using DVI.

Anyone having the same problems? It doesn't kill my installation, but certainly irritating.

---

### Post by johnc4510 on 2006-06-01
I assume that after the glx install, you did:
sudo nvidia-glx-config enable
If not, try that.

---

### Post by tseliot on 2006-06-01
Try this:
```
sudo nano -w /boot/grub/menu.lst
```

look for this line:
```
# defoptions=quiet splash
```

Remove the word "splash" from it.

Save and exit:
press CTRL+X

Then type this in Terminal or Konsole:
```
sudo update-grub
```

and restart your computer

---

### Post by nixt on 2006-06-01
john, thats what I did. My acceleration is working.

Thanks tseliot, i shall try that now

---

### Post by nixt on 2006-06-01
tseliot's solution works! Thanks a lot. I owe you one.

I don't get the fancy usplash anymore but it doens't matter anyway (I actually prefer the text output)

---

### Post by nixt on 2006-06-01
Solved

---

