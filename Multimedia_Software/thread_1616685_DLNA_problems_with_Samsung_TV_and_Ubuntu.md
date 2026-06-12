---
title: "DLNA problems with Samsung TV and Ubuntu"
date: 2010-11-08
forum: Multimedia Software
---

### Post by paparozoumis on 2010-11-08
I have a Samsung TV that can be and is connected via DLNA with my XP machines wirelessly. 

There is NO WAY I can make it see my Ubuntu machine though. 
I have the 10.04 and I have tried almost all the available programs for this OS. 
Name it and I have tried it: Mediatomb, ushare, PS3MediaServer and others that I cannot recall right now. 
These programs are installed with no errors and they look like they run correctly, their web interfaces work fine but that's all.  

None of them has been  ever found by the TV, -but it can see the native Samsung program PC Share runnning on the XPs.- 

What's the problem with my Ubuntu system and it cannot be recognised by the TV?
It's not that it won't play this or that file. It's that it won't see the server AT ALL. 

Any ideas?

---

### Post by bilbo1234 on 2010-11-26
I have had trouble getting my Sony BD player to see DLNA servers in ubuntu. The one that has worked the best for me is rygel -- maybe you should give it a try. It appears to be quite DLNA compliant.

---

### Post by Bone Down on 2010-11-26
I am using miniDLNA zero issues, easy to setup and works with my Samsung BDC6500 wirelessly. running on a headless Maverick server, with the miniDLNA plugin for webmin.

miniDLNA : [http://sourceforge.net/projects/minidlna/](http://sourceforge.net/projects/minidlna/)

miniDLNA Webmin : [http://minidlnawebmin.sourceforge.net/](http://minidlnawebmin.sourceforge.net/)

my file looks like this:

```
# port for HTTP (descriptions, SOAP, media transfer) traffic
port=8200

# network interface to bind to (this is the only interface that will serve files)
#network_interface=eth0

# set this to the directory you want scanned.
# * if have multiple directories, you can have multiple media_dir= lines
# * if you want to restrict a media_dir to a specific content type, you
#   can prepend the type, followed by a comma, to the directory:
#   + "A" for audio  (eg. media_dir=A,/home/jmaggard/Music)
#   + "V" for video  (eg. media_dir=V,/home/jmaggard/Videos)
#   + "P" for images (eg. media_dir=P,/home/jmaggard/Pictures)
# media_dir=/opt
media_dir=/media/FDrive/Series
media_dir=V,/media/Ext2TBXL/television
media_dir=V,/media/Ext2TBXL/theater
media_dir=A,/media/Ext2TBXL/jukebox

# set this if you want to customize the name that shows up on your clients
friendly_name=Maverick

# set this if you would like to specify the directory where you want MiniDLNA to store its database and album art cache
db_dir=/var/cache/minidlna

# this should be a list of file names to check for when searching for album art
# note: names should be delimited with a forward slash ("/")
album_art_names=Cover.jpg/cover.jpg/AlbumArtSmall.jpg/albumartsmall.jpg/AlbumArt.jpg/albumart.jpg/Album.jpg/album.jpg/Folder.jpg/folder.jpg/Thumb.jpg/thumb.jpg

# set this to no to disable inotify monitoring to automatically discover new files
# note: the default is yes
inotify=yes

# set this to yes to enable support for streaming .jpg and .mp3 files to a TiVo supporting HMO
enable_tivo=no

# set this to strictly adhere to DLNA standards.
# This will allow server-side downscaling of very large JPEG images which may hurt JPEG serving performance on (at least) Sony DLNA products.
strict_dlna=no

# default presentation url is http address on port 80
# presentation_url=http://www.mylan/index.php

# notify interval in seconds. default is 895 seconds.
notify_interval=1800

# serial and model number the daemon will report to clients
# in its XML description
serial=12345678
model_number=1
```

I tried others and found that this one has been the simplest, consistent, straight forward DLNA.
Mediatomb was inconsistant, and well the samsung setup simply sucked! miniDLNA updates newly added files automatically without interruption.

---

### Post by Jonners59 on 2010-12-04
**[COLOR=Red]HELLO!!!  IS ANYONE GOING TO HELP?  NO REPLIES IN 5 DAYS!!!![/COLOR]**


I have been trying to make this work on my new LG Tv for 2 weeks now.  I even have my own thread, listed as solved.

I did get it going but then lost the share capabilities with my other PCs and Laptops.

I  now have that working and the DNLA has stopped.  I go round in circles.  Tried re installing the miniDNLA and recreated the script, and the DNS  which is what made it work last time...  But it does not want to know.   The Tv sees the PC (we call it server) as [HTML]server:root[/HTML] but  it can not access the media.

The folders where the media I want  to view are stored in Partitions on a separate hard drive, so have  created mount points, so I have added to the script these mount points  as the location to search for the content.  I.e.

[HTML]media/shared[/HTML]

---

### Post by Bone Down on 2010-12-10
Sorry, I may not be much help, but I am certainly willing to give it a try. post up your current miniDLNA with in the ```

``` tags and let's see what you have going on. I will make sure to check this and my PM's more often.

---

### Post by Jonners59 on 2010-12-11
This is the config, though I believe that the issue is one of access to the directories, as the friendly name appears on the Tv as available DNLA servers and it DID work before I fixed SAMBA, which broke when I installed miniDNLA, see my Thread too at [http://ubuntuforums.org/showthread.php?t=1630547](http://ubuntuforums.org/showthread.php?t=1630547)...:

[HTML]# port for HTTP (descriptions, SOAP, media transfer) traffic
port=8200

# network interface to bind to (this is the only interface that will serve files)
# network_interface=eth0

# set this to the directory you want scanned.
# * if have multiple directories, you can have multiple media_dir= lines
# * if you want to restrict a media_dir to a specific content type, you
#   can prepend the type, followed by a comma, to the directory:
#   + "A" for audio  (eg. media_dir=A,/home/jmaggard/Music)
#   + "V" for video  (eg. media_dir=V,/home/jmaggard/Videos)
#   + "P" for images (eg. media_dir=P,/home/jmaggard/Pictures)
media_dir=/opt
media_dir=/Media/Baroni
media_dir=/Media/Chiara
media_dir=/Media/Configs 
media_dir=/Media/Monsters
media_dir=/Media/Resource
media_dir=/Media/Shared
media_dir=/Media/Teaching

# set this if you want to customize the name that shows up on your clients
friendly_name=Shared_Media

# set this if you would like to specify the directory where you want MiniDLNA to store its database and album art cache
db_dir=/var/cache/minidlna


# this should be a list of file names to check for when searching for album art
# note: names should be delimited with a forward slash ("/")
album_art_names=Cover.jpg/cover.jpg/AlbumArtSmall.jpg/albumartsmall.jpg/AlbumArt.jpg/albumart.jpg/Album.jpg/album.jpg/Folder.jpg/folder.jpg/Thumb.jpg/thumb.jpg

# set this to no to disable inotify monitoring to automatically discover new files
# note: the default is yes
inotify=yes

# set this to yes to enable support for streaming .jpg and .mp3 files to a TiVo supporting HMO
enable_tivo=no

# set this to strictly adhere to DLNA standards.
# This will allow server-side downscaling of very large JPEG images which may hurt JPEG serving performance on (at least) Sony DLNA products.
strict_dlna=no


# default presentation url is http address on port 80
# presentation_url=http://www.mylan/index.php

# notify interval in seconds. default is 895 seconds.
notify_interval=1800

# serial and model number the daemon will report to clients
# in its XML description
serial=12345678
model_number=1[/HTML]

---

### Post by Bone Down on 2010-12-11
> **Jonners59 said:**
> This is the config, though I believe that the issue is one of access to the directories, as the friendly name appears on the Tv as available DNLA servers and it DID work before I fixed SAMBA, which broke when I installed miniDNLA, see my Thread too at [http://ubuntuforums.org/showthread.php?t=1630547](http://ubuntuforums.org/showthread.php?t=1630547)...:

[HTML]# port for HTTP (descriptions, SOAP, media transfer) traffic
port=8200

# network interface to bind to (this is the only interface that will serve files)
# network_interface=eth0

# set this to the directory you want scanned.
# * if have multiple directories, you can have multiple media_dir= lines
# * if you want to restrict a media_dir to a specific content type, you
#   can prepend the type, followed by a comma, to the directory:
#   + "A" for audio  (eg. media_dir=A,/home/jmaggard/Music)
#   + "V" for video  (eg. media_dir=V,/home/jmaggard/Videos)
#   + "P" for images (eg. media_dir=P,/home/jmaggard/Pictures)
media_dir=/opt
media_dir=/Media/Baroni
media_dir=/Media/Chiara
media_dir=/Media/Configs 
media_dir=/Media/Monsters
media_dir=/Media/Resource
media_dir=/Media/Shared
media_dir=/Media/Teaching

# set this if you want to customize the name that shows up on your clients
friendly_name=Shared_Media

# set this if you would like to specify the directory where you want MiniDLNA to store its database and album art cache
db_dir=/var/cache/minidlna


# this should be a list of file names to check for when searching for album art
# note: names should be delimited with a forward slash ("/")
album_art_names=Cover.jpg/cover.jpg/AlbumArtSmall.jpg/albumartsmall.jpg/AlbumArt.jpg/albumart.jpg/Album.jpg/album.jpg/Folder.jpg/folder.jpg/Thumb.jpg/thumb.jpg

# set this to no to disable inotify monitoring to automatically discover new files
# note: the default is yes
inotify=yes

# set this to yes to enable support for streaming .jpg and .mp3 files to a TiVo supporting HMO
enable_tivo=no

# set this to strictly adhere to DLNA standards.
# This will allow server-side downscaling of very large JPEG images which may hurt JPEG serving performance on (at least) Sony DLNA products.
strict_dlna=no


# default presentation url is http address on port 80
# presentation_url=http://www.mylan/index.php

# notify interval in seconds. default is 895 seconds.
notify_interval=1800

# serial and model number the daemon will report to clients
# in its XML description
serial=12345678
model_number=1[/HTML]

Your miniDLNA config appears to be in order, aside from sorting them via:
#   + "A" for audio  (eg. media_dir=A,/home/jmaggard/Music)
#   + "V" for video  (eg. media_dir=V,/home/jmaggard/Videos)
#   + "P" for images (eg. media_dir=P,/home/jmaggard/Pictures)
which I believe is purely optional.
I would also check your samba settings and make sure all the directories listed above have the proper share settings.

---

### Post by Bone Down on 2010-12-11
do you have this file setup properly so that miniDLNA will start and stop?
```
#!/bin/sh

# chkconfig: 345 99 10
# description: Startup/shutdown script for MiniDLNA daemon
#
# $Id: minidlna.init.d.script,v 1.2 2009/07/02 00:33:15 jmaggard Exp $
# MiniUPnP project
# author: Thomas Bernard
# website: http://miniupnp.free.fr/ or http://miniupnp.tuxfamily.org/

MINIDLNA=/usr/sbin/minidlna
ARGS='-f /etc/minidlna.conf'

test -f $MINIDLNA || exit 0

. /lib/lsb/init-functions

case "$1" in
start)  log_daemon_msg "Starting minidlna" "minidlna"
        start-stop-daemon --start --quiet --pidfile /var/run/minidlna.pid --startas $MINIDLNA -- $ARGS $LSBNAMES
        log_end_msg $?
        ;;
stop)   log_daemon_msg "Stopping minidlna" "minidlna"
        start-stop-daemon --stop --quiet --pidfile /var/run/minidlna.pid
        log_end_msg $?
        ;;
restart|reload|force-reload)
        log_daemon_msg "Restarting minidlna" "minidlna"
        start-stop-daemon --stop --retry 5 --quiet --pidfile /var/run/minidlna.pid
        start-stop-daemon --start --quiet --pidfile /var/run/minidlna.pid --startas $MINIDLNA -- $ARGS $LSBNAMES
        log_end_msg $?
        ;;
*)      log_action_msg "Usage: /etc/init.d/minidlna {start|stop|restart|reload|force-reload}"
        exit 2
        ;;
esac
exit 0
```

---

### Post by Bone Down on 2010-12-11
here is a [step by step guide]("http://www.audiodude.nl/?p=84") that I found helpful, I am running Maverick and it worked out just fine for me. I am running a headless server utilizing Webmin; which happens to have a plugin for miniDLNA.

My suspicion is something changed when you fixed samba.

---

### Post by Jonners59 on 2010-12-11
> **Bone Down said:**
> Your miniDLNA config appears to be in order, aside from sorting them via:
#   + "A" for audio  (eg. media_dir=A,/home/jmaggard/Music)
#   + "V" for video  (eg. media_dir=V,/home/jmaggard/Videos)
#   + "P" for images (eg. media_dir=P,/home/jmaggard/Pictures)
which I believe is purely optional.
I would also check your samba settings and make sure all the directories listed above have the proper share settings.

My understanding is it should be optional, according to the file itself and some of the set up threads...


SAMBA is set as the following for all the directories:
[HTML][Shared]
        comment = Folder for sharing
        create mode = 660
        path = /media/Shared
        guest ok = yes
        directory mode = 770
        read only = no
available = yes
browsable = yes
public = yes
writable = yes[/HTML]

I can not recall how, but when I started it on an occasion it stated something like I did not have permission to access the directories, yet I can via SAMBA.

---

### Post by Jonners59 on 2010-12-11
> **Bone Down said:**
> do you have this file setup properly so that miniDLNA will start and stop?
```
#!/bin/sh

# chkconfig: 345 99 10
# description: Startup/shutdown script for MiniDLNA daemon
#
# $Id: minidlna.init.d.script,v 1.2 2009/07/02 00:33:15 jmaggard Exp $
# MiniUPnP project
# author: Thomas Bernard
# website: http://miniupnp.free.fr/ or http://miniupnp.tuxfamily.org/

MINIDLNA=/usr/sbin/minidlna
ARGS='-f /etc/minidlna.conf'

test -f $MINIDLNA || exit 0

. /lib/lsb/init-functions

case "$1" in
start)  log_daemon_msg "Starting minidlna" "minidlna"
        start-stop-daemon --start --quiet --pidfile /var/run/minidlna.pid --startas $MINIDLNA -- $ARGS $LSBNAMES
        log_end_msg $?
        ;;
stop)   log_daemon_msg "Stopping minidlna" "minidlna"
        start-stop-daemon --stop --quiet --pidfile /var/run/minidlna.pid
        log_end_msg $?
        ;;
restart|reload|force-reload)
        log_daemon_msg "Restarting minidlna" "minidlna"
        start-stop-daemon --stop --retry 5 --quiet --pidfile /var/run/minidlna.pid
        start-stop-daemon --start --quiet --pidfile /var/run/minidlna.pid --startas $MINIDLNA -- $ARGS $LSBNAMES
        log_end_msg $?
        ;;
*)      log_action_msg "Usage: /etc/init.d/minidlna {start|stop|restart|reload|force-reload}"
        exit 2
        ;;
esac
exit 0
```

Not familiar with this one...  Where is it kept?

I believe it starts OK, as the Tv shows the server and even has the name I gave it, "Shared_Media", which can only come from the miniDNLA config file.  The Tv would also not show the server at all if it did not have DNLA activated.

---

### Post by Jonners59 on 2010-12-11
> **Bone Down said:**
> here is a [step by step guide]("http://www.audiodude.nl/?p=84") that I found helpful, I am running Maverick and it worked out just fine for me. I am running a headless server utilizing Webmin; which happens to have a plugin for miniDLNA.

My suspicion is something changed when you fixed samaba.

I will give this a go.

PS.  WHat is a headless server?
PPS.  I agree.  There seems to be a conflict of some kind.

---

### Post by Bone Down on 2010-12-11
maybe start the minidlna server once manual to see if it works :
sudo /usr/sbin/minidlna &#8211;d &#8211;f /etc/minidlna.conf

The init.d script is as follows (I had to do the second portion to get it to work with Maverick server)

To auto start minidlna at server boot :
sudo cp minidlna.init.d.script /etc/init.d/minidlna
sudo chmod +x /etc/init.d/minidlna
sudo update-rc.d minidlna defaults

Some users had to make that last line into the folowing below to make it work. For me it worked as above :
sudo update-rc.d minidlna defaults 98 2

---

### Post by Bone Down on 2010-12-11
> **Jonners59 said:**
> I will give this a go.

PS.  WHat is a headless server?
PPS.  I agree.  There seems to be a conflict of some kind.

headless server = no monitor, no keyboard/mouse.
I access and control the server via webmin/ssh terminal from my laptop.

---

### Post by Bone Down on 2010-12-11
My server is a 9 year old box that was struggling to run WinXP desktop. I was finding it to be nothing more than a media server running Samsungs DLNA server; which did not auto update new files and I found it very tedious when ever a new TV show would complete it's download via torrent. 

I sought out a different way that used less bandwidth, was automated, a dlna server that would auto update when new content was added. Now my system rarely kills my bandwidth so that I can still use my internet, it automatically downloads TV shows via RSS feed, moves them to the proper directory(creates one if needed), renames them(rids the file of the long torrent file names), clears out the logs every 30 days, only downloads the latest episodes. I also have a shell script that downloads a series of video podcasts and stores them in the correct folder location as well. All of which is served up to my network via miniDLNA for viewing on my TV.

Ubuntu Maverick server
MySQL Server
Apache Server
Samba Server
PHP5
miniDLNA Server
Webmin
TorrentFlux B4rt
TransmissionCLI
Mashpodder
UFW with all ports closed (only opened required ports)
iptables/iplists for blocking ip's
and of course all required libraries

what was nearly a useless machine now runs like this a majority of the time:

System hostname	Maverick
Operating system	Ubuntu Linux 10.10
Webmin version	1.530
Time on system	Sat Dec 11 15:42:25 2010
Kernel and CPU	Linux 2.6.35-23-generic-pae on i686
Processor information	AMD Athlon(tm) XP 1800+, 1 cores
System uptime	2 days, 23 hours, 46 minutes
Running processes	97
CPU load averages	0.03 (1 min) 0.09 (5 mins) 0.08 (15 mins)
CPU usage	3% user, 1% kernel, 0% IO, 96% idle
Real memory	748.57 MB total, 225.27 MB used

Virtual memory	92 MB total, 16.30 MB used

Local disk space	183.28 GB total, 21 GB used

I enjoy this old computer now more than I did 3 months ago. Soon I will have vsftp setup on it and I will use it as my local web test server when working on sites.

---

### Post by Jonners59 on 2010-12-12
> **Bone Down said:**
> maybe start the minidlna server once manual to see if it works :
sudo /usr/sbin/minidlna &#8211;d &#8211;f /etc/minidlna.conf

The init.d script is as follows (I had to do the second portion to get it to work with Maverick server)

To auto start minidlna at server boot :
sudo cp minidlna.init.d.script /etc/init.d/minidlna
sudo chmod +x /etc/init.d/minidlna
sudo update-rc.d minidlna defaults

Some users had to make that last line into the folowing below to make it work. For me it worked as above :
sudo update-rc.d minidlna defaults 98 2

I got the following -

server@server:~$ sudo /usr/sbin/minidlna &#8211;d &#8211;f /etc/minidlna.conf
[sudo] password for server: 
Media directory not accessible! [/Media/Baroni]
Media directory not accessible! [/Media/Chiara]
Media directory not accessible! [/Media/Configs]
Media directory not accessible! [/Media/Monsters]
Media directory not accessible! [/Media/Resource]
Media directory not accessible! [/Media/Shared]
Media directory not accessible! [/Media/Teaching]
Unknown option: &#8211;d
Unknown option: &#8211;f
Unknown option: /etc/minidlna.conf

And for the last set of cmds I got:

server@server:~$ sudo cp minidlna.init.d.script /etc/init.d/minidlna
cp: cannot stat `minidlna.init.d.script': No such file or directory
server@server:~$ sudo chmod +x /etc/init.d/minidlna
server@server:~$ sudo update-rc.d minidlna defaults
update-rc.d: warning: /etc/init.d/minidlna missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/minidlna already exist.
server@server:~$ 


PS: The script does exist in /etc/init.d/ and it matches yours

---

### Post by Jonners59 on 2010-12-12
> **Bone Down said:**
> headless server = no monitor, no keyboard/mouse.
I access and control the server via webmin/ssh terminal from my laptop.

Oooh, would like to be able to do that.  Means I would not have to spend my evening up in my cold loft space on my own,,,  COuld sit in the warm with the family.

---

### Post by Jonners59 on 2010-12-12
> **Bone Down said:**
> My server is a 9 year old box that was struggling to run WinXP desktop. I was finding it to be nothing more than a media server running Samsungs DLNA server; which did not auto update new files and I found it very tedious when ever a new TV show would complete it's download via torrent. 

I sought out a different way that used less bandwidth, was automated, a dlna server that would auto update when new content was added. Now my system rarely kills my bandwidth so that I can still use my internet, it automatically downloads TV shows via RSS feed, moves them to the proper directory(creates one if needed), renames them(rids the file of the long torrent file names), clears out the logs every 30 days, only downloads the latest episodes. I also have a shell script that downloads a series of video podcasts and stores them in the correct folder location as well. All of which is served up to my network via miniDLNA for viewing on my TV.

Ubuntu Maverick server
MySQL Server
Apache Server
Samba Server
PHP5
miniDLNA Server
Webmin
TorrentFlux B4rt
TransmissionCLI
Mashpodder
UFW with all ports closed (only opened required ports)
iptables/iplists for blocking ip's
and of course all required libraries

what was nearly a useless machine now runs like this a majority of the time:

System hostname    Maverick
Operating system    Ubuntu Linux 10.10
Webmin version    1.530
Time on system    Sat Dec 11 15:42:25 2010
Kernel and CPU    Linux 2.6.35-23-generic-pae on i686
Processor information    AMD Athlon(tm) XP 1800+, 1 cores
System uptime    2 days, 23 hours, 46 minutes
Running processes    97
CPU load averages    0.03 (1 min) 0.09 (5 mins) 0.08 (15 mins)
CPU usage    3% user, 1% kernel, 0% IO, 96% idle
Real memory    748.57 MB total, 225.27 MB used

Virtual memory    92 MB total, 16.30 MB used

Local disk space    183.28 GB total, 21 GB used

I enjoy this old computer now more than I did 3 months ago. Soon I will have vsftp setup on it and I will use it as my local web test server when working on sites.

That sounds like what I want mine to do as well as:

Store our files and docs in a central place, which it does nicely
Host a VM running our telephone system (IP PBX) which it also does nicely (though it does not auto mount the VM if the system needs to restart).  This is Windows 7 running 3CX

Yours is the bit I am missing.  Once I have this fixed, please show me how to do what you have done.....  PS.  My machine (the server as we call it) is home build, 2nd time round.  It has a 1Tb HD for backups
1 x 700Gb split into 7 partitions for files and docs, etc (this is the bit I think the DNLA is having trouble with)
1 x 300Gb for the OS Windows Vista (not used), Ubuntu 10.04 LTS and a spare slot for my next Ubuntu upgrade (10.10 64-bit, the CD arrived today).
I use an AMD 64-bit processor, but only 4Gb RAM, which I need to think about upgrading.

---

### Post by Bone Down on 2010-12-12
> **Jonners59 said:**
> Oooh, would like to be able to do that.  Means I would not have to spend my evening up in my cold loft space on my own,,,  COuld sit in the warm with the family.

download [putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html") works with windows and linux, and will provide you with an SSH terminal to access your server from within your network. Via any other system say your laptop, or another desktop.

---

### Post by Bone Down on 2010-12-12
> **Jonners59 said:**
> I got the following -

server@server:~$ sudo /usr/sbin/minidlna –d –f /etc/minidlna.conf
[sudo] password for server: 
Media directory not accessible! [/Media/Baroni]
Media directory not accessible! [/Media/Chiara]
Media directory not accessible! [/Media/Configs]
Media directory not accessible! [/Media/Monsters]
Media directory not accessible! [/Media/Resource]
Media directory not accessible! [/Media/Shared]
Media directory not accessible! [/Media/Teaching]
Unknown option: –d
Unknown option: –f
Unknown option: /etc/minidlna.conf

And for the last set of cmds I got:

server@server:~$ sudo cp minidlna.init.d.script /etc/init.d/minidlna
cp: cannot stat `minidlna.init.d.script': No such file or directory
server@server:~$ sudo chmod +x /etc/init.d/minidlna
server@server:~$ sudo update-rc.d minidlna defaults
update-rc.d: warning: /etc/init.d/minidlna missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/minidlna already exist.
server@server:~$ 


PS: The script does exist in /etc/init.d/ and it matches yours
Media directory not accessible! <-- file permissions, I would start with linux access levels 0777 and scale back until it is not accessible then move back up to the minimum level that will allow access. My guess is this is what your problem is.

looks like the init.d script is already in place as long as miniDLNA is starting and stopping automatically you should be sorted.

---

### Post by Jonners59 on 2010-12-12
> **Bone Down said:**
> Media directory not accessible! <-- file permissions, I would start with linux access levels 0777 and scale back until it is not accessible then move back up to the minimum level that will allow access. My guess is this is what your problem is.

looks like the init.d script is already in place as long as miniDLNA is starting and stopping automatically you should be sorted.

OK...  I am kinda with you, but now stupid mode sets in, sorry.  Is it the SAMBA config that I set this?  WHich typically is:

[HTML][Shared]
        comment = Folder for sharing
        create mode = 660
        path = /media/Shared
        guest ok = yes
        directory mode = 770
        read only = no
available = yes
browsable = yes
public = yes
writable = yes
[/HTML]

And if so which one, I am assuming it is either create or directory....

And what are the levels, because this is now getting outside my comfort zone, not that I was in any anyway.

---

### Post by Bone Down on 2010-12-13
> **Jonners59 said:**
> OK...  I am kinda with you, but now stupid mode sets in, sorry.  Is it the SAMBA config that I set this?  WHich typically is:

[HTML][Shared]
        comment = Folder for sharing
        create mode = 660
        path = /media/Shared
        guest ok = yes
        directory mode = 770
        read only = no
available = yes
browsable = yes
public = yes
writable = yes
[/HTML]

And if so which one, I am assuming it is either create or directory....

And what are the levels, because this is now getting outside my comfort zone, not that I was in any anyway.

No like I mentioned in my previous post, I believe this to be your linux folder access levels. since miniDLNA is running on your linux install it is at this point that miniDLNA is having trouble accessing the directories. Samba allows your TV, or media streaming devices, windows systems to have access to the same directories. Your Samba settings look like they should be fine.

Edit: looks like your current settings are: directory mode = 770, try 775 if that doesn't work try 777. I am pretty much a newb and I am certain there is an easier way, but this is how I was able to get mine to work.

---

### Post by klyndt on 2010-12-21
May I also chime in with some tips.  First, I found the instructions here to be more applicable to the current setup of minidlna:
[http://www.richtechnologies.com/?p=206](http://www.richtechnologies.com/?p=206)

Also, Samba doesn't have anything to do with the DLNA server.  The permisions set on your folders is what matters.  chmod them like suggested before and that should fix it.  I had a problem in that my media was on a NTFS partition.  You can't change permissions on NTFS.  So I had to do it from fstab.  

I do still have one problem though. My minidlna will not autostart. But, I have not tried the sudo update-rc.d minidlna defaults 98 2 line as suggested.  Everything else works though.

Klyndt

---

### Post by Jonners59 on 2010-12-21
> **klyndt said:**
> May I also chime in with some tips.  First, I found the instructions here to be more applicable to the current setup of minidlna:
[http://www.richtechnologies.com/?p=206](http://www.richtechnologies.com/?p=206)

Also, Samba doesn't have anything to do with the DLNA server.  The permisions set on your folders is what matters.  chmod them like suggested before and that should fix it.  I had a problem in that my media was on a NTFS partition.  You can't change permissions on NTFS.  So I had to do it from fstab.  

I do still have one problem though. My minidlna will not autostart. But, I have not tried the sudo update-rc.d minidlna defaults 98 2 line as suggested.  Everything else works though.

Klyndt

Klyndt
Thank you. I will take a closer look at the link you sent.

If you go back to the start of my comments you'll see that I did get it going and have another thread ([http://ubuntuforums.org/showthread.php?t=1630547](http://ubuntuforums.org/showthread.php?t=1630547)) solved.  I was having trouble with my shares and in fixing that lost my DNLA.....

I too have the files on a separate hard drive running NTFS.  The problem seems to be one of permissions as you too point out.  When I run DNLA I get an error messaging saying I do not have permission to view the directories, though I do have full access as do the users on the LAN....

I do also have DNLA running on another machine, which I used to try it out, but that has the files on the same hard drive....

I am interested to know what code to put in terminal and how you got yours going.  Are yours auto mounted via mount points?  How do I chmod them?  I have tried but it makes no difference, so I must be doing it wrong.....

PS in return:

You need this script to auto start an dstop DNLA.  Create it by opening  "gedit" and pasting it in to the document and then save and make  "executable"

[HTML]#!/bin/sh

# chkconfig: 345 99 10
# description: Startup/shutdown script for MiniDLNA daemon
#
# $Id: minidlna.init.d.script,v 1.2 2009/07/02 00:33:15 jmaggard Exp $
# MiniUPnP project
# author: Thomas Bernard
# website: http://miniupnp.free.fr/ or http://miniupnp.tuxfamily.org/

MINIDLNA=/usr/sbin/minidlna
ARGS='-f /etc/minidlna.conf'

test -f $MINIDLNA || exit 0

. /lib/lsb/init-functions

case "$1" in
start)  log_daemon_msg "Starting minidlna" "minidlna"
        start-stop-daemon --start --quiet --pidfile /var/run/minidlna.pid --startas $MINIDLNA -- $ARGS $LSBNAMES
        log_end_msg $?
        ;;
stop)   log_daemon_msg "Stopping minidlna" "minidlna"
        start-stop-daemon --stop --quiet --pidfile /var/run/minidlna.pid
        log_end_msg $?
        ;;
restart|reload|force-reload)
        log_daemon_msg "Restarting minidlna" "minidlna"
        start-stop-daemon --stop --retry 5 --quiet --pidfile /var/run/minidlna.pid
        start-stop-daemon --start --quiet --pidfile /var/run/minidlna.pid --startas $MINIDLNA -- $ARGS $LSBNAMES
        log_end_msg $?
        ;;
*)      log_action_msg "Usage: /etc/init.d/minidlna {start|stop|restart|reload|force-reload}"
        exit 2
        ;;
esac
exit 0[/HTML]

---

### Post by klyndt on 2010-12-21
I do automount my drive using fstab at bootup.  I'm not sure what your setup is, but my fstab mount line is:
```
# /Data was on /dev/sda1 during installation
UUID=AAB8DA98B8DA61FD /Data           ntfs    defaults,umask=000,gid=46 0       0
```
The problem was the umask.  It was 007 which kept the DLNA devices from having permission on the folders on that drive (where my media is).  I changed it to 000 and all is good now.  It was easy to see the affect. When I did a 
ls -la
at first I could see the user group had no rwx permission. After this change all files now have rwx in the last group. My guess is that the umask doesn't have to be 000. It will work with 003 maybe. But since I don't care that much.... :)

---

### Post by klyndt on 2010-12-21
As far as the script goes, I have it. It is executable. I can start minidlna manually using: 
```
/etc/init.d/minidlna start
```
It just doesn't want to start at boot up. I'm thinking there must be a log file somewhere I can look at, but I'm not sure where to look.

Klyndt

---

### Post by Bone Down on 2010-12-22
@Jonners - I didn't realize that you were working with ntfs file structure, I had to add my external/internal ntfs drives to my fstab as well that is were you need to look to remedy your access errors.

@klyndt - Jonners has posted the file, and further back I have as well with a link and instructions on how to have miniDLNA auto- start/stop on shutdown/boot up.

---

### Post by Jonners59 on 2010-12-22
> **Bone Down said:**
> @Jonners - I didn't realize that you were working with ntfs file structure, I had to add my external/internal ntfs drives to my fstab as well that is were you need to look to remedy your access errors.

@klyndt - Jonners has posted the file, and further back I have as well with a link and instructions on how to have miniDLNA auto- start/stop on shutdown/boot up.

Cheers Bone
I thought I'd lost you.

I am quite out of my depth here, but Klyndt's comment about where the permissions had to change on the fstab looks like it may be the bit of puzzle I have been looking for.  I am just up and about to go into the office to have a go.....   Don't go away.  I may need you.  PS, I think all this should be picked up in my thread...

[http://ubuntuforums.org/showthread.php?t=1630547](http://ubuntuforums.org/showthread.php?t=1630547)

---

### Post by Jonners59 on 2010-12-22
> **klyndt said:**
> I do automount my drive using fstab at bootup.  I'm not sure what your setup is, but my fstab mount line is:
```
# /Data was on /dev/sda1 during installation
UUID=AAB8DA98B8DA61FD /Data           ntfs    defaults,umask=000,gid=46 0       0
```The problem was the umask.  It was 007 which kept the DLNA devices from having permission on the folders on that drive (where my media is).  I changed it to 000 and all is good now.  It was easy to see the affect. When I did a 
ls -la
at first I could see the user group had no rwx permission. After this change all files now have rwx in the last group. My guess is that the umask doesn't have to be 000. It will work with 003 maybe. But since I don't care that much.... :)

No, sadly that did not work either...

On the Tv I get "Shared_Media" come up, which is the name I gave the server, so the DNLA is working, but I can not see anything in there.  It says the folders are empty on the Tv.

Any other ideas guys, please?

---

### Post by Bone Down on 2010-12-22
I am at a loss at this point, but you could give [this thread]("http://sourceforge.net/projects/minidlna/forums/forum/879956/topic/3419652") a look and see if anything contained within might help you out.

maybe try running ```
sudo minidlna -R
```
This should rescan your media directories for new/old media (which it should be doing automatically).

Here are a list of the available commands minidlna utilizes
```
Usage:
        minidlna [-d] [-f config_file]
                [-a listening_ip] [-p port]
                [-s serial] [-m model_number]
                [-t notify_interval] [-P pid_filename]
                [-w url] [-R] [-V] [-h]

Notes:
        Notify interval is in seconds. Default is 895 seconds.
        Default pid file is /var/run/minidlna.pid.
        With -d minidlna will run in debug mode (not daemonize).
        -w sets the presentation url. Default is http address on port 80
        -h displays this text
        -R forces a full rescan
        -V print the version number
``` we have officially exceeded my capabilities. I hope you are able to sort this out sooner than later.

---

### Post by Jonners59 on 2010-12-22
> **Bone Down said:**
> I am at a loss at this point, but you could give [this thread]("http://sourceforge.net/projects/minidlna/forums/forum/879956/topic/3419652") a look and see if anything contained within might help you out.

maybe try running ```
sudo minidlna -R
```This should rescan your media directories for new/old media (which it should be doing automatically).


And this is what it states...

[HTML]server@server:~$ sudo minidlna -R
[sudo] password for server: 
Media directory not accessible! [/Media/Baroni]
Media directory not accessible! [/Media/Chiara]
Media directory not accessible! [/Media/Configs]
Media directory not accessible! [/Media/Monsters]
Media directory not accessible! [/Media/Resource]
Media directory not accessible! [/Media/Shared]
Media directory not accessible! [/Media/Teaching]
server@server:~$ [/HTML]

---

### Post by Bone Down on 2010-12-22
> **Jonners59 said:**
> And this is what it states...

[HTML]server@server:~$ sudo minidlna -R
[sudo] password for server: 
Media directory not accessible! [/Media/Baroni]
Media directory not accessible! [/Media/Chiara]
Media directory not accessible! [/Media/Configs]
Media directory not accessible! [/Media/Monsters]
Media directory not accessible! [/Media/Resource]
Media directory not accessible! [/Media/Shared]
Media directory not accessible! [/Media/Teaching]
server@server:~$ [/HTML]

run this command and post up the results.
```
ls -la 
```
I am curious under what user miniDLNA is running as.
Also did you download and install putty for your convenience? Putty would run on your laptop so that you can SSH into your linux box from the comfort of your sofa.

---

### Post by Jonners59 on 2010-12-22
> **Bone Down said:**
> run this command and post up the results.
```
ls -la 
```I am curious under what user miniDLNA is running as.
Also did you download and install putty for your convenience? Putty would run on your laptop so that you can SSH into your linux box from the comfort of your sofa.

It works, IT BEEEEEPing WORKS!!!:popcorn:

I did a search for all miniDNLA and put it all in the trash - knowing I could easily restore it.

Then I tried the new link and install

[http://www.richtechnologies.com/?p=206](http://www.richtechnologies.com/?p=206)

[HTML]This is what I did to share my MythTV media with the Sony BDP-S570:
 Add the unofficial MiniDLNA Ubuntu PPA:
        sudo add-apt-repository ppa:stedy6/stedy-minidna
Update the APT package index:
        sudo apt-get update
Install MiniDLNA:
        sudo apt-get install minidlna
Edit the /etc/minidlna.conf file:
        sudo vi /etc/minidlna.conf

Ensure the following in the config
port=8200

> media_dir=A,"directory for music"
media_dir=P,"directory for Pictures"
media_dir=V,"directory for Videos"
media_dir=V,"directory for Recordings"

or

> media_dir="directory for all media"

friendly_name=DLNA Server    > or whatever you want to call it
album_art_names=Cover.jpg/cover.jpg/AlbumArtSmall.jpg/albumartsmall.jpg/AlbumArt.jpg/albumart.jpg/Album.jpg/album.jpg/Folder.jpg/folder.jpg/Thumb.jpg/thumb.jpg
inotify=yes
enable_tivo=no
strict_dlna=no
notify_interval=900
serial=12345678
model_number=1
 
Restart the MiniDLNA server, removing the existing media list:
        sudo /etc/init.d/minidlna stop
        sudo rm -r /tmp/minidlna
         sudo /etc/init.d/minidlna start:D:D:D:D[/HTML]

Then create the auto start script:

```
#!/bin/sh

# chkconfig: 345 99 10
# description: Startup/shutdown script for MiniDLNA daemon
#
# $Id: minidlna.init.d.script,v 1.2 2009/07/02 00:33:15 jmaggard Exp $
# MiniUPnP project
# author: Thomas Bernard
# website: http://miniupnp.free.fr/ or http://miniupnp.tuxfamily.org/

MINIDLNA=/usr/sbin/minidlna
ARGS='-f /etc/minidlna.conf'

test -f $MINIDLNA || exit 0

. /lib/lsb/init-functions

case "$1" in
start)  log_daemon_msg "Starting minidlna" "minidlna"
        start-stop-daemon --start --quiet --pidfile /var/run/minidlna.pid --startas $MINIDLNA -- $ARGS $LSBNAMES
        log_end_msg $?
        ;;
stop)   log_daemon_msg "Stopping minidlna" "minidlna"
        start-stop-daemon --stop --quiet --pidfile /var/run/minidlna.pid
        log_end_msg $?
        ;;
restart|reload|force-reload)
        log_daemon_msg "Restarting minidlna" "minidlna"
        start-stop-daemon --stop --retry 5 --quiet --pidfile /var/run/minidlna.pid
        start-stop-daemon --start --quiet --pidfile /var/run/minidlna.pid --startas $MINIDLNA -- $ARGS $LSBNAMES
        log_end_msg $?
        ;;
*)      log_action_msg "Usage: /etc/init.d/minidlna {start|stop|restart|reload|force-reload}"
        exit 2
        ;;
esac
exit 0
```  Make executable.  I just open the hosting folder/directory using "Open as Administrator" then seklect the file/scropt and do a left click for properties and tick the "Execute" tab.

The pain is all over!!!!   :o  :popcorn:

PS, no I did not install Putty....  How do I, please???

---

### Post by Bone Down on 2010-12-23
> **Jonners59 said:**
> It works, IT BEEEEEPing WORKS!!!:popcorn:

I did a search for all miniDNLA and put it all in the trash - knowing I could easily restore it.

Then I tried the new link and install

[http://www.richtechnologies.com/?p=206](http://www.richtechnologies.com/?p=206)

[HTML]This is what I did to share my MythTV media with the Sony BDP-S570:
 Add the unofficial MiniDLNA Ubuntu PPA:
        sudo add-apt-repository ppa:stedy6/stedy-minidnaUpdate the APT package index:
        sudo apt-get updateInstall MiniDLNA:
        sudo apt-get install minidlnaEdit the /etc/minidlna.conf file:
        sudo vi /etc/minidlna.conf port=8200
network_interface=eth0
media_dir=A,/var/lib/mythtv/music
media_dir=P,/var/lib/mythtv/pictures
media_dir=V,/var/lib/mythtv/videos
media_dir=V,/var/lib/mythtv/recordings
friendly_name=MythTV DLNA Server
album_art_names=Cover.jpg/cover.jpg/AlbumArtSmall.jpg/albumartsmall.jpg/AlbumArt.jpg/albumart.jpg/Album.jpg/album.jpg/Folder.jpg/folder.jpg/Thumb.jpg/thumb.jpg
inotify=yes
enable_tivo=no
strict_dlna=no
notify_interval=900
serial=12345678
model_number=1
 
Restart the MiniDLNA server, removing the existing media list:
        sudo /etc/init.d/minidlna stop
                   sudo rm -r /tmp/minidlna
                   sudo /etc/init.d/minidlna start:D:D:D:D[/HTML]

The pain is all over!!!!

PS, no I did not install Putty....  How do I, please???

glorious what a fine moment. PUTTY is located [here]("http://www.putty.org/") I just heard about something called 'screen' I am going to look into it, but I have utilized putty for over a decade now its simple and it works.

---

### Post by klyndt on 2010-12-23
I'm glad you got things to work.  I decided to take your brute force method and apply it to my situation.  Sure enough, now it autostarts!  So I'm done too.

---

### Post by Jonners59 on 2010-12-24
Chuffed I was of service...  Have a great Chrimbo

---

