---
title: "Projector Hotplug to Laptop"
date: 2006-11-10
forum: Multimedia &amp; Video
---

### Post by ubtpenguin on 2006-11-10
Hey guys

Is there any easy way to hotplug projectors to my laptop?

I always have to make two xorg.conf file and restart X11 to make projector work. 

Like windows or MacOS, is there any way to hotplug this damn projectors? 

cheers, 
](*,)

---

### Post by Bosonator on 2006-11-14
I'd be interested in hearing a solution too. Even if someone could show me how to just get the projector to work at all would be good.

---

### Post by naomi on 2006-11-19
Hi! Could you please explain to us, how you manage to get your ubuntu laptop working with data projectors? I.e. please explain "make two xorg.conf file and restart X11" in a bit more detail.

Many thanks in advance!
Naomi

---

### Post by johns996 on 2006-11-22
here is how i got my display to clone onto a projector (using an intel i810 chip)

-backup
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

-edit
sudo gedit /etc/X11/xorg.conf

-in the "Device" section add these two lines:
Option "MonitorLayout" "CRT,LFP"
Option "Clone" "true"

-save changes
-restart X (you can do this with Ctrl+Alt_Backspace)

**source:** [http://ubuntuforums.org/archive/index.php/t-244590.html]("http://ubuntuforums.org/archive/index.php/t-244590.html")

---

### Post by sunny_nwho on 2006-11-22
i would suggest installing i810switch a small program tht can enable ur projector without changing anything and even without restarting

---

