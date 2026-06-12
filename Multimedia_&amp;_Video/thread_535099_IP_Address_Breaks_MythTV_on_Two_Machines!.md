---
title: "IP Address Breaks MythTV on Two Machines!"
date: 2007-08-26
forum: Multimedia &amp; Video
---

### Post by GenuineXP on 2007-08-26
So I wanted to give MythTV a try and installed it using Synaptic. I won't have television service until two days from now but I went ahead and configured the backend with a dummy antenna input. It seemed to work fine and I could start up the frontend and watch fuzzy broadcast channels.

I installed only the frontend on my laptop hoping I could patch it into the backend on my desktop box. To test this out, I changed the default backend IP from the loopback (127.0.0.1) to something I *thought* was reasonable: 192.168.3.1. First of all, let me know if there's something stupid about that address. Currently, my router assigns addresses via DHCP in the 192.168.1.x range, the router being 192.168.1.1. My modem has the address 192.168.2.1. I thought using 192.168.3.1 was fine.

Anyway, after I configured this in the backend setup tool I closed it down and told the prompt to run "mythtvfilldatabase". Well, that locked up for about fifteen minutes, so I closed it. After that, neither the frontend or backend would run any longer. What's worse is that I setup the frontend to look for the backend at the 192.168.3.1 address and it too no longer runs on my laptop!

I get this output when I run mythtv-setup on my desktop:

```
Stopping MythTV server: mythbackend .
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-08-26 02:34:38.172 Using runtime prefix = /usr
2007-08-26 02:34:38.189 Gnome-Screensaver support enabled
2007-08-26 02:34:38.189 DPMS is active.
2007-08-26 02:34:38.231 New DB connection, total: 1
```

And from there it just hangs. I noticed on my laptop similar output from the frontend that seems to repeatedly try to connect to the backend (the output slowly continues and mentions the 192.168.3.1 address).

I tried completely removing MythTV with apt-get --purge and reinstalling it but I get the same results now. It used to work just fine. How could an IP address completely destroy the software?!

Any help is very much appreciated! Thanks!

EDIT:

This output was appended to that shown above after five minutes or so:

```
2007-08-26 02:37:47.241 Unable to connect to database!
2007-08-26 02:37:47.242 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.3.1' (110)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-08-26 02:40:56.301 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...

```

Hopefully this is helpful. Note the IP address. Thanks again!

---

### Post by Scorpuk on 2007-08-26
IP addresses:


On a network the first three numbers need to be identical for computers to be able to talk to each other. IE.


192.168.1.2 will talk to 192.168.1.3, but

192.168.1.2 will not talk to 192.168.3.1


You sure your modem has the IP address of 192.168.2.1?


If it does then your router must be controlling that as a special address to keep the outside world seperate from your network. A bit beyond my knowledge.

Anywho...


As an example:

MythTV backend: 192.168.1.2
Laptop Frontend: 192.168.1.3 (although this can still be DHCP)

Setup the backend so that the mythbox and backend IP addresses are 192.168.1.2

Then when setting up the front end set the hostname to 192.168.1.2


A guide to setting up MythTV can be found here: [https://help.ubuntu.com/community/MythTV_Feisty](https://help.ubuntu.com/community/MythTV_Feisty)

---

### Post by GenuineXP on 2007-08-26
Thanks for the info; I had no idea about the IP addresses.

Anyway, I thought changing the IP address would probably fix the problem, but since the setup utility and the frontend never start, I don't know how I can change the IP!

Is there a manual way to change it? Perhaps a file?

Thanks again.

EDIT:

I tried following some instructions to delete the MySQL database for MythTV (which the guide said would remove all settings) and then I re-ran the mc.sql script. Even after that, I get the same output and the bad IP address is still there! I guess it's not stored in the database?

---

### Post by Scorpuk on 2007-08-26
Hmmmm


I wouldn't have thought the backend would fail to load even with incorrect IP addresses. It shoudl complain a lot and present you with the screen, eventually, to enter the correct details.


As for the front end if you run mythfrontend from a console does a lot of text whiz by complaining about errors? If it does let it run by and it shoudl eventually come up with a screen requesting country info and then the screen requesting the IP infor etc for the backend.  This should deff. happen a I had probs with Ip addresses back in my early days with mythtv and this would constantly happen until I worked it out and got the right Ip addresses.


So I would suggest the following:

1. Ensure both computers are on the network. ie Have an IP address of the sorts: 192.168.1.x

2. On the machine running the backend open a terminal window and type:


```
sudo /etc/init.d/mythtv-backend stop
```

It may say there isnt one running, but lets make sure.
Oh and dont forget to type in your user password.

```
mythtv-setup
```


If you don't eventually get to the setup pages let me know what happened. If a lot of error messages are whizzing by just let them and give it 5 - 10 minutes to see what happens.


If the above is successfull:

3. On the machine running the frontend open a terminal window and type:

```
mythfrontend
```

If a lot of error messages are whizzing by just let them and give it 5 - 10 minutes to see what happens.



4. All else fails a complete uninstall of mythtv and mysql and then follow the mythtv guide from start to end may help you out. BUT dont uninstall mysql if you have any other database running without backing them up...

---

### Post by GenuineXP on 2007-08-26
No dice.

I don't get a slew of error messages. Basically, the output I originally posted is all that I see and both the frontend and the setup utility never actually start.

I totally removed MythTV and MySQL with:

```
sudo apt-get --purge remove mythtv* mysql*
```

Which seemed to completely remove everything I got in the mythtv package because apt-get freed 140 MB of disk space (exactly how much it reported to consume when I installed it). After that, I restarted my system (just to be safe) and reinstalled the mythtv package with:

```
sudo apt-get install mythtv
```

It installed MythTV once again and when I tried to start mythtv-setup I got very similar output as I posted above (with the same darn IP address)! Here it is:

```
Stopping MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.
.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-08-26 11:18:31.879 Using runtime prefix = /usr
2007-08-26 11:18:31.911 Gnome-Screensaver support enabled
2007-08-26 11:18:31.912 DPMS is active.
2007-08-26 11:18:31.964 New DB connection, total: 1
2007-08-26 11:21:40.843 Unable to connect to database!
2007-08-26 11:21:40.843 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.3.1' (110)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-08-26 11:24:49.775 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-08-26 11:27:58.827 Unable to connect to database!
2007-08-26 11:27:58.827 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.3.1' (110)

QSqlQuery::exec: database not open

```

Where is this IP address stored? It can't be in a MySQL database because I completely removed MySQL and told it to delete any existing databases.

Should this be listed as some sort of bug? I find it very inconveniencing that entering a bad IP address disables an entire application like this.

Thanks again for any help. I appreciate it.

---

### Post by Scorpuk on 2007-08-26
sounds like somethign is not being uninstalled.


ok can you give me the output from:

```
ifconfig
```

on both computers. Really only need from backend as no point wondering about frontend until backend is working. :(


This will let us know what the IP address of each machine is.

---

### Post by GenuineXP on 2007-08-26
ifconfig gives me this:

```
eth0      Link encap:Ethernet  HWaddr 00:11:D8:92:9B:39  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:11:D8:92:AA:DB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth2      Link encap:Ethernet  HWaddr 00:0F:66:6D:6C:FF  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:66ff:fe6d:6cff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1013 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1064 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:909527 (888.2 KiB)  TX bytes:162334 (158.5 KiB)
          Interrupt:17 Memory:d5008000-d500a000 

eth0:avah Link encap:Ethernet  HWaddr 00:11:D8:92:9B:39  
          inet addr:169.254.7.1  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0x8000 

eth1:avah Link encap:Ethernet  HWaddr 00:11:D8:92:AA:DB  
          inet addr:169.254.10.103  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6364 (6.2 KiB)  TX bytes:6364 (6.2 KiB)


```

This is on the desktop (backend) machine. Like you said, no use worrying about the other machine if the backend isn't working correctly. Both computers are connected wirelessly, by the way. (Annoying, but it's my only option here.)

Also, mythtv-setup is still spewing out some output very slowly. Here's the full listing thus far:

```
Stopping MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.
.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-08-26 11:18:31.879 Using runtime prefix = /usr
2007-08-26 11:18:31.911 Gnome-Screensaver support enabled
2007-08-26 11:18:31.912 DPMS is active.
2007-08-26 11:18:31.964 New DB connection, total: 1
2007-08-26 11:21:40.843 Unable to connect to database!
2007-08-26 11:21:40.843 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.3.1' (110)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-08-26 11:24:49.775 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-08-26 11:27:58.827 Unable to connect to database!
2007-08-26 11:27:58.827 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.3.1' (110)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-08-26 11:31:06.717 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-08-26 11:31:06.773 Database not open while trying to load setting: GuiVidModeResolution
2007-08-26 11:34:15.773 Unable to connect to database!
2007-08-26 11:34:15.773 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.3.1' (110)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-08-26 11:37:24.654 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-08-26 11:37:24.710 Database not open while trying to load setting: GuiVidModeWidth
2007-08-26 11:40:33.710 Unable to connect to database!
2007-08-26 11:40:33.710 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.3.1' (110)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-08-26 11:43:42.766 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-08-26 11:43:42.822 Database not open while trying to load setting: GuiVidModeHeight
2007-08-26 11:46:51.262 Unable to connect to database!
2007-08-26 11:46:51.262 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.3.1' (110)

QSqlQuery::exec: database not open


```

---

### Post by Scorpuk on 2007-08-26
I'll get back to you shortly going to vnc my server and check a couple of things.

On dial-up too :( :(

---

### Post by Scorpuk on 2007-08-26
Bah still no idea.


All I can suggest is to leave those messages scrolling by and see what happens.


If I was at home and infront of my server I'd force a wrong IP address to see what happens, but not home for another week.


I'm about to finish work, half hour or so, so wont have internet access until tomorrow morning (7am GMT). Will check back before I leave and see if you are any further.

---

### Post by GenuineXP on 2007-08-26
No luck yet. Should I perhaps configure my network to dish out IP addresses in the 192.168.3.x range? Maybe that will at least give me what I need to start mythtv-setup. I'd have to make sure that my box got the right address though...

Has anyone else had this problem? It's doesn't seem right that it could occur so easily on two completely different machines (one is an x86 laptop while the other is an x86_64 desktop)!

---

### Post by psiu on 2007-08-26
According to the output from your backend machine, it's IP address is 192.168.1.5

I would think (completely off the top of my very un-Linuxy and Mythy head) that leaving the backend IP alone, and then simply telling the frontend box to look to 192.168.1.5 for the backend is the way to go.

And as someone pointed out...you sure it's 192.168.2.1 and etc? The IPs should be only be changing on the last digit.

---

### Post by Scorpuk on 2007-08-27
@psiu


Its the backend he is trying to setup at the moment.

Also it is possible to have the 2nd last digit different in a network as this makes it an exceedingly good firewall. Only what you permit to be passed to the other address range get through, everything else won't see the other network. Not sure what its called though, but have heard of a linux firewall machine with two network cards in the box to do this.


Anywho

If you are still having problems you could try changing the IP address of your backend to 192.168.3.1 as you suggested, although you would have to do this manually.

So:

1. Unplug backend from network.
2. Manually configure the backend to use the IP address 192.168.3.1

IP address: 192.168.3.1
Subnet Mask: 255.255.255.0 (This should be automatically filled in for you when you click on the field)
Gateway address: 192.168.3.255

3. Now check the IP address is set correctly:

```
iwconfig
```

This will give you details of your wireless adapter.

If it returns that your IP address is 192.168.3.1 we are good to go, well good to try anywho :o :)


Hopefully you will be able to get into mythtv setup.

If you do then at some point try changing the IP address to 192.168.1.5 (Your original IP address assigned by the router) for both fields - "IP address for mythbox" and "Master server IP address".


You can always setup mythtv and then change the IP address.


Goodluck!

---

### Post by GenuineXP on 2007-08-27
Okay, I manually configured my IP address and it worked like a charm. To be safe, I set the backend/frontend IP addresses all to the loopback (127.0.0.1). I had to manually fix the SQL database after that until I finally got myth to connect (had edit the database permissions and change the password).

After all of that, both the backend and frontend run, but the frontend never finds the master backend server! I have no idea what's happening since all the IP address are set to the loopback; how could the frontend not see the backend? I've ensured the backend is running and it still doesn't find it!

Any more good ideas? Thanks again for all the help. :-)

---

### Post by Scorpuk on 2007-08-28
If the frontend is on a different machine then you will need to set an IP address for the backend and direct the frontend to look for the backend on that IP address.


Since you have the address set to loop back you can play with DHCP settings all you want and it shouldnt give you any problems.


I would recomment setting your frontend machine to DHCP, see what IP address it gets and then set a static IP address on your backend based on that.


ie. 

DHCP assigns 192.168.1.2 to laptop
Set backend to 192.168.1.20

or

DHCP assigns 192.168.3.2 to laptop
Set backend to 192.168.3.20

etc.

use iwconfig to find out what your IP address is like before.


The backend is not set to the next sequential number as the DHCP server wont know that its being used and may try to assign the next number IF you attach another computer to the network.

---

### Post by GenuineXP on 2007-08-28
It's not the laptop that's the trouble, it's my desktop! The backend is running on the desktop and I have all the IP addresses in MythTV set to the loopback, yet the frontend (on the same machine) doesn't see the backend! I don't get it, because before I tried all of this (before I gave it the bad IP address) it worked. Now even with the IPs set to 127.0.0.1, the frontend never seems to find the backend (even though it's clearly running).

Any ideas...? This one's got me stumped.

---

### Post by newlinux on 2007-08-28
when you run the frontend from a terminal on the same machine as your running backend, what does it output?

---

### Post by GenuineXP on 2007-08-28
Here's the output:

```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-08-28 17:17:46.165 Using runtime prefix = /usr
2007-08-28 17:17:46.174 Gnome-Screensaver support enabled
2007-08-28 17:17:46.175 DPMS is active.
2007-08-28 17:17:46.355 New DB connection, total: 1
2007-08-28 17:17:46.442 Connected to database 'mythconverg' at host: 127.0.0.1
2007-08-28 17:17:46.458 Total desktop dim: 1280x1024, with 1 screen[s].
2007-08-28 17:17:46.535 Running in a window
2007-08-28 17:17:46.535 Using screen 0, 1280x974 at 0,25
2007-08-28 17:17:46.573 Current Schema Version: 1160
2007-08-28 17:17:46.573 mythfrontend version: 0.20.20060828-3 www.mythtv.org
2007-08-28 17:17:46.573 Enabled verbose msgs:  important general
2007-08-28 17:17:46.994 Total desktop dim: 1280x1024, with 1 screen[s].
2007-08-28 17:17:46.995 Running in a window
2007-08-28 17:17:46.995 Using screen 0, 1280x974 at 0,25
2007-08-28 17:17:46.996 Switching to square mode (G.A.N.T.)
2007-08-28 17:17:47.017 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-08-28 17:17:47.544 Joystick disabled.
2007-08-28 17:17:48.173 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml
2007-08-28 17:17:48.221 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-08-28 17:17:48.383 Registering Internal as a media playback plugin.
2007-08-28 17:18:01.350 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-08-28 17:18:01.351 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.
2007-08-28 17:18:03.768 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-08-28 17:18:03.769 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.
2007-08-28 17:18:06.400 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-08-28 17:18:06.400 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.

```

Notice it tries to connect to 127.0.0.1. How could that possibly be the wrong address? I also checked the port number, which is correct.

---

### Post by newlinux on 2007-08-28
This error can also happen due to a permissions problem with accessing the mysql database for the mythtv user. Did you follow a particular tutorial when setting this mythmachine up?  Have you checked information your mysql.txt file is correct for logging into the mysql? Sorry if you have already answered these questions, but I'm at work and don't quite have the time to read through the whole thread...

---

### Post by mekis on 2007-09-19
I have exactly the same problem as the one you describe but the error message tells me that mythtv tries to connect to mysql on the wrong IP address, 182.168.1.1 instead of 192.168.1.1.

The error started when I changed from using dhcp to using an fixed IP, maybe I entered this erroneus IP when updating. 

mythtv backend tries to start in the terminal but always comes back to:

Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-09-19 20:39:41.593 Database not open while trying to load setting: GuiVidModeWidth
2007-09-19 20:42:50.598 Unable to connect to database!
2007-09-19 20:42:50.598 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '182.168.1.1' (110)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-09-19 20:45:59.656 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-09-19 20:45:59.712 Database not open while trying to load setting: GuiVidModeHeight

I would also appreciate help on where to correct this error.

---

