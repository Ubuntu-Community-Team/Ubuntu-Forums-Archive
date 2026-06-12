---
title: "Packetfence"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by fcastillo4969 on 2010-02-23
I am new to packtefence. I installed packetfence 1.8.7 to ubuntu desktop. After the installation of Apache, php, snort, perl, and packetfence, as i start i recieve this error.:confused:

[SIZE=3]packetfencesyntax error at /usr/local/pf/bin/pfcmd line 58, near "use Readonly."[/SIZE]

[SIZE=1]It is frustrating [/SIZE]](*,)

Any Ideas????

---

### Post by tonymaro on 2010-10-24
For anyone else with this issue (I assume the poster either solved or gave up by now) it means you're missing the Perl module.

Ubuntu was missing a LOT of perl modules.  I finally got fedup and started using apt-get with regex to install most all the available perl modules in the repository.

---

### Post by dcstar on 2010-12-20
> **tonymaro said:**
> For anyone else with this issue (I assume the poster either solved or gave up by now) it means you're missing the Perl module.

Ubuntu was missing a LOT of perl modules.  I finally got fedup and started using apt-get with regex to install most all the available perl modules in the repository.

For those who wants to install Packetfence on Ubuntu, I just came across this HOWTO:

[http://www.linux.com/learn/tutorials/386610:install-packetfence-for-powerful-network-access-control](http://www.linux.com/learn/tutorials/386610:install-packetfence-for-powerful-network-access-control)

---

