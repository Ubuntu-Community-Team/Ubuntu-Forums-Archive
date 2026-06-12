---
title: "libmyth-python upgrade error - 2:31.0+fixes.202102201954.525e3b0bb4"
date: 2021-02-23
forum: Multimedia Software
---

### Post by jds013 on 2021-02-23
This flashes by in the apt console:

[HTML]Setting up libmyth-python (2:31.0+fixes.202102201954.525e3b0bb4~ubuntu20.04.1) ...
/usr/lib/python3/dist-packages/MythTV/tvmaze/utils.py:45: SyntaxWarning: "is not" with a literal. Did you mean "!="?
  if html is not None and html is not "":[/HTML]

---

### Post by Bashing-om on 2021-02-25
jds013; Hello - Welcome to the forum -

' apt list libmyth-python ' shows:
> 
libmyth-python/focal,focal 2:31.0+fixes.20200323.9579662cdc-0ubuntu1


so that begs the question of where you got the installed version from.
What shows from terminal command:
```

apt policy libmyth-python

```

See what is installed and where we go from there.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by deadflowr on 2021-02-25
> so that begs the question of where you got the installed version from.
It's from the mythtv ppa here:
[https://launchpad.net/~mythbuntu/+archive/ubuntu/31]("https://launchpad.net/~mythbuntu/+archive/ubuntu/31")

---

### Post by Bashing-om on 2021-02-25
\o/
PPA ^
> 
&#65532; mythtv	2:31.0+fixes.202102251823.b6ddf202a4~ubuntu20.04.1	Mythbuntu Team (8 hours ago)

from: 2:31.0+fixes.202102201954.525e3b0bb4~ubuntu20.04.1
Maybe now a fixed version ?

[INDENT]maybe yes
[/INDENT]

---

