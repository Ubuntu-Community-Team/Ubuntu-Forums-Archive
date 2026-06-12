---
title: "Media Server to replace DLink Media Lounge"
date: 2006-12-16
forum: Multimedia &amp; Video
---

### Post by spotslayer on 2006-12-16
Good afternoon,  I have a DLink DSM-320 media server. It uses a proprietary program, Media Lounge. I would like to kill off my last Windows box and get completely linux. To do this I need software to replace Media Lounge. Can anyone recommend a linux app that will work for me.

[http://www.dlink.com/products/?pid=318](http://www.dlink.com/products/?pid=318)

David

---

### Post by grantjohnston on 2006-12-16
I have the same mediaserver, and am still having troubles finding a free one... Twonkyvision worked great, but costs money after the first 30 days.. Gmediaserver is in apt-get but it unfortunately doesn't do video.  There was another thread on here... [http://www.ubuntuforums.com/showthread.php?t=165288&highlight=geexbox](http://www.ubuntuforums.com/showthread.php?t=165288&highlight=geexbox). However, as you can tell, I'm having troubles with it... Give it a shot and let me know what you get, maybe it's just my fubar'd computers. Also, I tried emulating the Medialounge through Wine, and that doesn't work, either.



Best of luck to both of us.




Grant

---

### Post by Nelson-Ray on 2006-12-16
Um ya'll need MythTV. Even if you dont plan or want to watch TV, MythTV has MythVideo plugin which will play all your video files and organize the movies with thumnails and imdb synopsis all with graphics like Windows Media Center (better imo). For music MythTV comes with MythMusic (to play your digitial music collection) and for photos MythPhoto which will archive your photo collection. Does everything except your laundry and has virtually endless possibilites. Awesome software.


[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by superm1 on 2006-12-16
> **spotslayer said:**
> Good afternoon,  I have a DLink DSM-320 media server. It uses a proprietary program, Media Lounge. I would like to kill off my last Windows box and get completely linux. To do this I need software to replace Media Lounge. Can anyone recommend a linux app that will work for me.

[http://www.dlink.com/products/?pid=318](http://www.dlink.com/products/?pid=318)

David

If this is anything like the DSM-520, and supports UPNP, you can natively use myth or a few other apps to broadcast to it.  Check and see if the device supports upnp.

---

### Post by grantjohnston on 2006-12-17
It does. I'm going to try and setup Myth tonight... See how I like it.



Thanks for the help guys.. I may have more questions. :D



Grant

---

### Post by superm1 on 2006-12-17
> **grantjohnston said:**
> It does. I'm going to try and setup Myth tonight... See how I like it.



Thanks for the help guys.. I may have more questions. :D



Grant
Grant,
To let you know, there is minor bug with the ubuntu packages.  If you set up a seperate backend and frontend, some of the files necessary to run UPNP weren't put in the backend package.   On your backend machine, you will need to install the frontend package too.

---

### Post by grantjohnston on 2006-12-17
Appreciate the help.. Am I understanding this correctly.. To install Myth, I need to start on a fresh install? Someone please tell me this isn't true...

---

### Post by superm1 on 2006-12-17
You don't need a fresh install, the wiki pages just show from the ground up.  You can pick up from right after you would have installed the OS to get going.  I would recommend that you do resize your drive though, and make a separate partition for recordings.  This partition will quickly fill up and programs will be autoexpired from it automatically.

---

### Post by grantjohnston on 2006-12-17
> **superm1 said:**
> You don't need a fresh install, the wiki pages just show from the ground up.  You can pick up from right after you would have installed the OS to get going.  I would recommend that you do resize your drive though, and make a separate partition for recordings.  This partition will quickly fill up and programs will be autoexpired from it automatically.



At this point, I don't have a TV tuner card, yet.. I'd like to do that down the road, but at this point, I'm simply needing it to be a mediaserver so I can use my DSM-320 again. Once again.. I'm having troubles getting the packages to install.. God, I swear my computers are the worst about screwing up...

---

### Post by superm1 on 2006-12-18
If your on edgy, the packages are in multiverse/universe.

---

### Post by grantjohnston on 2006-12-18
Which I am.. and here's one of the errors I get




```
grant@threeve:~$ sudo apt-get install mysql-server mythtv-backend mythtv-database 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  mythweb
Recommended packages:
  xmltv-util
The following NEW packages will be installed:
  mysql-server mythtv-backend mythtv-database
0 upgraded, 3 newly installed, 0 to remove and 10 not upgraded.
Need to get 0B/838kB of archives.
After unpacking 2580kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package mysql-server.
(Reading database ... 96380 files and directories currently installed.)
Unpacking mysql-server (from .../mysql-server_5.0.24a-9_all.deb) ...
Selecting previously deselected package mythtv-backend.
Unpacking mythtv-backend (from .../mythtv-backend_0.20-0.2ubuntu2_amd64.deb) ...
Selecting previously deselected package mythtv-database.
Unpacking mythtv-database (from .../mythtv-database_0.20-0.2ubuntu2_all.deb) ...
Setting up mysql-server (5.0.24a-9) ...
Setting up mythtv-backend (0.20-0.2ubuntu2) ...
udev active, devices will be created in /dev/.static/dev/
Starting MythTV server: mythbackendSession management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
.

Setting up mythtv-database (0.20-0.2ubuntu2) ...
Failed to connect to database: Access denied for user 'root'@'localhost' (using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mythtv-database
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


EDIT::: After reading the wiki a bit more. It's saying that I need to log out of my current user and log in under a mythtv user... Is there anyway around this? This is my main box, and I would prefer logging in under my username rather than theirs.. Also.. Could it be that I'm not logged under mythtv and that's why it's erroring?

---

### Post by superm1 on 2006-12-18
> **grantjohnston said:**
> Which I am.. and here's one of the errors I get




```
grant@threeve:~$ sudo apt-get install mysql-server mythtv-backend mythtv-database 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  mythweb
Recommended packages:
  xmltv-util
The following NEW packages will be installed:
  mysql-server mythtv-backend mythtv-database
0 upgraded, 3 newly installed, 0 to remove and 10 not upgraded.
Need to get 0B/838kB of archives.
After unpacking 2580kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package mysql-server.
(Reading database ... 96380 files and directories currently installed.)
Unpacking mysql-server (from .../mysql-server_5.0.24a-9_all.deb) ...
Selecting previously deselected package mythtv-backend.
Unpacking mythtv-backend (from .../mythtv-backend_0.20-0.2ubuntu2_amd64.deb) ...
Selecting previously deselected package mythtv-database.
Unpacking mythtv-database (from .../mythtv-database_0.20-0.2ubuntu2_all.deb) ...
Setting up mysql-server (5.0.24a-9) ...
Setting up mythtv-backend (0.20-0.2ubuntu2) ...
udev active, devices will be created in /dev/.static/dev/
Starting MythTV server: mythbackendSession management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
.

Setting up mythtv-database (0.20-0.2ubuntu2) ...
Failed to connect to database: Access denied for user 'root'@'localhost' (using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mythtv-database
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
EDIT::: After reading the wiki a bit more. It's saying that I need to log out of my current user and log in under a mythtv user... Is there anyway around this? This is my main box, and I would prefer logging in under my username rather than theirs.. Also.. Could it be that I'm not logged under mythtv and that's why it's erroring?

You don't need to necessarily be logged in under the mythtv user.  Which wiki page was indicating this?  It sounds more like you are having troubles with mythtv-database installing and connecting to mysql.  Have you previously tried to setup myth or anything on mysql?

---

### Post by grantjohnston on 2006-12-18
> **superm1 said:**
> You don't need to necessarily be logged in under the mythtv user.  Which wiki page was indicating this?  It sounds more like you are having troubles with mythtv-database installing and connecting to mysql.  Have you previously tried to setup myth or anything on mysql?

No, I haven't. I had it installed while trying to get mediatomb working a couple weeks ago.. But, once again, that failed miserably, too.. Couldn't find any support on it.


EDIT: Also... [http://www.mythtv.org/wiki/index.php/Ubuntu_Edgy_Installation_From_Source](http://www.mythtv.org/wiki/index.php/Ubuntu_Edgy_Installation_From_Source) That's the wiki.. Ugh, this is getting on my nerves.. I really wanna watch the movies I've copied. over the past couple weeks, and I can't, haha.

---

### Post by superm1 on 2006-12-18
> **grantjohnston said:**
> No, I haven't. I had it installed while trying to get mediatomb working a couple weeks ago.. But, once again, that failed miserably, too.. Couldn't find any support on it.


EDIT: Also... [http://www.mythtv.org/wiki/index.php/Ubuntu_Edgy_Installation_From_Source](http://www.mythtv.org/wiki/index.php/Ubuntu_Edgy_Installation_From_Source) That's the wiki.. Ugh, this is getting on my nerves.. I really wanna watch the movies I've copied. over the past couple weeks, and I can't, haha.

I'm really starting to despise some of these other wiki pages that don't provide good up to date information......
Okay - I'm attempting to maintain up to date pages at [http://help.ubuntu.com/community/MythTV](http://help.ubuntu.com/community/MythTV)

As of right now, you have an issue that you somehow have a mysql root password set.  Your very best bet right now is to open up synaptic/adept, and remove all myth packages (and their configuration files) as well as mysql-server.  If afterwords you have a /usr/local/share/mythtv, a /usr/share/mythtv, or a /etc/mythtv or a ~/.mythtv remove any of those directories.  Install the packages per the ubuntu guides that I'm linking to.  This should remove all setting for mysql as well as anywhere that other packaging source installs would have littered files causing problems.

---

### Post by grantjohnston on 2006-12-18
> **superm1 said:**
> I'm really starting to despise some of these other wiki pages that don't provide good up to date information......
Okay - I'm attempting to maintain up to date pages at [http://help.ubuntu.com/community/MythTV](http://help.ubuntu.com/community/MythTV)

As of right now, you have an issue that you somehow have a mysql root password set.  Your very best bet right now is to open up synaptic/adept, and remove all myth packages (and their configuration files) as well as mysql-server.  If afterwords you have a /usr/local/share/mythtv, a /usr/share/mythtv, or a /etc/mythtv or a ~/.mythtv remove any of those directories.  Install the packages per the ubuntu guides that I'm linking to.  This should remove all setting for mysql as well as anywhere that other packaging source installs would have littered files causing problems.

I agree with you on despising out of date info.. Or lack of support... Okay... Removed all of those, about to re-install. My other question is.. Which do I go with on your wiki? That's another one I tried messing with earlier and I couldn't figure out which would be the best suited for me.. As of right now I just need it to stream media from my PC to my DSM-320 less than 5 feet away.

---

### Post by superm1 on 2006-12-18
> **grantjohnston said:**
> I agree with you on despising out of date info.. Or lack of support... Okay... Removed all of those, about to re-install. My other question is.. Which do I go with on your wiki? That's another one I tried messing with earlier and I couldn't figure out which would be the best suited for me.. As of right now I just need it to stream media from my PC to my DSM-320 less than 5 feet away.

Well i'm also doing the best I can to provide support too at least for ubuntu :)

Go with a desktop, backend, frontend setup.  Easiest since you've only got this one PC, and already have it up and running as a desktop.  You'll need to go thru the initial mythtv-setup too even though you don't have a tuner yet too.

---

### Post by grantjohnston on 2006-12-18
Yay... More problems... After trying to install it, AGAIN from synaptic, I get a pop-up box that says


```

E: mythtv-database: subprocess post-installation script returned error exit status 1
E: mythtv: dependency problems - leaving unconfigured
```

Other than that, I believe everything else installs fine... At least that I can tell.

Have any ideas?

---

### Post by grantjohnston on 2006-12-18
> **superm1 said:**
> Well i'm also doing the best I can to provide support too at least for ubuntu :)

Go with a desktop, backend, frontend setup.  Easiest since you've only got this one PC, and already have it up and running as a desktop.  You'll need to go thru the initial mythtv-setup too even though you don't have a tuner yet too.

You're doing a hell of a job!!! I really appreciate it. Any idea on the other error I'm getting?

---

### Post by superm1 on 2006-12-18
> **grantjohnston said:**
> Yay... More problems... After trying to install it, AGAIN from synaptic, I get a pop-up box that says


```

E: mythtv-database: subprocess post-installation script returned error exit status 1
E: mythtv: dependency problems - leaving unconfigured
```Other than that, I believe everything else installs fine... At least that I can tell.

Have any ideas?
Go to the troubleshooting section, and follow the thing about the root password failing.
[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop#head-2ca13596b08d7736a909ba52b4bffd2b547fb4f4](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop#head-2ca13596b08d7736a909ba52b4bffd2b547fb4f4)

---

### Post by grantjohnston on 2006-12-18
> **superm1 said:**
> Go to the troubleshooting section, and follow the thing about the root password failing.
[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop#head-2ca13596b08d7736a909ba52b4bffd2b547fb4f4](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop#head-2ca13596b08d7736a909ba52b4bffd2b547fb4f4)

Well.. Thanks to Superm, we got the box to recognize a few files. However, they don't play.. I'm gonna have to research this one a bit more and see if there's a way to get it to... This is really getting on my nerves...

---

### Post by grantjohnston on 2006-12-26
> **grantjohnston said:**
> Well.. Thanks to Superm, we got the box to recognize a few files. However, they don't play.. I'm gonna have to research this one a bit more and see if there's a way to get it to... This is really getting on my nerves...

Well, a week later. The problem still arises. It recognizes the files, but won't play any of them.. Even the ones I know for a FACT play on the box.. Can anyone give me any insight? I'm lost..

---

### Post by grantjohnston on 2007-01-13
Update.. I have Samba put on my xubuntu box streaming to a windows machine running the proprietary D-link software, so, it works, but it uses a lot of network bandwidth, and the video is somewhat choppy.. Anyone have any ideas?

---

### Post by grantjohnston on 2007-01-28
Still confused, video still choppy, anyone?

---

### Post by Kossu on 2007-03-11
sorry to bring up such an old post, however I have a feeling theres more ppl with same problem, there is a patch to enable video playback on dsm 320 with mythtv available on mythtvs site.

---

