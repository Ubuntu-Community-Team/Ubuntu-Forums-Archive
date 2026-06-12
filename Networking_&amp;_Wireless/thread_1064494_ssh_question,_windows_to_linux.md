---
title: "ssh question, windows to linux"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by jmd9qs on 2009-02-08
hi all,

i am ssh'ing to my brothers linux box via putty in windows. i want to know if it is possible to open up a "joint-terminal" or even something like gedit to write back and forth. i have x11 forwarding enabled with putty, and it has been tested (it works!). 

also, i was wondering how i might take over a running programs x-session via ssh (ie - running firefox already on linux remote, takeover firefox via ssh on the host)


anyone know how i could go about this?


jmd9qs

---

### Post by doas777 on 2009-02-08
> **jmd9qs said:**
> hi all,

i am ssh'ing to my brothers linux box via putty in windows. i want to know if it is possible to open up a "joint-terminal" or even something like gedit to write back and forth. i have x11 forwarding enabled with putty, and it has been tested (it works!). 

also, i was wondering how i might take over a running programs x-session via ssh (ie - running firefox already on linux remote, takeover firefox via ssh on the host)


anyone know how i could go about this?


jmd9qs

well first, if I'm catching your drift about the gedit thing, i use winscp when doing file maintenence on remote boxes via ssh.

not sure on the rest, but if you use vnc you could share the same session.

good luck

---

### Post by TCSnyder on 2009-02-08
I am not sure what you mean by "joint Terminal" but you could just leave messages on the desktop.

for forwarding programs like firefox try this

```
ssh -X username@Hostname "name of program"
```

example 

```
ssh -X me@localhost firefox
```

hope that helps

---

### Post by jmd9qs on 2009-02-08
ya, thanks! i figured that out before... what i want to do is ssh into a machine that another user is on, and then communicate with them in some way. i don't want to use a chat client or irc or anything, i want to be able to use the command line if possible. i've looked into the "write" and "talk" commands, but now my issue is that i can't initiate a terminal in one user and switch to another via ssh without the terminal session terminating. (i've tried "ssh [email]user@hostname.com[/email] nohup gnome-terminal", but i dont think it worked; i ssh'd into the same user and ran ps -e, but gnome-terminal wasn't running).

any ideas?

---

### Post by TCSnyder on 2009-02-08
Here is a link to (i think) what you are looking for.

[http://ubuntuforums.org/showthread.php?t=299286]("http://ubuntuforums.org/showthread.php?t=299286")

Good Luck

---

### Post by jmd9qs on 2009-02-09
thanks! that's probably what i'll end up doing. appreciate your help.

---

