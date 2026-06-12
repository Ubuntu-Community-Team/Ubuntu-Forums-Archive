---
title: "Help! How to undo &quot;dpkg-reconfigure -phigh xserver-xorg&quot;?"
date: 2009-05-05
forum: Multimedia Software
---

### Post by ubu-for on 2009-05-05
I've entered "sudo dpkg-reconfigure -phigh xserver-xorg" one day ago to help a friend with Jaunty (long story) and now I've recognized some graphic issues. My second monitor (TV) doesn't show any errors.

I guess it's because of too high monitor frequencies. The "on screen display" (OSD) of my LCD monitor shows "H:80.0 KHZ" and "V:75.0 HZ". In my "xorg.conf" are much lower frequencies, so I think it's because of "-phigh".

GUI changes to lower frequencies were without effect.

Is it possible to undo "-phigh" with an other command?

Thank you very much in advance!

---

### Post by ubu-for on 2009-05-05
Now I've tested my monitor with the Jaunty Alpha 5 Live CD and Ubuntu sets the frequencies to recommended "H: 63.9 KHZ and V: 59.8 HZ" by default. No graphic errors at all!

Does anybody know how to change the frequencies to the recommended level?

---

### Post by ubu-for on 2009-05-06
I've installed the latest Nvidia drivers (185) from a PPA source, started "nvidia-settings" as root, changed the monitor frequency to "60 Hz" and saved it to xorg.conf.

Now the frequencies are at the recommended level but the graphic errors are still there!

After that I've downgraded the Nvidia drivers to version 173 because of the working Jaunty Alpha 5 Live CD, but without any changes!

Does anybody have further ideas?

---

### Post by ubu-for on 2009-05-06
I've updated the Nvidia drivers from 173 to 180 and the frequencies are now a little bit higher than recommended, but the graphic errors are still there. :(

P.S. The graphic errors appear only in the areas of colour gradients / shadings.

---

### Post by glotz on 2009-05-06
Running that command makes backups of your xorg.conf file. To locate it, do ```
updatedb
locate xorg.conf
```
The update part will take awhile, it's normal. Once you find the backup, move or remove the current /etc/X11/xorg.conf and replace it with the backup.

---

### Post by ubu-for on 2009-05-06
Thanks for your hint but I only get the following error message.

```
~$ updatedb
updatedb: unable to open temporary file `/var/lib/mlocate/mlocate.db'
```

P.S. Had to translate the German error message.

---

### Post by glotz on 2009-05-06
Oh, you probably need super user privileges, or```
sudo updatedb
```

---

### Post by ubu-for on 2009-05-06
> **glotz said:**
> Oh, you probably need super user privileges, or```
sudo updatedb
```

Done.

What's next?

I'm asking because my most recent "xorg.conf" is 30 minutes old and is called "xorg.conf.failsafe".

---

### Post by ubu-for on 2009-05-06
Now I've tested the Nvidia driver version 185 from the Nvidia website without success.

In the past with Feisty the monitor had a frequency of 50 Hz and I guess if I could force Jaunty to accept the "xorg.conf" settings the green pixels instead of shading would be gone.

---

### Post by glotz on 2009-05-06
The oldest backup contains settings before reconfiguring.

I'm not a big fan of this new style automagical xorg config.

---

### Post by ubu-for on 2009-05-07
> **glotz said:**
> I'm not a big fan of this new style automagical xorg config.

Me neither!

Now I've tested my monitor with an other PC and it looks like the high frequencies damaged the display.

Thanks for your help glotz!

---

### Post by glotz on 2009-05-07
You're quite welcome! Hope you get it all sorted out.

---

