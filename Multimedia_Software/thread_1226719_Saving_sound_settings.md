---
title: "Saving sound settings"
date: 2009-07-29
forum: Multimedia Software
---

### Post by zefiriss01 on 2009-07-29
hi, my sound volume alway muted every time started, it can be unmute easily by pressing the volume icon on tray bar, but kinda annoying have to press it every time. 
i try to use "saving sound setting" like it specified on help.ubuntu.org, but i got this one:
```
zefiriss@nirvash:~$ sudo alsactl store 0
E: core-util.c: Home directory /home/zefiriss not ours.
```
what it means?
thanks.

---

### Post by themusicalduck on 2009-07-29
Kinda looks like you're executing the command as root which doesn't have access to your home folder. Try the same command without sudo in front.

---

### Post by zefiriss01 on 2009-07-29
> **themusicalduck said:**
> Kinda looks like you're executing the command as root which doesn't have access to your home folder. Try the same command without sudo in front.
i got this one
```
zefiriss@nirvash:~$ alsactl store 0
alsactl: save_state:1541: Cannot open /var/lib/alsa/asound.state for writing: Permission denied
```

---

### Post by zefiriss01 on 2009-07-31
bump

---

### Post by martinbaselier on 2009-07-31
Have you checked the permissions? Looks like alsa doesn't have writing permission there. You might need to change group and user to sound?

---

### Post by zefiriss01 on 2009-07-31
> **martinbaselier said:**
> Have you checked the permissions? Looks like alsa doesn't have writing permission there. You might need to change group and user to sound?
how?
btw when startup and shutdown, internal pc speaker beeping and normal speaker silent, is this normal?

---

### Post by martinbaselier on 2009-07-31
Right click on the file/directory and choose properties, then go to the permissions tab.

btw: it's normal that the internal speaker is used during startup/shutdown

---

