---
title: "Myth-edgy backend not connected to cardinput"
date: 2007-04-05
forum: Multimedia &amp; Video
---

### Post by Panhead Bill on 2007-04-05
Phantom backend, it seems to be running but it isnt.  

I see two problems, "localhost is defined, but isn't attached to a cardinput. and QServerSocket: failed to bind or listen to the socket.

Any advise?


mythtv@ubuntuPVR:~$ mythbackend
2007-04-05 11:24:42.769 Using runtime prefix = /usr
2007-04-05 11:24:42.863 New DB connection, total: 1
2007-04-05 11:24:42.877 Connected to database 'mythconverg' at host: localhost
2007-04-05 11:24:42.892 Current Schema Version: 1160
Starting up as the master server.
2007-04-05 11:24:42.913 New DB connection, total: 2
2007-04-05 11:24:42.914 Connected to database 'mythconverg' at host: localhost
2007-04-05 11:24:42.917 mythbackend: MythBackend started as master server
2007-04-05 11:24:42.986 EITHelper: localtime offset -5:00:00 
2007-04-05 11:24:42.997 New DB connection, total: 3
2007-04-05 11:24:43.005 Connected to database 'mythconverg' at host: localhost
2007-04-05 11:24:43.186 EITHelper: localtime offset -5:00:00 
2007-04-05 11:24:43.308 New DB scheduler connection
2007-04-05 11:24:43.309 Connected to database 'mythconverg' at host: localhost
 is defined, but isn't attached to a cardinput.
2007-04-05 11:24:43.328 Main::Starting HttpServer
2007-04-05 11:24:43.449 Main::Registering HttpStatus Extension
2007-04-05 11:24:43.473 mythbackend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-04-05 11:24:43.473 Enabled verbose msgs:  important general
2007-04-05 11:24:43.474 AutoExpire: Found 2 recorders w/max rate of 144 MiB/min
2007-04-05 11:24:43.476 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
QServerSocket: failed to bind or listen to the socket
2007-04-05 11:24:43.601 Failed to bind port 6543. Exiting.

mythtv@ubuntuPVR:~$ ps -p `cat /var/run/mythtv/mythbackend.pid`
  PID TTY          TIME CMD
mythtv@ubuntuPVR:~$

---

### Post by superm1 on 2007-04-05
If it can't bind to 6543, but no other backend process is running - perhaps a different app grabbed the port:

```
sudo netstat -ntp | grep 6543
```

---

### Post by Panhead Bill on 2007-04-06
Well since that didn't indicate that the port was in use, what could I try next? 


mythtv@ubuntuPVR:~$ sudo netstat -ntp | grep 6543
Password:
mythtv@ubuntuPVR:~$ sudo netstat -ntp | grep 6543
mythtv@ubuntuPVR:~$ 

TIA
Panhead Bill

---

### Post by newlinux on 2007-04-06
I'm just taking a random shot... does mythbackend need to be run with sudo? Maybe try that. Have you had this backend working before?

where do you see the message?
> localhost is defined, but isn't attached to a cardinput

---

### Post by superm1 on 2007-04-06
> **Panhead Bill said:**
> Well since that didn't indicate that the port was in use, what could I try next? 


mythtv@ubuntuPVR:~$ sudo netstat -ntp | grep 6543
Password:
mythtv@ubuntuPVR:~$ sudo netstat -ntp | grep 6543
mythtv@ubuntuPVR:~$ 

TIA
Panhead Bill
Bill,
Do you have a network handing out dynamic ip addresses?  Perhaps your address has changed among reboots.  If this is the case, you may have configured mythbackend to bind to an address that you don't have previously in mythtv-setup.

Let me elaborate with a hypothetical situation:
Say you start out, and your router assigns your computer 192.168.1.100.  It leaves the lease valid for this address for say 10 hours.  You go into mythtv-setup, and in an effort to allow external machines to connect, you set the BackendServerIP (and possibly Master Server IP) to 192.168.1.100.  Now the first time you start mythbackend, you still have this IP and things are all fine and dandy.
For some reason or another, your computer is off when it comes time to renew the lease assigned by your router.  Your friend joe comes over with his laptop, connects to your router.  Immediately, your router sees that 192.168.1.100 is no longer in use and gives Joe this address.  Now sometime between when Joe's lease expires and then you turn back on your backend computer (perhaps to show off mythtv to Joe).  Your backend gets assigned an ip address of 192.168.1.101.  Now the mythtv startup scripts start out by querying /etc/mythtv/mysql.txt or ~/.mythtv/mysql.txt to locate the mysql server.  They see a localhost listed in the file, and connect to the local server at 127.0.0.1.  The backend process starts out by querying the mysql database for whether it is supposed to be master backend and what IP address to bind to.  Now it sees that it is supposed to be binding to 192.168.1.100, and attempts this.  It's unable to, since the only IP address assigned to the computer is 192.168.1.101.

Make sense?  Is this you?

---

### Post by superm1 on 2007-04-06
If this situation is you, here is your solution:

Setup static DHCP handouts if your router supports them.  This typically involves putting your MAC address in a table on the router.  Most netgear routers support this, but i'm not sure about a generality of other routers.  If your router doesn't support this, then you will have to setup a static address on the Ubuntu box.

Once you've got a static address setup, remove and purge mythtv-database and mysql-server-5.0.  This will force it to drop the mythconverg database (alleviating any other outstanding issues related to addresses).

Reinstall mysql-server-5.0 and mythtv-database.  Configure mythtv-setup as previously, and remember to use your static address for both the Master Server IP and IP of that Backend.

---

### Post by superm1 on 2007-04-06
> **newlinux said:**
> I'm just taking a random shot... does mythbackend need to be run with sudo? Maybe try that. Have you had this backend working before?

where do you see the message?
I think this message is directly related to my above concern.
About running mythbackend as sudo though,
the init script should be, but not the backend itself
sudo /etc/init.d/mythtv-backend start for example.

He was logged in as "mythtv", so launching the backend can just be done on the command line for experimental purposes to identify this problem.

---

### Post by Panhead Bill on 2007-04-07
Superm1;

  I scanned my belkin router's dhcp client list.  while I'm not sure that these address assignments are static, they are current -  all of the equipment listed is "on" and will stay that way for a bit.  

I went into mythtv-setup and set the IP address to be the one listed for the mythbox.  When I did a mythfrontend comand via terminal, there was no change to the box's (lack of) performance.  The output on the terminal window did change slightly; instead of getting errors on the loopback address, the errors are on the current IP address:

SIP listening on IP Address 192.168.2.2:5060 NAT address 192.168.2.2
SIP: Cannot register; proxy, username or password not set
2007-04-07 19:06:54.680 Starting media monitor.
2007-04-07 19:06:56.625 Connecting to backend server: 192.168.2.2:6543 (try 1 of 5)
2007-04-07 19:06:56.653 MythSocket(82de250:21): Protocol error: 'B' is not a valid size prefix. 82 bytes pending.
2007-04-07 19:06:56.654 Unexpected response to MYTH_PROTO_VERSION: 
2007-04-07 19:06:56.655 TV: Attempting to change from None to None
2007-04-07 19:07:08.181 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/status-ui.xml

Note: Four of the last five lines repeat until I stop mythtv with only the mythsocket(address) changing.  (The "TV:" line is only in the first set.

One question, would the dynamic addressing affect my mythbox that is a combined frontend/backend, since the frontend backend and master backend all reside at the same IP address?

- - - - - - - 

On a different note, my "borked" mythbox still teases me in many ways.  I couldn't play a temp recording with mplayer when I tried to verify that my capture cards were still functional, but yesterday I used the command line to do this and mplayer works.  If I try to use mplayer through gnome, all I get is a "Fatal Error!" window that states: "Error opening/initializing the selected video_out (-vo) device."

Any advise on this puzzle?

- - - - - - - 

I'm having new and different problems on the second box I'm building, but I'll post them on a different thread.



TIA

"Panhead Bill"

---

### Post by Panhead Bill on 2007-04-08
The router I use defaults to "forever" assigned I.P. addresses, and the router has been running for months w/o powerdown or reboot.  I'd feel safe in saying that the I.P. address has not changed since my mythbox was first connected to the router.

Still troubleshooting;
Panhead Bill

---

### Post by mfalcon on 2007-04-15
For me, using Ubuntu 6.10 / PVR-150 / MythTV, changing the ip address to static worked without having to rebuild the db. I did have to 'empty' the 'Program' table in the [Mythconverg] database, then run 'mythfilldatabase'.

---

