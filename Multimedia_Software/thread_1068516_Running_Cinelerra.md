---
title: "Running Cinelerra"
date: 2009-02-13
forum: Multimedia Software
---

### Post by LobbyDizzle on 2009-02-13
Like all of my posts, I have a stupid question. I installed Cinelerra, but cannot figure out how to run it. 

jared@jared-laptop:~$ sudo cinelerra
[sudo] password for jared: 
sudo: cinelerra: command not found
jared@jared-laptop:~$ 

Any suggestions are greatly welcome.

---

### Post by ilioscio on 2009-02-13
can you post the output of ```
whereis cinelerra
```

if that doesn't work try 
```
sudo updatedb
sudo mlocate cinelerra

```

and post it's output (if it isn't too long)

---

### Post by LobbyDizzle on 2009-02-13
Whoa, I learned a new command from you (whereis) ! Thanks!

jared@jared-laptop:~$ whereis cinelerra
cinelerra:

jared@jared-laptop:~$ sudo updatedb
[sudo] password for jared: 
jared@jared-laptop:~$ sudo mlocate cinelerra
jared@jared-laptop:~$ 

hmm, those don't look right..

Before you ask, I used this command straight from the website: 
wget -q [http://akirad.cinelerra.org/pool/addakirad.deb](http://akirad.cinelerra.org/pool/addakirad.deb) && sudo dpkg -i addakirad.deb && rm addakirad.deb && sudo apt-get update

---

### Post by LobbyDizzle on 2009-02-13
I'm still having trouble trying to figure this out... so I will buuuuummmmp.

---

### Post by ilioscio on 2009-02-14
yeah.. mlocate should've given some output showing files belonging to cinelerra.. let me look into it real quick

---

### Post by ilioscio on 2009-02-14
try clicking on this [link]("apt:cinelerra") and tell me if it asks you to install cinelerra OR if it tells you it is already installed.

---

### Post by LobbyDizzle on 2009-02-14
Whoa, it had me install, and now it f'en works. Thanks man, I greatly appreciate it.

---

### Post by ilioscio on 2009-02-14
no problem, enjoy cinelerra. :)

---

