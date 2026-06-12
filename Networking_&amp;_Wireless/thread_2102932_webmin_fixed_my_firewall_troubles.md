---
title: "webmin fixed my firewall troubles"
date: 2013-01-08
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2013-01-08
What a wonderful tool. After struggling lost for days in a google cloud, I came upon webmin on ubuntugeek web page.

It allowed me to reset my firewall using a nice gui tool.
And now all my 3 of my PC's can happily talk and share files to each other.

[IMG]https://lh4.googleusercontent.com/-JLN674cmEuc/UOx_lsKNoNI/AAAAAAAAEXo/GtGZ8LHzexA/s1440/fixedfirewall.png

I used this to install, login info comes up in the terminal window for website.
[http://www.ubuntugeek.com/how-to-install-webmin-on-ubuntu-12-04-precise-server.html](http://www.ubuntugeek.com/how-to-install-webmin-on-ubuntu-12-04-precise-server.html)

> scott@scott-P5QC:~$ sudo dpkg -i webmin_1.580_all.deb
Selecting previously unselected package webmin.
(Reading database ... 229686 files and directories currently installed.)
Unpacking webmin (from webmin_1.580_all.deb) ...
Setting up webmin (1.580) ...
**Webmin install complete. You can now login to [https://scott-P5QC:10000/](https://scott-P5QC:10000/)**
as root with your root password, or as any user who can use sudo
to run commands as root.
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
scott@scott-P5QC:~$ 


Really great to find the answer, nothing else I did made any sense. Static routes, iptables firestarter gufw all lead me down a rabbit hole.
When going there you get a security warning which I disregarded. Might there be some way to eliminate it?

---

### Post by Calinou on 2013-01-08
>2013
>firewalls

Anyway... cool story. Do you need any help now?

---

### Post by sdowney717 on 2013-01-08
Not at the moment. I update the many threads I had started.
Really did not even know how to ask the right questions.
So learned a lot and did not give up.
I knew it could be done somehow.

check out this working tracert from a pc on the outside of ubuntu router, to a pc on inside of ubuntu router. And goes thru 2 hardware routers on its way.
Ubuntu router has 2 nics with wildly different ip's


```

C:\Users\scott>tracert 10.42.0.19

Tracing route to SCOTT-PC [10.42.0.19]
over a maximum of 30 hops:

  1     1 ms    <1 ms    <1 ms  hubrouter.westell.com [192.168.200.1]
  2    45 ms    18 ms    17 ms  192.168.1.1
  3    47 ms    16 ms    44 ms  SCOTT-P5QC [192.168.1.102]
  4    17 ms     1 ms     1 ms  SCOTT-PC [10.42.0.19]

Trace complete.

C:\Users\scott>
```

---

### Post by lisati on 2013-01-08
*cough*
Not a support request, and is a repeat of information found [here]("http://ubuntuforums.org/showthread.php?p=12445422#post12445422")

Thread closed.

---

