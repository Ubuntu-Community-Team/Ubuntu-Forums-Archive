---
title: "Off to a rocky start..."
date: 2009-08-26
forum: Multimedia Software
---

### Post by rmp5s on 2009-08-26
Hello everyone!  After contemplating it for a week or so, I installed Ubuntu NBR on my HP Mini 1030NR last night!  (Bye bye, Windows!)  I booted from the thumb drive to try it out for quite some time and REALLY liked it.  I still do.  It runs great!  Surfing the net is CRAZY fast...just the way I like it.  But...I'm having a VERY major problem.

I have NO streaming media!!!  No youtube, no pandora, no google videos, no nothin!  Beings as surfing the web looking at random vids and listening to Pandora is pretty much all I do on this thing, this is a MAJOR issue.

So...today, after reading and trying everything I could find on the matter, and there's a LOT out there, I still have nothin'.  I just completely reinstalled Ubuntu NBR to start from scratch.  I need some PROFESSIONAL HELP THOUGH!  I'm really new to the Linux world so dealing with problems is rough.  I'm actually an IT professional (networking for the United States Marines...and we use command lines aaaaall day so don't be afraid to hit me with code!  I can take it!  lol) but only deal with windows.  So...if anyone can help get this problem sorted out for me, I would REALLY appreciate it.

Background:

Before the re-install, I installed all the codecs I could find in an attempt to make the sites I use often work.  I tried following this:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

...and the output I get after entering the command **sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update** is as follows:

```
rmp5s@rmp5s:~$ sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
[sudo] password for rmp5s: 
[sudo] password for rmp5s: 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty Release.gpg
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/main Translation-en_US
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security Release.gpg
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/main Translation-en_US
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty Release.gpg
Ign [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty/free Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security Release
Ign [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty/non-free Translation-en_US
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty Release
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty Release
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates Release
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/main Packages
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty/free Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/main Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/restricted Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/main Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/restricted Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/universe Packages
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty/non-free Packages
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty/free Sources
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty/non-free Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/main Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/universe Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/universe Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/universe Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/multiverse Sources
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security Release.gpg
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/main Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty Release.gpg
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/main Translation-en_US
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty Release.gpg
Ign [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty/free Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security Release
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/multiverse Translation-en_US
Ign [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty/non-free Translation-en_US
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty Release
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty Release
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates Release
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/main Packages
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty/free Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/main Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/main Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/restricted Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/restricted Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/main Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/restricted Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/universe Packages
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty/non-free Packages
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty/free Sources
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty/non-free Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/universe Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/universe Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/restricted Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/universe Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/multiverse Sources
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
rmp5s@rmp5s:~$
```

Being new to this, I have pretty much no idea how to interpret this output so any help would be appreciated...lol

---

### Post by lisati on 2009-08-27
First suggestion from me: make sure that the update window is closed and try again.

---

### Post by rmp5s on 2009-08-27
> **lisati said:**
> First suggestion from me: make sure that the update window is closed and try again.

Alright.  I did so and this is what I got:

```
rmp5s@rmp5s:~$ sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
[sudo] password for rmp5s: 
--2009-08-27 06:59:59--  http://www.medibuntu.org/sources.list.d/jaunty.list
Resolving www.medibuntu.org... 87.98.242.110
Connecting to www.medibuntu.org|87.98.242.110|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 280 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[===================================================================================>] 280         --.-K/s   in 0s      

2009-08-27 06:59:59 (2.52 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [280/280]

Hit http://security.ubuntu.com jaunty-security Release.gpg
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Hit http://us.archive.ubuntu.com jaunty Release.gpg
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US
Hit http://packages.medibuntu.org jaunty Release.gpg
Ign http://packages.medibuntu.org jaunty/free Translation-en_US
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release
Get:1 http://us.archive.ubuntu.com jaunty-updates Release.gpg [189B]
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_US
Hit http://packages.medibuntu.org jaunty Release
Hit http://us.archive.ubuntu.com jaunty Release
Get:2 http://us.archive.ubuntu.com jaunty-updates Release [49.6kB]
Hit http://security.ubuntu.com jaunty-security/main Packages
Hit http://packages.medibuntu.org jaunty/free Packages
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://packages.medibuntu.org jaunty/non-free Packages
Hit http://packages.medibuntu.org jaunty/free Sources
Hit http://packages.medibuntu.org jaunty/non-free Sources
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty/main Packages
Hit http://us.archive.ubuntu.com jaunty/restricted Packages
Hit http://us.archive.ubuntu.com jaunty/main Sources
Hit http://us.archive.ubuntu.com jaunty/restricted Sources
Hit http://us.archive.ubuntu.com jaunty/universe Packages
Hit http://us.archive.ubuntu.com jaunty/universe Sources
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources
Get:3 http://us.archive.ubuntu.com jaunty-updates/main Packages [160kB]
Get:4 http://us.archive.ubuntu.com jaunty-updates/restricted Packages [2589B]
Get:5 http://us.archive.ubuntu.com jaunty-updates/main Sources [44.9kB]
Get:6 http://us.archive.ubuntu.com jaunty-updates/restricted Sources [623B]
Get:7 http://us.archive.ubuntu.com jaunty-updates/universe Packages [54.0kB]
Get:8 http://us.archive.ubuntu.com jaunty-updates/universe Sources [14.9kB]
Get:9 http://us.archive.ubuntu.com jaunty-updates/multiverse Packages [6637B]
Get:10 http://us.archive.ubuntu.com jaunty-updates/multiverse Sources [2117B]
Fetched 336kB in 4s (73.4kB/s)
Reading package lists...
W: Duplicate sources.list entry http://packages.medibuntu.org jaunty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-i386_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org jaunty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists...
Building dependency tree...
Reading state information...
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  medibuntu-keyring
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 3448B of archives.
After this operation, 49.2kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Authentication warning overridden.
Get:1 http://packages.medibuntu.org jaunty/free medibuntu-keyring 2008.04.20 [3448B]
Fetched 3448B in 0s (4521B/s)
Selecting previously deselected package medibuntu-keyring.
(Reading database ... 120137 files and directories currently installed.)
Unpacking medibuntu-keyring (from .../medibuntu-keyring_2008.04.20_all.deb) ...
Setting up medibuntu-keyring (2008.04.20) ...
OK

Hit http://security.ubuntu.com jaunty-security Release.gpg
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com jaunty Release.gpg
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US
Hit http://packages.medibuntu.org jaunty Release.gpg
Ign http://packages.medibuntu.org jaunty/free Translation-en_US
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Hit http://packages.medibuntu.org jaunty Release
Hit http://us.archive.ubuntu.com jaunty Release
Hit http://us.archive.ubuntu.com jaunty-updates Release
Hit http://security.ubuntu.com jaunty-security/main Packages
Hit http://packages.medibuntu.org jaunty/free Packages
Hit http://us.archive.ubuntu.com jaunty/main Packages
Hit http://us.archive.ubuntu.com jaunty/restricted Packages
Hit http://us.archive.ubuntu.com jaunty/main Sources
Hit http://us.archive.ubuntu.com jaunty/restricted Sources
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://packages.medibuntu.org jaunty/non-free Packages
Hit http://packages.medibuntu.org jaunty/free Sources
Hit http://packages.medibuntu.org jaunty/non-free Sources
Hit http://us.archive.ubuntu.com jaunty/universe Packages
Hit http://us.archive.ubuntu.com jaunty/universe Sources
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Reading package lists...
rmp5s@rmp5s:~$ 
```

Is that what it was supposed to do?  lol

---

### Post by rmp5s on 2009-08-28
Well...it works.  Everything works PERFECT now.  Dunno if it was that or not (99% sure I did that the other day...) but hey...it works and that's all I care about.  Thanks!!!

---

### Post by ad_267 on 2009-08-28
You don't usually need the Medibuntu repositories, just install the ubuntu-restricted-extras package. That will give you flash, mp3 and anything else you would need.

---

