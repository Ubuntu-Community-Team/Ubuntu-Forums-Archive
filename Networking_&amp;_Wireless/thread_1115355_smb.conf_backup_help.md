---
title: "smb.conf backup help"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by inobe on 2009-04-03
i can open my smb.conf with one of two commands to edit the file either in konsole or kate' so i am good there, but what is the command to backup smb.conf ?

thanks :)

---

### Post by capscrew on 2009-04-03
> **inobe said:**
> i can open my smb.conf with one of two commands to edit the file either in konsole or kate' so i am good there, but what is the command to backup smb.conf ?

thanks :)

Copy 

As in```
cp /etc/samba/smb.conf /etc/samba/smb.conf.backup
```

---

### Post by inobe on 2009-04-03
thanks capscrew :p

i should have asked before, how would i restore the backup in command line, or revert back.

much appreciated

---

### Post by capscrew on 2009-04-03
> **inobe said:**
> thanks capscrew :p

i should have asked before, how would i restore the backup in command line, or revert back.

much appreciated

You can copy it back.

As in```
cp /etc/samba/smb.conf.backup /etc/samba/smb.conf
```

This will overwrite the existing file of smb.conf with the smb.conf.backup file.

---

### Post by inobe on 2009-04-03
great stuff capscrew :guitar:

now i am all set for encase of disaster :lol:


back to editing, it took me a few hours to figure out how to edit this file in kubuntu, kinda funny actually because kate is the default text editor and being so use to gnome/ ubuntu i tried 

```
sudo gedit /etc/samba/smb.conf
```


but found that either one of these work well

```
sudo nano /etc/samba/smb.conf
```

```
kdesudo kate /etc/samba/smb.conf
```


just a story of my experience trying to edit a config file lols

---

