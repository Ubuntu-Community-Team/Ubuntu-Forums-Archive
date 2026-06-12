---
title: "ubuntu broke my 20&quot; flat panel :("
date: 2006-08-12
forum: Multimedia &amp; Video
---

### Post by bigcletus on 2006-08-12
This is a bummer.  After spending several days getting ubuntu on my machine, it boots and then shuts off my monitor, permenantly.  And now it will no longer work with a DVI cable.  Only vga :(  There is a lessoned to be learned here i guess.  And I have learned it.](*,)

---

### Post by tseliot on 2006-08-12
Ubuntu didn't break anything.

Try this:
boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver (or the driver you used before). And when it asks you about the Resolution and Refresh rate select the Advanced choice. Then you will need to set the Vertical and Horizontal refresh rate (which depends on your monitor).

Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```


And boot as usual

---

### Post by bigcletus on 2006-08-12
I wish it was that easy.  The monitor NEVER comes out of standby mode at all anymore from the time the computer turns on; before, during, or after POST.  Regardless if I have unbuntu, windows, or even a hard disk in the machine.  Nothing.  Dead blank screen.

---

### Post by tseliot on 2006-08-12
> **bigcletus said:**
> I wish it was that easy.  The monitor NEVER comes out of standby mode at all anymore from the time the computer turns on; before, during, or after POST.  Regardless if I have unbuntu, windows, or even a hard disk in the machine.  Nothing.  Dead blank screen.

Ok, if it doesn't work on Windows I guess your monitor died a natural death.

---

