---
title: "Mythfront unable to conntect to backend"
date: 2010-01-12
forum: Mythbuntu
---

### Post by hrobinson on 2010-01-12
Hello everyone.

I see these messages though out the message boards.  but it seems what ever I do does not fix it.

Here is my setup.

Mythbuntu 9.10 with a front end and backend.  it does not have a tuner card, as right now I am using it to store my videos.  Both Front end and Back end seem to be working just fine.

I have decided to expand my system and add a front end to the living room tv.


So I found an unused Dell inspiron 6000 with TV out.  My first step was to install mythbuntu.  I accidently installed the wrong version, so i wiped the hard drive and installed again.  The second install I was getting grub errors when it would start.  So I wiped the hard drive again, and installed mythbuntu with a 100mb /boot partition a 1.6G swap and the rest to "/"  This is running fine.

The problem is this.  The backend/frontend (called astro) works great, I have been using it at my desk for about a month, again, it does not have a tuner card installed yet.

the front end (the Dell inspiron 6000), called rosie gets the following error:

"Could not connect to the master backend server -- is it running? is the ip address set for it in the setup program correct?"

IPaddress of astro:  10.1.1.13
IPaddress of rosie:  DHCP -> current address 10.1.1.174

Database configuration for Rosie:
hostname:  10.1.1.13
Ping Test SErver checked
Port (default blank)
database name:  mythconverg
user:  mythtv
password: ********** (password blanked for security reasons)

Database configuration for astro
hostname:  localhost
ping test server checked
port (blank default)
database name:  mythconverg
user:  mythtv
password ********** (Password blanked for security reasons)

I have also executed the following commands:

sudo dpkg-reconfigure mythtv-database
     I answered yes to the question to allow remote hosts access the mysql database
sudo service mythtv-backend restart

started the front end on astro, and works perfectly.
started the front end on rosie, and get the same error.

If I go into media library and Watch videos, I can see the three shows I have loaded up on the server (same error shows up though).  If I click OK to dismiss the error and go into one of my shows (Dexter for example).  I can see the shows, and the descriptions I entered but it will not access the video if I highlight an episode hit enter, and then hit play.  Nothing happens it just returns to the list of episodes I have.

so I only have it partially working and i am missing something here, can someone see what I did wrong?

Thanks a lot for all your help.

Sincerely,

Harold Robinson

---

### Post by radnor on 2010-01-12
1st, I'm going to tell you record ALL setting before you change them.

Astro (FE/BE) in the BE setup General tab you will see localhost replace it with the actual IP addr (10.1.1.13) both places.  

Can help more when I get home.  I have a BE & RFE setup.

---

### Post by azmyth on 2010-01-12
Also may want to check perms on the db

log into mysql then

mysgl> SHOW GRANTS FOR mythtv;

I suspect the localhost setting is your issue though.

---

### Post by hrobinson on 2010-01-12
Hi Randor:  Thanks for your suggestion.  On Astro I went here:  Utilities / Setup -> Setup -> General ->Database Configuration 1/2 - Database Server Settings - HostName from local host to 10.1.1.13  I could not find the other place where I should change it.  I did change it on Rosie already.  Host name is set to 10.1.1.13 and the password is the same on both ends.

Result:  Same error 

Hi Azmyth:  I attempted the following command:  mysql --user=mythtv --password=******** mythtv.
mysql:  error 1045 (28000) access denied for user 'mythtv'@'localhost' (using password: YES).  according to the man page I am entering this correctly.

Thanks again for all your help.

Sincerely,

Harold Robinson

---

### Post by hrobinson on 2010-01-12
Azmyth:  Sorry I was entering the wrong password.  here are my results:

mysql> show grants for mythtv;
[FONT=Courier New]+-------------------------------------------------------------------------------------------------------+
| Grants for mythtv@%                                                                                               |
+-------------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'mythtv'@'%' IDENTIFIED BY PASSWORD '*D2744506F079F2D7267CEF314A504CE1B9CB2355' |
| GRANT ALL PRIVILEGES ON `mythconverg`.* TO 'mythtv'@'%'                                               |
+-------------------------------------------------------------------------------------------------------+
2 rows in set (0.00 sec)

mysql>

[FONT=Verdana]Thanks again for your help.

Sincerely,

Harold Robinson
[/FONT][/FONT]

---

### Post by azmyth on 2010-01-12
Okay, your db permissions look good.

Stop the backend and enter mythtv-setup, CLick on General. The first screen will have two places that specify the IP. If any of those are set as 127.0.0.1, please change to the IP address of the computer where the BE resides then try again.

---

### Post by hrobinson on 2010-01-12
azmyth:  Hi!

Ok, I shut down the backend of Astro by using the following:

[FONT=Courier New]sudo service mythtv-backend stop[/FONT]

I had to wait a minute while it shutdown

Next I started mythtv-setup from the command prompt

[FONT=Courier New]sudo mythtv-setup[/FONT]

a box opened up stating:

[FONT=Courier New]Mythbackend must be closed before continuing.
is it OK to close any currently running mythbackend processes?
[/FONT]
I answered OK

I selected General  There are two sections to this screen.  Local Backend (astro) and Master backend.  I changed the 127.0.0.1 to the ip address of astro which is 10.1.1.13, for both sections.  I then hit NEXT through the rest of the screens.

Though it probally was not necessary, I rebooted Astro. and tested with Rosie.

"Success" its working.  

I have rebooted rosie (for completeness sake) and now I am going to attempt to look at my media library and watch a program... (sound of the jeopardy song playing in the background)

*** Test ***

Now I am on Rosie, I start myttv with no errors and select media Library -> Watch Videos -> Select Dexter -> select Hungry Man to play.  It shows the description of the episode and the whole works, still no errors.  I hit enter to select "Hungry Man".  Everything looks good at this point.  I select play and hit enter.  The play screen goes away (back to the previous screen) and no Dexter on Rosie.  If I go to Astro, it plays just fine.

I am almost there, I can feel it.  if i can get past this hurdle, My wife will love me, I wont have to put the ugly server next to the TV.

Thanks for all your help.

Sincerely,

Harold Robinson

---

### Post by azmyth on 2010-01-12
Yeah, the remote FE can't access the files on the remote BE server. There's a few ways to tackle this. You can setup nfs or samba shares. What I did and this was the easiest.

I fired mythtv-setup again and scroll down to storage groups and you'll select videos. I then entered the path of the videos so say you have all your videos in /var/lib/mythtv/recordings I added this as the group. Please note, when you do this _you'll lose all your imdb information and you'll have to rescan for changes._

Restart everything and you'll be good to go.

---

### Post by jquintana on 2010-01-13
Make sure your time zones are both set to the same time zone. Also, check out this thread: [http://ubuntuforums.org/showthread.php?t=1378435](http://ubuntuforums.org/showthread.php?t=1378435)

---

### Post by hrobinson on 2010-01-13
jquintana:  Thanks for the suggestion, but both systems are on the same timezone

azmyth:  Thanks for the suggestions, Finally I have all that working.  I had to install NFS server on Astro, and NFS client on Rosie create the directory /var/lib/mithtv/videos and mount the directory in the correct directory:  /var/lib/mthtv/videos.  then specifiy the directory on rosie in the videos configuration screen. Everything is playing great.

Thanks for all your help.

Sincerely,

Harold Robinson

P.S.  How do I mark this as solved?

---

### Post by SiHa on 2010-01-13
> P.S. How do I mark this as solved?
At the top of the thread. Thread Tools -> Mark as Solved

---

### Post by hrobinson on 2010-01-13
SiHa:  Thanks, I had to look for it, but found it.  Harold

---

