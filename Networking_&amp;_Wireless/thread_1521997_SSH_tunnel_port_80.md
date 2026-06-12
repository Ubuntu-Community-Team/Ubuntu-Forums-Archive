---
title: "SSH tunnel port 80"
date: 2010-07-01
forum: Networking &amp; Wireless
---

### Post by xcurtisx on 2010-07-01
Hello all.
Simple enough problem. Did a bit of digging on google but couldn't find what I needed here we go:
I have a linux machine off site. It has ssh running and I can get into it no problem on the CLI. I need to access the httpd on port 80. I am on a vista machine.
So I know I can tunnel port 80 from my Linux box to my localhost with putty, but I dont know how.
Please advise.
I can access port 80 when I am at the location so all of that is working just not from where I am right now.
Thanks!

---

### Post by jonobr on 2010-07-01
Hello


I think the second piece of [This]("http://www.medicalnerds.com/port-forwarding-with-sshputty/") useful article describes exactly what your looking for

> Accessing a remote webserver
You want to access a web server running on port 80 your remote machine.

From your local machine, type:




---

### Post by xcurtisx on 2010-07-02
Thanks. I am giving this a try but failing.
Let me outline my setup a bit more.
Me (Vista)--DSL Router---Interwebs--DSL Router with DynDNSname: myhost.dyndns.org---Linux Host I am trying to reach.

Now port 80 is not forwarded from the DSL router to the Linux Box. 
Port 22 is.
I know there is a way to access the port 80 form my Vista machine via ssh, but the guide posted about (Thanks for that) is failing telling me host doesn't exist, but I can ssh to the host no problem.
Thanks all.

EDIT - Got it to work:
from vista command line: plink -ssh YOURHOST -L 8080:127.0.0.1:443 -l root -pw YOURPASS
in your browser: [https://127.0.0.1:8080/](https://127.0.0.1:8080/)

I also realized I needed port 443 not 80. But you can see how it works.
Thanks!

---

