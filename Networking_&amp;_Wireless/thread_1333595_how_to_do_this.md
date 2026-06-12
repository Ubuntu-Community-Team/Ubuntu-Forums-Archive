---
title: "how to do this?"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by gfunkera on 2009-11-21
i want to remotely control my computer from another computer on my home network. both are running the newest versions of ubuntu..

i tried remote desktop but it was really slow and i didnt see it respond to my clicks and stuff....

any ideas?

:popcorn:

---

### Post by Zyprexa on 2009-11-21
I use SSH to control my Ubuntu Server from a Vista computer, using [Putty]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/"). I am not sure how i set it up, since it's a long time ago, but i remember it was a fairly easy and quick process, eventhough i had little linux experience. To control a desktop i would use VNC.

Edit: regarding SSH i seem to remember using a howto from this forum.

---

### Post by gfunkera on 2009-11-21
whats the difference between using ssh and vnc? do i have to use both or just one? im a little confused..

---

### Post by .nedberg on 2009-11-21
> **gfunkera said:**
> whats the difference between using ssh and vnc? do i have to use both or just one? im a little confused..

ssh is command line, vnc gives you a gui.

I use ssh for all my servers (they have no gui), but I also use VNC to some clients. Vino is the default vnc-server in Ubuntu, it should work OK.

You install ssh with 
```

sudo apt-get install openssh-server
```

---

### Post by gfunkera on 2009-11-21
when i type vino in the command line, it doesnt recognize it when i do the sudo apt-get install vino it comes back saying its already at the newest version... confusion is getting worse...


i installed the ssh server... how do i use it?

---

### Post by .nedberg on 2009-11-22
You can laund vino with
```

/usr/lib/vino/vino-server

```

First you need to configure it with 
```

vino-preferences 

```

If you installed openssh-server, it should already be started. Connect from another machine with:
```

ssh [username@]<ip>

```
Replace username with your username (or leave it out if it is the same as on the machine you connect from). Replace <ip> with the ip of the machine you want to connect to. It will ask for a password, input the password of the user you are connecting with (on the server).

Hope this helps!

---

