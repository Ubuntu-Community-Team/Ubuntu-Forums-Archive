---
title: "Flash Player- how to install in ocelot ?"
date: 2012-01-12
forum: Multimedia Software
---

### Post by grey1beard on 2012-01-12
I've now got Ocelot running(somewhat) on a toshiba A30 laptop,
and I'm trying to watch BBC news clips.
It tells me to download the correct version of FP.
Clicked on the link, downloaded and saved the .tar.gz version, but now stuck, as I can't remember what to do next.
Perhaps it would have been better to use terminal, but I'm struggling with the new layout of Ocelot ( is this "Unity" that I see referred to ?).
Sense that I'm beginning to ramble on, so guidance appreciated.

John

---

### Post by howefield on 2012-01-12
Extract your download and copy libflashpayer.so to /usr/lib/mozilla/plugins and restart your browser if you had it open.

---

### Post by IWantFroyo on 2012-01-12
It's better to use the repository version of Flash. More likely to work with more stability, in my experience.

I know the Flash player is included in ubuntu-restricted-extras.

Because I am not on my Ubuntu computer, I can't look for the file that contains only the flash player, but if there is one, you'll find it with:
```
apt-cache search flash
```

---

### Post by grey1beard on 2012-01-12
> **howefield said:**
> Extract your download and copy libflashpayer.so to /usr/lib/mozilla/plugins and restart your browser if you had it open.
Do I need to change the permission to "Allow executing" in order to get it to copy across ?
I'd extracted to Desktop.

---

### Post by grey1beard on 2012-01-12
> **grey1beard said:**
> I've now got Ocelot running(somewhat) .................


Now it's frozen so I've rebooted, again.
This time it's not responding to the mouse correctly.
It will open windows from the icons on the left of the screen, but not anything else - wont select anything in the window, nor close the windows, so I'll just have to crash the system, again.
EDIT
Not sure what I did, but I tried the super key(?) and enter, and it started to respond again.
For how long, though ?

---

### Post by howefield on 2012-01-12
> **grey1beard said:**
> Do I need to change the permission to "Allow executing" in order to get it to copy across ?
I'd extracted to Desktop.

Easiest way would be to open a terminal and issue the following commands..

```
cd Desktop
```

```
sudo mv libflashplayer.so /usr/lib/mozilla/plugins
```

This will allow all accounts on your machine to access the flash player.

If you only have the one account on the machine you can install into /home folder. I think it would be .mozilla/plugins

---

### Post by grey1beard on 2012-01-12
Thanks howefield.
The last attempt to reboot has it frozen at the spash screen, so I'm trying again.
The system at this moment seems to be completely unstable, so by late tonight I might make a decision to revert to 10.10 !
EDIT
Thanks again. At least I've now got Flash Player working 
Regards
John

---

