---
title: "totem movie player stuck in fullscreen"
date: 2007-12-13
forum: Multimedia &amp; Video
---

### Post by alexander.forster on 2007-12-13
Totem movie player used to work just fine until recently. When i used to open a file using it it would open the .avi at the correct size, but now it opens in fullscreen and i cannot get out of fullscreen. 

yesterday i thought i had found a solution. i uninstalled then installed the movie player then ran it in the terminal then opened the file in totem, which gave me the file in its proper size and i was able to enter and exit fullscreen as i pleased. then i even tried opening the file by double clicking it and it opened in its normal size.

now i cannot get the movie player out of fullscreen. any help would be really appreciated. thanks!

---

### Post by alexander.forster on 2007-12-13
alright . . . i guess its working normally again now . . . not really sure what's going on here,

anyone have an idea of whats going on here?

---

### Post by jharris on 2007-12-14
Are you running Compiz by any chance? I had the same problem once and found a solution here on these boards...somewhere.

In the terminal type:
```
metacity --replace
```
then load up Totem and get it back to normal size. Now switch back to the terminal and type:
```
compiz --replace
```

Hope this helps.

---

### Post by alexander.forster on 2007-12-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/176204](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/176204) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				:D:D:D thank you very much!

worked like a charm!

have a wonderful day, and i hope you enjoy whichever holiday you celebrate!:KS

---

