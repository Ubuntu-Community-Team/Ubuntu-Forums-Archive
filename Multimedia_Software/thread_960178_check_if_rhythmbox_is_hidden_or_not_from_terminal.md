---
title: "check if rhythmbox is hidden or not from terminal"
date: 2008-10-27
forum: Multimedia Software
---

### Post by superaktieboy on 2008-10-27
hi

i was just mapping some multimedia buttons through xbindkeys, but i have a button thats a bit doesn't do much, and since i use rhythmbox a lot, i wanted to map that key to a if else statement. i wanted it to check if the program was running, it would hide it, or if it was hidden or it wasn't running, it would open the main window.. if got the part working where it check if its running after some google, and to hide it as well.. but i dont how to check if it is running but hidden.. 
the current statement it runs is 

```
if ps ax | grep -v grep | grep 'rhythmbox' > /dev/null; then rhythmbox-client --hide; else rhythmbox; fi; pause
```

that seems to work fine, but if its hidden, it doesn't show the main window.. so my question is if its possible to do this and how?

thanks in advance..

---

