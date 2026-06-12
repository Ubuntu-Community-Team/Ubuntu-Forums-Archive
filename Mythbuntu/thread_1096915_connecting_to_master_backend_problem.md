---
title: "connecting to master backend problem"
date: 2009-03-15
forum: Mythbuntu
---

### Post by ashdavely on 2009-03-15
Hi.

I'm having trouble connecting to my master backend from any remote frontend. It works from the local frontend but nothing across the lan. I used the default passwords and set a root mysql password, Mythweb works. I looked at mysql,txt. On the front end in the "control centre" the mysql test button reports "sucess!" connecting to the database but in mythtv i get the message that it could not connect to the master backend. I'm not sure what else to check. I've reinstalled both several times.

Any suggestions on where to go now would be helpful. I' m using Mythbuntu 8.10

---

### Post by ashdavely on 2009-03-15
I've also just tried using the livecd frontend. No luck.

---

### Post by nickrout on 2009-03-15
> **ashdavely said:**
> I've also just tried using the livecd frontend. No luck.

what do the frontend logs say?

---

### Post by 4dognight on 2009-03-16
My guess is your mysql permissions are not set correct for remote connections. User 'mythtv' connecting local doesnt necessarily mean user 'mythtv' from a remote connection is the same. I would install the mysql admin package and check out your user settings for remote connections.

---

### Post by nickrout on 2009-03-16
> **4dognight said:**
> My guess is your mysql permissions are not set correct for remote connections. User 'mythtv' connecting local doesnt necessarily mean user 'mythtv' from a remote connection is the same. I would install the mysql admin package and check out your user settings for remote connections.

But then the "test" button on the frontend would not work. the logs would help.

---

### Post by Chris Musampa on 2009-03-16
Its not that pesky PIN number that caught me out is it?

---

### Post by nickrout on 2009-03-16
> **Chris Musampa said:**
> Its not that pesky PIN number that caught me out is it?

I think you might be posting to the wrong thread!

N

---

### Post by Chris Musampa on 2009-03-16
> **nickrout said:**
> I think you might be posting to the wrong thread!

N

Why so?  I offered a pointer to an simple oversight which had me scratching my head as to why my laptop frontend refused to connect to the backend, it may not be the solution but from memory the symptoms were similar.

---

### Post by nickrout on 2009-03-16
what do you mean pin number? 

If you are referring to the mysql password, it is not a PIN number, it is a password. As far as I know myth does have two PIN systems, one for controlling access to setup and one for controlling parental levels for videos.

And if you read the original post, you'll see he has the password right as the test button works in mythbuntu-control-center.

---

### Post by ashdavely on 2009-03-16
Here's my mythfrontend.log. I see a problem but I'm not sure where to correct it. Mythfrontend thinks my backend IP is 127.0.0.1. The mysql.txt in that location has the correct ip address for my backend though.

Also, XBMC works just fine on my frontend system so it seems the database is working OK on the backend.

Starting mythfrontend.real..
2009-03-16 16:25:32.786 New DB connection, total: 2
2009-03-16 16:25:32.798 Connected to database 'mythconverg' at host: 192.168.1.107
2009-03-16 16:25:32.813 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-03-16 16:25:32.813 Enabled verbose msgs:  important general
2009-03-16 16:25:34.051 Could not open settings file /home/frontend/.mythtv/mysql.txt for writing
2009-03-16 16:25:34.089 No theme dir: /home/frontend/.mythtv/themes/G.A.N.T
2009-03-16 16:25:34.092 Primary screen 0.
2009-03-16 16:25:34.094 Using screen 0, 1920x1080 at 0,0
2009-03-16 16:25:34.096 No theme dir: /home/frontend/.mythtv/themes/G.A.N.T
2009-03-16 16:25:34.097 Switching to square mode (G.A.N.T)
2009-03-16 16:25:34.140 Using the Qt painter
2009-03-16 16:25:34.140 JoystickMenuClient Error: Joystick disabled - Failed to read /home/frontend/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-03-16 16:25:34.140 lirc_init failed for mythtv, see preceding messages
2009-03-16 16:25:37.273 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-03-16 16:25:37.602 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-03-16 16:25:37.980 Registering Internal as a media playback plugin.
2009-03-16 16:25:38.112 No theme dir: /home/frontend/.mythtv/themes/G.A.N.T
tail: error reading `/proc/driver/nvidia/cards': Is a directory
tail: error reading `/proc/driver/nvidia/warnings': Is a directory
2009-03-16 16:26:29.881 Could not open settings file /home/frontend/.mythtv/mysql.txt for writing
2009-03-16 16:26:29.901 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-03-16 16:26:29.901 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-03-16 16:26:31.482 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-03-16 16:26:31.482 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-03-16 16:26:53.065 Could not open settings file /home/frontend/.mythtv/mysql.txt for writing
2009-03-16 16:26:53.092 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-03-16 16:26:53.092 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-03-16 16:26:54.322 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-03-16 16:26:54.322 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.

Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done

---

### Post by QA_manager on 2009-03-16
This seems to be a very, very common problem, judging from my own experience and my research while trying to solve it.  (I have not yet solved it.)

This also seems to me to be either an implementation error or a design error (or maybe both).  If the test passes then the front end should work, but it doesn't.

Did you have to use the 'sudo dpkg-reconfigure mythtv-database' incantation on the backend?  I always have to take that step (after every backend install) before the test will report success.  That seems to me another bug; if I install a master backend it should be automatically and fully configured to function as a backend.

I hope someone can solve your problem; I am eagerly awaiting the answer!

---

### Post by ashdavely on 2009-03-16
I figured it out. The "Master backend" field on the backend setup (general) had ip 127.0.0.1 where as it should have been 192.168.1.107 which is it's own ip address. A little confusing.

Works like a charm now.

---

### Post by QA_manager on 2009-03-16
Thank you for posting the fix; I will look at that.

Did you have to use the 'sudo dpkg-reconfigure mythtv-database' step before you could get 'Success' from the test?

---

### Post by ashdavely on 2009-03-17
No, I don't think you would run that on the frontend cause there isn't a mysql database. To get the test button to report success you just need to make sure your Mysql username and password are correct in those fields. If you left them alone during initial install it should work out of the box. Username is supposed to be mythtv password C1RFOKlE

What problem are you having?

---

### Post by nickrout on 2009-03-17
> **ashdavely said:**
> No, I don't think you would run that on the frontend cause there isn't a mysql database. To get the test button to report success you just need to make sure your Mysql username and password are correct in those fields. If you left them alone during initial install it should work out of the box. Username is supposed to be mythtv password C1RFOKlE

What problem are you having?

Actually the password is random, so will be different on different systems

---

### Post by ashdavely on 2009-03-17
So that's why it didn't work the first time.

---

### Post by QA_manager on 2009-03-17
Some people have said that you must use the 'sudo dpkg-reconfigure mythtv-database' step on the Backend in order to solve the "Unable to connect" problem.  I am trying to determine whether that is in fact a necessary step.

---

### Post by dudeskeeroo on 2009-04-06
> **QA_manager said:**
> Some people have said that you must use the 'sudo dpkg-reconfigure mythtv-database' step on the Backend in order to solve the "Unable to connect" problem.  I am trying to determine whether that is in fact a necessary step.

I had similar connection problems that just popped up one day.  I was getting this from remote frontends, local frontend worked fine:

[email]aaron@puppy:~/.mythtv[/email]$ 2009-04-07 13:06:21.407 Connecting to backend server: nas:6543 (try 1 of 5)
2009-04-07 13:06:21.407 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.

I was troubleshooting all sorts of things for days but the simple 'sudo dpkg-reconfigure mythtv-database' seemed to bring back the remote clients.

Now, if I can only figure out why mythtv-setup doesn't work.  It dumps core before the GUI is shown.  It means I have to make all my config changes using mysql clients!

A.

---

