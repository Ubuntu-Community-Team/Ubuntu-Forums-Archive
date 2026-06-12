---
title: "mount -t smbfs ok but in Nautilus not"
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by torstenkarusseit on 2009-07-25
Hi
using Ubuntu 9.04
mount -t smbfs //192.168.xx.yy/share0 /mnt
is successful,
but trying to view this share with nautilus (2.26.2) is not
(same problem was in ubuntu 8.10)
thanks for your help
Torsten

---

### Post by synapsys on 2009-07-25
Are you getting any error messages? If not try opening from the terminal and see if it gives you any error messages. 

```
sudo nautilus /mnt/nameoffolder
```

---

### Post by torstenkarusseit on 2009-07-25
Thanks for your replay.
it seems that we misunderstand eachother.

this is what i tried:
1.
on terminal:
sudo mount -t smbfs //192.168.xx.yy/share0 /mnt -o user=u,pass=p,dom=d
and it went ok, I can see all files, and can work with it, all ok.
2.
without first mount this share !!
I try to view the Network in Nautilus -> it shows my computers on the LAN.
But when I try to go to one of them (the same I successfully mounted in the first place),
it pops up the password dialog, where I put in the same like in the first place,
and then I get an error:
"Einhängen des Ortes nicht möglich"
"Einhängen des Windows-Speichers fehlgeschlagen"
english may be:
"mounting this not possible"
"mounting of Windows-device failed"
That is my problem I'm not understanding.

Trying to start Nautilus in a terminal
give me a lot of error messages (two pages or so),
but it seems that they according to problems starting Nautilus that way.
Do you want to see these messages ?
so long
Torsten

---

### Post by Iowan on 2009-07-26
Unless you specifically need it, **smbfs** is deprecated in favor of **cifs**. [Here]("http://ubuntuforums.org/showthread.php?t=288534") is a How-To that may be helpful.

---

### Post by torstenkarusseit on 2009-07-26
Thanks for that,
I tried cifs also, the same behavior.
googling some about the issue shows, that it has posslibly to do with upgrade to ubuntu 9.04. Older versions of ubunto dont show this difficulties.
So I giving up and stay with manually mounting the shares.
With a bit patience and luck there will be a solution within short time.
so long
Torsten

---

