---
title: "Can't telnet into Mythtv"
date: 2014-05-06
forum: Mythbuntu
---

### Post by williamwright-orsk on 2014-05-06
Hi!

I have been trying to set up Mythtv on Debian Wheezy. However, I have been having an issue in which I can't connect to the backend server. 

When I run mythfilldatabase, it tells me that “Connection to master server timed out.”. So what I did then was I tried to Telnet into it. When I do it tells me:

```

server@media-server:~$ telnet localhost 6543 
 Trying ::1... 
 Trying 127.0.0.1... 
 telnet: Unable to connect to remote host: Connection refused 

```

So then I do an nmap Port Scan on Localhost to see what is going on, the results show that “Mythtv” isnt even listed:
```

 server@media-server:~$ nmap localhost 
 
 Starting Nmap 6.00 ( http://nmap.org ) at 2014-05-06 09:21 BST 
 Nmap scan report for localhost (127.0.0.1) 
 Host is up (0.00076s latency). 
 Other addresses for localhost (not scanned): 127.0.0.1 
 Not shown: 984 closed ports 
 PORT     STATE SERVICE 
 21/tcp   open  ftp 
 22/tcp   open  ssh 
 25/tcp   open  smtp 
 53/tcp   open  domain 
 111/tcp  open  rpcbind 
 139/tcp  open  netbios-ssn 
 445/tcp  open  microsoft-ds 
 901/tcp  open  samba-swat 
 3306/tcp open  mysql 
 5050/tcp open  mmcc 
 5901/tcp open  vnc-1 
 6001/tcp open  X11:1 
 6502/tcp open  netop-rc 
 8080/tcp open  http-proxy 
 8181/tcp open  unknown 
 9091/tcp open  xmltec-xmlmail 
  
 Nmap done: 1 IP address (1 host up) scanned in 0.19 seconds 
```

According to some of the stuff on other forums, there should be “6543/tcp open  mythtv” in this Port Scan. However, there isn't.  

 

 Any ideas?

---

### Post by blm-ubunet on 2014-05-06
How far thru' the install/setup have you progressed?
Have you run mythtv-setup (first making sure  mythbackend is stopped)?

Does mythtv-setup start successfully?

The backend does not support a true telnet interface.

---

### Post by williamwright-orsk on 2014-05-06
Yeah I've ran Mythtv-setup which runs normally. However, the issue I have had is accessing the Backend.

However, when I run netstat -an | grep LISTEN it does not show anything to do with Mythtv.

---

### Post by williamwright-orsk on 2014-05-06
Hi again, 

I have found some other stuff about the Backend. Some quite strange stuff:

Firstly, I decide to start the backend and I get this: 

```

server@media-server:/etc/init$ sudo /etc/init.d/mythtv-backend start
Starting MythTV server: mythbackend .

```

Then, I tell it to restart it:

```

server@media-server:/etc/init$ sudo /etc/init.d/mythtv-backend restart
Restarting MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.
.
.

```

I then check it using the command  pgrep mythbackend and it goes to a return prompt! 

Finally, I run mythbackend and it runs through like this: 

```

server@media-server:/etc/init$ mythbackend
2014-05-06 15:21:00.353257 C  mythbackend version:  [v0.26.1] www.mythtv.org
2014-05-06 15:21:00.353300 C  Qt version: compile: 4.8.2, runtime: 4.8.2
2014-05-06 15:21:00.353308 N  Enabled verbose msgs:  general
2014-05-06 15:21:00.353340 N  Setting Log Level to LOG_INFO
2014-05-06 15:21:00.355333 I  Setup Interrupt handler
2014-05-06 15:21:00.355366 I  Setup Terminated handler
2014-05-06 15:21:00.355386 I  Setup Segmentation fault handler
2014-05-06 15:21:00.355409 I  Setup Aborted handler
2014-05-06 15:21:00.355432 I  Setup Bus error handler
2014-05-06 15:21:00.355449 I  Setup Floating point exception handler
2014-05-06 15:21:00.355473 I  Setup Illegal instruction handler
2014-05-06 15:21:00.355504 I  Setup Real-time signal 0 handler
2014-05-06 15:21:00.355606 N  Using runtime prefix = /usr
2014-05-06 15:21:00.355642 N  Using configuration directory = /home/server/.mythtv
2014-05-06 15:21:00.355840 I  Assumed character encoding: en_GB.UTF-8
2014-05-06 15:21:00.356622 N  Empty LocalHostName.
2014-05-06 15:21:00.356645 I  Using localhost value of media-server
2014-05-06 15:21:00.356724 I  Testing network connectivity to '192.168.1.185'
2014-05-06 15:21:00.357133 I  Added logging to the console
2014-05-06 15:21:00.359711 I  Starting process signal handler
2014-05-06 15:21:00.361670 I  Starting process manager
2014-05-06 15:21:00.363122 I  Starting IO manager (write)
2014-05-06 15:21:00.366640 I  Starting IO manager (read)
2014-05-06 15:21:00.541143 N  Setting QT default locale to en_GB
2014-05-06 15:21:00.541176 I  Current locale en_GB
2014-05-06 15:21:00.541298 N  Reading locale defaults from /usr/share/mythtv//locales/en_gb.xml
2014-05-06 15:21:00.563314 I  Current MythTV Schema Version (DBSchemaVer): 1307
2014-05-06 15:21:00.565119 I  Loading en_gb translation for module mythfrontend
2014-05-06 15:21:00.571484 N  MythBackend: Running as a slave backend.
2014-05-06 15:21:00.576375 E  TVRec(3): Problem finding starting channel, setting to default of '3'.
2014-05-06 15:21:00.576734 W  DVBChan(3:): Opening DVB frontend device failed.
            eno: No such file or directory (2)
2014-05-06 15:21:00.576752 E  DVBChan(3:): Failed to open DVB frontend device due to fatal error or too many attempts.
2014-05-06 15:21:00.576765 E  ChannelBase: CreateChannel() Error: Failed to open device 
2014-05-06 15:21:00.576832 E  Problem with capture cards. Card 3 failed init
2014-05-06 15:21:00.576880 W  MythBackend: No valid capture cards are defined in the database.
2014-05-06 15:21:00.581640 I  Added logging to mythlogserver at TCP:35327

```

---

### Post by steeldriver on 2014-05-06
is this intentional? or is this instance supposed to be the master?

```

2014-05-06 15:21:00.571484 N  MythBackend: [COLOR=#ff0000]**Running as a slave backend**[/COLOR].

```

---

### Post by williamwright-orsk on 2014-05-06
I'm not really sure. I'm quite new to it.

But I suppose it should be master.

---

### Post by dannyboy79 on 2014-05-06
if you don't have at least 1 master backend on the LAN than yes, this machine needs to be the master. can you connect to your mythconverg database using mysql?
```
mysql -u mythtv -p mythconverg
```
enter the password you can find within /home/mythtv/.mythtv/config.xml which should be the same as the password found in /etc/mythtv/config.xml
if it refuses connection than that's why, your mysql database isn't allowing connections for mythtv user

---

### Post by williamwright-orsk on 2014-05-06
I can connect into the database with my Passwd.

---

### Post by dannyboy79 on 2014-05-06
you'll need to resolve your capture card failure issues i believe otherwise the backend won't start correctly. besides not being able to telnet into the backend, what's the issue?

---

### Post by williamwright-orsk on 2014-05-06
Would it allow connection if there was no capture card?

---

### Post by dannyboy79 on 2014-05-06
no, i believe you have to setup a tuner correctly for the master backend to work properly. here's a thread that talks about setting up a fake tuner, fake video source, etc etc. [http://www.gossamer-threads.com/lists/mythtv/users/421624](http://www.gossamer-threads.com/lists/mythtv/users/421624)

---

