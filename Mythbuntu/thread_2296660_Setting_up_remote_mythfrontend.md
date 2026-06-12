---
title: "Setting up remote mythfrontend"
date: 2015-09-27
forum: Mythbuntu
---

### Post by lemayspencer on 2015-09-27
So I setup a mythtv frontend/backend thing that works great. I tried setting up a remote frontend and it keeps telling me that it can't connect to the backend complaining that it isn't turned on/ip is not setup correctly. 
After spending quite a few hours reading forum posts and changing settings for what appears to be the exact same value in 5 different places I am about to give up. I can watch recordings on the frontend without sound, but no live TV and an error message that wont stop blinking.   Oh also I can't access the settings of the remote frontend because if I try to use the gui it will ask for a password, but not let me enter a password.    

192.168.1.214 is my frontend/backend  
192.168.1.187 is my frontend. 

   backend log [http://pastebin.com/4u6mepzs](http://pastebin.com/4u6mepzs)  
frontend log [http://pastebin.com/k824xqYm](http://pastebin.com/k824xqYm)

---

### Post by Mythological on 2015-09-28
Just a suggestion, if you do decide to give up on Myth, try TVHeadend.  It's a little different to set up and there's a bit of a learning curve, but once you get the hang of it, it's easier to configure than Myth ever was and you don't don't run into as many weird issues.  I like Myth when it works, but it's so difficult to set up in the first place and then to keep it working after upgrades that I finally gave up and went to TVHeadend for my backend software.  IMHO it's really the only other decent alternative right now.

---

### Post by khPWXxF on 2015-09-29
If you can set up a combo FE/BE then you are way up the learning curve and must be nearly there!  A few things to check:

1.  Network ok??    Ping BE from FE.

2.  Mythbuntu setup > MySQL.  Enable access to MySQL from ethernet (top box).

3.  Backend setup > General.  There are two IPv4 address boxes.  Set these to your BE address [COLOR=#000000]192.168.1.214[/COLOR] (not localhost or 127.0.0.1).

4.  The FE needs database credentials (not your login password).  These are held in /home/mythtv/.mythtv/config.xml for backend and ~/.mythtv/config.xml for the frontends.  You can also see them in the FE setup > general.    If you want the sledgehammer way of setting these then edit  ~/.mythtv/config.xml on your remote frontend.

Must rush - hope this helps.

Phil

---

### Post by lemayspencer on 2015-09-29
Thanks [**[COLOR=#000000]khPWXxF[/COLOR]**]("http://ubuntuforums.org/member.php?u=1844453") but I have tried all of those.

1. Good their.
2. Got that.
3. Done
4. and did that.

Like I said it is completely puzzling and makes me want to rip my hair out.

Also I need to do everything the sledgehammer way on the frontend as I can't access the settings gui period.

---

### Post by khPWXxF on 2015-10-05
Still suffering? My settings for Backend setup > general are:

IPv4 address:  set to 192.168.x.y
IPv6:       set to ::1     (null?)
Listen on link-local addresses -    ticked
Port:  6543
Status Port:  6544
Pin:  0000 (if non zero frontend must match I think)
Master backend:  192.168.x.y
Port:  6543

Anything different?
Phil

---

### Post by spyderdyne on 2015-10-05
> **Mythological said:**
> Just a suggestion, if you do decide to give up on Myth, try TVHeadend.  It's a little different to set up and there's a bit of a learning curve, but once you get the hang of it, it's easier to configure than Myth ever was and you don't don't run into as many weird issues.  I like Myth when it works, but it's so difficult to set up in the first place and then to **keep it working after upgrades** that I finally gave up and went to TVHeadend for my backend software.  IMHO it's really the only other decent alternative right now.

Since you are essentially creating an appliance with MythTV, it is generally recommended to limit upgrades whenever possible.  Unless you have to replace a bad card or add new functionality you should try to avoid making any changes.  Comcast and Dish Network dont upgrade to a new kernel every time there is a release.  They just patch vulnerabilities until the box no longer supports the required features and then replace it with a new one.

Good to know though.

Thanks.

---

### Post by spyderdyne on 2015-10-05
1.  On the backend server make sure MySQL is running:

```
$ netstat -untap | grep 3306
```

You should see that port 3306 is bound to your NIC's IP address (not 127.0.0.1 or localhost loopback addresses) and that the MySQL service owns that socket.  If you do not see it then make sure MySQL is running and check again.

2.  On the backend server, make sure the backend services are running:

```
$ netstat -untap | grep 654*
```

As above, you should see port 6543 and 6544 are up and also bound to the external IP address.  If they are not then make sure your backend service is  still running.

```
$ ps aux | grep myth
```

This command will show you all the mythtv processes that are currently running.  If you see multiple instances of the same service you should kill them both and restart the backend.

3.  Once you are sure that everything is as it should be, check to see if you are able to connect to them from the external frontend.

```
$ telnet <backend.server.ip.address> 3306
quit
$ telnet <backend.server.ip.address> 6543
quit
$ telnet <backend.server.ip.address> 6544
quit
```

If you completed steps 1 and 2, but are still not able to connect to the socket (socket = address + port) then you may have a firewall in the way or one of your backend services may have died.  Repeat steps 1 & 2 as needed to verify connectivity to the backend server, if the backend services are still up, and you are able to ping the backend server from the frontend then you need to make sure you do not have a firewall running on either machine that is blocking incoming traffic.

If at any point you find that you are binding to localhost or 127.0.01. you will need to run mythsetup again with the database running and ensure you have the correct credentials, set the correct values, and restart everything after you have exited it.  Once your system comes back up you need to manually restart the services (MySQL and mythtv-backend) and run these checks again to ensure they are running.  For some reason they are not automatically run at startup by default.

If all of this checks out then you probably have a database access issue.  Your mythtv-setup application provides an option to make the database accessible to remote and local frontends depending on what options you select.  For my locla only setup I did a could weeks ago on Vivid it didnt work correctly when binding to the external IP address and I had to manually grant access to the database.

```
$ myslq -u root
```

this will give you a MYSQL prompt.  Be very careful here.  You can easily blow your install if you arent sure what you are doing.  Enter the following:

```
mysql> GRANT ALL PRIVILEGES ON mythconverg.* TO 'mythtv'@'%' IDENTIFIED BY '<your_password>';
```

This will allow remote machines to access the database on any port that it is attached to as long as they send the correct username (mythtv,)  and password (whatever you set it to.)  This also allows you to log in to the database with MySQL Workbench and play around if you need to.  Once this is completed your shiny new frontend should be up and running. 

Probably.

---

### Post by lemayspencer on 2015-10-12
FIXED IT. Changed the command from the post above to the following and it worked

mysql> GRANT ALL PRIVILEGES ON mythconverg.* TO 'mythtv'@'192.168.1.%' IDENTIFIED BY '<your_password>';

---

