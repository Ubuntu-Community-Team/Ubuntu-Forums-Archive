---
title: "&quot;dhcpd: Can't create new lease file: Permission denied&quot; on 12:10 &amp;13.04 server"
date: 2013-05-03
forum: Networking &amp; Wireless
---

### Post by Archguy on 2013-05-03
Hi all,


I've been having a problem with my DHCP server (isc-dhcp-server) ever since I upgraded to 12.10 (seems the same on a 13.04 test VM as well).


When the DHCP server starts, the upstart script forces the owner:group of /var/lib/dhcp & /var/lib/dhcpd.leases* to root:root. The server works fine and hands out leases then after an hour, when dhcpd tries to rotate the lease file, I get a "dhcpd: Can't create new lease file: Permission denied" in syslog.


I suspect it is failing when it tries to create the temporary lease file before renaming dhcp.leases to dhcpd.leases~

If I change the ownership of /var/lib/dhcp & /var/lib/dhcpd.leases* to dhcpd:dhcpd after the server has started then it works fine. This all seems to be since the following bug fix, and apparmor gets in the way if I undo this change.

> 
[COLOR=#000000]isc-dhcp (4.2.4-1ubuntu4) quantal; urgency=low[/COLOR]

  * debian/isc-dhcp-server.isc-dhcp-server[6].upstart: chown /var/lib/dhcp    and the lease files to 'root:root'. This is needed due to the change    in 4.2.4-1ubuntu1 to use the upstream code for dropping privileges which    requires the lease files be owned by root. (LP: #1028526)


Any advice would be much appreciated.

**Update: Whilst I still think there is something fundamentally wrong in how and when it drops privileges, I'll wait for a fix. Everyone using the ISC dhcp server must have the same problem, and hopefully one of them has the ear of the devs. In the meantime I'll just reset ownership manually after each restart.**

---

### Post by capscrew on 2013-05-03
> If I change the ownership of /var/lib/dhcp & /var/lib/dhcpd.leases* to dhcpd:dhcpd after the server has started then it works fine. This all seems to be since the following bug fix, and apparmor gets in the way if I undo this change.


Put apparmor in complain mode for that profile for the time being.  See ```
man apparmor

man apparmor.d

apparmor_status

```

---

### Post by Archguy on 2013-05-04
Thanks capscrew. I put apparmor into complain mode as you suggested.

```

1 processes are in complain mode.
   /usr/sbin/dhcpd (24146)

```

There is nothing coming back from apparmor in any of the scenarios I then tested, so I'm thinking it's just good old ownerships/permissions that's the the problem.

If I run the upstart script in its default configuration then I get "permission denied" on the next rotation. If I comment out all the fiddling of permissions in the upstart script and set the ownership of the directory and lease files to dhcpd:dhcpd, then I get the following on the next rotation:

```

dhcpd: Can't backup lease database /var/lib/dhcp/dhcpd.leases to /var/lib/dhcp/dhcpd.leases~: Operation not permitted
kernel: [140681.213522] non-accessible hardlink creation was attempted by: dhcpd

```


It seems that the initial lease file rotation is done before dropping privileges, so what I think is happening is:


[LIST=1]
[*]Run *service isc-dhcp-server start* (or *restart*).
[*]The lease file is immediately rotated on startup as root:root, with ownership of the lease file set as such.
[*]The service then drops privileges to dhcpd:dhcpd (*dhcpd -user dhcpd -group dhcpd ...*).
[*]After an hour dhcpd tries to rotate the lease file as dhcpd:dhcpd and fails because the current lease file is owned by root:root.
[/LIST]

I guess this is confirmed by the only workaround which I can currently find, which is to chown the directory and lease files back to dhcpd:dhcpd manually after every restart of dhcpd. To be honest it's no great hardship having to to this as I don't restart the service very often, but of course I would prefer it if I could get it to work as intended.

**Update: I'm a bit of an apparmor noob, but I am thinking that maybe "non-accessible hardlink creation was attempted by: dhcpd" is a result of apparmor?**

Cheers.

---

### Post by capscrew on 2013-05-04
> **Archguy said:**
> ...
If I run the upstart script in its default configuration then I get "permission denied" on the next rotation. If I comment out all the fiddling of permissions in the upstart script and set the ownership of the directory and lease files to dhcpd:dhcpd, then I get the following on the next rotation:

```

dhcpd: Can't backup lease database /var/lib/dhcp/dhcpd.leases to /var/lib/dhcp/dhcpd.leases~: Operation not permitted
kernel: [140681.213522] non-accessible hardlink creation was attempted by: dhcpd

```


It seems that the initial lease file rotation is done before dropping privileges, so what I think is happening is:


[LIST=1]
[*]Run *service isc-dhcp-server start* (or *restart*).
[*]The lease file is immediately rotated on startup as root:root, with ownership of the lease file set as such.
[*]The service then drops privileges to dhcpd:dhcpd (*dhcpd -user dhcpd -group dhcpd ...*).
[*]After an hour dhcpd tries to rotate the lease file as dhcpd:dhcpd and fails because the current lease file is owned by root:root.
[/LIST]

I guess this is confirmed by the only workaround which I can currently find, which is to chown the directory and lease files back to dhcpd:dhcpd manually after every restart of dhcpd. To be honest it's no great hardship having to to this as I don't restart the service very often, but of course I would prefer it if I could get it to work as intended.

**Update: I'm a bit of an apparmor noob, but I am thinking that maybe "non-accessible hardlink creation was attempted by: dhcpd" is a result of apparmor?**

Cheers.
That sure seems like an apparmor profile in action.  I don't use isc-dhcp-server and have know real idea what apparmor profiles might be added.  Therefore I wouldn't have any idea what the proper patch or workaround folks use.  A quick search on the term "non-accessible hardlink creation was attempted by: dhcpd" reveals [**_[COLOR="#0000FF"]this[/COLOR]_**]("https://lists.ubuntu.com/archives/kernel-team/2010-May/010495.html").

---

### Post by Dagaroth on 2013-06-20
seems as this file **dhcpd.leases~** is created after you do a service isc-dhcp-server start
i know that gedit will make these file's if you have it set in preferences to save after editiing.
however i know that it still makes a backup if u tell it not to so i think a bug somewhere probably gedit.
cuz even though u tell it not to make backsup in preferences it does it anyway.

---

### Post by SeijiSensei on 2013-06-20
Is there any reason to use AppArmor on a dhcpd server that does nothing but hand out leases to clients on the internal LAN?  What security problem is this protecting against?

I'd just disable AppArmor for this service.

---

### Post by Dagaroth on 2013-06-22
there was a patch otherday for dhcp but still getting the same permission denied as the OP in syslog for an update.
removing the file with ~ seemed to help, if u need the backup file may want to save it somewhere.

> dhcpd: Can't create new lease file: Permission denied

---

### Post by Scrumps on 2013-07-11
I seem to have this issue as well

---

### Post by smeerbartje on 2013-08-11
Me too, what can we do about this?

---

### Post by adrianwalters on 2013-10-31
Has anyone found a solution to this problem?

---

### Post by sinical on 2014-04-25
Its also happening on 14.04

as a work around edit /etc/rc.local and put 

chown -R dhcpd:dhcpd /var/lib/dhcp

above the 
exit 0

line

---

### Post by ateamp66 on 2014-08-21
Sorry, the last post didn't work in my system (ubuntu server 14.04).
I decided to use acls. ([FONT=lucida console]aptitude install acl[FONT=arial], see [/FONT][/FONT][FONT=arial]https://help.ubuntu.com/community/FilePermissionsACLs[/FONT])

[FONT=lucida console]sudo setfacl -dm u:dhcpd:rwx /var/lib/dhcp[/FONT]
[FONT=lucida console]sudo setfacl -m u:dhcpd:rwx /var/lib/dhcp[/FONT]

done. :D

---

### Post by gurubert on 2014-08-28
Reported as bug: [https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/1186662](https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/1186662)

---

### Post by ThomasNovin on 2014-09-04
Gah! This is why it was impossible to get the feature 'execute' within a dhcpd.conf to work, no matter which binary I called and no matter what their permission was, I got permission denied.

> execute_statement argv[0] = /tmp/test
execute_statement argv[1] = pw-101:45.0
Unable to execute /tmp/test: Permission denied
execute: /tmp/test exit status 32512

Now, after removing /usr/sbin/dhcpd from apparmor, it works as intended. The better fix would be to tweak the current apparmor-profile I guess.

---

### Post by Hammi on 2014-09-28
In the launchpad bug (see link above), there is a modified apparmor profile for dhcp.

---

