---
title: "Gmusic Brower not working"
date: 2014-05-19
forum: Multimedia Software
---

### Post by josh45 on 2014-05-19
Gmusic browser no longer works on my computer. When I click on it from the menu, it does not load. 

When I try to open it in terminal, I get this:
```


print() on closed filehandle $fifofh at /usr/bin/gmusicbrowser line 328.
GStreamer::Interfaces perl module not found -> visuals not available
Reading saved tags in /home/joshua/.config/gmusicbrowser/gmbrc ...
Can't read '/home/joshua/.config/gmusicbrowser/gmbrc', aborting...



```

Please help! Thanks in advance.

---

### Post by Yellow Pasque on 2014-05-19
> Can't read '/home/joshua/.config/gmusicbrowser/gmbrc', aborting...

It sounds like the file got corrupted (or deleted). Show output of:
```
ls ~/.config/gmusicbrowser
```

It may just be a matter of using the backup copy:
```
mv gmbrc gmrbc.old
mv gmbrc.bak gmbrc
```

---

### Post by josh45 on 2014-05-25
The output of ls ~/.config/gmusicbrowser

```
gmbrc      gmbrc.bak.20140425.xz  gmbrc.bak.20140427.xz  gmbrc.bak.20140429.xzgmbrc.bak  gmbrc.bak.20140426.xz  gmbrc.bak.20140428.xz  gmusicbrowser.fifo

```

---

### Post by Yellow Pasque on 2014-05-25
Did you try to use one of the backups?

---

### Post by Elfy on 2014-05-25
so you have more than one backup

got through them, cd into the right place so 

```
cd .config/gmusicbrowser/
```

then 
```
mv gmbrc gmrbc.old
```

then you can start trying the backups

```
mv mv gmbrc.bak gmbrc
```

first, then you can go back through the older backups

The older backups have been compressed, you'll probably need to decompress them before trying with those ones

```
gmbrc.bak.20140426.xz
gmbrc.bak.20140427.xz
gmbrc.bak.20140428.xz
gmbrc.bak.20140429.xz
```

---

