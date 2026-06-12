---
title: "Mysql Cannot Connect"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by computerfox on 2011-03-08
Hey guys,

I know I posted this before, but that thread pretty much died for some reason.  

My problem is that for some reason I can't connect to my MySQL on my server.  I know it's not the script, other than the information that I'm using to connect.

The MySQL server is set to "localhost" so I set the host in my php script to "localhost"
I check for the username and they say I should try "root" so I set the username to "root"
Then I put in my root password.

When I go to where my php script actually starts, it gives me the error saying that I cannot connect.  I know the rest of the script works and the error refers to the info I'm using to go in.

Some more information about the server:
I'm using Webmin to administer it
the master DNS is foxwebhosting.dyndns.org
The port for MySQL is 3306 (default).
It listens on 127.0.0.0.0 (default-localhost).

Any ideas?

computerfox

---

### Post by SoftwareExplorer on 2011-03-09
There can be a different root password for mysql than for the rest of the system. 
And just to clarify, the script and mysql server are running on the same machine?

---

### Post by computerfox on 2011-03-10
on the same machine? yes

different password?  well, when i was installing mysql it asked me for a master password and i noted it down.  that's the password i'm trying to go onto it with.

could it be that the server is named localhost or that doesn't matter?

---

### Post by SoftwareExplorer on 2011-03-11
> **computerfox said:**
> on the same machine? yes

different password?  well, when i was installing mysql it asked me for a master password and i noted it down.  that's the password i'm trying to go onto it with.
Ok, sounds like you have the right password.
> **computerfox said:**
> could it be that the server is named localhost or that doesn't matter?
That shouldn't matter. Localhost is a DNS name of sorts that points to the IP address for the current computer. In IPv4 that 127.0.0.1, which is the IP address of the current computer, no matter what computer you are on. If mysql is listening on 127.0.0.1 (or the IPv6 equivalent, ::1) then connecting using the name localhost should work. 

Can I suggest installing MySQL Administrator? (You can find it by searching in the Software Center.) It will let us test logging in from localhost to the Mysql server, and it will let us see what users there are.

---

### Post by computerfox on 2011-03-14
that's actually a good idea.  i'm not sure if i already have it though because i do have a section for mysql in webmin.  i believe i provided snapshots of that.

---

### Post by SoftwareExplorer on 2011-03-14
> **computerfox said:**
> that's actually a good idea.  i'm not sure if i already have it though because i do have a section for mysql in webmin.  i believe i provided snapshots of that.

You probably don't already have it; it's separate from webmin.

---

### Post by computerfox on 2011-03-15
it is?  okay.  i believe i did install it, how would i confirm that?

---

### Post by SoftwareExplorer on 2011-03-15
> **computerfox said:**
> it is?  okay.  i believe i did install it, how would i confirm that?
If you have it installed, it would be in the Applications>Programming>MySQL Administrator. (If you don't even have Applications>Programming then you probably don't have it installed). Another way you could check is by finding it in software center and seeing if it says it is installed.

---

### Post by falko on 2011-03-15
What's the output of ```
netstat -tap
```?

---

### Post by computerfox on 2011-03-15
```

adminabel@foxwebhosting:~$ netstat -tap
(No info could be read for "-p": geteuid()=1000 but you should be root.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:mysql         *:*                     LISTEN      -               
tcp        0      0 *:www                   *:*                     LISTEN      -               
tcp        0      0 192.168.122.1:domain    *:*                     LISTEN      -               
tcp        0      0 foxwebhosting.dy:domain *:*                     LISTEN      -               
tcp        0      0 localhost:domain        *:*                     LISTEN      -               
tcp        0      0 *:ssh                   *:*                     LISTEN      -               
tcp        0      0 localhost:953           *:*                     LISTEN      -               
tcp        0      0 *:666                   *:*                     LISTEN      -               
tcp        0      0 foxwebhosting.dyndn:ssh socrates.home:45982     ESTABLISHED -               
tcp6       0      0 localhost:8005          [::]:*                  LISTEN      -               
tcp6       0      0 [::]:http-alt           [::]:*                  LISTEN      -               
tcp6       0      0 [::]:domain             [::]:*                  LISTEN      -               
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      -               
tcp6       0      0 localhost:953           [::]:*                  LISTEN 

```

Ummm, okay?

---

