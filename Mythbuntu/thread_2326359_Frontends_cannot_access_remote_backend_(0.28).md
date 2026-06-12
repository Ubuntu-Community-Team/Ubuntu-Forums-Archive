---
title: "Frontends cannot access remote backend (0.28)"
date: 2016-05-31
forum: Mythbuntu
---

### Post by Frederico_Zenozzog on 2016-05-31
Hi,
I'm a long time Mythtv user. My house has a a number of mythtv/kodi clients, both linux/kodi/mythfrontends and android/kodi accessing a single mythbuntu backend.  

This setup had been working well going back many years. I had been running mythtv 0.27 since the release of mythbuntu 14.04LTS.

After a HDD failure on the backend server two weeks ago, I replaced the disk and did a clean install of mythbuntu 16.04 LTS. All clients were upgraded to mythtv 0.28 frontends. 

In the backend's configuration the host address is set to the fixed IP address, assume 192.168.1.2 - the backend runs fine when restarted.

However, if I check /etc/mythtv/config.xml I see that the host address is stored as localhost - If I attempt to change this to the server's fixed IP address the backend will not start. The log reports a connection timed out error on the fixed IP address, i.e. 192.168.1.2 (!?). 
[B]
Similarly, none of the front ends will start, locking themselves into an endless loop of exit code 139 and restarts. The log reports a connection time out on the server's IP address. It seems to me that the backend will only run with a host of localhost in the config.xml. 


[/B]Oddly **kodi (16.1) and kodi-pver-mythtv clients access the backend server ok.**

I am completely stumped on this. Any hints, tips etc to help me get my head around this madness are greatly appreciated because I do like using the mythtv frontend for some things.

Cheers

---

### Post by uteck on 2016-05-31
Since you reinstalled the backend, did you update the database password on the frontends?
It's been awhile since I used MythFrontend, but I recall it needing that.

---

### Post by Frederico_Zenozzog on 2016-05-31
> **uteck said:**
> Since you reinstalled the backend, did you update the database password on the frontends?
It's been awhile since I used MythFrontend, but I recall it needing that.

Yes. All of the obvious stuff has been done. I had also tried plugging the appropriate values into the respective mythtv/config.xml files. The Frontend never gets past the Language settings before it crashes. As I said, it appears to be an IP address setting issue. 

What I cannot get my head around is that in the backend's GUI configuration the IP adresses are set to the fixed IP for the server. Yet the config.xml file says it is localhost. Maybe something has changed in the 0.28 settings that I am not aware of. What's worse most of the mythtv wiki stuff is so old that it went down with the Ark. No practical help anywhere. 

It's all them more frustrating because Kodi clients work fine; all they want is the backend server IP address and port. 

On the upside the 0.28 myth webserver is nice so maybe I can learn to live without the mythtv frontend.

---

### Post by philip7 on 2016-06-01
Have you configured the Mythtv database to allow access from remote frontends, details are near the bottom of this page: [https://www.mythtv.org/wiki/Mythfrontend](https://www.mythtv.org/wiki/Mythfrontend)

I don't recall changing the config.xml file on my backend, this is because the database and backend are on the same PC so localhost should work (Not in front of my machine so can't check at the moment).

The config.xml file will need changing for your remote frontends though, they should point to the IP address of your backend.

Not an expert but I believe the Kodi Mythtv add on uses the Mythtv services, these services are all provided via the web server by default: [https://www.mythtv.org/wiki/Frontend_Service](https://www.mythtv.org/wiki/Frontend_Service)

The Mythtv frontend doesn't use a service but needs to connect directly to the MYSQL database, by default access is limited to the localhost, remote access needs to be configured.

---

### Post by Frederico_Zenozzog on 2016-06-01
The issue turned out to be mysql, so thanks for the heads up, utek.

For the benefit of anyone else  who might have a similar setup/ conflict:

I had installed the (fresh) 16.04LTS mythtbuntu server backend with the option that other remote frontends will be accessing it. I had, not unreasonably, assumed that the installer was smart enough to create a correct configuration. [B]
It doesn't![/B] It omits a bind address from my.cnf, which prevented network client connections. You can  fix it as follows:

sudo nano /etc/mysql/my.cnf

Check for, and if necessary add

```
[mysqld]
bind-address = nnn.nnn.nnn.nnn

```

"nnn.nnn.nnn.nnn" is the server's IP address.
For example if the backend is on 192.1.1.2, that's what you should enter for nnn,nnn.nnn.nnn

Restart mysql server with
```
sudo service mysql restart
```

I note from the logs that mythfilldatabase had also fallen in a heap, which may or may not have been related to the bind-address omission. That's behaving as well now.

Thanks for the feed back, people.

Cheers

---

### Post by mtbdrew on 2016-06-16
For me my remote frontends were stuck at the country/language setup page. Trying to pass this caused the frontends to crash with codes 130 or 139. Had to edit both the /etc/mythtv/config.xml and ~/.mythtv/config.xml to change "localhost" and "password" to the actual and address/password used by master backend. With these extra modifications I could run the frontends but they game constant error message about not being able to connect to the master backend. The only way I can get the remote frontends to connecting to the master backend is by running command "sudo mythtv-setup" command. This clears the connection error for each remote frontend. This command has to be run after every system boot otherwise the remote frontends will not connect.

---

### Post by blm-ubunet on 2016-06-17
@mtbdrew
Running mythtv-setup typically causes mythtv-backend service to be stopped & restarted.
You could just try to stop/start the backend directly to see if it fixes your problem.

Your problem sounds like backend is starting before networking is up & the MBE is binding to link-local.
Have a look in MBE log files, should be in the first 20 or so lines..
Do you use static IP or other means to get same IP ?

Check your remote FEs don't (accidentally) have slave BE services running; this seems to be broken in master but has different symptoms.

---

### Post by mtbdrew on 2016-06-18
The master is set up for dynamic but I have my switch setup to assign a fixed IP to this machine. The FEs have no backends installed.

---

### Post by mtbdrew on 2016-06-19
To clarify, the backend setup command has to done with sudo or it doesn't work. Using the shortcut created during install does not fix the connection issue.

---

