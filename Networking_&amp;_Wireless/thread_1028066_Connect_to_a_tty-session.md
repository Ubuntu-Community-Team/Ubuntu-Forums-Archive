---
title: "Connect to a tty-session"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by mtreece on 2009-01-02
Hi,

Does anyone know of a way to connect to a tty-session (e.g. ctrl+alt+f2) after SSH'ing into a server -- assuming that a screen session hasn't already been initiated?

I would like to access a session I have open on a remote server on tty2 (ctrl+alt+f2), but I didn't start a "screen" command on tty2 prior to leaving the server.

Is there any hope?  I've tried prying around on Google, and the only results I've been able to find are websites that suggest using "screen" or those that you have to subscribe to a pay-service to access their answers.

Thank you!:)

---

### Post by mtreece on 2009-01-02
PS -- Reviewing my thread, I might not have put this thread in the right category (and if so, I apologize), but it seemed a "networking" problem (sort of) at the time.

---

### Post by mtreece on 2009-01-03
Bump

---

### Post by lswb on 2009-01-03
I'm not understanding; Are you saying that you disconnected from an SSH session, without running screen, but the session is still somehow running? In my experience once you disconnect from the server, the tty is shut down/freed and user processes killed (unless nohupped) just as if you had logged off. and no longer accessible, without using screen (or something like it)

---

### Post by mtreece on 2009-01-04
> **lswb said:**
> I'm not understanding; Are you saying that you disconnected from an SSH session, without running screen, but the session is still somehow running? In my experience once you disconnect from the server, the tty is shut down/freed and user processes killed (unless nohupped) just as if you had logged off. and no longer accessible, without using screen (or something like it)

Ah, I apologize for not being clearer.

What I am referring to is this:
On the server, I did Ctrl+Alt+F2, and this brings up "tty2", a non-graphical basic terminal for the system (the same happens with any F1-F6, each bringing up tty1-6, respectively).  I log in to tty2, run a command, then walk away from the computer (with everything still logged in, etc).  How (if possible) can I open this session and continue it via SSH?  Because the session is still technically running on the server, on "Ctrl+Alt+F2", yet I am several miles away from my server now.

---

### Post by lswb on 2009-01-05
I can't say it is impossible but without running screen first or making some other provision, I know of no way to take over a running tty or pty. What you could do is ssh in to a new session and kill the old one and any processes you started from it.

---

### Post by mtreece on 2009-01-05
> **lswb said:**
> I can't say it is impossible but without running screen first or making some other provision, I know of no way to take over a running tty or pty. What you could do is ssh in to a new session and kill the old one and any processes you started from it.

Ah, okay, I guess this could work.  I'm not desperate to take total control over the session, but the idea struck my mind the other day, and I kept wondering if it was possible.

Thank you for your suggestion!

---

### Post by davepc on 2010-05-27
Here's a solution if your still looking for one:
[http://www.ryanwalsh.ca/blog/?p=7](http://www.ryanwalsh.ca/blog/?p=7)

> Some of us have run across situations where we want to be able to keep user-mode programs running in a Linux TTY session, but still want to be able to manage them remotely through SSH or other means.

One solution is the ‘linuxvnc’ utility, which can grab a TTY session and display it for use in a VNC window. I will be covering this utility, as tested on Ubuntu 7.04 Feisty (although it should work for virtually any distro).

For starters, let’s grab linuxvnc from the repositories with apt:

   ```
 sudo apt-get install linuxvnc
```

Once that is done, fire it up: (root access is required to grab TTYs)

   ```
 sudo linuxvnc X
```

Where ‘X’ is the TTY # you want to grab. linuxvnc should indicate that it’s listening on port 5900.

You can now connect with any VNC client, such as RealVNC, KRDC, or whatever. One thing I’ve noted is that KRDC has trouble with linuxvnc sessions if it attempts to use ‘Tight’ VNC encoding. I would recommend using zlib instead.

Of course if you’re using VNC over the Internet, I strongly recommend tunneling it through SSH. That, however, is a tip for another day.

---

### Post by geet89 on 2010-05-27
give me some time to answer

---

### Post by tsenapathy on 2012-02-14
Thanks davepc.  This one works fine.

---

