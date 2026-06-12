---
title: "Black screen on shutdown/restart"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by tonioab49 on 2006-07-24
Hi,

I have a ATI X700 SE on an AMD64 arch, everything works fine with the fglrx drivers apart from the fact that i get a black screen when i want to shutdown or restart my computer. I have to do a hard-reset or shutdown...
My monitor is a Samsung 205BW (Wide TFT) and it keeps switching between "Analog" and "Digital", showing a black screen, when i want to shutdown my computer; eventually it turns itself off, as if there was a problem... 

Thank you

---

### Post by tseliot on 2006-07-24
I don't know if it works with ATI cards too:

Try this:
```

sudo nano -w /boot/grub/menu.lst

```

look for this line:

```
# defoptions=quiet splash
```


Remove the word "splash" from it.

Save and exit: press CTRL+X

Then type this in Terminal or Konsole:
```

sudo update-grub
```

and restart your computer

After that, you will have no pretty usplash screen to look at anymore but the bug should be gone.

---

