---
title: "can ping/nslookup but not apt-get"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by leeby on 2009-12-14
Hi all, 
 
I'm running ubuntu 9.10 server in vmware workstation (setup with NAT) which yesterday worked correctly, I could apt-get and use lynx etc. Part way through today I can no longer apt-get or use lynx. The only difference is I have been setting up this server as a bugzilla box, so I now have Apache2 and mysql running.
 
When i try to apt-get I recieve
```
connect (101 network is unreachable)
```and then later on in the list I get:
```
connect (111 connection refused)
```when I try to connect through lynx I get 
```
ALERT! unable to connect to remote host
```I can ping an external address ([www.google.com]("http://www.google.com")) and run nslookup.
My initial thought is that I have a proxy problem as my office uses a proxy, however this was working this morning so maybe I've done something when setting up bugzilla (although if i stop the apache process it still doesn't work) Google isn't being my friend anymore, so hopefully someone here can help?
 
Let me know if anymore info is needed, I've tried to include everything that has happened so far.
Thanks

---

