---
title: "How to log out and hibernate using ssh (simple hopefully)"
date: 2011-08-11
forum: Networking &amp; Wireless
---

### Post by Matt Pellegrini on 2011-08-11
So i'm connecting to a local server via ssh and when i'm done i hibernate the server but once i do the command sudo pm-hibernate i'm then stuck in the terminal window on the client unable to do anything (even  ctrl + C doesn't work). So is there a better way to hibernate the server but log out just before?

I'm sure this is just a simple solution, hopefully anyway.

Thanks in advance 
Matt

---

### Post by ajgreeny on 2011-08-11
I have no idea if it will work, but can you issue the ```
sleep 60; pm-hibernate
``` from a root terminal which you may be able to get with ```
sudo -i
``` once you are logged in with ssh to the server.  I'm not sure if the "sudo -i" will even work over ssh

There may also be many other reasons why it will not work that I have not thought about, but I am brainstorming here.

---

### Post by Matt Pellegrini on 2011-08-12
That command still doesn't let you do anything before hibernation, the sleep command doesn't allow input while waiting. I need to be able to pm-hibernate; exit to log out before the server goes into hibernation but this doesn't work and thus the terminal on the client is stuck, i can close it and open another terminal, but that's a pain and not very slick.

Thanks for trying though

---

### Post by aeiah on 2011-08-12
normally, commands will halt if you logout, so you'd have to detach the command using either screen, tmux or nohup.

in this case, nohup would be the best solution. something like this, probably:
```

nohup (sleep 10 && pm-hibernate) &
exit

```

---

### Post by Matt Pellegrini on 2011-08-12
I just get an unexpected token 'sleep' error, man page for nohup isn't helpful either, do i need the brackets? Thanks though this looks like the solution i just can't get it working yet.

---

### Post by aeiah on 2011-08-12
i wasnt able to test, you might need the brackets elsewhere.. i just thought that if you didnt use them, you'd 'nohup' the sleep command and not the hibernate command. maybe try something like:
```

(sleep 10 && nohup pm-hibernate) & exit

```

---

### Post by aeiah on 2011-08-12
oops, that obviously wouldnt work (you'll have exited before the nohup command)

this works, but creates a nohup.out file
```

(nohup sleep 5; mp-hibernate) & exit

```

---

### Post by Matt Pellegrini on 2011-08-12
this still doesn't work and i'm still left with no control over the terminal. As in the screenshot.

The reason is that i'm still logged into 'Desktop' which i just hibernated...

Thanks for the continued effort

---

### Post by lykwydchykyn on 2011-08-12
Don't know if this will work in your situation, but I've used the tilde commands now and then to end a stuck session:

[http://www.cyberciti.biz/faq/openssh-linux-unix-osx-kill-hung-ssh-session/](http://www.cyberciti.biz/faq/openssh-linux-unix-osx-kill-hung-ssh-session/)

---

### Post by papibe on 2011-08-12
Try this:
```
$ screen -dm  bash -c 'sleep 10; pm-hibernate' ; exit
```
You may need to install screen:
```
$ sudo apt-get update
$ sudo apt-get install screen
```
Regards.

---

### Post by Matt Pellegrini on 2011-08-12
This is all a lot more complicated than i expected, it's actually just simpler to do sudo pm-hibernate and then physically close the inactive terminal. If only pm-hibernate had a timer on it, such that i could pm-hibernate (in ten seconds) and logout during those ten seconds.

thanks for all the help though, i think the last suggestion might work but the problem is you need to log in as root to make pm-hibernate work so you only exit one level back down to user@Desktop before getting stuck. Like i said much simple to just let it be and close the terminal window after.

---

