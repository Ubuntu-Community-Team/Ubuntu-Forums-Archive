---
title: "Launch Browser - Proxy over SSH"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by PerfectReign on 2009-09-17
I've searched here and on google but cannot find an answer.

i want to proxy my browser to my home network from work or other location.

I have a laptop at home sitting on 192.168.0.103.  I have the login.

I can most easily connect to it using an ssh command:
[FONT=Fixedsys][COLOR=Blue]
^Croot@r2d2:/home/kai/appsssh -Y -l daniel 6.15.19.24
daniel@6.15.19.24's password: 
Linux xwing 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)

10 packages can be updated.
0 updates are security updates.

Last login: Wed Sep 16 08:03:53 2009 from pc5662.temp.co.la.ca.us
daniel@xwing:~$ whoami
daniel
daniel@xwing:~$ [/COLOR][/FONT]

From there I can launch firefox or whatever and have it run from the local station.  I want to - however - use the tunnel remotely.

I use the following command - previously entered in a batch file - to connect:

[FONT=Fixedsys][COLOR=Blue]ssh -C2qTnN -D 8080 daniel@6.15.19.24[/COLOR][/FONT]

Using this command I can connect.

I have Seamonkey setup to use a proxy at 127.0.0.1 port 8080.  If I hadn't connected, I get a proxy error. If I have connected, I don't get out through the internet, just a blank screen.

What gives?



I had this working under openSUSE: [http://linux.derkeiler.com/Mailing-Lists/SuSE/2009-02/msg00394.html](http://linux.derkeiler.com/Mailing-Lists/SuSE/2009-02/msg00394.html)

However, I cannot get it working with Ubuntu.  As you see below, I have simply a blank browser window:


[IMG]http://www.perfectreign.com/stuff/2009/proxy_config.png[/IMG]


Here are some other references.



[http://paulstamatiou.com/how-to-surf-securely-with-ssh-tunnel](http://paulstamatiou.com/how-to-surf-securely-with-ssh-tunnel)

[http://wiki.freaks-unidos.net/ssh-port-forwarding](http://wiki.freaks-unidos.net/ssh-port-forwarding)

[http://www.linux.com/archive/feature/119744](http://www.linux.com/archive/feature/119744)

---

### Post by PerfectReign on 2009-09-19
Okay, got it working.

I have the following line:

ssh -D 8080 -Nf remote_user_name@256.256.256.256

I can do this as regular user since the port is not reserved.

It still doesn't work with SeaMonkey but does work just fine with Firefox. Also in Firefox, I can just use FoxyProxy and set one of the proxies to this.

Solved.

---

