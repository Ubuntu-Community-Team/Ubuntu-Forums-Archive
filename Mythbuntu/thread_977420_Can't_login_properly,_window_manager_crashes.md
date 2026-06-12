---
title: "Can't login properly, window manager crashes?"
date: 2008-11-10
forum: Mythbuntu
---

### Post by 316097 on 2008-11-10
Hi, I've just upgraded my system from 8.04 to 8.10, everything went smooth, but after restart I can't get into the desktop anymore. I choose my user and put in my password, then it starts to flash by at the bottom, starting various stuff, but then suddenly it crashes and I get back to the login and it's all the same over and over again.

Clearly there's something wrong...below is output from dmesg.

Any help appreciated!

```
[  136.529204] xfce4-session[7165]: segfault at b72d22f8 ip b72d22f8 sp bfdb94d0 error 4 in LC_CTYPE[b72d8000+3f000]
[  137.193109] mtrr: no MTRR for e3000000,e00000 found
[  138.932380] mtrr: base(0xe3000000) is not aligned on a size(0xe00000) boundary
[  223.413502] xfce4-session[9262]: segfault at b70e42f8 ip b70e42f8 sp bf9c8290 error 4 in LC_CTYPE[b70ea000+3f000]
[  224.596043] mtrr: no MTRR for e3000000,e00000 found
[  226.802373] mtrr: base(0xe3000000) is not aligned on a size(0xe00000) boundary
[  328.426542] xfce4-session[11716]: segfault at b71a72f8 ip b71a72f8 sp bfe92200 error 4 in LC_CTYPE[b71ad000+3f000]
[  329.144955] mtrr: no MTRR for e3000000,e00000 found
[  330.747373] mtrr: base(0xe3000000) is not aligned on a size(0xe00000) boundary
[  427.914002] xfce4-session[13841]: segfault at b71cd2f8 ip b71cd2f8 sp bf9b0f20 error 4 in LC_CTYPE[b71d3000+3f000]
[  434.446835] mtrr: no MTRR for e3000000,e00000 found
[  437.291545] mtrr: base(0xe3000000) is not aligned on a size(0xe00000) boundary

```

---

### Post by funkydan2 on 2008-11-10
What happens if you get to a command prompt (press Ctrl+Alt+F1) and login and then 'get rid' of your ~/.config directory (```
mv ~/.config ~/.config.old
``` this will just rename it, just incase this doesn't work) and then try logging in again.  It may be that something in your xfce-session or in your AutoStart directory is causing problems with the upgraded version of XFCE.

If that doesn't work, just mv your .config.old directory back to where it was.

DS

---

### Post by 316097 on 2008-11-17
It worked, but now I don't get up the login window, and when I get to the desktop, there's no toolbar, only some icons on the desktop and a little box in the upper left corner with some star in it, I think it said launcher.

Is there a way to configure the desktop from scratch or revert to default settings for 8.10, as it is shipped?

---

### Post by Tuxi on 2008-11-30
Following the thread above, I did the following
```

mv ~/.config/xfce4-session ~/.config/xfce4-sesion.old

```
I got all my default xfce4 set up from before.

---

### Post by 316097 on 2008-12-08
> **Tuxi said:**
> Following the thread above, I did the following
```

mv ~/.config/xfce4-session ~/.config/xfce4-sesion.old

```
I got all my default xfce4 set up from before.

I wish this had worked, but I have no file or directory called xfce4-session.

---

