---
title: "uShare &amp; Xbox 360. Firewall problem?"
date: 2010-05-11
forum: Multimedia Software
---

### Post by iTheBadGuy on 2010-05-11
So like the tittle says, I have followed several tutorials on how ot get this thing to work, and to tell you the truth.. I'm about to give up. This is so easy with WMP11. All I have to do is allow the xbox. That's it.

But enough about that.. Here's what I get when I try to start uShare with ```
ushare -x
``` ```
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Initializing UPnP subsystem ...
UPnP MediaServer listening on 192.168.1.103:49201
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /home/michael
Found 14 files and subdirectories.

```
says my eth0 is down.. um no it's not, I open the browser and my connection is fine. I'm also on my Xbox, signed on to the same connection. So it's fine.

These are my settings ```
# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=Ubuntu

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49200

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=1337


 Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/michael

# Use to override what happens when iconv fails to parse a file name. The default uShare behaviour is to not add the entry in the media list This option overrides that behaviour and adds the non-iconv'ed string into the media list, with the assumption that the renderer will be able to handle it. Devices like Noxon 2 have no problem with strings being passed as is. (Umlauts for all!)

# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
USHARE_ENABLE_WEB=YES

# Enable Telnet control interface (yes/no)
USHARE_ENABLE_TELNET=NO

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=YES

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
USHARE_ENABLE_DLNA=NO

```

Ok, so there it is.. can someone help me? let me know whats wrong and what I have to do to fix it?! PLEASE! I'm running out of ideas here.

P.S Running Ubuntu 10.04. Installed uShare from the repository, and all that has to do with uShare.
P.S2 Xbox finds uShare on the media list, but when I select it.. it says something about firewall problems, idk..

---

### Post by PratterFak on 2010-05-14
There are a few problems here.

I see this- UPnP MediaServer listening on 192.168.1.103:**49201**
and your below config is 49200.

Now over a year ago when I first set up uShare, the documentation I went by noted to use port 49153.

OK, so I use port 49153 and I've been sharing flawlessly to my 360 on Ubuntu 9.10 since the beginning.

However, I am unable to share files to my 360 on Ubuntu 10.04, so there is a deeper issue with this. If you can get get your other problem resolved, running 10.04, you 360 will see your Ubuntu share, but will not connect to it and the PC connect test will fail. I have dual boot at the moment, so if I can pop back to 9.10 to share files.

I'm at a wall on this and nobody seems to have any answers at the moment or at least that I can find.

---

### Post by Snoman314 on 2010-06-14
Thirded. I have exactly the same situation as the OP.

---

### Post by Only Loki on 2010-06-17
I was having the exact same problem, but I got mine to work.  I noticed that my network connections were given to separate names.  There was the name that is in the network connections configuration and in the status menu in the tray.  And then there was the the name that is in the Device-Network tools menu (System/Administration/Network Tools)

Long story short,  what use to be Eth0 in both changed when I upgraded to 10.04  became Auto Ethernet and Eth1 respectively.

ushare requires the device name so I just changed my ushare setting to Eth1 and I'm running fine now

---

### Post by iTheBadGuy on 2010-06-17
Well, after I tried several times I gave up (yes I'm a quitter lol) and re-installed windows. Now I'm installing 10.04 again. This time I'm dual-booting. I just can't live without sharing media with my Xbox. My Xbox is where I watch all my movies and shows. So yeah.. This is "high-priority" if I want to have Ubuntu as a "always use" OS.

So thanks for the replies I'll try what's been said here. Thanks.

---

### Post by iTheBadGuy on 2010-06-17
I'm not getting this.. It's saying my Interface is down (eth0) but it isn't. I'm positive its not. So can someone please tell me what the **** is going on? I'm seriously getting frustrated with this..

EDIT: BTW it says under "Network connections" Auto eth0: Last Used: Never. huh? I'm using it right now.. -_-'

---

### Post by iTheBadGuy on 2010-06-17
SERIOUSLY! How hard can this be?! dammit! what the heck am i doing wrong? can someone please explain.. is there any other way of sharing media with the Xbox with Ubuntu? because this terminal ushare crap is pissing me off. Is there a GUI version of this? or is this it? is this all there is to it?.

If there isn't a GUI version of this, or even a good step by step tutorial on how to do this, a good one.. not all this crap of "1, 2, 3. You're done!" cuz it's 'a load of crap. I've never been so pissed off in my life.. jesus. I continue to get the same results no matter what I change/do. So can someone seriously just tell me what I'm doing wrong? Changing the port didn't work. Changing the name of my interface/connection didn't work. I checked under System > Administration > Network Tools. All I found was that my ethernet was called (eth0). SO why when I start uShare the first hting I see is "Interface eth0 is down. Please recheck settings and try again" WTF?!

Now it doesn't even appear on my Xbox that uShare is trying to share media. Before it would show and then say that it had firewall problems. THIS IS RIDICULOUS! Why is this so freaking complicated?. dammit!. Someone just please post a solution?..

---

### Post by EllisDeeInMe on 2010-06-18
i dunno but mine says the same thing that eth0 is down, but sharing still works with my xbox.

---

### Post by EllisDeeInMe on 2010-06-19
Try putting a yes after the USHARE_OVERRIDE_ICONV_ERR=yes and add this to the beginning of the file after the comments USHARE_OPTIONS=-x.

---

### Post by quattroman on 2010-07-21
try this command on terminal
```

sudo dpkg-reconfigure ushare
```

This will guide you through the entire configuration, when it gets to the network adapter it will give you all your options available.

:popcorn:

---

### Post by smokes2345 on 2010-08-12
After my xbox was complaining about a firewall, I was able to get my xbox working by disabling the dlna profile.  starting ushare by hand, it still says eth0 is down, but it still works.

---

### Post by lbaxter on 2010-10-03
Yep, starting ushare by hand did the trick for me.

ushare -n Name -i eth1 -x -c directory

Complained about the adapter being down too. So there's definitely a bug in logic. More likely then not, the output changed with 10.4 and instead of getting eth1. It's output is probably being returned with a few extra characters. Or a big fat null, either will make it puke.

Going to the ushare site, it looks like the program is going to die. Time to move onto something being supported.

---

### Post by jester13 on 2010-12-27
Just wanted to let everyone know what resolved this issue for me.  I was having the exact same issue as the poster.  I installed ushare via synaptic, updated my ushare.conf file and then started the service.  Upon attempting to connect with my 360 I received the "firewall" error.

The changes I made to the ushare.conf file consisted of the enablement of web interface, xbox and dlna.  Also, I of course updated the USHARE_DIR parameter.

As smokes2345 posted, disabling the dlna option fixed this issue for me as well.  I am still however starting the service via init.d or service.  I had dlna enabled because I also have a ps3, but the ps3 is still streaming media fine with dlna disabled.

This is strange, since I just migrated from my old computer running 10.04 to a new computer with a fresh install of 10.04 and ushare with dlna enabled on the old computer was working fine with xbox.  Oh well.

---

