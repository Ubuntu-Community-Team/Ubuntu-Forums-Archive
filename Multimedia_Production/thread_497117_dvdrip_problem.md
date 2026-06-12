---
title: "dvdrip problem"
date: 2007-07-09
forum: Multimedia Production
---

### Post by tetsura on 2007-07-09
this is probably something really simple but im kinda stuck.
im trying to rip a dvd to an external hard drive but it just hangs when i try to rip it, i get these errors in preferences:

Default data base directory: has whitespace : NOT Ok
Default directory for .rip project files: has whitespace : NOT Ok


can anyone point out what's wrong?
thanks

---

### Post by Norst on 2007-07-10
make sure the name of the directory you have set to rip to does not have whitespace (spaces!). Use underscores or dashes if you like but not spaces. eg. /folder/my ripped dvds/  should be renamed /folder/my_ripped_dvds/

I'm sure there are other ways of solving this but this is the easiest I can think of.

---

### Post by tetsura on 2007-07-10
aha. i knew it would be something really obvious like that, i was thinking white space refered to something about the hard drive or something lol. il try that when i get home but im pretty sure thats the problem, thanks :)

---

### Post by torelli on 2007-07-14
if you don't want to rename your folders just use symbolic links:
  ln -s /home/my\ ripped\ dvds /home/my_ripped_dvds

---

