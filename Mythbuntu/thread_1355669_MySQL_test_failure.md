---
title: "MySQL test failure"
date: 2009-12-15
forum: Mythbuntu
---

### Post by mfeijen on 2009-12-15
Hi,

I just started installing mythbuntu - by adding to my ubuntu 9.10. However, I get stuck: the "Test MySQL Connection" at the Ubuntu control center indicates "failure". The information in mysql.txt at /etc/mythtv corresponds to the information at the MySQL window of the Mythbuntu Control Center.

What's going wrong and how do I solve this?

(I could not recognise this problem at this forum but maybe that's because my ubuntu & linux skills are pretty limited :( )

thanks for the help in advance;)
kind regards,
mfeijen

---

### Post by SiHa on 2009-12-15
Not sure if this will help, but here goes.

I'm fairly sure that when I was setting up my frontend, I got stuck at this point as well, when setting up a remote frontend. IIRC it was because I was putting the hostname in the 'server' field. In the end I found it worked by entering the IP address of the server instead.

Not sure why, but I've found my 9.10 install doesn't resolve hostnames at all. For VNC I have to use the IP address as well, whereas the hostname worked fine in 8.04.

Edit: Also, I think Mythbuntu defaults to localhost: 127.0.0.1, in the backend setup as well.

---

### Post by mfeijen on 2009-12-16
Hi SiHa,

Thanks for your reply. Unfortenately your suggestion to use the ip address did not work in my case; I included "DBHostName=127.0.0.1" in the mysql.txt file and the Test MySQL Connection still indicated 'Failure'.

regards
mfeijen

---

### Post by superm1 on 2009-12-16
> **mfeijen said:**
> Hi,

I just started installing mythbuntu - by adding to my ubuntu 9.10. However, I get stuck: the "Test MySQL Connection" at the Ubuntu control center indicates "failure". The information in mysql.txt at /etc/mythtv corresponds to the information at the MySQL window of the Mythbuntu Control Center.

What's going wrong and how do I solve this?

(I could not recognise this problem at this forum but maybe that's because my ubuntu & linux skills are pretty limited :( )

thanks for the help in advance;)
kind regards,
mfeijen
Are you trying to add a new frontend and have an existing backend I hope? 
If not, then you're in the wrong place and should install the backend role on this machine.

If yes you are adding a new frontend, go to the backend and check the services tab to make sure that mysql is Enabled.

---

### Post by superm1 on 2009-12-16
> **SiHa said:**
> Not sure if this will help, but here goes.

I'm fairly sure that when I was setting up my frontend, I got stuck at this point as well, when setting up a remote frontend. IIRC it was because I was putting the hostname in the 'server' field. In the end I found it worked by entering the IP address of the server instead.

Not sure why, but I've found my 9.10 install doesn't resolve hostnames at all. For VNC I have to use the IP address as well, whereas the hostname worked fine in 8.04.

Edit: Also, I think Mythbuntu defaults to localhost: 127.0.0.1, in the backend setup as well.
That's really weird.  Are you sure you haven't changed routers or anything like that since switching from 8.04?  It is probably by how the router is resolving DNS for you.

---

### Post by SiHa on 2009-12-16
> **superm1 said:**
> That's really weird.  Are you sure you haven't changed routers or anything like that since switching from 8.04?  It is probably by how the router is resolving DNS for you.
No, the frontend is new, but the BE/FE and the router are identical.

I did wonder if it was the router doing something screwy, but I don't know enough about the black-art that is networking to solve it. Also, in VNC viewer, for example, I used to enter ```
mythbox@192.168.1.152
``` but now that doesn't work, which suggests (to me, anyway) that it's the machine that doesn't recognise the hostname, rather than a router issue. 

It's not a biggie anyway, I have far bigger Myth fish to fry :)

---

### Post by novellahub on 2009-12-17
> **SiHa said:**
> No, the frontend is new, but the BE/FE and the router are identical.

I did wonder if it was the router doing something screwy, but I don't know enough about the black-art that is networking to solve it. Also, in VNC viewer, for example, I used to enter ```
mythbox@192.168.1.152
``` but now that doesn't work, which suggests (to me, anyway) that it's the machine that doesn't recognise the hostname, rather than a router issue. 

It's not a biggie anyway, I have far bigger Myth fish to fry :)

You need to edit your /etc/hosts file and put in the appropriate hostnames.  Here is what mine looks like:

```

127.0.0.1 localhost
192.168.0.106 mythtvmaster
192.168.0.104 mythvslave
192.168.0.107 mythtvslave

```

You need to do this on both your master and slave machines.

---

### Post by SiHa on 2009-12-17
Thanks.

So why didn't I need to do this with 8.04, I wonder?

---

### Post by novellahub on 2009-12-17
> **SiHa said:**
> Thanks.

So why didn't I need to do this with 8.04, I wonder?

I have always done it as part of my mythtv setup procedure so it was the norm for me. Especially when branching out into Slave / Master machine relationships.

---

