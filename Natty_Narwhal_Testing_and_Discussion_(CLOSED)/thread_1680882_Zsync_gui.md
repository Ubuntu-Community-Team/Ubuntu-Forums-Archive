---
title: "Zsync gui"
date: 2011-02-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by alaukikyo on 2011-02-03
here a zsync script made by geirha of askubuntu ([http://askubuntu.com/users/9016/geirha](http://askubuntu.com/users/9016/geirha)).

it means you can easily update your natty daily build iso.

[IMG]http://i.imgur.com/Vt29t.png[/IMG]
[IMG]http://i.imgur.com/ToZXO.png[/IMG]

---

### Post by VMC on 2011-02-03
I must be missing something here. Using the command line, zsync does show progress - % downloaded and ETA, just not a gui.  It appears that's all the zsync script does.

---

### Post by tjeremiah on 2011-02-03
but the old way of updating keeps you up to date, no need to iso every time,  or is there something im not understanding :( ?

---

### Post by cariboo on 2011-02-03
I use the following two scriplets:

update_64

```
zsync http://cdimage.ubuntu.com/daily-live/current/natty-desktop-amd64.iso.zsync

```

update_32

```
zsync http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.iso.zsync

```

---

### Post by ronacc on 2011-02-03
zsync is to update the daily .iso if you are using that to test it , it saves redownloading the whole .iso every day .

@ cariboo907 I use the same scriptlet I just call it something different:p

---

### Post by VMC on 2011-02-03
I have my zsync set up in alias as such:

```
alias NAT='zsync -i /media/NTFS/natty-desktop-amd64.iso http://cdimage.ubuntu.com/daily-live/current/natty-desktop-amd64.iso.zsync'
alias NAT32='zsync -i /media/NTFS/natty-desktop-i386.iso http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.iso.zsync'
```

and for Lucid upcoming 10.4.2:

```
alias LUC32='zsync -i /media/NTFS/lucid-desktop-i386.iso http://cdimage.ubuntu.com/lucid/daily-live/current/lucid-desktop-i386.iso.zsync'
alias LUC='zsync -i /media/NTFS/lucid-desktop-amd64.iso http://cdimage.ubuntu.com/lucid/daily-live/current/lucid-desktop-amd64.iso.zsync'
```

---

