---
title: "How to leave processes running when killing SSH"
date: 2012-12-23
forum: Networking &amp; Wireless
---

### Post by jacksonleigh on 2012-12-23
Hi everyone

I am using ubuntu to set up alot of remote access to my home files and its great.
I mainly use SSH, and sometimes with the '-X' flag for some GUI stuff.

One thing I would like to be able to do though, to leave the processes on my server running when i logout from my remote machine. I would like this for uses such as, a CLI torrent client (such as rtorrent) and a CLI DC++ client for my school. Or logging into my server, configuring my LAMP server and leaving it that way even though i turn my remote machine off.

So basically, I guess if the account is running, and I could just use SSH to access it, then i can just "leave" it.

any help is much appreciated. even just a point in the general direction
Thansk!

---

### Post by Lars Noodén on 2012-12-23
For text-based programs that you launch from the shell, you can use [nohup](http://manpages.ubuntu.com/manpages/precise/en/man1/nohup.1.html).  Launching them with nohup will keep them from shutting down when you log out.

```

nohup /usr/local/bin/sometool &

```

Another option is [screen](http://manpages.ubuntu.com/manpages/precise/en/man1/screen.1.html).  With that you can reattach a detached session and resume work where you left off.  First, start screen.  Then run the programs you want.  That way you can detach and reconnect whenever you want.

tmux is also an option like screen, but simpler in the assortment of capabilities it offers.

---

### Post by jacksonleigh on 2012-12-25
but with both of those methods when i shut off my remote machine, the host machine still logs me out of the SSH and closes transmission.

---

### Post by Lars Noodén on 2012-12-25
When you shut off the remote machine, the one you have the ssh server running on and have logged into, then your remote session will end.  But if you use nohup or screen, the program or session will stay running if you shut off the local machine (client) instead.

---

