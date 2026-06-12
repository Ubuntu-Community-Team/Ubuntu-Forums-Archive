---
title: "Broken PATH?"
date: 2010-12-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2010-12-03
Can anyone on an up-to-date Natty tell me the output of ```
echo $PATH
``` from a terminal?

Mine is just '/usr/local/bin:/usr/bin:/bin' and I get complaints like ```
Command '...' is available in '/sbin/...'
The command could not be located because '/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
...: command not found
```

---

### Post by go7Ul1ai on 2010-12-03
On a fully updated natty I get this:


/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

---

### Post by Quackers on 2010-12-03
On my newly installed/fully updated Natty Alpha1 install I get

```
nattyalpha@nattyalpha-VGN-AR51SU:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
nattyalpha@nattyalpha-VGN-AR51SU:~$ 

```

---

### Post by MacUntu on 2010-12-03
Cool, thanks!

So I broke it, hallelujah!

**Edit:**

It seems I messed up my /etc/environment when purging a language from the system (which was a PITA task). Now I just need to find out, who's responsible for creating that file (unfortunately it doesn't belong to any package).

**Edit 2:**

So it seems to come from libpam-modules, but a simple dpkg-reconfigure or reinstall won't do, so I ended up just editing /etc/environment by hand, adding:```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```

---

