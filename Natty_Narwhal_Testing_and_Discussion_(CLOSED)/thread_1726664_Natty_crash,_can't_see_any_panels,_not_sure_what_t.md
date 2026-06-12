---
title: "Natty crash, can't see any panels, not sure what to do"
date: 2011-04-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by k3jsparks on 2011-04-11
I installed Natty. I knew it was beta but I wasted to test it out. Now I have a problem. I was playing with the compiz-config to get the desktop cube. It unchecked  something (can't recall what now) but it also said it would affect something about large monitors (sorry I can't recall the exact things that went on). I said OK because I don't have a overly large monitor and did not think I would need that setting.

As soon as i did that Compiz-config crashed, well everything I could see crashed. I have my desktop pic--no panels, nothing else. Everything seems to be running (I assume) but I can't see anything. I right-clicked and selected to Change Desktop Background, then selected "Get More Backgrounds Online" so I could get online. All I can do is <Ctrl> + <Alt> + F1 to get a screen to type commands, but I do not know what to type to get this running again. I did type sudo apt-get upgrade and it upgraded a lot of files, but still nothing is seen. What can I try now? I am not knowledgeable enough to fix anything (and yes, I learned my lesson and would love to go back to 10.x but I dont know how to even do that without a complete reinstall from a thumb drive--and I would lose everything then.)

---

### Post by Elfy on 2011-04-11
move to natty

---

### Post by r-senior on 2011-04-11
From one of your virtual terminals (Ctrl-Alt-F1, etc), do:

```

sudo service gdm restart

```

You should then get back to a login screen. Choose "Ubuntu Classic No Effects" from the menu at the bottom and log in. That should work OK. You should then be able to run CCSM again and undo what you did. Log out and back in, selecting "Ubuntu" from the aforesaid menu.

Repeat as required.

---

### Post by Version Dependency on 2011-04-11
The above post should allow you to go back and undo whatever caused the problem.  I had a similar problem when I enabled the compiz wallpaper plugin.

---

### Post by garvinrick4 on 2011-04-11
If you can open a terminal with ctrl/alt/t and
```
gnome-session-save --kill
```above will get to log out.
```
ccsm
```above you can make sure Ubuntu Unity plugin is checked and maybe resolve other compiz issues.

---

