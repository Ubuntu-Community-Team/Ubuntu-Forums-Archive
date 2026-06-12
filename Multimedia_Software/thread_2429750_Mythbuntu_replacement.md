---
title: "Mythbuntu replacement?"
date: 2019-10-22
forum: Multimedia Software
---

### Post by jazz53 on 2019-10-22
I am thinking about making/buying a linux based TV Box.
I see Mythbuntu is discontinued.  Is there a replacement?
Are there any TV boxes pre-configured using Linux?
Any good links on where to start?

TIA

---

### Post by TheFu on 2019-10-22
I'm looking for a better solution myself.  

Define "TV Box", since there are many, many, different capabilities that different people would call "TV box."  Make a list of what you expect.  Most of the commercial solutions have huge gotchas, but if you aren't willing to tinker, they are probably the only solution. 
* Do you want to record CATV/Satellite/OTA?
* Do you want to stream the video anywhere in your house or anywhere in the world?
* How much do you care about privacy?
* Do home videos, photos, music need to be included in the "media"?

Have everything except TV schedule grid-based recordings working already and a still need a legal source for free schedule data.  Come January 1, my current source disappears.  Setting up OTA recordings for future times is something I have solved, but it is highly manual for each week.  I suspect my free solution will need to pull schedule data at 6pm daily, then schedule recordings based on titles or keywords for the next 24 hrs. Might have to do it in 4-6 hour periods, since OTA data in the broadcast streams is often limited to 4 hrs here.

Your challenges could be different. Depends on where you are in the world.

MythTV isn't dying to my knowledge, so you can always install that onto an Ubuntu system.

---

### Post by jazz53 on 2019-10-22
OK,  Hmmm
I would like to treat it like a DVR, but not have cable.
Download from the internet as they become available and store to a ext. or internal drive to watch at a later date/time.
Possibly using a streaming service or torrents.
There is no OTA where I live.
A schedule would be nice.
So a HDMI cable for hooking to TV, a remote for selecting, pausing and other normal functions.
I do not think I would need a tuner as no OTA or cable.

---

### Post by TheFu on 2019-10-23
Torrents are illegal where I live, so I can't discuss that, plus I don't use them.

Streaming of content is a live thing. Not download and view later.  That violates all ToS I've ever seen, so we cannot discuss that either.

Kodi can easily handle streaming and any local content that arrives to specific places in the library file system.  Most paid streaming services have DRM that are problems for normal Linux in my experience. Getting any specific paid service working is a constant hassle as DRM changes.  I use a mix of Kodi on Raspberry Pi devices ($45/ea) and a Roku for DRM streaming.

Kodi is pretty much plug-in-play.  Only recommendation I have is to avoid any Android-based machines.  Android brings all sorts of overhead that just isn't needed.  On Intel systems, **apt install kodi** is all you need on Ubuntu/Debian desktops. On a R-pi, there are special distributions that you just **dd** onto the microSD and boot.  I use OSMC (debian-based) and it has plenty of support, careful upgrades, etc.  Every quarter or so, I'll upgrade my OSMC right after I clone the microSD. If anything fails or doesn't work after the upgrade, just swap the cloned SD back and WAF is high.

If you live in north America and want to try some antenna stuff, Kodi has any easy addon for HDHR devices that don't use cableCARD.

If you go with a raspberry Pi, know that it is a display device, not really a "server" for media.  People do use it as a server to other devices, but the I/O and networking for all raspberry Pi devices is limited.  For $10-$30 more, there are other SBCs which support real GigE, real SATA and real USB3 capabilities.  AmeriDroid is a reseller of those things - good to get a feel for what is available.  None of these is suitable for transcoding video.  If that is something you need, stay with x86 for the server.

---

### Post by jazz53 on 2019-10-24
OK thanks,
Looks like rasberrypi4 has most of the things you mention
I have had little luck with Kodi on my home comp, so trying to stay away from that if I can
Any other useful info is always welcome.

---

### Post by MoebusNet on 2019-10-25
LinHES is an Arch-based OS designed to simplify the process of setting up Mythtv. It claims to be able to to go from installation to operation in 20 minutes (after you've done it a few times). I'm running LinHES 8.5.1 on a dual-core i386 with 8MB RAM, so most modern computers should be capable. To view over-the-air television (OTA), I've had the best luck with the SiliconDust HDHomerun line of network tuners over Ethernet for my DVR. I use ScheduleDirect ($25/year) for my programming line-up updates. 

[http://linhes.org/](http://linhes.org/)

[https://www.silicondust.com/hdhomerun/](https://www.silicondust.com/hdhomerun/)

[http://www.schedulesdirect.org/](http://www.schedulesdirect.org/)

---

### Post by TheFu on 2019-10-25
I use HDHR tuners for OTA/Antenna use too.  Picked up a quad-tuner on a deal for $70 a few months ago.

I live outside a metro area and need an amplifier to get over 20 channels, but my cheap amp ($22) is much too strong, so I had to add an attenuator ($6) to cut the amplified signal down by 8dB.  The results have been spectacular.  Finally in the Goldy Locks range for all the major channels.  Receiving 96 channels now, with about 30 actually channels with something interesting on monthly.

I'll likely end up paying for ScheduleDirect.  In the USA, TV schedule data is copyrighted and their aren't any free providers suitable for program use.  Attempts are constantly made to scrap schedule data from a number of websites, but it is like a format war with monthly changes to the sites to break the scrapers, I understand.  I think in Europe and elsewhere, schedule data is freely available.

I have a TiVo with lifetime schedule data. There might be a way to gain access to that data, somehow.

---

### Post by MoebusNet on 2019-10-25
Just to make life interesting, LinHES (and I suppose Mythtv) are changing from DataDirect-type scheduling to JSON-based scheduling as of Mythtv version 31. Unfortunately, it looks like the only way to scan for or modify channel selection will be by CLI, which will add to the challenges faced by new users.

Although Tivo boxes run on Linux, by now it is proprietary enough so that you would have to have quite an in-depth knowledge of Linux, database management and Tivo file formats to try to work with them; it seems much simpler to work with the open-source options available. With a $110 investment in hardware for a Raspberry PI 4 complete kit, someone else has done almost all of the coding to be able to use Kodi as a DVR.

---

### Post by Tadaen_Sylvermane on 2019-10-26
Mythtv is fairly simple to set up. I do mine on a plain ubuntu server installation. everything is in separate lxd containers. 5-10 minutes + package install time. This is the short list of much googling I've done over the last couple years testing, finding what worked, how to change, and ultimately this is my cheat sheet.


```
apt install mythtv-backend
```

If you are putting sql on the same machine either mysql or mariadb. I've gone with mariadb as I detest Oracle. It seems better supported and faster.

```
apt install mariadb-server
```

edit /etc/mythtv/config.xml to point to your sql server. this is mine. this step is overlooked by most guides i've seen. on an ubuntu package install it sets a random password for the backend, therefore the guides that say mythtv for the password don't work.

```
# cat /etc/mythtv/config.xml <Configuration>
  <Database>
    <PingHost>1</PingHost>
    <Host>sql.mylan.home</Host>
    <UserName>mythtv</UserName>
    <Password>mythtv</Password>
    <DatabaseName>mythconverg</DatabaseName>
    <Port>3306</Port>
  </Database>
  <WakeOnLAN>
    <Enabled>0</Enabled>
    <SQLReconnectWaitTime>0</SQLReconnectWaitTime>
    <SQLConnectRetry>5</SQLConnectRetry>
    <Command>echo 'WOLsqlServerCommand not set'</Command>
  </WakeOnLAN>
</Configuration>
```

On your sql server open up the bind address. Probably more secure to just open to the ip of the sql server. I don't honestly know. I do this in a separate conf.d file.

```
# cat /etc/mysql/mariadb.conf.d/99-kodi-optimize.cnf 
[mysqld]


optimizer_search_depth = 1
skip-name-resolve
innodb_adaptive_hash_index = off
bind-address            = 0.0.0.0
```

The above settings other than the bind-address speed up Kodi access big time. Pretty sure they are mariadb only, don't quote that. Found on a google search.

Run these commands on your sql server to create the user and database. Change localhost to '%' with the quotes if you want any lan machine to connect, else the ip of the backend.

```
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"][COLOR=#D73A49]CREATE[/COLOR] [COLOR=#D73A49]DATABASE[/COLOR] [COLOR=#6F42C1]IF[/COLOR] NOT EXISTS mythconverg;[/TD]
[/TR]
[TR]
[TD="class: blob-num js-line-number, align: right"][/TD]
[TD="class: blob-code blob-code-inner js-file-line"][COLOR=#D73A49]GRANT[/COLOR] ALL [COLOR=#D73A49]ON[/COLOR] mythconverg.[COLOR=#D73A49]*[/COLOR] TO mythtv@localhost IDENTIFIED BY [COLOR=#032F62]"mythtv"[/COLOR];[/TD]
[/TR]
[TR]
[TD="class: blob-num js-line-number, align: right"][/TD]
[TD="class: blob-code blob-code-inner js-file-line"]FLUSH PRIVILEGES;[/TD]
[/TR]
[TR]
[TD="class: blob-num js-line-number, align: right"][/TD]
[TD="class: blob-code blob-code-inner js-file-line"][COLOR=#D73A49]GRANT[/COLOR] CREATE TEMPORARY TABLES [COLOR=#D73A49]ON[/COLOR] mythconverg.[COLOR=#D73A49]*[/COLOR] TO mythtv@localhost IDENTIFIED BY [COLOR=#032F62]"mythtv"[/COLOR];[/TD]
[/TR]
[TR]
[TD="class: blob-num js-line-number, align: right"][/TD]
[TD="class: blob-code blob-code-inner js-file-line"]FLUSH PRIVILEGES;[/TD]
[/TR]
[/TABLE]

```
Restart your sql server, then your mythtv backend. Make sure the user you intend to use to configure mythtv is in the mythtv group and has sudo access.

From a remote machine ```
ssh -X user@mythtv.server "mythtv-setup"
```

Then work through it. Once this is done manually restart the service for good measure. ```
systemctl restart mythtv-backend
```, then ```
systemctl status mythtv-backend
``` if all green you are running. enjoy. connect clients as needed.

*EDIT* Note. As long as I've been messing with this stuff the mythtv config always tells me that the directory isn't writeable every single time i exit the ssh config session. Ignore it. As long as the path is 755 mythtv:mythtv it will work. I've no clue why this error pops every single time for me.

---

### Post by MoebusNet on 2019-10-28
The issue I've had with Mythtv has been once I've installed it, I still have difficulty connecting backend to front-end, designating the different storage locations and generally getting the software configured properly so that it works as designed. To make things more interesting, Myth has changed the mandatory GUI-based-configuration completely as of version 30, not to mention the upcoming version 31 JSON channel-scanning-and-editing-by-CLI goat-roap. Not newbie-friendly at all. While admittedly imperfect, LinHES saves me mucho teeth-gnashing and head-banging for both installation and configuration. Of course, once you've gotten several installations up and running properly as designed, you'll have a much clearer idea of how to get thing installed and running from scratch to make the system tailored to your needs. This is all predicated on x86-type hardware; the recent development seems to have moved to the inexpensive Raspberry-type ARM single-board systems using Kodi as basis for a media & DVR system.

---

### Post by polvino on 2020-01-20
Is there such a thing as a "simple" DVR implementation? I've been toying with the idea of having a linux-based solution, but it seems awfully complex. Here's what I want:
[LIST=1]
[*]Linux server running 24/7 with a 2-channel capture card for ATSC signals
[*]Front end client that can read the recordings and play them back thru an HDMI cable
[*]Easy enough for my wife to operate (I imagine you switch TV source to the front end client, and then use another remote to access the content)
[*]Reliable! I don't want to have to troubleshoot 2 new machines to figure out why nothing works after an update. Can it be up for 2 years with no downtime?
[/LIST]

I believe Mythbuntu had a solution like this at one time. I need guidance on what the front-end client would look like: type of motherboard, form factor, disk, fans, IR receiver, remote, etc. Also compatible tuners for whatever ubuntu distro.

Our primary use will be to pause/rewind live TV, and skip annoying commercials on newscasts and other programming. I'm in the US and my location has very strong OTA signals.

---

### Post by TheFu on 2020-01-20
polvino,

Both "thread jacking" and "necro-posting" are discouraged in these forums.
Please create a new thread and ask your question.  Would be helpful to state your experience level with Linux too, since what I might consider "simple" after over 25 yrs with Linux often doesn't apply to others with a few months of experience.

---

