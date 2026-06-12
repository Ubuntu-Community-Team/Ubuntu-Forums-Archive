---
title: "LIRC config"
date: 2010-04-12
forum: Mythbuntu
---

### Post by Iceman692 on 2010-04-12
I'm setting up my new Mythbuntu box with an IR remote. I have 2 newbish questions:

1. I want a certain button to launch mythtv (or pull it back to the front if its behind other windows). I have the following code set up but linux program paths are so foreign to me. What path should I put in here to open MythTV?

```
begin
    remote = MCE_via_iMON
    prog = irexec
    button = WINDOWSMCE
    config = ???
    repeat = 0
    delay = 0
end
```

If anyone has an info page or would like to explain to me how to find program paths, i would be greatly appreciative.

2. The reason I need a button to open/bring MythTV to the front is because I plan to add a menu option to MythTV that allows me to launch Boxee. My second question is: I assume I have to add a whole new list of entires in the LIRC config file for Boxee. If MythTV is open in the background, with boxee in front, will all of my ir strokes be applied to mythTV as well or only Boxee? Is it even possible to have a program on top of MythTV or is it configed to be "always on top"?


Thanks!

---

