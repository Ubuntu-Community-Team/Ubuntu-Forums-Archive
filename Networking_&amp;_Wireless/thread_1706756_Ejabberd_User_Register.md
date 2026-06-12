---
title: "Ejabberd User Register"
date: 2011-03-14
forum: Networking &amp; Wireless
---

### Post by madana.gopal on 2011-03-14
Hi
I have installed ejabberd server on ubuntu(on oracle VM virtual box manager., and all this is on windows 7)

I could not get to register the initial user for the server.,  below are what I figure some details  that has to do with the issue;

the hosts file contains these;
```
127.0.0.1    localhost
127.0.0.1    madan-laptop
127.0.0.1    jabb<dot>gaachat<dot>com

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```the settings I modified in ejabberd.cfg are;
```
%% Admin user
{acl, admin, {user, "adm", "jabb<dot>gaachat<dot>com"}}.
%% Host name
{hosts, ["localhost","madan-laptop","jabb<dot>gaachat<dot>com"]}
```
My current hostname;
```
root@jmadan-laptop:/etc# sudo hostname
madan-laptop
```When I do the following to register the username;
```
root@madan-laptop:/etc# sudo ejabberdctl register adm madan-laptop 123456
```the error I get is;
**Can't register user "adm@madan-laptop" at node 'ejabberd@madan-laptop': not_allowed**

If I try to register the user on localhost (hostname);
```
root@madan-laptop:/etc# sudo ejabberdctl register adm localhost 123456
```There is no error message displayed., but trying to login at  **localhost:5280<slash>admin**   on the browser ( with the set username: adm@localhost , password: 123456 ) ;

It throws a  "401 Unauthorized" error.

Any idea what could be wrong?. I have been pulling my hair over this for many hours now.

Would really appreciate any help.

---

