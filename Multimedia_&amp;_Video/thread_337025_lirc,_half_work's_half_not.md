---
title: "lirc, half work's half not"
date: 2007-01-12
forum: Multimedia &amp; Video
---

### Post by nkwai on 2007-01-12
OK I finally managed to install lirc, and it almost works. If I want to run a command with "irexec" it work's widouth problems. If I whant to pause mplayer it don't work.

Here is the "lircrc" cnfig file:
```
begin
    button = mod
    prog = mplayer
    config = pause
    repeat = 0
end

begin
 button = 1
 prog = irexec
 config = /usr/bin/xmms
end
```

"ldd" on mplayer outputs the following:
```
nkwai@nkwai-laptop:~$ ldd /usr/bin/mplayer | grep lirc
        liblirc_client.so.0 => /usr/lib/liblirc_client.so.0 (0xb6d97000)
nkwai@nkwai-laptop:~$ 

```

Anyone have any idea what's wrong?
Thank You.

---

### Post by majoridiot on 2007-01-12
you need to config the button to the command:

```
begin
    button = play
    prog = mplayer
    config = pause
    repeat = 0
end
```

you can assign whichever button you want, in this case, it's the play buttton.

---

### Post by nkwai on 2007-01-12
Yes I know. In my case the button name is "mod".

---

