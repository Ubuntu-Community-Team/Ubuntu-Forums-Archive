---
title: "trying to setup frontend"
date: 2008-01-28
forum: Mythbuntu
---

### Post by taehC on 2008-01-28
can anyone help?
i need to connect to my backend machine but i am not sure how.  what to i do and how to i find out any info i need?

---

### Post by stdPikachu on 2008-01-28
Presumably you mean a remote frontend (i.e. a different machine) rather than a local frontend?

First off, you need to configure the frontend to point at the myth backend. Secondly you need to edit /etc/mythtv/mysql.txt on your frontend to add login credentials for the database, and thirdly check that you have a user set up to access the database with.

Don't know if mythbuntu has some special method for adding users to databases since I've impoted my old database instead of starting from scratch but if you go onto your backend and do something along the lines of:
```
mysql -u yourmythtvusername -p
Password:
mysql> grant all privileges on mythconverg.* to 'yourfrontendusername'@'yourfrontendhostname' identified by 'somepassword';
quit
```
If you trust your LAN you can swap 'yourfrontendhostname' for '%' which means any host, so it'll work from any machine/IP address.

You can then chuck those values for the user you've just created into the mysql.txt on the frontend and you should be good to go.

Looking at the my.cnf on my mythbuntu frontend machine, looks like MySQL is configured to not listen on the network by default. I suspect that if you go into the Myth configurator on your backend machine and ensure the machine role is set to "backend with remote frontends" or whatever it's called will set the database to be available over the network. You can check this with nmap or suchlike:
```
banquo@banquo:~$ nmap prospero

Starting Nmap 4.20 ( http://insecure.org ) at 2008-01-28 05:58 GMT
Interesting ports on prospero (192.168.1.30):
PORT     STATE SERVICE
22/tcp   open  ssh
53/tcp   open  domain
443/tcp  open  https
3306/tcp open  mysql
6543/tcp open  mythtv
6544/tcp open  mythtv
```
NB - I'm probably making this vastly too complicated so be prepared for someone to tell you there's a much simpler way to do it without using the command line :)

---

### Post by taehC on 2008-01-28
ok it looked like i had everything setup and in the control center it said when i tried to connect to my backend that the connection was successful and it still does but when i am in the frontend it fails. here is what i get when i run the frontend in a terminal
```

2008-01-27 22:43:54.282 Using runtime prefix = /usr
2008-01-27 22:43:54.290 Gnome-Screensaver support enabled
2008-01-27 22:43:54.290 DPMS is active.
2008-01-27 22:43:54.300 New DB connection, total: 1
2008-01-27 22:43:54.319 Connected to database 'mythconverg' at host: 192.168.1.100
2008-01-27 22:43:54.320 Total desktop dim: 1280x1024, with 1 screen[s].
2008-01-27 22:43:54.324 Using screen 0, 1280x1024 at 0,0
2008-01-27 22:43:54.332 Current Schema Version: 1160
2008-01-27 22:43:54.334 mythfrontend version: 0.20.20070821-1 www.mythtv.org
2008-01-27 22:43:54.334 Enabled verbose msgs:  important general
2008-01-27 22:43:54.677 Total desktop dim: 1280x1024, with 1 screen[s].
2008-01-27 22:43:54.678 Using screen 0, 1280x1024 at 0,0
2008-01-27 22:43:54.680 Switching to square mode (Iulius)
2008-01-27 22:43:54.696 Using the OpenGL painter
2008-01-27 22:43:55.019 New DB connection, total: 2
2008-01-27 22:43:55.020 Joystick disabled.
2008-01-27 22:43:55.472 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-01-27 22:43:55.628 Registering Internal as a media playback plugin.
2008-01-27 22:43:55.677 Registering MythDVD DVD Media Handler as a media handler ext()
2008-01-27 22:43:55.679 Registering MythDVD VCD Media Handler as a media handler ext()
2008-01-27 22:43:55.714 Registering MythGallery Media Handler 1/2 as a media handler ext()
2008-01-27 22:43:55.715 Registering MythGallery Media Handler 2/2 as a media handler ext(gif,jpg,png)
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
2008-01-27 22:43:55.810 Registering MythMusic Media Handler 1/2 as a media handler ext()
2008-01-27 22:43:55.811 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
2008-01-27 22:43:55.872 New DB connection, total: 3
2008-01-27 22:43:55.952 Using NV NPOT texture extension
2008-01-27 22:44:00.077 Connected to database 'mythconverg' at host: 192.168.1.100
2008-01-27 22:44:00.093 Connected to database 'mythconverg' at host: 192.168.1.100
SIP listening on IP Address 192.168.1.101:5060 NAT address 192.168.1.101
SIP: Cannot register; proxy, username or password not set
2008-01-27 22:44:16.210 Connecting to backend server: 192.168.1.105:6543 (try 1 of 5)
2008-01-27 22:44:16.362 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.
2008-01-27 22:44:17.069 TV: Attempting to change from None to None
2008-01-27 22:44:17.581 Connecting to backend server: 192.168.1.105:6543 (try 1 of 5)
2008-01-27 22:44:17.593 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.
2008-01-27 22:44:18.004 TV: Attempting to change from None to None


```

---

### Post by stdPikachu on 2008-01-28
Are your database and backend running on different machines? You have them both configured on different machines:
```
2008-01-27 22:44:00.077 Connected to database 'mythconverg' at host: 192.168.1.100
2008-01-27 22:44:16.210 Connecting to backend server: 192.168.1.105:6543
```

---

### Post by ahood on 2008-01-28
> **taehC said:**
> can anyone help?
i need to connect to my backend machine but i am not sure how.  what to i do and how to i find out any info i need?

A little bit of information about your situation would be helpful. For instance...

What version of Mythbuntu are you running, Gutsy (latest), Feisty, other?

What operating system do you want to use for the frontend client (Mythbuntu, Ubuntu, Kubuntu, Xubuntu, Windows)?

**GENERAL STEPS**
I recently successfully configured a mythfrontend on my desktop running Ubuntu Gutsy to work with my Mythbuntu (based on Gutsy) machine across my home network. Below are some general steps on how I got this to work...The steps are very general and not cook book. I plan to write a How To tonight on getting this to work....

*Note: The instructions below assumes the user knows the difference between a frontend and a backend and how to access the configuration screens of each.*

**1. Configure Mythbuntu (Gutsy) Host Machine**
[LIST]
[*]The host must have a unique IP address (usually 192.168.0.xxx or 192.168.1.xxx) specified in the mythtv backend configuration (General section).
*If the IP address is 127.0.0.1 (i.e., local), then this MUST be changed to an IP address compatible with the LAN.*
[*]The host must have remote network access enabled in the mythtv backend configuration (General section).
[*]The host must have either Samba or NFS enabled (see Mythbuntu Media Conctrol Center on host machine). Samba is enabled by default. No need to enable NFS unless this service is preferred.
[*]Write down the mysql database name (default is mythconverg), user name (default is mythtv), and password (no default, must look it up in backend configuration General screen).
[*]Write down the location where TV (default is /var/lib/mythtv/recordings), music (/var/lib/mythtv/music), video (/var/lib/mythtv/video), etc. are stored on the host machine. 
[*]Must share the folders where TV recordings, music, and videos are stored on the host machine.
*This is done outside of myth frontend or backend. It is done in the XFCE desktop by clicking on Administration --> Personal --> Shared Folders.*
[/LIST]

**2. Install packages on the Ubuntu (Gutsy) Client machine that will run just the Mythtv frontend**
[LIST]
[*]mythfrontend
[*]mythmusic
[*]mythvideo
[/LIST]
*Note: There might be other plugins (e.g., mythweather, mythflix, etc.) that might also be desired, thus installed.*

**3. Mount Shared folders on Ubuntu (Gutsy) Client machine running the frontend**
> sudo mkdir /mnt/tv
sudo smbmount //192.168.0.xxx/var/lib/mythtv/recordings /mnt/tv
sudo mkdir /mnt/music
sudo smbmount //192.168.0.xxx/var/lib/mythtv/music /mnt/music
sudo mkdir /mnt/video
sudo smbmount //192.168.0.xxx/var/lib/mythtv/video /mnt/video

*Note: Replace the IP address above with the correct IP address of the host machine running Mythbuntu.*

**4. Configure the location of media stored on Ubuntu (Gutsy) Client machine running the frontend.**
[LIST]
[*]Launch MythFrontEnd
[*]Click on Setup and navigate to TV, music and video sections and specify /mnt/tv, /mnt/music, and /mnt/video, respectively.
[/LIST]

The above is very quick and dirty instructions. I know I have left out a lot of detail. Better instructions are forthcoming if interested. 

I hope the above helps.

---

### Post by taehC on 2008-01-28
> **stdPikachu said:**
> Are your database and backend running on different machines? You have them both configured on different machines:
```
2008-01-27 22:44:00.077 Connected to database 'mythconverg' at host: 192.168.1.100
2008-01-27 22:44:16.210 Connecting to backend server: 192.168.1.105:6543
```

the second ip is what that computer used to be...  for some reason it changed to 192.168.1.100 and i thought i changed everything to that ip

---

### Post by stdPikachu on 2008-01-29
If you've gone with the defaults, chances are you'll be using a dynamic IP address. Set it to a manually allocated static address via the network manager (icon, top right) and use that IP address exclusively. You'll be wanting a static IP address for any machine that hosts a service you want to be remotely accessible.

It's possible to set up a DHCP server that will give out dynamic addresses to everyone but static addresses to certain machines; some home routers have this functionality too, but that's outside the remit of this forum :)

---

### Post by taehC on 2008-02-02
i am too much of a beginner to know what to do what you are telling me to do...
can you tell me in more detail?

---

### Post by taehC on 2008-02-10
i still have no clue what to do...

---

