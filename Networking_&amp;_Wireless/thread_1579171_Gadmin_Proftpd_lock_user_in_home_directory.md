---
title: "Gadmin Proftpd lock user in home directory"
date: 2010-09-21
forum: Networking &amp; Wireless
---

### Post by Osamabingandhi on 2010-09-21
I've managed to get everything working except I only get access to the files from the home directory that my user has. Any other folders i share i cannot see.

I understand that the program and settings, lock the user in this home directory....kind of strange that i can share other folders then!

Anyone know how to unlock this setting?

---

### Post by Baneblade on 2011-06-20
Directory Aliasing. So the other directories would appear inside the home directory.

I'm currently trying to set it up at the minute, but can't seem to find the option in Gadmin.

Did you ever sort it out?

---

### Post by Baneblade on 2011-06-21
Still haven't found out how to do it, but a work-around in the mean time that seems to work fine for me is to mount the other directories into the users home directory. 
This creates a copy for them there, identical and sync'd to the original location without duplicating the data.

```
To have an exact duplicate of the /var/ftp/incoming directory available in 
/home/bob/incoming and /home/dave/incoming, use one of these commands:

Linux (as of the 2.4.0 kernel):
  mount --bind /var/ftp/incoming /home/bob/incoming
  mount --bind /var/ftp/incoming /home/dave/incoming
or, alternatively:
  mount -o bind /var/ftp/incoming /home/bob/incoming
  mount -o bind /var/ftp/incoming /home/dave/incoming
```


Found Here: [http://www.proftpd.org/docs/howto/Chroot.html]("http://www.proftpd.org/docs/howto/Chroot.html")

---

