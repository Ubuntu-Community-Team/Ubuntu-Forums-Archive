---
title: "ATI installer 8.19.10"
date: 2005-11-23
forum: Multimedia &amp; Video
---

### Post by Cybercool on 2005-11-23
Hello everyone,

I want to install the new ati drivers, and i want to ask you if it can be done with the ati installer, making a deb package and installing this deb package.
Or is there more to o.
I have a ati 9700 mobile.
Now i have the 8.16.20 driver installed.

Cybercool thinks it's a shame that ubuntu doesn't help ati bij setting the drivers in the apt installation system when ati releases her drivers!!!

---

### Post by Molikk on 2005-11-23
yes during instalation installer will ask you what to do

---

### Post by Cybercool on 2005-11-23
[QUOTE=Molikk]yes during instalation installer will ask you what to do[/QUOTE]


Yes i know
You can choose to make a packages. But i get an error when doing so at the end.
but can you use the installer as installer?

I saw some howto's where they are doing allot to install the new driver.
Like this one:
[http://www.ubuntuforums.org/showthread.php?t=78466&highlight=fglrx+8.19.10http://www.ubuntuforums.org/showthread.php?t=78466&highlight=fglrx+8.19.10]("http://www.ubuntuforums.org/showthread.php?t=78466&highlight=fglrx+8.19.10http://www.ubuntuforums.org/showthread.php?t=78466&highlight=fglrx+8.19.10")
Is this nessary?

---

### Post by Robocoastie on 2005-11-23
yes follow the steps in that how-to exactly as mloker said and it WILL work. I had to enable the universe and multiverse repository though in order to apt-get one of the many programs he mentions that you'll need. And I think the order of the .deb's to install that the ati-installer generates is wrong I don't recall which one but it tells you when you get to that step will say something like "missing dependency blah blah" just means switch the order around.

If like me, you end up at a terminal (x crashes) after installing ubuntu and you don't know how to enable those repositories from command line then just use vi to edit your /etc/X11/xorg.conf and change driver=ati to driver=vesa then save it and startx, go to synaptic and enable the universe and multiverse repositories then proceed with the steps.

The only other snag I got was being stuck at 1024x768 after running fglrxconfig (last step) I had to run the other xorg config which crashed X so via command line had to re-run fglrxconfig again at which time I then was at 1280x1024 and whatever resolutions I wanted. The issue I believe boiled down to monitor choosing "simple" kept mucking it up so I chose medium and picked my own hz rateings for the resolutions. This step was a lot of trial and error wasn't an exact science. But mloker's steps DO work after a bit of trial and error. I've had them work on both 32 and 64 bit 5.10 versions.

Rob

---

### Post by Cybercool on 2005-11-23
[QUOTE=Robocoastie]yes follow the steps in that how-to exactly as mloker said and it WILL work. I had to enable the universe and multiverse repository though in order to apt-get one of the many programs he mentions that you'll need. And I think the order of the .deb's to install that the ati-installer generates is wrong I don't recall which one but it tells you when you get to that step will say something like "missing dependency blah blah" just means switch the order around.

If like me, you end up at a terminal (x crashes) after installing ubuntu and you don't know how to enable those repositories from command line then just use vi to edit your /etc/X11/xorg.conf and change driver=ati to driver=vesa then save it and startx, go to synaptic and enable the universe and multiverse repositories then proceed with the steps.

The only other snag I got was being stuck at 1024x768 after running fglrxconfig (last step) I had to run the other xorg config which crashed X so via command line had to re-run fglrxconfig again at which time I then was at 1280x1024 and whatever resolutions I wanted. The issue I believe boiled down to monitor choosing "simple" kept mucking it up so I chose medium and picked my own hz rateings for the resolutions. This step was a lot of trial and error wasn't an exact science. But mloker's steps DO work after a bit of trial and error. I've had them work on both 32 and 64 bit 5.10 versions.

Rob[/QUOTE]


I did the installation.
And it works!!

---

### Post by Robocoastie on 2005-11-24
good to hear! bravo bravo

---

