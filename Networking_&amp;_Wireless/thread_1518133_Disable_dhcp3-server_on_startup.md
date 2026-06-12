---
title: "Disable dhcp3-server on startup"
date: 2010-06-26
forum: Networking &amp; Wireless
---

### Post by purelinuxuser on 2010-06-26
I have an old Linksys WUSB54G USB wireless card lying around, and occasionally I like to use it as an access point for my laptop.  For assigning IP addresses I use dhcp3-server.  The only problem is that the server attempts to start itself up on boot, which I do not want- I want to start it up manually if I need it.  Does anyone know how to disable this service on boot?

Thanks in advance.

---

### Post by Iowan on 2010-06-26
In olden days, I might have suggested checking in the /etc/rc#.d directories. Now with upstart, I'm not quite sure where to check.

---

### Post by purelinuxuser on 2010-06-26
> **Iowan said:**
> In olden days, I might have suggested checking in the /etc/rc#.d directories. Now with upstart, I'm not quite sure where to check.

It turns out those directories still exist, and they have items within them- perhaps I'll run a good ol' "find /etc/rc*.d -name dhcp*."  I guess the proper way would be through upstart though... :(

---

### Post by CharlesA on 2010-06-26
I guess you could always stick this in .bashrc:

```
service dhcp3-server stop
```

Not sure how well it would work.

If that doesn't work, you can always rename dhcpd.conf to something else and the server won't start.

---

### Post by purelinuxuser on 2010-06-26
> **CharlesA said:**
> I guess you could always stick this in .bashrc:

```
service dhcp3-server stop
```

I'm not sure if that's run at startup though.  Plus, I don't want the service to start and then be stopped, I don't want it to start at all.  Period.

---

### Post by CharlesA on 2010-06-26
Is this a desktop install? Check start up programs and see if DHCP Server is listed there.

---

### Post by purelinuxuser on 2010-06-26
> **CharlesA said:**
> Is this a desktop install? Check start up programs and see if DHCP Server is listed there.

Not there.  Besides, this is a system-wide service, so it wouldn't appear in something user-specific like that. ;)

---

### Post by CharlesA on 2010-06-26
Bit of a pain in the ***, but if you remove the execute permission from /etc/init.d/dhcp3-server the service won't start. You need to add the execute permission back to start it.

---

### Post by purelinuxuser on 2010-06-26
> **CharlesA said:**
> Bit of a pain in the ***, but if you remove the execute permission from /etc/init.d/dhcp3-server the service won't start. You need to add the execute permission back to start it.

Works for me though, since it just prevents that script from running at startup.  Thanks for the suggestion! :)

For the record, it's pretty easy to remove executable flags, just run a
```
sudo chmod -x /path/to/file
```

Edit: Yeah, this worked for me.  Got a "Cannot execute /etc/rc2.d/dchp3-server permission denied" error, but it's not that big of an issue.  Thanks for your help!

---

### Post by Nimonie on 2010-08-08
I know this is a bit of an old post but just want to let you know that if your server is the same setup as mine the dhcp3 startup is in rc.2 all you have to do is change the name from S##dhcp3-server to K##dhcp3-server you can do this with the move command and it will keep it from loading and take care of that error as well. Then if you ever want to set it back up just change it back to S using the same commands.  :)

---

