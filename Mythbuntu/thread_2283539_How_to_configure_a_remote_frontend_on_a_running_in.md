---
title: "How to configure a remote frontend on a running install of mythtv"
date: 2015-06-22
forum: Mythbuntu
---

### Post by brian_hayward on 2015-06-22
I have a running mythtv system that has been up and running since mythbuntu 14.00 has been around.  I would always run a modified mythrename.pl script to rename all of the episodes and move them off the mythtv system to my plex server.  I don't want to do that anymore, and i bought a larger hard drive so i can keep all of my recordings on my myth box.  However I cannot get a remote frontend to connect to my mythbox.  Any help or if anybody knows of a GOOD how to would be greatly appreciated.  I tried everything that i found on the web and it now I've completely screwed up my mythtv box.  Thanks.

---

### Post by Lester_Burnham on 2015-06-22
Hi,

Go into Mythbuntu Control Centre on the machine with the Mythbackend and click on the MYSQL button on the right. Select enable "MYSQL service on ethernet interfaces".
You may also need to go into mythbackend setup>General and make sure the master backend IP is not set to 127.0.0.1, but the machines external static IP.

Lester

---

### Post by brian_hayward on 2015-06-23
I did all that already.  Still wouldn't connect.  I suspect after doing some more research and looking at some mythfrontend logs that the problem is on my remote frontend machine.  I set it up originally as a primary backend and frontend and later tried to change it to a frontend only machine.  I believe it is trying to connect to a local database that doesn't exist.  I am going to dig through some .mythtv/config.xml files and change the host name values to my backend ip address.  I will report back about my progress.  Thanks.

---

### Post by Lester_Burnham on 2015-06-23
Hi,

I used to have a similar problem, where I'd retired the backend on a combined machine to run as a frontend only.
I'd go into Mythbuntu Control Centre and select frontend only, but every time I did updates, backend-master would find its way back on and the frontend would reconnect to it.
In the end I think I purged all mythtv packages and only installed Mythfrontend. 
Looks like you've got your password problems in MYSQL to work through first though.
Lester

---

### Post by brian_hayward on 2015-06-25
Ok, so here is the situation.  I had to restore my backend from a previous backup.  This was due to other issues.  I tried changing the password to the mythtv user in the mysql database and it really made a mess of things.  I also reinstalled mythbuntu on my frontend machine and did a "frontend only" installation.  I changed all of the config.xml files to point to my mythtv backend, with username mythtv and password mythtv and i still can't connect.  This is strange to me since my android client can connect and i can watch shows on my phone.  Any other ideas or suggestions?

---

### Post by aelfric55 on 2015-06-25
Not enough information. Running mythfrontend from a terminal, or setting up a mythfrontend logfile, to see what sort of errors are happening and posting up the output here might help. Making sure 0000 is set as the PIN in the backend setup may help. You mentioned that your remote frontend used to be a master backend. If it still has its old unused mythconverg on it, strange problems sometimes ensue.

---

### Post by Lester_Burnham on 2015-06-26
Hi,

Can you log into MySQL from the frontend machine?

I have also experienced the strange problems that ensue :) 

Lester

---

### Post by brian_hayward on 2015-06-29
So i checked my log file.  and here is the output:

```
Jun 29 06:13:34 mythfrontend mythfrontend.real: mythfrontend[1647]: I SendMessage mythcorecontext.cpp:423 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: localhost:6543 (try 1 of 1)
Jun 29 06:13:34 mythfrontend mythfrontend.real: mythfrontend[1647]: E SendMessage mythcorecontext.cpp:889 (GetBackendServerIP) No address defined for host: localhost
Jun 29 06:13:34 mythfrontend mythfrontend.real: mythfrontend[1647]: E MythSocketThread(-1) mythsocket.cpp:661 (ConnectToHostReal) MythSocket(7f98e40b7790:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 29 06:13:34 mythfrontend mythfrontend.real: mythfrontend[1647]: E SendMessage mythcorecontext.cpp:493 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
```

Apparently, my frontend is still trying to connect to localhost:6543.  I double checked all of the config.xml files (the file under the /etc/mythtv directory, and under my local user .mythtv directory and the mythtv user .mythtv directory), and the ip addresses were set to the backend ip address and i verified that my backend ip address was correct in the mythtv frontend settings.  

The machine i am trying to use for my frontend box is a "frontend only" install.  At this point i am unsure if mythbuntu installs mysql with a mythconverge database on frontend only installs, i did not check.  

Do i need to change an ip addresses in /etc/mysql/my.cnf file?  What more do i need to check?

---

### Post by aelfric55 on 2015-06-29
The error message "No address defined for host: localhost" is a message that usually appears when there's a leftover mysql.txt  in the user's .mythtv directory that the frontend is trying to use for connection info instead of the config.xml.  If you still have a leftover mysql.txt, it should be got rid of (or filled out correctly, with a the server ip address replacing "localhost"). 

Also, as [**[COLOR=#000000]Lester_Burnham[/COLOR]**]("http://ubuntuforums.org/member.php?u=149719") mentioned earlier, check that you can actually log into your backend mythconverg from a frontend terminal. Something like ```
mysql -u mythtv -p -h <ip-address-of-server>
```If you can't connect, then mythfrontend can't either. If you can log into your master backend mysql server from the frontend, then clearly the my.cnf file on the server that you were worried about is not an issue.

For a minimum mythfrontend install (to, say, a non-myth Ubuntu machine) one usually adds just the two packages mythtv-common and mythtv-frontend, but not the package mythtv-backend. However, if your frontend-only machine happens to have the mythtv-backend package installed already (as part of the mythtv "metapackage"), I don't know if you can remove the mythtv-backend package alone without the Ubuntu package manager getting testy and trying to jettison all of mythtv. I've never tried it.

---

### Post by brian_hayward on 2015-06-30
Sooooooooo.......I'm not sure what went wrong (i'm guessing i typed an incorrect password) but now my frontend can connect to my backend.  Not without issue though.  now when i try to run mythweb it won't connect.  it just spits out a lot of mysql errors 

> "Fatal Error
!!NoTrans: Access denied for user 'mythtv'@'192.168.1.200' (using password: YES) [#1045]

The only thing i did was redo the grant all privileges command under mysql to mythtv (this time i typed in the right password) and after that mythweb gave me the mysql errors.  I tried removing the plugin and adding it back but that didn't work.  Do i need to reconfigure the plugin instead of removing and adding it again?  i can log into the mysql database on the backend from other machines on my network so i know that the password is correct.  Again...thanks for all your help.  I really do appreciate it.

Brian

---

### Post by brian_hayward on 2015-06-30
Forgot to mention, mythweb doesn't work on remote machines or the backend machine.

---

### Post by aelfric55 on 2015-06-30
Try this from a yearish ago: [http://ubuntuforums.org/showthread.php?t=2245405](http://ubuntuforums.org/showthread.php?t=2245405)

---

### Post by brian_hayward on 2015-06-30
Quick update.  For kicks I thought i would try running > sudo dpkg-reconfigure mythweb to see what would happen and it fixed my mythweb problems.  It would seem that all of my issues are now solved.  Thank you all for your help.

---

