---
title: "Mythtv backend only install"
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by mjatromp on 2007-06-12
I followed the guide in [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend), but once I remotely start mythtv-setup, it fails with:
Xlib:  extension "XInputExtension" missing on display "localhost:10.0".
and ultimately segfaults.

Does anyone else see this problem and is there a solution? The following bug report seems related:
[http://svn.mythtv.org/trac/ticket/3401](http://svn.mythtv.org/trac/ticket/3401)

Marcel
--

---

### Post by barney_1 on 2007-06-12
The link you posted is for a combined frontend and backend machine.  You want this link:

[https://help.ubuntu.com/community/MythTV_Feisty_Backend](https://help.ubuntu.com/community/MythTV_Feisty_Backend)

To run setup remotely, use this command (replace [email]username@address.of.the.back[/email]end with the appropriate info):

```
$ ssh -X -Y username@address.of.the.backend /usr/bin/mythtv-setup
```

---

### Post by mjatromp on 2007-06-12
I posted the wrong link. I actually followed the one you pointed to and used ssh to tunnel X. This gives me the problem described.

---

### Post by mjatromp on 2007-06-17
Problem is related to vnc. When I use a live cd (slax) with an xserver I can execute all commands as listed in the howto.

Marcel
--

---

### Post by woZa on 2007-09-09
Hi. New to ubuntu (switched from gentoo) and I too am getting the above seg fault error. I am trying to do this from a laptop running os x (with an x-server). Not sure how to resolve this...

Should I use a live cd on my mac and try again?

Thanks

---

### Post by woZa on 2007-09-09
Well after struggling to find a small live cd for ppc I found an emulator [qemu]("http://www.kju-app.org/kju/index.php?p=dd&build=Q-0.9.0a89.dmg") that I used to run slax and set up mythtv like that. Very slow but it worked.

---

### Post by egoon on 2007-11-01
woZa: could you please explain ho you did that?

I've looked around and only managed to make gemu hang... =(

---

