---
title: "Mythbuntu 14.04, Dedicated backend, Disable X on startup?"
date: 2014-07-14
forum: Mythbuntu
---

### Post by mattlach on 2014-07-14
Hey all,

So, I am running my dedicated backend on a machine with some ram limitations.  X with XFCE is pretty lightweight, but it is much more lightweight if it isn't running at all :p

Is it safe to just stop X from starting on boot, or is there some component of the backend that needs it to be running?

I know I will need X in order to do the backend startup, but I figured I can accomplish that by just running "startx" from the console when needed, that way the ram won't be wasted when I am not running the setup.


So, assuming this IS safe, how do I accomplish it?   How do I tell mythbuntu to behave like ubuntu server edition on boot and just give me a text login prompt?

Thanks,
Matt

---

### Post by Bashing-om on 2014-07-14
mattlach; Hello.

Mind you I do not run Mythbuntu, but I can not see where a GUI is required for it's operation.
To not start 'X' at boot up one can edit one of grub's config files to start in "text" mode.
```

sudo cp /etc/default/grub /etc/default/grub-14jul2014 #SOP for any time a file is edited, make a backup#
gksudo gedit /etc/default/grub

```
change the line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to:
GRUB_CMDLINE_LINUX_DEFAULT="text" ##replacing the terms "quiet splash" with the term "text"##
save the file and in terminal execute command:
```

sudo update-grub

``` to propagate the change.

When you re-boot you then will boot to the terminal TTY1.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by mattlach on 2014-07-14
> **Bashing-om said:**
> mattlach; Hello.

Mind you I do not run Mythbuntu, but I can not see where a GUI is required for it's operation.
To not start 'X' at boot up one can edit one of grub's config files to start in "text" mode.
```

sudo cp /etc/default/grub /etc/default/grub-14jul2014 #SOP for any time a file is edited, make a backup#
gksudo gedit /etc/default/grub

```
change the line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to:
GRUB_CMDLINE_LINUX_DEFAULT="text" ##replacing the terms "quiet splash" with the term "text"##
save the file and in terminal execute command:
```

sudo update-grub

``` to propagate the change.

When you re-boot you then will boot to the terminal TTY1.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

Thank you for the prompt help!  :)

Once I do this, and if I need X for any reason and start it with "startx" will I be able to kill it again, or will it just keep reloading when killed, like it does by default?

---

### Post by Bashing-om on 2014-07-14
mattlach; Welp.

I also run xfce4 for my DE, and when I choose "logout" -> logout I revert to TTY1 and X is no longer running. But be aware I do not use a login manager, If you do It is possible that your mileage "may" vary .. 
In that event we will be glad to work through any issues ( if any at all ) .. try and see what results.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]it is all fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

