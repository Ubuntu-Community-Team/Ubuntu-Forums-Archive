---
title: "Problem to access apache2"
date: 2011-07-04
forum: Networking &amp; Wireless
---

### Post by parthbhagat on 2011-07-04
Hi all,

I am using Ubuntu 64 bit edition. This server is running on virtual machine. I have installed Postgresql database server on it. What I want to do it I want a web interface install on the same server to access Postgresql database. For that I've installed **phppgadmin **interface on the same machine.

On the same machine port 80 & port 8080 is in use so I've changed port from 80 to 8888. When I check whether that apache2 service is started or not then it is showing me that the service is started. The status is something like this:
[COLOR=Red]**tcp        0      0 0.0.0.0:8888            0.0.0.0:*               LISTEN      20762/apache2**[/COLOR]

But when I hit url from my machine (remote machine) then it is not whowing any message, it is simply a white screen without any response on the browser window.

Can anyone help me out?

---

### Post by jmoorse on 2011-07-12
What happens when you 'telnet [ip of server] 8888' and type 'get' ?  What output do you get?

---

### Post by parthbhagat on 2011-07-13
> **jmoorse said:**
> What happens when you 'telnet [ip of server] 8888' and type 'get' ?  What output do you get?

But I do not get ip of the server, I mean as I mentioned earlier the apache2 service is started with ip 0.0.0.0:8888, & if I am not wrong then this ip is reserved ip address.

And by mean of using **get **command do you mean **getstatus **command of telnet command mode?

---

