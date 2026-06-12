---
title: "Handy multimedia problem command"
date: 2009-04-12
forum: Multimedia Software
---

### Post by Roanoke on 2009-04-12
Have a problem? Execute this command in the terminal and put the contents of info.txt in your post:
```

touch ~/info.txt && date >> info.txt && echo ---Xorg.conf--- >> info.txt && cat /etc/X11/xorg.conf >> info.txt && echo ---lspci--- >> info.txt && lspci >> info.txt

```
Or append this to .bashrc (or wherever your aliases live):
```

alias ginfo="touch info.txt && date >> info.txt && echo ---Xorg.conf--- >> info.txt && cat /etc/X11/xorg.conf >> info.txt && echo ---lspci--- >> info.txt && lspci >> info.txt"

```
And a human-readable form:
```

touch ~/info.txt \
&& date >> info.txt \
&& echo ---Xorg.conf--- >> info.txt \
&& cat /etc/X11/xorg.conf >> info.txt \
&& echo ---lspci--- >> info.txt \
&& lspci >> info.txt

```
Any other commands that would be helpful to include? Sorry if this is the wrong forum.

---

