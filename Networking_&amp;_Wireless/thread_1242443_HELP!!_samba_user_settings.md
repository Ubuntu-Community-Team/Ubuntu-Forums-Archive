---
title: "HELP!! samba user settings"
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by bird_in_the_windows on 2009-08-17
Alright 
     i created two samba users [mermaid and emach] for the 2 unix users in mind [ariell and emachine]
     I dont want them to be able to login at the physical machine
I  just want them to be able to access files over samba

so far ive been told: 
they dont need a valid login shell
home directory not needed
the shell can be /sbin/nologin
home directory should be /dev/null

     and so i tried the /sbin and /dev/null while making the unix accounts
but after they didnt show up on the unix users list
so i gave them each a home directory 
/home/temp/mermaid 
/home/temp/emach
(wont let me give a blank answer) and the normal login shell
which works but they can login locally


i dont want them to be able to login at the machine
i just want them to be able to access files over samba

suggestions
i wont be able to answer right away 
so just keep the em coming

---

