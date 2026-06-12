---
title: "Firewall Setup for server"
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by sandeepb on 2009-08-17
HI everyone,

I've installed apache, php, mysql, and phpmyadmin on my server, forwarded all ports needed etc.

Now all I need to do is make sure I have a working firewall to make sure I don't get any intrusions on my system.

Can any network admins guide me on this?

Thanks

---

### Post by dmizer on 2009-08-17
Okay, you said that you've forwarded all ports needed. I assume that means you have a router? If so, the router IS your firewall, and it's already configured.

Also, a firewall won't necessarily prevent your system from getting hacked.

---

### Post by sandeepb on 2009-08-17
O that's great then, so I won't need to install any firewall on ubuntu?

What other way's can I prevent the system from being hacked then?

---

### Post by wojox on 2009-08-17
I don't. I have the same set-up and I let my router handle the firewall.

Strong passwords and staying up to date with patches and such.

---

### Post by dmizer on 2009-08-17
> **sandeepb said:**
> O that's great then, so I won't need to install any firewall on ubuntu?
I rely on my router's firewall for my server. So, no. There's no need to have two firewalls.

> **sandeepb said:**
> What other way's can I prevent the system from being hacked then?

Study Apache security very carefully. Spend lots of time in the [security discussions](http://ubuntuforums.org/forumdisplay.php?f=338) and [server platforms](http://ubuntuforums.org/forumdisplay.php?f=339) sections.

Try searching the "I've been hacked" threads.

If you're writing your own code, be sure it's thoroughly tested before making it live. If you don't trust your own coding skills, rely on a [peer reviewed CMS](http://php.opensourcecms.com/) to render your page and be careful about what plugins you add.

Backup constantly, because as a new web administrator, you WILL make mistakes, and expect to be hacked as a result of those mistakes. So, you'll also need complete backups in place so you can recover quickly.

---

### Post by update_manager on 2009-08-19
> **sandeepb said:**
> HI everyone,

I've installed apache, php, mysql, and phpmyadmin on my server, forwarded all ports needed etc.

Now all I need to do is make sure I have a working firewall to make sure I don't get any intrusions on my system.

Can any network admins guide me on this?

Thanks

If you've never used iptables before, you can start with a frontend like ufw ([https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)).

Figure out what ports (80) you'll need unauthenticated access to. You'll also want stateful access (iptables -A INPUT -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT) to high level ports - most iptables front ends handle this part for you.

You can do some advanced rules with iptables, such as dropping invalid combinations of TCP flags ([http://pikt.org/pikt/samples/iptables_tcp_flags_programs.cfg.html](http://pikt.org/pikt/samples/iptables_tcp_flags_programs.cfg.html)) and basic IDS functionality ([http://pikt.org/pikt/samples/iptables_tcp_flags_programs.cfg.html](http://pikt.org/pikt/samples/iptables_tcp_flags_programs.cfg.html)).

You might be able to restrict access to some ports from to networks only (iptables -A INPUT -p tcp -s 192.168.2.0/24 --dport 8080 -j ACCEPT).

---

### Post by sandeepb on 2009-08-19
Thanks everyone for your help, I'll get along with reading and trying everything I can.

Thanks again.

---

### Post by sandeepb on 2009-08-19
Just a quick check, are these firewall rules I setup alright?

[IMG]http://i27.tinypic.com/28s0kzr.jpg[/IMG]

Thanks

---

