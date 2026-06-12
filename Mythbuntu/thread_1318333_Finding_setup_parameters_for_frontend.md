---
title: "Finding setup parameters for frontend"
date: 2009-11-07
forum: Mythbuntu
---

### Post by hundred1906 on 2009-11-07
I have a working combined backend and frontend. Now I am trying out the potential of a second stand-alone frontend, starting with a liveCD (from Linux Format Mag').

In setting up the frontend configuration does anyone know (1) how/where to find the correct IP address for the backend and (2) what password is needed. Is it the Mqsql password, or the password for the backend user login.

I am getting the "Could not connect to the master backend server ..." message.

The threads I have looked at seem to emphasise the need to use the backend external IP (ie not loopback and not localhost) without saying clearly how to find it. Ditto they leave me confused over which password to use.

Is there a way to see the front to back connection status perhaps?

---

### Post by ian dobson on 2009-11-07
Hi,

Have a look for mysql.txt on your working frontend, you'll find most of the information you need there.

Regards
Ian Dobson

---

### Post by hundred1906 on 2009-11-08
I have already been there. It does not tell which is the correct IP address. It has the mysql password but is that the one that is needed for a remote frontend.

How does the backend host validate the incoming connection. Is another password required?

And/or do I need to use the wake and command settings?

Regards. Trevor.

---

### Post by pootle1 on 2009-11-08
your backend probably isn't set up for a running a separate frontend.

Did you build the current combined system from a mythbuntu CD, or did you add myth to an existing ubuntu PC?

If the former and you set it to work with multiple backends, then you should be able to go into myth - Utilities/setup - setup - General and on the front screen there is the name or address of the server.  If it says localhost you aren't set up for a separate front end and its a bit more complicated ;).

---

### Post by hundred1906 on 2009-11-08
You guessed it - it's the complicated option. Myth added to Ubuntu and localhost showing.

I did run: sudo dpkg-reconfigure mythtv-database

and selected for remote front-ends (I cannot remember the details of the option without going through it again).

---

### Post by pootle1 on 2009-11-08
Ah well! should have guessed.

I think the best way then is this:


[LIST=1]
[*]check that mysql database can be accessed from you new front end, and fix any problems
[*]reconfigure your current combined system and check it still works
[*]configure your new frontend only and get it working
[/LIST]
[SIZE=3]Checking mysql[/SIZE]
get the IP address of your combined system - ifconfig in a terminal if you don't already know the answer.  Might be better to give it a fixed address, but most DHCP servers (like the one built into most broadband routers) will keep dishing out the same address forever so you don't HAVE to do this.

on your new front end up a terminal and run up the mysql client to check it can connect:
```
mysql -h 192.168.1.199 -u mythtv -p mythconverg
```then enter the mysql password from your combined system.

This checks that you can connect to the mythtv database from the front end, with the mythtv account

Use your own IP address, (assuming you are using the standard username and database name)

If this fails then you need to do the following:

[LIST=1]
[*]check and change the networking setting in /etc/mysql/my.cnf
[*] - change the value in the bind-address line to be the server's IP address(or if you still have problems you can set it to 0.0.0.0 if your server is not accessible in any way from the internet)
[*]make sure that the user mythtv has remote login rights - run mysql on the combined system, logging in as root using the password you provided when first setting up the system, the issue the following sql commands:
[/LIST]
```
create user 'mythtv'@'192.%' identified by 'ynvUwe2U';
grant all privileges on mythconverg.* to 'mythtv'@'localhost';
grant all privileges on mythconverg.* to 'mythtv'@'192.%';

```[SIZE=3]

change the current combined system [/SIZE]
on your current combined system change the two places in general setup on the first screen from 'localhost' to your combined system's IP address.  Sounds daft, but the setting here appears to be also picked up by clients.

Check that your combined system still works OK by running up the front end and opening up a tv channel

[SIZE=3]Configure the new front end and check it works[/SIZE]
Hopefully now this should just work.

run up mythfront end on your new front end and enter the details on the database config screen.

Now it should work!  If not check in /var/log/mythtv/mythfrontend.log (last 20 lines should do) to see if there's any helpful info there.

Good luck!

---

### Post by hundred1906 on 2009-11-11
Thanks for the response. Have a bigger problem right now with the entire filing system, including losing database and VirtualBox.

Hopefully will get sorted then come back to try your suggestions.

Regards.

---

### Post by maddojf on 2009-11-15
Thank you pootle1.  That worked to fix a whole host of problems that I have been having.  

It took me a while to find this thread since I was searching for different terms so I will list the problems this fixed for me to make it easier for others to find.

I have a combined frontend/backend which does all my recording and stores all my videos. I put the external ip in both fields in the backend-setup,  but I could still only connect to the database with the frontend by using localhost in the settings.  If I tried to use the external ip from the frontend I would get a "could not connect to database" error.  

I also use my laptop as a remote frontend.  When I first tried to launch the remote frontend after upgrading to 9.10, I couldn't see any of the recordings or the videos.  I thought it was a storage groups problem so I mounted the directories using NFS the way I used to with 9.04.  This allowed me to view the videos, but I couldn't watch Live TV or recordings.  What still confuses me is that the remote frontend was somehow able to connect to the database on the backend to get the information on the recorded shows.  Although I could see the recordings in the file structure, play them with mplayer, and they showed up in the frontend menu, I would get a "file can not be found" error whenever I would try to play a recording through the frontend.  According to a few threads this same behavior can be produced by using different time zones on the different machines.  I was also able to use XBMC to connect to the database and watch recording even though mythtv wouldn't connect.

I tried to use mythbuntu-control-centre to disable and then re-enable mysql on the ethernet port but that didn't work.  Anyway.  After following the directions in the above post, I am able to connect with the local frontend using the external ip, and I am able to watch recordings and Live TV on the remote frontend.  I also removed the NFS stuff that I had set up and now the storage groups are working fine.

What was tricky is that the database info was showing up in the frontend even though I couldn't login to the database.

---

### Post by hundred1906 on 2009-11-20
OK, I am back having fixed my crashed system. Your suggestions worked.

I found the network address using ifconfig, then amended the etc/mysql/my.cnf file to use the network address (by overwriting the 127.0.0.1 value).

The backend settings were then changed by overwriting the 'localhost' with the network address in two places.

I also needed to set the pin value to 0000 (or whatever you choose), do not leave it blank.

My frontend is the office laptop running Mythbuntu from a Linux Format magazine DVD (LXFDVD111). I chose a frontend only configuration using Mythbuntu Setup and started the frontend. In the pop-up that appears I put in the Mysql password and the backend network ip address (from above).

Bingo! 

Now I just plug in an ethernet/mains connector to watch Tv and recordings anywhere in the house. Thankyou.

---

