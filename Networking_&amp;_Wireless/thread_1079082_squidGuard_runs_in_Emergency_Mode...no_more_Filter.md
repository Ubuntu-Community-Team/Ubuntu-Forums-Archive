---
title: "squidGuard runs in Emergency Mode...no more Filtering"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by NagWolf on 2009-02-24
Good day
I hope there's an Advanced Squid and squidGuard user/administrator somewhere on this forum

I'm running Squid 2.6 STABLE14 and squidGuard 1.3 and the db in use is a scaled down version of the "shallalist.tar.gz"
All traffic is just passed through and none of the Group filters and Blocks work
Two errors/problems I can see: 1) the squidGuard.log shows a "syntax error in configfile /etc/squidGuard.conf line 50" after all the dbfiles were loaded. This then causes I gather the Emergency Mode that squidGuard is running in.
Checking the squidGuard.conf file on line 50 shows only acl {   and I cecked and even copied this over from a sample .conf file

A google searched solution suggested that it could be due to access rights to the DBs...
I have checked that all the db files are compiled after edits by running this cmd: /usr/sbin/squidGuard -c /etc/squidGuard.conf -C all
This took forever and never came to the point where it returned back to the shell prompt, so after about two hours I pressed Ctrl+C

The db files are there with current dates
After this I did a chown squid.root *.db and then a squid -k reconfigure as per said Google suggestions

A complete restart of the server was done as well.
Now though I get a Msg in the squidGuard.log that the /etc/squidGuard.conf can't be opened and still the 'going into emergency mode' msg

I did also check in the /etc/squid/squid.conf file and found that the cache_effective_user is ... squid , and then passing a chown squid.squid /etc/squidGuard.conf returns that squid.squid : invalid user  (that's why I tried squid.root which did not return any errors, except that now, as said, the fle can't be opened anymore)


I'm at wit's end...
So in summary: How do I get squidGuard to open it's own squidGuard.conf file again? The only user on this setup is the root
How do I trace what's causing it exactly to start in emergency mode seeing as the setting on line 50 does not contain syntax errors?

Please and thank you

---

### Post by NagWolf on 2009-02-25
Nobody using Ubuntu as Proxy server?

---

### Post by scottishnarn on 2009-02-25
the owner of the files needs to be proxy.proxy not squid.root so run
```
 sudo chown -R proxy.proxy /var/lib/squid/db
```

---

### Post by NagWolf on 2009-02-26
thank you for the reply, but then I get the reply that proxy.proxy :invalid user

on another forum someone said that I should actually use group:user notation as the use of semi-colon is now the new way, but delivered the same results, invalid user

---

### Post by scottishnarn on 2009-02-27
Can I ask what version of ubuntu you're using? (My squid server is running 8.04 but I have a desktop 8.10 that I could install squid on to have a look if that's what you're running.)

---

