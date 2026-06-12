---
title: "Removing and reinstall BIND9 -- no default config files anymore"
date: 2010-06-20
forum: Networking &amp; Wireless
---

### Post by sysko on 2010-06-20
Hi Guys,

Running Ubuntu 8.04.4 LTS

I was having a bit of an issue with my home lab DNS setup and I removed and reintalled the BIND9 package just to redo my setup from scratch.

```
apt-get remove bind9
```
The above command did not return any errors, which was good.

From there I did  a little  rm -Rf /etc/bind just to delete the files that 'apt-get remove bind9' did not delete.

I reinstalled BIND9 with with:
```
apt-get install bind9
```
That didn't bark any errors either so I thought I should be good...


My issue is that I don't have the default config files being reinstalled in /etc/bind/

/etc/bind/named.conf
/etc/bind/named.conf.options
...

Those files were there initialy, the first time I installed the service (a few months ago) but now no matter how I uninstall/reinstall it, the default config files aren't being installed/created.

Would anyone have an idea on why 'apt-get install bind9' does not create these files upon reinstall?


Regards,


Sysko

---

### Post by sysko on 2010-06-26
Any idea, anyone?

Regards,

Sysko

---

### Post by xtropx on 2012-07-22
BUMP, I have exactly the same problem.

EDIT: FOUND IT:

> try apt-get remove --purge bind9 and/or apt-get install --reinstall bind9

James Dupin

---

