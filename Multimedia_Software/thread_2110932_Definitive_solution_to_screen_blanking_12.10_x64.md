---
title: "Definitive solution to screen blanking 12.10 x64"
date: 2013-01-31
forum: Multimedia Software
---

### Post by Rebecca_D on 2013-01-31
Can someone help with the problem of screen blanking in Ubuntu 12.10. I have set 'Turn screen off when inactive for' to never and in order to use my system (desktop) effectively, I have used the advice given in Ask Ubuntu, [**Disable blank screen in 12.04**]("http://askubuntu.com/questions/248601/definitive-solution-to-screen-blanking-12-10-x64") i.e.

    xset -dpms s off s noblank s 0 0 s noexpose

this however only works for a session and I have to go through the same thing again each time I start up. Seems mighty strange that an OS has a setting that doesn't work. I am new to Ubuntu so can I have any advice or instructions in clear terms. Do not assume I know anything about the file system or anything else.

Thank you.

---

### Post by bryanl on 2013-01-31
I put the 'xset s 0 0' at the end of /etc/profile so it gets run at every login. Solved the problem for me.

```
gksudo gedit /etc/profile
```
provide the proper password, scroll to the end of the file, add the line, save, exit

next login should not blank screen

---

