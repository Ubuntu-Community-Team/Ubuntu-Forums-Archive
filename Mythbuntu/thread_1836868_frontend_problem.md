---
title: "frontend problem"
date: 2011-08-31
forum: Mythbuntu
---

### Post by Cobramlw on 2011-08-31
Ive tried every thing i can think of every time i try to connect with a separate frontend it says "cannot". ive got the correct ip using ifconfig on the backend machine. its a fresh install of mythbuntu 11.04 ive Commented out the "bind-address" line in /etc/mysql/conf.d/mythtv.cnf
 Commented out the "bind-address" line in /etc/mysql/my.cnf what am i missing?

2011-08-31 16:50:51.545 UPnPautoconf() - No UPnP backends found
2011-08-31 16:50:51.577 No UPnP backends found

The log says

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2011-08-31 16:50:51.778 Deleting UPnP client...
2011-08-31 16:50:52.543 Failed to init MythContext.
2011-08-31 16:54:40.499 mythbackend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-08-31 16:54:40.553 Using runtime prefix = /usr
2011-08-31 16:54:40.603 Using configuration directory = /home/mythtv/.mythtv
2011-08-31 16:54:40.637 Empty LocalHostName.
2011-08-31 16:54:40.670 Using localhost value of Mark-004
2011-08-31 16:54:40.697 Testing network connectivity to '10.0.0.3'
2011-08-31 16:54:40.839 New DB connection, total: 1
2011-08-31 16:54:40.930 Unable to connect to database!
2011-08-31 16:54:40.964 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'10.0.0.2' (using password: YES)

---

### Post by thatguruguy on 2011-08-31
How is your backend set up?  Specifically, what values are set in the areas which I have circled:

---

### Post by Cobramlw on 2011-08-31
> **thatguruguy said:**
> How is your backend set up?  Specifically, what values are set in the areas which I have circled:


local backend
ip adress 127.0.0.1
port 6543             status port 6544
security pin 0000

master backend
ip address 127.0.0.1 port 6543

ive tried changing the ip to what ifconfig says and changeing the port numbers but no luck.  thanks for replying

---

### Post by thatguruguy on 2011-08-31
OK, your backend is set up to point to itself as a loopback.  It can't share to the rest of the network that way.

My suggestion is to set up a fixed ip for your server on the network. That way, if you need to reboot, it won't change, and the rest of the network can always find it.  Run ifconfig on your backend again and post the results here, and I may be able to walk you through what you need to do.

BTW, you state that you "Commented out the "bind-address" line in /etc/mysql/my.cnf". Why?

---

### Post by Cobramlw on 2011-09-01
> **thatguruguy said:**
> OK, your backend is set up to point to itself as a loopback.  It can't share to the rest of the network that way.

My suggestion is to set up a fixed ip for your server on the network. That way, if you need to reboot, it won't change, and the rest of the network can always find it.  Run ifconfig on your backend again and post the results here, and I may be able to walk you through what you need to do.

BTW, you state that you "Commented out the "bind-address" line in /etc/mysql/my.cnf". Why?

I commented out the bind address in /etc/mysql/my.cnf for the same reson as  /etc/mysql/conf.d/mythtv.cnf some people write to do both ive tried everything I could find with google :) the output of ifconfig is

 cobra@Mark-005-Mythtv:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:2e:31:dd:59  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2002:c0a8:142:e472:201:2eff:fe31:dd59/64 Scope:Global
          inet6 addr: fe80::201:2eff:fe31:dd59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2069 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2360754 (2.3 MB)  TX bytes:343932 (343.9 KB)
          Interrupt:43 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9348 (9.3 KB)  TX bytes:9348 (9.3 KB)

thanks

---

### Post by thatguruguy on 2011-09-04
> **Cobramlw said:**
> I commented out the bind address in /etc/mysql/my.cnf for the same reson as  /etc/mysql/conf.d/mythtv.cnf some people write to do both ive tried everything I could find with google :) the output of ifconfig is

thanks

Set both of the boxes on your backend to 10.0.0.4.  Make sure that your frontend also points to 10.0.0.4.

I haven't commented out anything on my set-up, and I'd be leary about making changes based on recommendations concerning earlier versions of mythtv.

Speaking of versions of mythtv, are you running the same version on both computers?  If not, that can cause problems.  Also, have you installed mythbuntu control center on the frontend computer?

---

### Post by Cobramlw on 2011-09-08
no good ive changed the backend to 10.0.0.4 and when I run the frontend after i select the username ip and password it says "cannot".  :(  Im getting the frontend info from /home/mythtv/.mythtv/mysql.txt and the frontend is 0.24.0+fixes the backend is a fresh install of 11.04 no updates yet.

---

### Post by PatrickD-52761 on 2011-09-09
> **Cobramlw said:**
> no good ive changed the backend to 10.0.0.4 and when I run the frontend after i select the username ip and password it says "cannot".  :(  Im getting the frontend info from /home/mythtv/.mythtv/mysql.txt and the frontend is 0.24.0+fixes the backend is a fresh install of 11.04 no updates yet.

This might be the problem.  Your backend may be a different version than the frontend. 

On both the computer running the mythtv backend, and the frontend, type
```
dpkg -l mythtv*
``` and hit enter.

If the versions of the backend and frontend aren't the same, then the frontend won't be able to connect to the backend.  For example, on my backend, it says 0.24+fixes.20110831.... and on my laptop, the frontend is just 0.24+fixes. So my frontend won't be able to connect to the backend, since they're different builds.

I could be wrong about this, so you might want to wait for thatguruguy to respond, but I'm about 99% positive that you'll need to update mythtv-backend to the same build as the frontend (or vice versa).

Have a great day:)
Patrick.

---

### Post by nickrout on 2011-09-10
Rubbish, any 0.24 will connect to any 0.24, it's only when you try to mix, eg 0.23 with 0.24 that you get problems.

---

### Post by Cobramlw on 2011-09-18
It connected YAY I dont know why it connected but I think it was a ethernet cable problem.  Now it says  "Your frontend and backend are configured in different timezones.  You must correct this mismatch to continue" ive set both times the same except the backend says America/Chicago and the frontend computer just says Chicago could that be the problem? if so how do I change it?  The time & date settings dont allow me to change this how do i do it with terminal?  thanks for all the help im so close i can feel it.;)

---

### Post by thatguruguy on 2011-09-18
> **Cobramlw said:**
> It connected YAY I dont know why it connected but I think it was a ethernet cable problem.  Now it says  "Your frontend and backend are configured in different timezones.  You must correct this mismatch to continue" ive set both times the same except the backend says America/Chicago and the frontend computer just says Chicago could that be the problem? if so how do I change it?  The time & date settings dont allow me to change this how do i do it with terminal?  thanks for all the help im so close i can feel it.;)

I'm glad you got it connected.  I had the same problem with timezones; apparently, mythbuntu and ubuntu (as of Natty) use slightly different timezone formats.  On your frontend computer, you can go into a terminal and type:
```
gksu gedit /etc/timezone
```
... and then make sure that it says the same thing that your backend's /etc/timezone says, which in your case is America/Chicago.  That should fix it, and shouldn't cause any issues on your frontend.

---

### Post by Cobramlw on 2011-09-18
That fixed the problem perfectly.  Thanks for all the help.  Later

---

