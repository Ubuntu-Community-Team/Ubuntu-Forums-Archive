---
title: "Filecopy between remote samba shares."
date: 2009-07-26
forum: Networking &amp; Wireless
---

### Post by dercaS on 2009-07-26
Hello.

I've currently set up Samba so that I can access various shares on my desktop from my laptop.
These are automounted via fstab and consists of a total of 5 shares (so far).

Now when I'm on my laptop and want to remotely manage files on my desktop computer I would for instance want to copy files directly from one remote share to another. However filecopy seems to go via the LAN instead of directly from hardrive/partition to harddrive/partition on my desktop computer. And thus needles to say making it alot slower than it would via inter- harddrive or SATA copy.

Is there any way I can make this kind of filecopy not go via LAN?

Edit:
Just to give an example
When I'm on my laptop and use

cp /media/dercas-desktop/Downloaded/movie.avi /media/dercas-desktop/Movies/movie.avi 

the file transfer goes over the lan instead of directly between the harddrives in my desktop computer.

---

### Post by swerdna on 2009-07-26
You can manipulate the files directly on the desk computer using ssh (or fish), rdp or vnc -- all remote control.

---

### Post by dercaS on 2009-07-26
Yeah well I know about vnc/remote desktop. I allready have set up remote desktop for system settings configuration from my laptop.

However for simple file manipulation it would be preferable to be able to use for instance Gnome Commander for file copy.

Seems like files being copied gets cached on my laptop when copying.

---

