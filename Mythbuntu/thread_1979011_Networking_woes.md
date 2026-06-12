---
title: "Networking woes"
date: 2012-05-12
forum: Mythbuntu
---

### Post by kcsoft on 2012-05-12
Hi all, I'm probably just overlooking something here.
I've tried mythbuntu 11.10 and 12.04 and have not had any joy getting a remote frontend connected or mythweb working over my lan. If I enable a mythweb password it asks for it then just times out, there seems to be no upnp either. A remote frontend won't connect even if pointed at the ip and port.

Local machine access works fine. Mythweb and frontend are working on it with no problem.
I've used the proper ip address in mythbackend setup.
This seems strange to me and almost hardware related as on a previous machine it was virtually plug and play, I changed the ip in mythbackend setup and away it went.

Previous machine was an acer aspire 4920g, current one is a toshiba m50

Thanks in advance

---

### Post by klc5555 on 2012-05-12
> **kcsoft said:**
> Hi all, I'm probably just overlooking something here.
I've tried mythbuntu 11.10 and 12.04 and have not had any joy getting a remote frontend connected or mythweb working over my lan. If I enable a mythweb password it asks for it then just times out, there seems to be no upnp either. A remote frontend won't connect even if pointed at the ip and port.

Local machine access works fine. Mythweb and frontend are working on it with no problem.
I've used the proper ip address in mythbackend setup.
This seems strange to me and almost hardware related as on a previous machine it was virtually plug and play, I changed the ip in mythbackend setup and away it went.

Previous machine was an acer aspire 4920g, current one is a toshiba m50

Thanks in advance

Sounds like MYSQL on the server is not configured to listen to remote IPs. This is usually set in the mythbuntu control centre by simply checking the appropriate box in the Services section. 

Or the my.cnf file under /etc may be edited to make sure the line "skip-networking" is not present or remarked out (i.e. preceded by #) and you've added the line ```
bind-address =  
``` where your server's IP address is placed after the = 

Then the mysql service is restarted to incorporate the changes.

---

### Post by kcsoft on 2012-05-12
Skip-networking line was not present. I changed Bind-address to reflect the physical ip address. Unfortunatly no change. I just don't get it

---

### Post by nickrout on 2012-05-12
> **kcsoft said:**
> Skip-networking line was not present. I changed Bind-address to reflect the physical ip address. Unfortunatly no change. I just don't get it

did you restart mysqld?

logs?

---

### Post by kcsoft on 2012-05-12
> **nickrout said:**
> did you restart mysqld?

logs?

i restarted the whole machine.

hey where are the logs? i'll post the backend and mysql ones

---

### Post by kcsoft on 2012-05-12
backend : [http://pastebin.com/RsXvycHS](http://pastebin.com/RsXvycHS)
mysql error log : [http://pastebin.com/1i20jBVd](http://pastebin.com/1i20jBVd)
my.cnf : [http://pastebin.com/MA7KQXhc](http://pastebin.com/MA7KQXhc)

i can post up any others that are needed.
please note that i have a fresh install and i have not yet set up tv

---

### Post by nickrout on 2012-05-12
> **kcsoft said:**
> backend : [http://pastebin.com/RsXvycHS](http://pastebin.com/RsXvycHS)
mysql error log : [http://pastebin.com/1i20jBVd](http://pastebin.com/1i20jBVd)
my.cnf : [http://pastebin.com/MA7KQXhc](http://pastebin.com/MA7KQXhc)

i can post up any others that are needed.
please note that i have a fresh install and i have not yet set up tv

AFAIK the backend will not even run without a capture card defined.

What you probably need is the log of a frontend when it starts and tries to connect.

other things to try:

Backend

```
sudo netstat -tanp|grep 3306
```

will tell you if mysql is running

On the frontend

```
mysql -h backendmachine -u mythtv -p mythconverg
```

see if mysql is contactable from the frontend.

---

### Post by kcsoft on 2012-05-12
[QUOTE=nickrout;11930456]AFAIK the backend will not even run without a capture card defined.

What you probably need is the log of a frontend when it starts and tries to connect.

other things to try:

Backend

```
sudo netstat -tanp|grep 3306
```

interesting

```
casey@casey-Satellite-M50:~$ sudo netstat -tanp|grep 3306
[sudo] password for casey: 
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      825/mysqld      

```

```
mysql -h backendmachine -u mythtv -p mythconverg
```

frontend is on a windows machine, no problems before, i'll try this from a virtualbox mythbuntu

---

### Post by klc5555 on 2012-05-12
Some distributions insert a line:

SKIP="--skip-networking"

into the rc.mysqld script or other /init.d or /rc.d script in the /etc directory used to start or restart mysqld. I'm not sure at the moment whether Ubuntu does it this way, as currently my only Ubuntu machines are being used as frontends.

If the line is present in the rc.mysqld or equivalent on your server, it will also need to be remarked out as:

# SKIP="--skip-networking"

---

### Post by kcsoft on 2012-05-12
> **klc5555 said:**
> Some distributions insert a line:

SKIP="--skip-networking"

into the rc.mysqld script or other /init.d or /rc.d script in the /etc directory used to start or restart mysqld. I'm not sure at the moment whether Ubuntu does it this way, as currently my only Ubuntu machines are being used as frontends.

If the line is present in the rc.mysqld or equivalent on your server, it will also need to be remarked out as:

# SKIP="--skip-networking"

already done

frontend log : [http://pastebin.com/kzBqYViK](http://pastebin.com/kzBqYViK)

---

### Post by nickrout on 2012-05-12
> **kcsoft said:**
> [QUOTE=nickrout;11930456]AFAIK the backend will not even run without a capture card defined.

What you probably need is the log of a frontend when it starts and tries to connect.

other things to try:

Backend

```
sudo netstat -tanp|grep 3306
```

interesting

```
casey@casey-Satellite-M50:~$ sudo netstat -tanp|grep 3306
[sudo] password for casey: 
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      825/mysqld      

```

```
mysql -h backendmachine -u mythtv -p mythconverg
```

frontend is on a windows machine, no problems before, i'll try this from a virtualbox mythbuntu

There is no reason you shouldn't be able to run that command from windows.

Are you sure you have the right username and password setup for the frontend? The username is mythtv, the password can usually be found on the backend mahine in mysql.txt.

---

### Post by kcsoft on 2012-05-12
> **nickrout said:**
> [QUOTE=kcsoft;11930528]

There is no reason you shouldn't be able to run that command from windows.

Are you sure you have the right username and password setup for the frontend? The username is mythtv, the password can usually be found on the backend mahine in mysql.txt.

double checked password seems that mysql command wont work under windblows

i can ping the machine on the network but i cant connect a frontend or mythweb. got me stumped.

this is my 6th fresh install.

---

### Post by nickrout on 2012-05-12
> **kcsoft said:**
> [QUOTE=nickrout;11930643]

double checked password seems that mysql command wont work under windblows

i can ping the machine on the network but i cant connect a frontend or mythweb. got me stumped.

this is my 6th fresh install.

try mythfrontend -v database and see if there are any clues there.

I suppose mysql is not installed on windows. Never mind. 

Try -v database and see where you get to.

Also telnet  backendmachine 3306 (actually you may need to check the windows telnet command help, telnet /? as I am not 100% sure of the syntax).

telnet should connect to the mysql port on the backendmachine, you will then get some garbage on the screen, but at least you will know whether or not you are getting a connection to mysql.

---

### Post by kcsoft on 2012-05-13
telnet using putty windows gave me :
```
 5.1.58-1ubuntu1¼<X'V]P["BcO@4"NBA\-ot packets out of order 
```
so mysql is running i guess.
mythfrontend -v database : [http://pastebin.com/Q3K1j6MZ](http://pastebin.com/Q3K1j6MZ)

mythbuntu frontend in virtualbox wont connect either. i dont know why its telling me:
```
 Access denied for user 'mythtv'@'Bedroom.BigPond' (using password: YES) 
```i have the correct password.

bedroom is the pc with the frontend

frustration....

---

### Post by kcsoft on 2012-05-13
just noticed this

```
 casey@casey-Satellite-M50:~$ grep mythtv: /etc/groupmythtv:x:117:casey
casey@casey-Satellite-M50:~$ sudo netstat -tanp|grep 3306
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      825/mysqld      
casey@casey-Satellite-M50:~$ 

```

why is it telling me 0.0.0.0:* shouldn't there be an ip address there?

---

### Post by nickrout on 2012-05-13
0.0.0.0 means it is listening for all IP addresses, mine reads like that, don't worry.

Looks like mysql is not accepting authentication from other hosts. This is a separate problem to it having it's port open to other hosts.

try ```
sudo dpkg-reconfigure mythtv-common
sudo dpkg-reconfigure mythtv-database
```

On the backend.

---

### Post by kcsoft on 2012-05-13
> **nickrout said:**
> 0.0.0.0 means it is listening for all IP addresses, mine reads like that, don't worry.

Looks like mysql is not accepting authentication from other hosts. This is a separate problem to it having it's port open to other hosts.

try ```
sudo dpkg-reconfigure mythtv-common
sudo dpkg-reconfigure mythtv-database
```

On the backend.

no change. is there something in the mysql config i can change?? i dont care if the system is left wide open security wise. i just want it to work.

---

### Post by kcsoft on 2012-05-13
im going to update the system thru update manager and see what happens.

---

### Post by nickrout on 2012-05-13
> **kcsoft said:**
> im going to update the system thru update manager and see what happens.

why?

look at your user table in the mysql database

---

### Post by kcsoft on 2012-05-13
> **nickrout said:**
> why?

look at your user table in the mysql database

i like to be up to date in case there are fixes

how do i look at the user table and how and what should i do to it.
thank you for your patience with a mythtv noob

---

### Post by klc5555 on 2012-05-13
nickrout brings up a very good point in that apparently you haven't seen yet whether you can actually log in to mysql and get a mysql prompt locally on the backend machine.

From a prompt on the backend machine itself, try: ```
mysql -u mythtv -p
```

The machine will then ask you for the randomly generated mysql password (found in the file mysql.txt, symlinked under the ../.mythtv directory under /home/[your-username] or /home/mythtv/ and elsewhere)

If supplying this password doesn't get us to a nice mysql> prompt, then the mysql problem may be closer to home than a remote connection problem.

If you are able to login locally to mysql, you can check at the mysql prompt whether mythconverg exists: ```
mysql> SHOW databases;
```

If user mythtv can login locally to mysql and find the skimpy initial mythconverg database, then the problem likely really is just remote connections. I note the following in your my.cnf:

# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#

Now 'buntu variants unlike some other distros tend to rely on apparmor in part to compensate for things like emaciated root user security and a guest account that is present and activated by default. So you may wish to check for the specified file and whether it has a setting that's interfering with mysql's network connectivity that will need modification.

---

