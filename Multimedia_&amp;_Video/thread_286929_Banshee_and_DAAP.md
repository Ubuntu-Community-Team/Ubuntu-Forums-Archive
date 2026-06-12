---
title: "Banshee and DAAP"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by tool462rules on 2006-10-28
I have installed Banshee from the Ubuntu repositories.  I also installed the official plugins and daap packages.
Whenever I open banshee up it tells me that it could not be initialized.(see screenshot)
Any ideas?
I have tried to restart thinking that would help, but no dice.
:confused: I'm out of ideas.

O and here's the console output of when I start banshee from there and try to start DAAP.

```
ryan@ryan-desktop:~$ banshee
Warning: [10/28/2006 10:16:17 AM] (Cannot connect to NetworkManager) - An available, working network connection will be assumed

(/usr/lib/banshee/banshee.exe:5432): GLib-GObject-WARNING **: value "128" of type `gint' is invalid or out of range for property `bitrate' of type `gint'
Debug: [10/28/2006 10:16:18 AM] (Default player engine) - GStreamer 0.10
Debug: [10/28/2006 10:16:18 AM] (Audio CD Core Initialized) - 
Setting MusicBrainz proxy to www.musicbrainz.org:80
Audioscrobbler starting protocol engine
Loading Podcast Feeds:  42 ms
Warning: [10/28/2006 10:17:16 AM] (Could not initialize plugin `Daap') - Daemon not running
```

---

### Post by tool462rules on 2006-10-28
*Fixed*
You must start the mDNS service discovery in System->Administration->Services

---

### Post by vloris on 2006-10-28
Enabling mDNS doesn't fix it here. Still the daap module is disabled...

---

### Post by tool462rules on 2006-10-28
You're going to have to give me some more info if I can even try to help.
Try and run the program in terminal and enable DAAP in the plugins.
Post the output, also give some general info about your computer.

---

### Post by vloris on 2006-10-29
The problem is that I cannot enable DAAP in the plugins page. It is grayed out and it gives the message "This plugin could not be initialized"

When starting banshee from a terminal this is the response:
```
Warning: [10/29/2006 4:57:44 PM] (Cannot connect to NetworkManager) - An available, working network connection will be assumed
Debug: [10/29/2006 4:57:47 PM] (Default player engine) - GStreamer 0.10
Debug: [10/29/2006 4:57:47 PM] (Audio CD Core Initialized) - 
Setting MusicBrainz proxy to www.musicbrainz.org:80
Audioscrobbler starting protocol engine
**Warning: [10/29/2006 4:57:49 PM] (Could not initialize plugin `Daap') - Daemon not running**

```

If that last line is referring to avahi-daemon, I cannot find any process running with 'avahi' in it's name. But when I look in System->Administration->Services, the checkmark in front of avahi-daemon is in fact checked.

---

### Post by vloris on 2006-10-29
Problem solved: avahi-daemon doesn't start until you manually edit the file /etc/default/avahi-daemon and set the value of AVAHI_DAEMON_START to 1.
The default value is 0, so any attempt to start avahi-daemon will silently fail without error.

---

### Post by stinkypudding on 2006-11-10
I have MDNS enabled and avahi start set to 1, but I'm still getting the following daap error when I try to connect to itunes 7.0.2:

ryanr@ryanr-laptop:~$ banshee

(/usr/local/lib/banshee/banshee.exe:27771): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
Debug: [11/10/2006 10:30:25 PM] (Loading audio profiles) - /usr/local/share/banshee/audio-profiles

(/usr/local/lib/banshee/banshee.exe:27771): GLib-GObject-WARNING **: value "128" of type `gint' is invalid or out of range for property `bitrate' of type `gint'
Debug: [11/10/2006 10:30:27 PM] (Default player engine) - GStreamer 0.10
Debug: [11/10/2006 10:30:27 PM] (Audio CD Core Initialized) - 
Building initial DAAP database from local library...
Starting DAAP Server
: Could not grab key 174 (maybe another application has grabbed this key)
: Could not grab key 160 (maybe another application has grabbed this key)
: Could not grab key 176 (maybe another application has grabbed this key)
Setting MusicBrainz proxy to [www.musicbrainz.org:80](www.musicbrainz.org:80)
Loading Podcast Feeds:  307 ms
Connecting to DAAP share: 192.168.1.100:3689 (My itunes)
Error: [11/10/2006 10:31:27 PM] (Cannot login to DAAP share) - Failed to login

Can anyone help?   running banshee 0.11.2 on edgy.

---

### Post by possiblyj on 2006-12-03
I'm in the same boat as stinkypudding.

j@j-desktop:~$ exec banshee
Warning: [12/3/2006 9:34:30 PM] (Cannot connect to NetworkManager) - An available, working network connection will be assumed
Debug: [12/3/2006 9:34:34 PM] (Default player engine) - GStreamer 0.10
Debug: [12/3/2006 9:34:35 PM] (Audio CD Core Initialized) - 
Audioscrobbler starting protocol engine
Warning: [12/3/2006 9:34:35 PM] (Could not initialize plugin `Daap') - Daemon not running
Setting MusicBrainz proxy to [www.musicbrainz.org:80](www.musicbrainz.org:80)

**Update:** Looks like this thread is dead, but figured I'd post this anyway.  I finally got it to work by adding a few more packages in the universe that mentioned zeroconf and avahi.

---

### Post by bonovoxpsu on 2006-12-04
i get the same problem as well - failed to login. :(

my google fu is not strong enough so far...

---

### Post by bonovoxpsu on 2006-12-04
see this thread:

[http://www.ubuntuforums.org/showthread.php?t=260672&highlight=itunes+daap](http://www.ubuntuforums.org/showthread.php?t=260672&highlight=itunes+daap)

seems a change in apple's daap protocol....

c'mon linux hackers - beat apple (again)

---

