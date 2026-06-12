---
title: "uShare on 11.04, won't link to xbox"
date: 2011-01-09
forum: Multimedia Software
---

### Post by tk1269 on 2011-01-09
I have been using uShare for a few years now, and up until now it has worked great.  A few snags here and there, but nothing I couldn't figure out, although after five years using Ubuntu, i still consider myself a noob.  Now I am on a new machine, running Ubuntu 11.04 (my last one was running 9.04) and I am having trouble with uShare again.  Its installed, configured, and runs just fine, but my xbox won't recognize it.  

Here's the catch: the first night I set it up, after a few errors, I got it working!  Watched a movie, smiled, and went to bed.  Woke up the next morning, booted up the comp, fired up ushare and BAM!  Nothing.  I hadn't changed any settings, moved any cables, downloaded anything new, but no dice.  After a little searching, I updated the .conf file to reflect a change I noticed in the IFACE.  Sometimes when I boot my computer, it connects to the router on eth0, sometimes on eth1, and sometimes on eth0-eth1.  I'm not sure what is up with that, but that may be a problem for another day.  For right now, I just want uShare to work.  Please help.

**ushare.conf**
# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=Desktop

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth0-eth1

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49153

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/thomas

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
ENABLE_WEB=

# Enable Telnet control interface (yes/no)
ENABLE_TELNET=

# Use XboX 360 compatibility mode (yes/no)
ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
ENABLE_DLNA=

**ifconfig**
eth0-eth1 Link encap:Ethernet  HWaddr 00:26:5a:84:6e:80  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:5aff:fe84:6e80/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40424 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28578 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49660630 (49.6 MB)  TX bytes:4339429 (4.3 MB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9768 (9.7 KB)  TX bytes:9768 (9.7 KB)

---

### Post by tk1269 on 2011-01-09
For some more info or a longer story, please see the last 2 posts on this thread:

[http://ubuntuforums.org/showthread.php?t=903204&page=2](http://ubuntuforums.org/showthread.php?t=903204&page=2)

---

### Post by tk1269 on 2011-01-16
Please?  I could really use some help here.

---

### Post by tk1269 on 2011-01-16
Ok, another note.  The PS3 works fine with all these settings.  It might be something with my xbox I guess, but we all know Microsoft doesn't want any tampering with their precious machines. . .

---

### Post by Rhoan on 2011-09-04
I am having similar problems running ushare on 10.4., Xbox won't recognize the shared files as being on the network. Interesting note, though, is if you set ENABLE_USHARE_DLNA=yes , the xbox will recognize the folder as being shared, but won't be able to access them. This leads me to believe that the reason ushare isn't working has something to do with how my network is set up. in terminal:

rick@ubuntu:~$ ushare
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 192.168.0.102:49206
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /home/rick/Shared
Found 1 files and subdirectories.

so i'm not sure whats up

---

### Post by tk1269 on 2011-09-04
Well at least I know I'm not crazy.  I am on 11.04 now, I'm not sure if I have even tried to use my xbox for streaming for a while now.  I jut tried it though, and still nothing.  I have experienced being able to access the folder before as you said up there ^, but have no files available in it.  I have also tried to contact uShare developers, but have gotten useless responses if any at all.  Its too bad, I really liked uShare.  The place where I am currently living I have a PS3, so I still get to use it.  But once I move out of here, I will be out of luck.  On that note, I plan on having my computer located closer to the TV in the next place so I can just run a display cable directly from my PC to the television and watch everything through VLC.  There are still so many filetypes that neither PS3 or Xbox support, so most things I watch I have to download a few versions or crappier versions to get to play.

Anyways, thanks for throwing your two cents in, maybe if we get a few more, we can actually get some help on this problem.

---

### Post by syerges on 2012-05-06
Mine only works on both XBox 360 and playstation 3 with the following settings exactly...if i change any of them, then it stops working.
USHARE_OVERRIDE_ICONV_ERR=yes
USHARE_ENABLE_WEB=yes
USHARE_ENABLE_TELNET=no
USHARE_ENABLE_XBOX=yes
USHARE_ENABLE_DLNA=no


The enable_dlna really messed me up because it says ps3 won't work without it, but it's wrong.  also make sure to look up your xbox and ps3 ip addresses and open up the port to them from your pc.

My computer's IP address was found by right clicking on my internet connection and then clicking on "connection information" and it is 192.168.0.11

My Xbox and PS3's IP addresses were found by going to network settings, they are 192.168.0.10 and 192.168.0.13 so I had to use the following codes in terminal. sorry, don't know how to do that code thing here....

I used the same port as you so you shouldn't have to change that number.

sudo ufw allow proto tcp from 192.168.0.11 to 192.168.0.10 port 49153
sudo ufw allow proto tcp from 192.168.0.11 to 192.168.0.13 port 49153

---

### Post by tk1269 on 2012-05-06
First off, thanks for your input Syerges.  It was good information although it turned out to not be the answer I was looking for.  But I have learned some things and I am back to share for anyone who is having problems with this.

Since I posted this thread, I have upgraded twice and am now running 12.04, running Gnome classic.  This however did not change the problems I was having with uShare.  Until now I had given up on streaming to the xbox entirely, and was only using my PS3.  But I am about to lose my PS3 (don't ask) so I figured it was time to get this taken care of.  I'm still not great with running things in terminal, so forgive me if this isn't as concise as it could be.

I am now streaming video to my Xbox successfully, but havent checked on audio or pics yet.  Here is my ushare.conf file:

# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=uShare

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth0
USHARE_IFACE=eth1


# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49153

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/thomas

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=YES

# Enable Web interface (yes/no)
ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
ENABLE_TELNET=no

# Use XboX 360 compatibility mode (yes/no)
ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
ENABLE_DLNA=no


There are a few things to note abot the changes I have made and why.  

Firstly, the interface that runs on my computer is eth1.  I don't know why it isn't the default eth0, maybe because my ethernet card is a secondary to the motherboard chip that has fried.

The port is 49153. I don't remember where I picked that one up, but it works.

You are supposed to be able to share more than one directory, but I haven't been able to get any besides the first in the list to load.  Instead, I have my home directory shared, and I have created link folders to my video collection that is kept on my external hard drive.  Sometimes if the external has been sitting for too long, I have to open it in a file browser to 'wake it up' and then restare ushare.  But, it passes so for now, thats how it stays.

I took my last settings for the web, telnet, xbox, and dlna from Syerges.  Contrary to popular belief, you do not need dlna enabled to share with a PS3.  These settings work for both xbox and PS3.  In fact, I just fired them both up to make sure, and no problems.

Now, other than turning the dlna off, I haven't made any major changes in order to get my xbox to recognize the ushare file.  But I did figure something out.  In the past, I have been running ushare by opening a terminal and typing:

sudo /etc/init.d/ushare start

Eons ago, when I last had ushare streaming to my xbox, this command worked just fine.  But for some reason, it just doesn't cut it.  But when I run it another way:

ushare -xD

its great.  Now, changing the .conf file to have the xbox argument as 'yes' should take care of having to add the flag every time you run the program, but it doesn't I guess.  And the 'D' is to run it in the background so as not to need a terminal open on your desktop the entire time you're streaming.  I guess I haven't tried running it without the '-x', it may work.  That'll be next.  In any case, running it with the first command will stream to the ps3 just fine, but the xbox won't pick it up.  I tried looking around in the shell script for ushare in /etc/init.d but that was over my head, so I didn't mess around.

Now, I got it streaming properly, but I still had to open up a terminal and run it.  Not too difficult, but why not streamline it a little.  So I created a launcher on my toolbar.  Called it ushare, and gave it the 'ushare -xD' command.  Now I can click on the icon down there, and it fires right up.  Also, I added it to the startup applications the same way.  'Applications:System Tools:Preferences:Startup Applications'  Fires up right away when I boot up my system.  It takes a minute to load, but then is ready to rock.

I still need to figure out a few things, like if I need the '-x' flag every time.  Also, how to kill the process.  Currently, if I update one of the folders or add another title, I have to reboot my whle computer to stop ushare.  If I try to start ushare while it is running, this is what I get:

Interface eth1 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.
bind: Address already in use

But, for now it is streaming to my xbox, and that is what matters.  If I can figure out the rest, its just bonus.

I hope this helps someone out there, I've spent enough time trying to figure it out, and didn't run across a single person with the same problem.  Also, if anyone has any more ideas, I would love to hear them.  Thanks!

---

### Post by syerges on 2012-06-20
Thanks for the added info... I've given up on streaming to my xbox. Apparently ushare can't handle my multitude of files and no longer will add new video's so I said so long to xbox sharing!

---

