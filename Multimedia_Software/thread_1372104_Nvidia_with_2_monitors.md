---
title: "Nvidia with 2 monitors"
date: 2010-01-04
forum: Multimedia Software
---

### Post by thockin on 2010-01-04
Just installed Karmic.  I have an Nvida something-something GPU with 2 Dell monitors.  The NVidia control panel applet finds them both and can enable them.  They work.

But rebooting loses that config.

So I hit the "Save to X Config File" button in the NV applet, and I get "Failed to parse existing X config file '/etc/X11/xorg.conf'!".

What's going on?

Tim

---

### Post by mad_max0204 on 2010-01-04
sudo nvidia-settings

---

### Post by howefield on 2010-01-04
> **mad_max0204 said:**
> sudo nvidia-settings

Try

```
gksudo nvidia-settings
```

---

### Post by mad_max0204 on 2010-01-04
Whats the diff ?
I know theoretically but in practice ?
Never had problems with sudo.

---

### Post by howefield on 2010-01-04
> **mad_max0204 said:**
> Never had problems with sudo.

Good for you, hope it continues that way.

You answered your own question, you know the theory, but it probably isn't a good idea to assume or hope that others will share your good fortune/luck.

---

### Post by Belizeian on 2010-01-04
The reason the machine resets the config is you are runing the setup as a user and the X config file is owned by root so you can't edit it.

Hence the need for sudo or gksu.

The difference between sudo and gksu is sude is issued from in a terminal and gksu is graphical version that you can use without opening a terminal.

to permentaly fix ths issue I would recommend useing the menu editor go to the entry "Nividia X server settings" select it and click properties.

In the feild labled command insert gksu infront of the existing command insureing you put a space between the u and the first letter of the command.

Save and exit.

Now when you click the item in the menu it will ask for credentials and any changes you make can be saved.

---

### Post by realzippy on 2010-01-04
"Failed to parse existing X config file '/etc/X11/xorg.conf'!".

What's going on?


You have to delete existing xorg.conf first and then create a new one:

[B]sudo rm /etc/X11/xorg.conf
sudo nvidia-xconfig
[/B]
then save settings:

**gksudo nvidia-settings**
,no more parsing error.

---

### Post by Belizeian on 2010-01-04
> **realzippy said:**
> "Failed to parse existing X config file '/etc/X11/xorg.conf'!".

What's going on?


You have to delete existing xorg.conf first and then create a new one:

[B]sudo rm /etc/X11/xorg.conf
sudo nvidia-xconfig
[/B]
then save settings:

**gksudo nvidia-settings**
,no more parsing error.

Always back up a config file before editing and especial before removeing.

IE
cp /etc/X11/xorg.conf /home/username/xorg.conf.old

---

### Post by realzippy on 2010-01-04
> **Belizeian said:**
> Always back up a config file before editing and especial before removeing.

IE
cp /etc/X11/xorg.conf /home/username/xorg.conf.old

Absolutely no need to do so with nvidiadriver.BTW.Karmic also needs no xorg.conf.

This existing xorg.conf file is the problem (parser error),what do you want with a problem.backup? ;-)
After settings are done (written to xorg.conf) it is a good idea to backup the new file....

---

### Post by Belizeian on 2010-01-04
Of course I do, what if the card dies and I need x back with the built in.  It's just good practice to always back up configs.  Train as if you would fight, as it where.  Good habits are hard to beat.

---

### Post by realzippy on 2010-01-04
> **Belizeian said:**
> Of course I do, what if the card dies and I need x back with the built in.  It's just good practice to always back up configs.  Train as if you would fight, as it where.  Good habits are hard to beat.

Backing up an invalid file cannot be good practice/habit.
If OP.s card would die,he would do the same: sudo nvidia-xconfig
If he was not on Karmic/NVIDIA I would have told him to backup.

---

### Post by thockin on 2010-01-04
Removing the old file did the trick!

Thanks.

---

### Post by Belizeian on 2010-01-04
Philosopical disagreement.  Mine is base more consistance, maybe it's just me but config files are small and yes some don't really matter, but consider that not all users know the difference between which are and aren't.  It realy harms nothing by just backing up every config file before you alter it in any way.  As a further step personaly when I back up a config for change I comment the file as to why it was backed up.  Half a dozen of the other really pure preference as neither option causes harm.

---

