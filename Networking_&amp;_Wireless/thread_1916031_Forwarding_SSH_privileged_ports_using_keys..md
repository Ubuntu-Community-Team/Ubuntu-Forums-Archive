---
title: "Forwarding SSH privileged ports using keys."
date: 2012-01-27
forum: Networking &amp; Wireless
---

### Post by tehowe on 2012-01-27
I've recently stopped using passwords for SSH, instead preferring to distribute keys to ~/.ssh/authorized_keys file for the various machines I need access to.

However, you need to be root to forward a port such as 80, which I want to do to get into my server's MythWeb interface. Unfortunately

```
ssh me.myvnc.com -L 80:localhost:80
```

gets us "Privileged ports can only be forwarded by root." as we'd expect. So we can try  

```
sudo ssh me.myvnc.com -L 80:localhost:80
```

At this point I'm prompted for my password. This results in "Permission denied (publickey)."

Of course, root doesn't have a publickey set up on the remote server!

But Ubuntu also doesn't have a root user! So how does one get around this - do you have to create a root user and generate keys? That doesn't seem ideal since root doesn't exist on Ubuntu for security reasons as I understand things.  Thanks!

---

### Post by kevdog on 2012-01-27
Not an ideal solution, but could you just plain ssh into the box, and then as root set up a reverse ssh tunnel?

---

### Post by tehowe on 2012-01-27
> **kevdog said:**
> Not an ideal solution, but could you just plain ssh into the box, and then as root set up a reverse ssh tunnel?

I ran into the same problem, but in the other direction.

Turns out the easiest way to accomplish what I want is

```
ssh -L 8080:localhost:80 me.myvnc.com
```

then I can just punch "localhost:8080" into the browser to get my remote Apache server and MythWeb. 8080 isn't privileged, so no need to be root.

This isn't going to let me tunnel port 80 directly over ssh, but now I'm on a mission to figure that out as well. >:)

---

