---
title: "run vlc as root"
date: 2007-01-16
forum: Multimedia &amp; Video
---

### Post by ways on 2007-01-16
hi

i have the need to run vlc as root sometimes to access files only available to root. it worked nice before, but with 6.10 vlc got a root wrapper to hinder this. now vlc falls back to normal user by setuid, and wont open other files than the one given at commandline. any way to avoid it?

---

### Post by 23meg on 2007-01-16
Why are the files you want to view only available to root?

---

### Post by ways on 2007-01-17
> **23meg said:**
> Why are the files you want to view only available to root?

'cause it's porn

---

### Post by Biggus on 2007-01-17
Might it be simpler to amend the file permissions so that the porno files are owned by your own user, rather than the root user?

---

### Post by ways on 2007-01-17
> **Biggus said:**
> Might it be simpler to amend the file permissions so that the porno files are owned by your own user, rather than the root user?

well, yes. but this keeps others away by requiering my password. simply hiding it in a dot-folder isn't good enough, 'cause people can search or stumble upon my it. loop-mounting is an option, but too tedious and fixedsize container only.

the disk is encrypted, by the way. this last hinder is just because i often leave my pc on.

so, there is no way around? i'll have to go on using mplayer/totem. sucks, 'cause they keep hanging or failing to read some formats. thanks anyway.

---

### Post by zzarr on 2007-01-18
Hello!

Don't "sudo vlc my_video.avi" work? (or gksu if using gnome, and I think it is kdsu in kde)

I have no problems when I do it my self.

Greetings Zzarr

---

### Post by ways on 2007-01-18
> **zzarr said:**
> Hello!

Don't "sudo vlc my_video.avi" work? (or gksu if using gnome, and I think it is kdsu in kde)

I have no problems when I do it my self.

Greetings Zzarr

works for reading _one_ file. but doesn't allow to open other files than the one given as parameter.

```
lars@aotearoa:~$ sudo vlc 
Password:
VLC media player 0.8.6 Janus
starting VLC root wrapper... using UID 1000 (lars)
GTK Accessibility Module initialized

```

do you not get the wrapper-section when starting with sudo?

---

