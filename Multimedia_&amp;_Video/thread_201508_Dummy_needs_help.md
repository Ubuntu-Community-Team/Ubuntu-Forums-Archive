---
title: "Dummy needs help"
date: 2006-06-21
forum: Multimedia &amp; Video
---

### Post by loserboy on 2006-06-21
I got beep media player and can't put skins in the skinsa folder 
/usr/share/bmp/skins 

says i dont have permission...  I R confused

---

### Post by presentt on 2006-06-21
[quote=loserboy] says i dont have permission...[/quote] 
I'm not familiar with beep media player or its skins, but permission errors normally result from just what it says--you not having permissions.  Try doing whatever it is you need to do using the command line, and prefacing each command with "sudo," meaning "superuser do"

For example (and not this won't apply to your problem, it's just to show sudo"

```
sudo rm -dr /home/username/some_restricted_directory
``` will delete the given directory, even if you, as a regular user, don't have permission.

---

### Post by loserboy on 2006-06-22
lol omg i figured it out,   the folder i was suppose to go to was in my home folder, i looked there but it was hidden... so now i just feel stupid cuz i put like 3 posts about this....... sorry all

---

