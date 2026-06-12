---
title: "squid start error"
date: 2012-03-30
forum: Networking &amp; Wireless
---

### Post by rzippert on 2012-03-30
Good afternoon.

I'm trying to set up a network server with ubuntu 11.10. I had to install 10.10 and then upgrade to 11.04 and then 11.10. After that got dhcpd and bind up and the next step would be squid, however I'm getting some weird errors.

It's been installed from apt-get and I have configured squid.conf with some basic settings to match my network, however when I tried to start the squid service it would say "squid start/running, process 6730", but it stops immediatly after that with no error prompt.

I checked the syslog and there I found out that it didn't have write permissions to its logs folder. Apparently the folder was created for a user named "proxy" and squid created a user named "squid". To fix that I did a chmod 777 to the folder, but now it is giving me:

"FATAL: Failed to verify one of the swap directories, check cache.log for details. Run 'squid -z' to create swap directories if needed, or if running squid for the first time"

Even if I run "squid -z" as root it gives me this same error. cache.log simply repeats this message with no more info after starting some other things.

Does anybody know where can I set up this "squid" user or another solution?

I appreciate your attention.

---

### Post by SeijiSensei on 2012-03-31
Typically the squid user will be added to /etc/passwd and /etc/group when squid is installed.  To check this, run "grep squid /etc/passwd".  If that returns nothing, you'll need to create the squid user yourself with "adduser squid".

Now lets turn to the swap directories.  There should be a directory called /var/spool/squid with a lot of subdirectories.  You can recreate the cache by running

```

sudo rm -rf /var/spool/squid/*
sudo squid -z

```

Check to make sure that /var/spool/squid and all its subdirectories are writable by the squid user.  If they are not, then run

```
sudo chown squid.squid -R /var/spool/squid
```

Then try starting squid again.

More info:  [https://help.ubuntu.com/community/Squid](https://help.ubuntu.com/community/Squid)

---

### Post by rzippert on 2012-04-17
> **SeijiSensei said:**
> Typically the squid user will be added to /etc/passwd and /etc/group when squid is installed.  To check this, run "grep squid /etc/passwd".  If that returns nothing, you'll need to create the squid user yourself with "adduser squid".

Now lets turn to the swap directories.  There should be a directory called /var/spool/squid with a lot of subdirectories.  You can recreate the cache by running

```

sudo rm -rf /var/spool/squid/*
sudo squid -z

```

Check to make sure that /var/spool/squid and all its subdirectories are writable by the squid user.  If they are not, then run

```
sudo chown squid.squid -R /var/spool/squid
```

Then try starting squid again.

More info:  [https://help.ubuntu.com/community/Squid](https://help.ubuntu.com/community/Squid)
Finally could try again to fix this. Your tips worked to solve the cache access problem, however squid kept starting and then immediatly stopping (but now simply weren't giving a single error message anywhere). I sort of removed a lot of things, even by force, and resintalled and apparently it's working.

Thank you very much =)

---

