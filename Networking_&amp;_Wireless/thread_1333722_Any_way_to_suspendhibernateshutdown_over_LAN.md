---
title: "Any way to suspend/hibernate/shutdown over LAN?"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by kwaanens on 2009-11-21
I managed to set up wakeonlan, but I want to take this a step further by being able to run a simple command to suspend, hibernate or shutdown my file server/ multimedia station over LAN. Is there any simple way to do this?

Both computers run Karmic if that matters.

Thanks!

---

### Post by twidget on 2009-11-21
set up ssh on your server. then log in over ssh and use 
```
sudo shutdown -P now
```
to shut down.

---

### Post by kwaanens on 2009-11-21
> **twidget said:**
> set up ssh on your server. then log in over ssh and use 
```
sudo shutdown -P now
```
to shut down.

Thanks, that will get me about 1/3 there, at least :)
How do I suspend and hibernate over ssh?

And is there any way to do this in one easy shell script?

---

### Post by Lars Noodén on 2009-11-22
> **kwaanens said:**
> Thanks, that will get me about 1/3 there, at least :)
How do I suspend and hibernate over ssh?

And is there any way to do this in one easy shell script?

That method works as a shell script.  Shell scripts can be run via ssh either manually or as an argument to ssh.  

You'll have to experiment to see what happens on your system and you may need to adjust the bios. That varies from brand to brand and model to model, so it means sitting physically at the computer and experimenting with suspend/hibernate/shutdown until it works the way you like it.  

One thing to double check is if your hardware requires an explicit power-off or halt. (-P or -H).  Some hardware will need one or the other or both and the OS will turn off but the power still run...

When testing scripts or parameters for shutdown, you can try -k to avoid actually shutting down the system. It's more useful in a mult-user environment.

If you have another machine available, even a router, on the same subnet with a wake-on-lan tool and if the server's network hardware can be activated with [wake-on-lan](http://manpages.ubuntu.com/manpages/karmic/en/man1/wakeonlan.1.html), then you have ways to turn the machine on and off remotely.

From /etc/[sudoers](http://manpages.ubuntu.com/manpages/lucid/en/man5/sudoers.5.html):
```

%downers ALL=(ALL) NOEXEC: NOSETENV: NOPASSWD: /sbin/shutdown -[rhHPkc] [+0-9n][0-9\:ow]*

```

In the above (barring errors in the configuration) members of the group downers can have the machine suspend, hibernate or shutdown, if shutdown allows it.  
You can change the NOPASSWD to PASSWD, if you want the action confirmed by the user's own password.

---

