---
title: "frontend 2 ip error"
date: 2010-09-21
forum: Mythbuntu
---

### Post by blkbx on 2010-09-21
Hi
I have error that comes up when I turn on mythbuntu front end. It's 'cannot connect to backend server. Have you configured the ip address in the setup menu.' 
The ip between the fe/be is 192.168.2.13 but myth is using 192.168.2.10 also which connects to nothing. I've tried to find whats using it so that I can change it to the ip I've set with no luck. I've checked the my.cnf, mysql.txt, hosts anything that might have had ip number. also I've reinstalled mythbuntu  thinking if I start fresh I can set the ip number I need but it was there in the setup page host ***.10. I'd like to be able to set a static ip for the fe/be but need to use dhcp I'm looking into changing that but for now all I want is to know what is using the ip number so that I can change it.

---

### Post by joho500 on 2010-09-21
If you have a combined FE/BE you can use the localhost address 127.0.0.1. You can set that in the Main setup page of the frontend.

If you have a separate frontend and backend you should enter - at the same setup page in your frontend - the ip address of your backend which should be a static ip address AFAIK.

Joost

---

### Post by blkbx on 2010-09-21
Thanks for your reply
I am using a separate fe/be setup and have the ip number of the backend 192.168.2.13 entered there but if I start the front end using the console here is the errors that I get.

tomas@myth-front:~$ /usr/share/mythtv/mythfrontend.sh 
2010-09-22 10:37:07.465 mythfrontend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2010-09-22 10:37:07.466 Using runtime prefix = /usr
2010-09-22 10:37:07.466 Using configuration directory = /home/tomas/.mythtv
2010-09-22 10:37:08.154 Empty LocalHostName.
2010-09-22 10:37:08.154 Using localhost value of myth-front
2010-09-22 10:37:08.155 Testing network connectivity to '192.168.2.10'

2010-09-22 10:37:14.327 UPnPautoconf() - Found one UPnP backend
2010-09-22 10:37:20.355 HttpComms::done() - NetworkOperation Error on Finish: HTTP request failed (1): url: 'http://192.168.2.10:6544/Myth'
2010-09-22 10:37:20.365 MythXMLClient::GetConnectionInfo Failed - (1) unexpected end of file
2010-09-22 10:37:20.365 Testing network connectivity to '192.168.2.10'
2010-09-22 10:37:26.355 Cannot find (ping) database host 192.168.2.10 on the network
2010-09-22 10:37:26.356 Primary screen: 0.
2010-09-22 10:37:26.356 Using screen 0, 1280x1024 at 0,0
2010-09-22 10:37:26.356 Could not find theme:  - Switching to Terra
2010-09-22 10:37:26.357 Using theme base resolution of 1280x720
2010-09-22 10:37:26.364 Desktop video mode: 1280x1024 60.0204 Hz
2010-09-22 10:37:27.162 get_ip: Name or service not known
2010-09-22 10:37:27.162 LIRC, Error: Failed to parse IP address ''
2010-09-22 10:37:27.162 JoystickMenuThread Error: Joystick disabled - Failed to read /home/tomas/.mythtv/joystickmenurc
2010-09-22 10:37:27.165 New DB connection, total: 1
2010-09-22 10:37:27.177 Using Frameless Window
2010-09-22 10:37:27.177 Using Full Screen Window
2010-09-22 10:37:27.187 Using the Qt painter
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
2010-09-22 10:37:46.613 Writing settings file /home/tomas/.mythtv/mysql.txt
2010-09-22 10:37:46.613 Closing DB connection named 'DBManager0'
2010-09-22 10:37:46.624 Testing network connectivity to '192.168.2.13'
2010-09-22 10:37:46.628 Closing DB connection named 'DBManager0'

See how it's using the ip address192.168.2.10 then later goes to ***.***.*.13and I've no idea where it is getting it from. I've changed all the ones I can think of and checked every file thats named mythtv or mysql.
If I leave the ip settings empty on the fe setup page it will automatically fill in the wrong ip .10 if that can help find the file responsible.
thanks for your help

---

### Post by joho500 on 2010-09-22
Did you look at the contents of the file config.xml in /home/tomas/.mythtv ? (I'm not sure whether this is the correct name. I'm not at home at the moment.) I won't be at home till tomorrow evening. I can look at it then.

Joost

---

### Post by blkbx on 2010-09-22
I did, I did a find on 'mythtv' 'mysql' and went through everything thing that it churned out. Everything has the ip that I added but it still tries to use the 192.***.10 and if I leave the host field empty it will still default to 192.***.10 instead of 192.***.13. I want to do a static ip and use .10 but my router doesn't allow it only dhcp. I've thrown all the money I can at this setup so getting another router that supports static ip addresses isn't something that I can do. Do you have any other ideas?. I thought of monitoring what mythtv does went it starts up. What system calls it uses, external programs it call etc but I've no idea how to do that. I'm stumped and myth-less

---

### Post by ian dobson on 2010-09-22
Hi,

Could it be that you have a mysql.txt floating about somewhere.

go to the terminal any type:-
locate mysql.txt

This will produce a list of all files with the name mysql.txt.  Now go through each file checking which ip address is being used.
Do this on both your backend and frontend.
Note: You should always use ip addresses and avoid using DHCP. If you need to use DHCP then configure the DHCP server so that the backend always gets the same IP address.

Then on your backend check that mysql is configures correctly, so that the frontnd can access it. In the file /etc/mysql/my.cnf check that the line "bind-address           = 127.0.0.1" is disabled (# infront of the line).

When that's done restart the backend and the frontend. Then check the log file on the backend (/var/log/mythtv/mythtvbackend.log) and check that the backend has started correctly.

Regards
Ian Dobson

ps: I don't normaly like being PM'ed asking for help. If I see an intersting thread then I'll get involved.

---

### Post by blkbx on 2010-09-23
Hi Ian
I did want you suggested about the mysql.txt files. I'd already read about binding the local address to the ip address used by the router. So that was already done.    	 	 	 	 	 	  
locate found 4 mysql.txt files, /etc/mythtv/mysql.txt, /home/homefolder/.mythtv/mysql.txt, /home/mythtv/.mythtv/mysql.txt, /usr/share/mythtv/mysql.txt.dist. 

None of these files contain the ip number  192.168.2.10.
  
here are the errors cut from the terminal when I used sudo  mythfrontend  to start mythtv.

tomas@myth-front:~$ sudo  mythfrontend
2010-09-23 23:44:58.468 mythfrontend version:  branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2010-09-23  23:44:58.468 Using runtime prefix = /usr
2010-09-23 23:44:58.468  Using configuration directory = /home/tomas/.mythtv
2010-09-23  23:44:59.157 Empty LocalHostName.
2010-09-23 23:44:59.157 Using  localhost value of myth-front
2010-09-23 23:44:59.157 Testing network  connectivity to '192.168.2.13'
2010-09-23 23:44:59.165 New DB  connection, total: 1
2010-09-23 23:44:59.414 Connected to database  'mythconverg' at host: 192.168.2.13
2010-09-23 23:44:59.415 Closing  DB connection named 'DBManager0'
2010-09-23 23:44:59.422  ScreenSaverX11Private: XScreenSaver support enabled
2010-09-23  23:44:59.423 DPMS is disabled.
2010-09-23 23:44:59.424 Primary  screen: 0.
2010-09-23 23:44:59.676 Connected to database  'mythconverg' at host: 192.168.2.13

"I cut a large section here  that mainly dealt with the theme, tomas"

2010-09-23 23:45:10.231  MythContext: Connecting to backend server: 192.168.2.10:6543 (try 1 of  1)
2010-09-23 23:45:13.235 Connection to master server timed out.
             Either the server is down or the master server settings
             in mythtv-settings does not contain the proper IP address

2010-09-23  23:45:18.238 MythContext: Connecting to backend server:  192.168.2.10:6543 (try 1 of 1)
2010-09-23 23:45:21.239 Connection to  master server timed out.
            Either the server is down or the  master server settings
            in mythtv-settings does not  contain the proper IP address

And it will repeat the last 5  lines.
Also attacked a jpg of what it looks like on screen.
cheers

---

### Post by ian dobson on 2010-09-23
Hi,

OK, lets first check that mysql is actually up and running:-
have a look in the /var/log/mythtv/mythtvbackend.log to see if the backend is starting and connecting to the sql server. 

If thats OK check if the configuration for the mythtv backend is ok by running mythtv-setup and check the IP address set for the sql server and the backend.

When thats OK, go over to the frontend and try pinging the IP address of the backend, then run mcc and check the configuration of the IP address for the backend/sql server.

Also have a look at the config.xml files on your backend and frontend checking the IP address configured there:-
```
<Configuration>
  <UPnP>
    <MythFrontend>
      <DefaultBackend>
        <DBHostName>192.168.0.2</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>xxxxxxxxx</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>0</DBPort>
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
</Configuration>

```

That should keep you busy for a while :)

Regards
Ian Dobson

---

### Post by blkbx on 2010-09-24
hi Ian,
Thanks for telling me to check the backend. I'd ssh to it for the whole time I'd been having problems. Meanly because Id packed it away and didn't want to have to drag it out again.
As soon as I'd put a monitor on the backend I found out were my 192.168.2.10 problem was coming from, 'first page'. A real newbie mistake and I'm so sorry that I hadn't checked it before I went nuts. But I'm glad that it made made me hook a monitor to the backend and look for errors. Going to leave it connected from now on just in case.
Thanks alot  for your help. 
tomas

---

### Post by ian dobson on 2010-09-24
Hi,

No problems, sometimes the bugs are about 30cm infront of the monitor :)

Enjoy your new Myth system.

Edit: You know you can open an X capable ssh connection into the remote system don't you? I do this all the time using cgwin when I need to run myth-setup on my backend, as my backend does not have a usable monitor (7inch VGA tft screen that only displays graphics at 640x480 and 48hz), text mode is OK, but if I start X on that screen is starts whistling/clicking until it switches off, and the only way to get it running again is to unplug the power and wait 10-20minutes.
  
Regards
Ian Dobson

---

### Post by blkbx on 2010-09-26
I read the Linux Format magazine (linuxformat.co.uk)and they did a roundup on remote desktop.
They looked at Krdc, Remmina, oMichineNX, RealVNCJava, TeamViewer, TigerVNC, Vinadre. Remmina came out on top.As for not using one I thought that I had all the tools I needed with ssh. Live and learn.
tomas

---

