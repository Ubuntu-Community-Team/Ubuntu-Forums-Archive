---
title: "Accessing Logs on A Linksys Router"
date: 2011-03-30
forum: Networking &amp; Wireless
---

### Post by ccdwiu on 2011-03-30
Hello,

  I have recently enabled logs on my home wireless router. It is a Linksys WAP54G. I am able to view a non-detailed log directly within the configuration of the router (by directing by browser to 192.168.1.245). However, I also entered my Internal IP so that I can be sent the actual logs but I am unable to read them. I understand that I have to open up a port on my computer, and be able to read the logs in but I am lost on how to do it. I ended up messing with it and googling for about 2 hours but I still can't figure it out. I have tried configuring syslog-ng but I seem to get syntax errors when I edit the configuration file. If anybody can shed some light and just point me in the right direction, that would be great. Thanks.

Here is the output when I try to run syslog-ng after editing syslog-ng.conf:

```

syntax error in /etc/syslog-ng/syslog-ng.conf at line 20.

syslog-ng documentation: http://www.balabit.com/support/documentation/?product=syslog-ng
mailing list: https://lists.balabit.hu/mailman/listinfo/syslog-ng

```

The line it is refering to reads: 
```

                file("/proc/kmsg" program_override("kernel"));

```

I have read through the documentation but still am having trouble.

---

### Post by ccdwiu on 2011-03-31
I found a package that will open up port 514 and create logs sent from the router.
If anybody is interested, [https://sourceforge.net/projects/wap54g-log/](https://sourceforge.net/projects/wap54g-log/)

---

