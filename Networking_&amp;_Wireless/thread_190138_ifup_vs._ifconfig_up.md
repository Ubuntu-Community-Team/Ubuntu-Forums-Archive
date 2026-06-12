---
title: "ifup vs. ifconfig up"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by shorty0927 on 2006-06-05
While trying out various people's methods in hopes of getting my wireless to work, I've found a couple of commands that seem to do the same thing, but I don't know for sure.  I thought I'd ask in case I shouldn't be using one or the other of them.

The first:
```

ifup eth0
```

The second:

```
ifconfig eth0 up
```

What's the difference??

---

### Post by spd106 on 2006-06-06
I believe the main difference is that ifup and ifdown use the /etc/network/interfaces file for configuration information. Whereas ifconfig configures the interfaces directly. So it only uses the information already set up. I have to say I'm not entirely sure if this is accurate.
The best suggestion I have is to look through the man pages for more details.

---

### Post by slakkie on 2006-06-06
spd106:

You are correct, from the ifup man page:

> 
DESCRIPTION
       The  ifup  and  ifdown  commands  may  be used to configure (or, respectively, deconfigure) network interfaces based on
       interface definitions in the file /etc/network/interfaces.


From the ifconfig man page:
> 
DESCRIPTION
       Ifconfig  is  used to configure the kernel-resident network interfaces.
       It is used at boot time to set up interfaces as necessary.  After that,
       it  is  usually  only  needed  when  debugging or when system tuning is
       needed.

       If no arguments are given, ifconfig displays the  status  of  the  cur-
       rently  active interfaces.  If a single interface argument is given, it
       displays the status of the given interface only; if a single  -a  argu-
       ment  is  given,  it  displays the status of all interfaces, even those
       that are down.  Otherwise, it configures an interface.


Yet ifup/ifdown are using ifconfig and route:
> 
NOTES
       ifup and ifdown are actually the same program called by different names.

       The  program  does not configure network interfaces directly; it runs low level utilities such as ifconfig and route to
       do its dirty work.


I always use ifconfig, as this is present under all Unix platforms and ifup/ifdown aren't. 

And because I can simply change an interface and bring it up in one command. Which will take two commands if you use ifup/down (but this boils down to percentage of lazyness in body and soul ;) ).

---

