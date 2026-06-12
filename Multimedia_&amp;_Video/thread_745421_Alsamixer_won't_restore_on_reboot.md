---
title: "Alsamixer won't restore on reboot"
date: 2008-04-04
forum: Multimedia &amp; Video
---

### Post by stumpalump on 2008-04-04
So about a week ago I made the mistake of trying to get my xfi to work with oss. Since then I've been dealing with the headache of removing oss and restoring alsa back to it's original state. As of right now I'm sitting pretty good. I have sound including spdif and everything.

The only problem I'm having is alsamixer won't restore the settings saved in asound.state automatically! I have had to add an entry in my sessions with the command 

```

alsactl restore 0

```

This is the only way I can get alsamixer to restore the settings. It is an acceptable workaround, however, I don't have any of the sounds at the login screen which is kind of annoying.

I'm wondering if anyone knows enough about alsa to know how I can have alsamixer restore the settings on it's own without me calling it like it's supposed to.

---

### Post by warp99 on 2008-04-04
Set the levels with alsamixer then do the following:

```
sudo alsa store 
```

then they will restore on reboot. The reason they are not stored is because you didn't use the sudo command.

---

### Post by stumpalump on 2008-04-05
I used sudo when I stored them. I'm just not using sudo to restore the settings on reboot.

any other ideas???

---

### Post by warp99 on 2008-04-05
It could be that you desktop mixer program is resetting them. Set you levels with alsamixer, then store them. Boot to a login page then press ctrl-alt-f2 to get a console. Login and see if your levels are still the same. To get back to your login page press ctrl-alt-f7.

The file for the settings is located in /var/lib/alsa/asound.state. Check the permission for the file using the ls -l switch:

```
/var/lib/alsa$ ls -l
total 12
-rw-r--r-- 1 root root 9127 2008-04-05 10:44 asound.state
```

---

### Post by stumpalump on 2008-04-08
Here is my permissions on the file. (Mine is in /etc btw)

```
-rw-r--r--  1 root root      8616 2008-04-04 13:15 asound.state

```

Maybe it has something to do with the file being in /etc rather than /var ?

---

### Post by warp99 on 2008-04-08
Let's put a symlink between /var/alsa and /etc:

```
sudo ln -s /etc/asound.state /var/lib/alsa/asound.state
```

If the directory /var/lib/alsa does not exist then create it:

```
sudo mkdir /var/lib/alsa
```

then repeat the symlink string.

---

### Post by stumpalump on 2008-04-08
Thanks for helping, warp. It's nice to know that I can get a response when I can't find answers on here otherwise. I'll try these things and get back

---

