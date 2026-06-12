---
title: "is there any way to run this from myth"
date: 2008-02-05
forum: Mythbuntu
---

### Post by onesojourner on 2008-02-05
cd ~/xwii && ./xwii profiles/classic.xwii

This is the command I type in terminal to get my controller working. is there any way I could make it a one click option in myth?

---

### Post by superm1 on 2008-02-05
> **onesojourner said:**
> cd ~/xwii && ./xwii profiles/classic.xwii

This is the command I type in terminal to get my controller working. is there any way I could make it a one click option in myth?
Add it to a session startup script.  The mythbuntu session checks for a file

~/.mythtv/session to launch customized commands just like this.

Make that file, and in it make these contents

```
#!/bin/sh
cd ~/xwii && ./xwii profiles/classic.xwii

```
Make the file executable (```
chmod +x ~/.mythtv/session
```) and log out and back int.  Thing should work.

---

### Post by onesojourner on 2008-02-06
I dont want it it run all the time thats the problem. once I run that I have to hit to buttons on my remote to synce it then it will stay connected until I close the terminal.

---

### Post by superm1 on 2008-02-06
> **onesojourner said:**
> I dont want it it run all the time thats the problem. once I run that I have to hit to buttons on my remote to synce it then it will stay connected until I close the terminal.
Ah.  Well this being the case, there are a set of xml files in /usr/share/mythtv.  Add your item wherever you please.

probably something like xterm -e "command"& so it pops up in a terminal that you can easily close.

---

