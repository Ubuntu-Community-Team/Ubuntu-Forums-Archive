---
title: "Nvidia Upgrade"
date: 2007-03-09
forum: Multimedia &amp; Video
---

### Post by siciliancasanova on 2007-03-09
I recently was attempting to install beryl and went through the walk through and got the new nvidia drivers from the repository.  Ran everything and it installed it, asked me to reboot to make changes and at the reboot it brought to the black terminal screen, telling me there's a problem with my video card and when I hit ok it takes me again to the black terminal screen where I can log in.

Not sure what's going on, I'm very new to ubuntu and the whole concept of command line.  If there is a way to revert back to the old settings, that would be ideal.

---

### Post by renzokuken on 2007-03-09
at the terminal screen where it asks you to log-in....well....login !!

then run the following command

```
sudo nano /etc/X11/xorg.conf
```

scroll down to the [color=red]Section   "Device"[/color] part and look for the line 'Driver' 
it will probably look something like this

```

Section   "Device"
      Identifier          "card name"
      Driver               "nvidia"        [color=blue]# this is the line we are interested in[/color]
End Section

```

the change whatever is in the inverted commas to vesa so it now looks like

```

Section   "Device"
      Identifier          "card name"
      Driver               "vesa"        [color=blue]# changed[/color]
End Section

```

now save the file and exit ( Ctrl+X , Y and then Enter)

reboot and see if it you get your grafix back

---

