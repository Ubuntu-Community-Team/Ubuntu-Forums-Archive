---
title: "Problems after apt-get upgrade"
date: 2014-09-19
forum: Mythbuntu
---

### Post by mattlach on 2014-09-19
Hey all,

Did my ~monthly 14.04 Mythbuntu backend drive image and package upgrade yesterday, and was actually forced to roll back to the image for the first time since installing myhtbuntu.

After the upgrade I had a constant runaway mythbackend process at 100% CPU, frequent frontend disconnects while watching live tv, as well as an unresponsive mythweb.

These were the packages that updated:

```

The following packages will be upgraded:
  apport apport-gtk apport-noui apt apt-transport-https apt-utils
  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg-extra curl
  exo-utils flashplugin-installer gcc-4.9-base gir1.2-gudev-1.0
  gir1.2-javascriptcoregtk-3.0 gir1.2-webkit-3.0 irqbalance
  libapache2-mod-php5 libapt-inst1.5 libapt-pkg4.12 libc-bin libc-dev-bin
  libc6 libc6-dbg libc6-dev libcups2 libcupsimage2 libcurl3 libcurl3-gnutls
  libexo-1-0 libexo-common libexo-helpers libgcc1 libgcrypt11 libgudev-1.0-0
  libharfbuzz-icu0 libharfbuzz0b libjavascriptcoregtk-3.0-0 libnss3 libnss3-1d
  libnss3-nssdb libpam-systemd libsystemd-daemon0 libsystemd-login0 libudev1
  libwebkitgtk-3.0-0 libwebkitgtk-3.0-common lightdm-gtk-greeter
  linux-firmware linux-libc-dev multiarch-support mythbuntu-bare-client php5
  php5-cli php5-common php5-mysql php5-readline python3-apport
  python3-distupgrade python3-problem-report rsyslog systemd-services
  ubuntu-drivers-common ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk udev xserver-common xserver-xorg-core
  xserver-xorg-video-intel
69 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Since I am not sure what caused the problem, I don't think I am at a stage where I can file a bug yet.

Has anyone else had problems?  Any thoughts what could be going on?

---

### Post by mattlach on 2014-10-08
Just tried upgrading again, after rolling back, same thing, almost immediately upon starting playback, I get a runaway 100% mythbackend process.

When this happens, Mythweb loads the main page, but pressing "status" link never brings up anything.

So frustrated with this.

Has anyone else had this problem?

I'm wondering if it is related to [this issue](http://forum.xbmc.org/showthread.php?tid=150334).

Anyone?

---

### Post by mattlach on 2014-10-08
When this happens, the log seems spammed with these, whatever they mean:

```

Oct  8 20:27:35 myth mythbackend: mythbackend[1867]: E TVRecEvent mythdbcon.cpp:839 (prepare) Driver error was [2/144]:#012QMYSQL3: Unable to prepare statement#012Database error was:#012Table './mythconverg/recordedseek' is marked as crashed and last (automatic?) repair failed
Oct  8 20:27:35 myth mythbackend: mythbackend[1867]: E TVRecEvent mythdb.cpp:183 (DBError) DB Error (delta position map insert):#012Query was:#012INSERT INTO recordedseek (chanid, starttime, mark, type, offset)  VALUES ( :CHANID , :STARTTIME , :MARK , :TYPE , :OFFSET )#012Bindings were:#012:CHANID=1508, :MARK=32200, :OFFSET=925950196, :STARTTIME=2014-10-09T00:18:28Z,#012:TYPE=9#012Driver error was [2/1064]:#012QMYSQL: Unable to execute query#012Database error was:#012You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':CHANID , :STARTTIME , :MARK , :TYPE , :OFFSET )' at line 1
Oct  8 20:27:35 myth mythbackend: mythbackend[1867]: E TVRecEvent mythdbcon.cpp:837 (prepare) Error preparing query: INSERT INTO recordedseek (chanid, starttime, mark, type, offset)  VALUES ( :CHANID , :STARTTIME , :MARK , :TYPE , :OFFSET )
Oct  8 20:27:35 myth mythbackend: mythbackend[1867]: E TVRecEvent mythdbcon.cpp:839 (prepare) Driver error was [2/144]:#012QMYSQL3: Unable to prepare statement#012Database error was:#012Table './mythconverg/recordedseek' is marked as crashed and last (automatic?) repair failed
Oct  8 20:27:35 myth mythbackend: mythbackend[1867]: E TVRecEvent mythdb.cpp:183 (DBError) DB Error (delta position map insert):#012Query was:#012INSERT INTO recordedseek (chanid, starttime, mark, type, offset)  VALUES ( :CHANID , :STARTTIME , :MARK , :TYPE , :OFFSET )#012Bindings were:#012:CHANID=1508, :MARK=32200, :OFFSET=537220, :STARTTIME=2014-10-09T00:18:28Z,#012:TYPE=33#012Driver error was [2/1064]:#012QMYSQL: Unable to execute query#012Database error was:#012You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':CHANID , :STARTTIME , :MARK , :TYPE , :OFFSET )' at line 1

```

---

### Post by neutron68 on 2014-10-09
I want to THANK YOU the warning!  I don't like to be blindsided by poison updates!

I'm also curious what software you use to do a drive image?

Eric

---

### Post by tgm4883 on 2014-10-09
> **mattlach said:**
> When this happens, the log seems spammed with these, whatever they mean:

```

Oct  8 20:27:35 myth mythbackend: mythbackend[1867]: E TVRecEvent mythdbcon.cpp:839 (prepare) Driver error was [2/144]:#012QMYSQL3: Unable to prepare statement#012Database error was:#012Table './mythconverg/recordedseek' is marked as crashed and last (automatic?) repair failed
Oct  8 20:27:35 myth mythbackend: mythbackend[1867]: E TVRecEvent mythdb.cpp:183 (DBError) DB Error (delta position map insert):#012Query was:#012INSERT INTO recordedseek (chanid, starttime, mark, type, offset)  VALUES ( :CHANID , :STARTTIME , :MARK , :TYPE , :OFFSET )#012Bindings were:#012:CHANID=1508, :MARK=32200, :OFFSET=925950196, :STARTTIME=2014-10-09T00:18:28Z,#012:TYPE=9#012Driver error was [2/1064]:#012QMYSQL: Unable to execute query#012Database error was:#012You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':CHANID , :STARTTIME , :MARK , :TYPE , :OFFSET )' at line 1
Oct  8 20:27:35 myth mythbackend: mythbackend[1867]: E TVRecEvent mythdbcon.cpp:837 (prepare) Error preparing query: INSERT INTO recordedseek (chanid, starttime, mark, type, offset)  VALUES ( :CHANID , :STARTTIME , :MARK , :TYPE , :OFFSET )
Oct  8 20:27:35 myth mythbackend: mythbackend[1867]: E TVRecEvent mythdbcon.cpp:839 (prepare) Driver error was [2/144]:#012QMYSQL3: Unable to prepare statement#012Database error was:#012Table './mythconverg/recordedseek' is marked as crashed and last (automatic?) repair failed
Oct  8 20:27:35 myth mythbackend: mythbackend[1867]: E TVRecEvent mythdb.cpp:183 (DBError) DB Error (delta position map insert):#012Query was:#012INSERT INTO recordedseek (chanid, starttime, mark, type, offset)  VALUES ( :CHANID , :STARTTIME , :MARK , :TYPE , :OFFSET )#012Bindings were:#012:CHANID=1508, :MARK=32200, :OFFSET=537220, :STARTTIME=2014-10-09T00:18:28Z,#012:TYPE=33#012Driver error was [2/1064]:#012QMYSQL: Unable to execute query#012Database error was:#012You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':CHANID , :STARTTIME , :MARK , :TYPE , :OFFSET )' at line 1

```

That generally means exactly what it says. 

> Unable to prepare statement#012**Database error was**:#012Table './mythconverg/recordedseek' is **marked as crashed** and last (automatic?)** repair failed**

Basically you need to restore from a backup.

> **neutron68 said:**
> I want to THANK YOU the warning!  I don't like to be blindsided by poison updates!

I'm also curious what software you use to do a drive image?

Eric

Poison updates? I'm running the latest version right now without any issues. As I said above, he has mysql tables that have crashed and needs to restore working ones.

---

### Post by mattlach on 2014-10-09
I suspected a database error at first, but if that is the case, why does the database work just fine when I downgrade the package upgrades again?

Could some package be incompatible with my system causing trouble reading from the database?

After downgrading the same database is going strong...

---

### Post by mattlach on 2014-10-09
> **neutron68 said:**
> I want to THANK YOU the warning!  I don't like to be blindsided by poison updates!

I'm also curious what software you use to do a drive image?

Eric

Well, this particular instance is on a VMWare ESXi server, so its as easy as shutting down the guest and copying the disk image file, but if you are running bare metal, there are plenty of good imaging tools.

Clonezilla is pretty good.   Its a bootable ISO that you can use to image directly to a local drive or via the network using one of a few network protocols.

---

### Post by tgm4883 on 2014-10-10
> **mattlach said:**
> I suspected a database error at first, but if that is the case, why does the database work just fine when I downgrade the package upgrades again?

Could some package be incompatible with my system causing trouble reading from the database?

After downgrading the same database is going strong...

That is really odd. Did you upgrade major mythtv versions?

---

### Post by mattlach on 2014-10-10
> **tgm4883 said:**
> That is really odd. Did you upgrade major mythtv versions?

To my knowledge, no.

Most of the packages updated just look like various system dependencies (see list in first post)

mythbuntu-bare-client IS on that list, but if this is the client, I am not even running it on this machine, as it is a dedicated back end.

---

### Post by mattlach on 2014-10-10
For whatever reason, it seems to happen more when the machine running XBMC with the MythTV PVR plugin is used as a frontend as opposed to the various linux boxes using the official MythTV Linux client.

Is it possible there is some sort of versioning incompatibility and the XBMC PVR plugin is sending malformed sql requests tot he database?  (Does the frontend even communicate directly with the database, or does this go through the backend?)

---

### Post by mattlach on 2014-10-10
> **tgm4883 said:**
> 
Poison updates? I'm running the latest version right now without any issues. As I said above, he has mysql tables that have crashed and needs to restore working ones.


Yeah, I wouldn't go that far either.

MythTV is a tricky one, in that it has a relatively small user base and a relatively large amount of dependencies and hardware combinations in use.

Even in the best of situations devs can't test all combinations before releasing an update (and sometimes they don't even have a choice, like when it comes from the upstream Ubuntu repositories), and this just becomes more convoluted with a release like MythTV.

I am aware this is an issue every time I upgrade packages, so I make a point out of shutting down, imaging the drive and then doing the upgrade, just in case.  (I don't do this on any of my other machines, only the MythTV backend.)

---

### Post by tgm4883 on 2014-10-10
> **mattlach said:**
> For whatever reason, it seems to happen more when the machine running XBMC with the MythTV PVR plugin is used as a frontend as opposed to the various linux boxes using the official MythTV Linux client.

Is it possible there is some sort of versioning incompatibility and the XBMC PVR plugin is sending malformed sql requests tot he database?  (Does the frontend even communicate directly with the database, or does this go through the backend?)

This is entirely possible. The XMBC is made by XBMC people, not MythTV devs.

---

### Post by mattlach on 2014-10-10
> **tgm4883 said:**
> This is entirely possible. The XMBC is made by XBMC people, not MythTV devs.

yep, that is what I was thinking.   My theory is something like XBMC PVR frontend uses some sort of legacy sql requests no longer used by the official frontend, and this update made those no longer work...

Still can't figure out which of the above packages would result in a change to how frontends communicate with the database.  Nothing there (though I admit, I don't know what all of those packages are) seems to directly be related to that process.

---

