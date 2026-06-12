---
title: "Restarting DHCP with www-data user"
date: 2011-07-21
forum: Networking &amp; Wireless
---

### Post by Pontiac on 2011-07-21
I'm attempting to write a web service that works only on my LAN and is not accessible via the internet.  I need to restart the DHCP service without granting full root access, but I'm having trouble using the [/etc/init.d/dhcp3-server restart] command.  It gives back a failure message that reports nothing:

$ /etc/init.d/dhcp3-server restart
dhcpd self-test failed. Please fix the config file.
The error was:
$

Looking at the script itself, I found the command its trying to execute, and it came back with this:

$ /usr/sbin/dhcpd3 -t -cf /etc/dhcp3/dhcpd.conf
drop_privileges: could not set group id: Operation not permitted

So I went and changed the dhcp: and dhcpd: AND www-data: in /etc/group so that www-data (The apache user) was part of the group, and still the init.d script wouldn't run.

I would prefer to NOT give passwordless access to the www-data user as I do other web services on this machine, however, giving access to stop my DHCP server is a risk I'm willing to take. ;)

The question is, how can I restart the DHCP with apache so I can apply changes?

---

### Post by SeijiSensei on 2011-07-22
Your only option is to run another instance of Apache on a separate port that retains root privileges. No one other than root can start the DHCP server.  (Only root can create a process that binds to a port < 1024.) The other possibility is to use Webmin which natively runs as root.

In the past I've used a semaphoring system where the web app creates a file whose existence is monitored by a script running from cron every minute.  The script runs as root and can then take the appropriate actions.  This means a delay of up to a minute between your giving it the command from the web page and the process being started.

---

### Post by Pontiac on 2011-07-22
> **SeijiSensei said:**
> Your only option is to run another instance of Apache on a separate port that retains root privileges. No one other than root can start the DHCP server.  (Only root can create a process that binds to a port < 1024.) The other possibility is to use Webmin which natively runs as root.


I actually found another way of doing this after a lot of deep digging around with google as my partner.

First, I gave www-data access to the **dhcp **and **dhcpd **group.  Not 100% sure if that is a part of the puzzle yet.  It works and I'm not sure I wanna touch it. ;)  I also gave www-data access to bash, but again, not sure if this was a part of the puzzle.

Second, I added the following line to sudoers:

```
www-data ALL = NOPASSWD: /etc/init.d/dhcp3-server
```

In my PHP I call the restart as:

```
$systemreturn=exec("sudo /etc/init.d/dhcp3-server restart",$sys);
```

Now that things ARE running, I'll start stripping out the groups and removing the bash access (And return it to /dev/null or whatever) and see at what point things break.

---

