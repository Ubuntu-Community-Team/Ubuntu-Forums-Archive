---
title: "problem with internet connection"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by udimtu on 2009-02-11
hi there
ubuntu noob here
have some issues. well not exactly an problem in ubuntu but i want to know if something needs to be done inside ubuntu
situation:
i already have an existing OS.. windows XP. i installed ubuntu yesterday. went fine and internet connection was even automatically detected. when i switched back to windows, the OS cannot detect LAN or was not connected at all. switched off my laptop and turned it on this morning. went to XP first and LAN connection (including internet) was back. switched to ubuntu and internet was ok. switched back to XP and it was gone again. i havent checked again as i need to go to work.
is there something that needs to be done in ubuntu so that i can have both systems connected everytime without any hassle??
thanks.

---

### Post by odium1 on 2009-02-11
wow.. that's odd lol.. what kernel are you running in ubuntu?
type this in the terminal and post the results:
```
uname -a
```

i'm wondering if it has anything to do with the *-11 kernel bug. i shouldn't affect windows but i'm still curious.

---

### Post by Iowan on 2009-02-11
I've read threads with the reverse problem ([here]("http://ubuntuforums.org/showthread.php?t=1066502")  is one) - rebooting from Windows to Ubuntu left no network, but a power-down let Ubuntu access network again.  Like a driver wasn't getting reset.

---

### Post by udimtu on 2009-02-11
thanks for the quick response odium.
unfortunately, i dont know what kernel is it running. ill find out later when i get home.
there's also one thing ive noticed. after my installation (inside windows), i did a reboot as instructed.. then chose ubuntu. a black screen will appear then right? its the grubloader i think. and it should contain ubuntu and other systems on my HD... then i can choose. the grubloader screen appeared but there were no items on it.. it has 4 or 5 options but it seems that the text are missing. kept on pressing enter but nothing is happening. so decided to just press the shut down button. power on again.. chose ubuntu then it went straight to the login screen.. weird right??
i have exatly no idea if this has something to do with this issue.

---

### Post by udimtu on 2009-02-11
thanks Iowan
so the cold boot could do the trick? 
im fine with this but im hoping to find a temporary solution.
ill see what i can find and keep you updated
thanks again

---

