---
title: "Privoxy"
date: 2011-12-03
forum: Networking &amp; Wireless
---

### Post by CJ_Hudson on 2011-12-03
Hi,
I installed Privoxy and it was working fine, but the next day refuses to connect and gives me this message:

The proxy server is refusing connections
      
Firefox is configured to use a proxy server that is refusing connections.
        
Check the proxy settings to make sure that they are correct.
  Contact your network administrator to make sure the proxy server is
    working.

Please could someone give me some advice or ANYTHING that would help sort this out?
Thankyou in advance

---

### Post by CJ_Hudson on 2011-12-07
Bump.

---

### Post by vasa1 on 2011-12-07
> **MogBug said:**
> Bump.
```
sudo service privoxy restart
``` ?

---

### Post by CJ_Hudson on 2011-12-12
Thankyou very much vasa1.:popcorn:

---

### Post by CJ_Hudson on 2011-12-13
Please, it seems I  have to restart Privoxy every time I start Ubuntu, is there any way I can have it start automatically whenever I boot?
Thankyou.

---

### Post by vasa1 on 2011-12-13
> **MogBug said:**
> Please, it seems I  have to restart Privoxy every time I start Ubuntu, is there any way I can have it start automatically whenever I boot?
Thankyou.
According to [http://www.privoxy.org/user-manual/startup.html](http://www.privoxy.org/user-manual/startup.html), "Note that **Debian typically starts Privoxy upon booting per default**. It will use the file /etc/privoxy/config as its main configuration file." So you really shouldn't have to do anything but ...
> So... I changed in /etc/privoxy/config
Code:
**listen-address  localhost:8118**
to
Code:
**listen-address  127.0.0.1:8118**
and everything works !!  over here: [http://ubuntuforums.org/showthread.php?p=9188263](http://ubuntuforums.org/showthread.php?p=9188263)
I too have "**listen-address  127.0.0.1:8118**" in my config file (/etc/privoxy/config). If you have the other one, maybe you can try editing the file as suggested. You'll need admin rights and should make a back-up first.

---

### Post by CJ_Hudson on 2011-12-13
Thankyou very much vasa1.

I also removed the comment on

forward         192.168.0.1/

so I can log into my router controls.
[edit]
...but I get the error:

* Restarting filtering proxy server privoxy                                    Dec 14 08:24:28.222 b77288d0 Error: Wrong number of parameters for forward directive in configuration file.
                                                                         [ OK ]

Please, how do I fix this?

---

### Post by CJ_Hudson on 2012-02-24
There's a new version of Privoxy :

[http://packages.ubuntu.com/precise/privoxy]("http://packages.ubuntu.com/precise/privoxy")

apparently with no dependencies, which should work in 11.10.

It doesn't seem to need the gksudo gedit file editing to start afresh after each reboot on its own.

---

