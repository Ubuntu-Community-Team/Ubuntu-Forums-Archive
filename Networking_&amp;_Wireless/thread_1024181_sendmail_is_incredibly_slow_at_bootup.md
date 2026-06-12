---
title: "sendmail is incredibly slow at bootup"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by fontenot_1031 on 2008-12-28
I was wondering if it's normal for the sendmail daemon to take a long time (about 30sec - 1min) at startup? I recently installed sendmail and starttls to check gmail on gnus.

for example here's what happens when I time the restart of sendmail
```

david@laptopskis:~$ time sudo /etc/init.d/sendmail restart
 * Restarting Mail Transport Agent (MTA) sendmail                        [ OK ] 

real	1m4.609s
user	0m0.244s
sys	0m0.232s

```

---

### Post by holotone on 2009-04-22
I second that - How in the hey do I run sendmail without doubling my boot-up time?

---

### Post by iponeverything on 2009-04-22
add an entry for your external address in your /etc/hosts to match the machine name.

---

### Post by xodeus on 2009-05-31
I've this issue too. How do I do that?
My external IP is not static. 
Should I start setting up a dyndns?
Then add something like this to the /etc/hosts

my.dyndns.com localhost
my.dyndns.com 127.0.0.1

Or how. Please explain..

Is it somehow possible to start a service in the background like it is in arch with just putting a "@" in front of the serivce name in rc.conf?

---

### Post by tedchou12 on 2012-10-02
Put & at the end
Eg sendmail  &

---

