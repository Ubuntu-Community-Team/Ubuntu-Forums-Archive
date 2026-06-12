---
title: "Windows clients lose ability to resolve local domain names"
date: 2010-12-02
forum: Networking &amp; Wireless
---

### Post by fongd on 2010-12-02
I have an internal domain (dev.lan) for which my Ubuntu server is authoritative. We have a number of subdomains under that domain (test.dev.lan, svn.dev.lan, etc.). The server also acts as the primary DNS server for my office. It was originally set up under Ubuntu 8 and worked great.

However, ever since we upgraded to Ubuntu 10, our Windows clients periodically lose the ability to resolve domains on the dev.lan domain. Internal IP addresses can still be pinged from the Windows machines so it does not appear to be a network-connectivity issue. External domain names continue to resolve without any problems. The only workaround is to restart networking on the Windows clients. It's frustrating because it happens several times a day.

bind9 logs no obvious error messages. Any ideas what's happening here and how to fix it?

---

### Post by endotherm on 2010-12-02
first off. how dynamic is your domain? do addresses change several times a day?

try running this command on your wintel hosts when they loose query capacity:
```
ipconfig /flushdns
```and try to nslookup the server name again
```
nslookup <servername>
```

do you have a default domain search extension on set in system.cpl and in your network adapters IP settings as well?

---

### Post by fongd on 2010-12-02
> **endotherm said:**
> first off. how dynamic is your domain? do addresses change several times a day?

The addresses don't change several times a day, but I do have dev.lan set up as a wildcard domain:

*               IN      A       192.168.88.2

For reference purposes (so that we know which subdomains are considered "reserved" by us), I also have the following additional subdomains explicitly defined:

svn             IN      A       192.168.88.2
trac             IN     A        192.168.88.2

> **endotherm said:**
> do you have a default domain search extension on set in system.cpl and in your network adapters IP settings as well?

None that I know of. Should I add a default search extension?

---

### Post by endotherm on 2010-12-02
> **fongd said:**
> The addresses don't change several times a day, but I do have dev.lan set up as a wildcard domain:

*               IN      A       192.168.88.2

For reference purposes (so that we know which subdomains are considered "reserved" by us), I also have the following additional subdomains explicitly defined:

svn             IN      A       192.168.88.2
trac             IN     A        192.168.88.2



None that I know of. Should I add a default search extension?
if you don;t have a dns suffix set for the host in the system..cpl. then searching domains by shortnames can be a real pain, so I would give it a try and see if that doesn't help. 
otherwise check your nslookup output on the client. is teh responding server responding, and is the client asking for the FQDN? if so, then search domains prolly aren't your problem. I'm curious if its saying the domain is nx or the remote host.

---

