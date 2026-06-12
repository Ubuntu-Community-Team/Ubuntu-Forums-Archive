---
title: "Mythbuntu Weekly builds"
date: 2008-02-04
forum: Mythbuntu
---

### Post by ian dobson on 2008-02-04
Hi All,

Are the weekly builds still being run?
I've not seen any updates for my Myth frontend for almost 2 weeks now.

Regards
Ian Dobson

---

### Post by Nikas on 2008-02-04
When are they supposed to be built?

---

### Post by superm1 on 2008-02-04
There have been no significant changes to -fixes, so the focus is on trunk.  Up until 0.21 is released, we're going to hold off on more -fixes builds.

-trunk will continue however, and is entering multiverse for hardy as we speak.

---

### Post by algae105 on 2008-02-05
Hi,

I'm a bit confused.  I've been using mythbuntu's weekly build of the -fixes branch which has worked perfectly for the last few months.  However, today, adept told me an upgrade for the mythtv packages was available and wants to install ' 0.20.99+trunk15758-0ubuntu0~mythbuntu1'.

That looks like my nice, safe 0.20.2-fixes mythtv is going to be upgraded to a trunk build.

Is that to be expected ? I would have thought you should let them release 0.21 before everyone upgrades ;)

Btw, my apt sources list contains what I thought was the -fixes repo :

deb [http://weeklybuilds.mythbuntu.org/mythbuntu/ubuntu](http://weeklybuilds.mythbuntu.org/mythbuntu/ubuntu) gutsy multiverse universe restricted main

Have I done something wrong ?

Regards,
Andrew

---

### Post by Nikas on 2008-02-05
I'm waiting for the Weekly trunk build. When can i expect to see them with apt-get?

---

### Post by algae105 on 2008-02-05
I think that's the point - at the moment, -fixes and -trunk appear to be the same thing.  In fact, -fixes was built from mythtv's SVN yesterday whereas -trunk was last built a few days earlier. 

So if you want a recent 'trunk' build, you could get it from the -fixes weekly build !

---

### Post by algae105 on 2008-02-05
Looks like it was a mistake in the last -weekly autobuild.

Superm1 is doing a rebuild as I write.

Thanks all !

---

### Post by the Goat on 2008-02-05
That is a pretty major mistake.  It hosed my setup no problem.

---

### Post by superm1 on 2008-02-05
sorry for any inconveniences here folks.  Some of the builds got pushed to the wrong PPA when they failed to build.  As soon as we were notified, they were pulled.

For what it's worth though, there is a big warning before it lets you install the packages.

---

### Post by Nikas on 2008-02-05
> **superm1 said:**
> sorry for any inconveniences here folks.  Some of the builds got pushed to the wrong PPA when they failed to build.  As soon as we were notified, they were pulled.

For what it's worth though, there is a big warning before it lets you install the packages.

When can we expect the latests trunk build?
Thanks!

---

### Post by superm1 on 2008-02-06
They should be on the trunk repo now that the fail to build from source is resolved ( took a few manual changes due to upstream changes)

---

### Post by Archmage on 2008-02-06
I'm sorry to bother, but the weekly builds leave a few questions open.

I had been noticed, that I'm now upgrading to 0.2**1**. After I did accept this, should I now switch from the 0.20.2 Fixes Builds to the MythTV Trunk builds in my sources.list?

Furthermore I did notice that MythVideo is not working anymore. Will this be fixed, when I switch to the MythTV Trunk  builds?

---

### Post by Nikas on 2008-02-06
> **superm1 said:**
> They should be on the trunk repo now that the fail to build from source is resolved ( took a few manual changes due to upstream changes)

I don't get any updates when running apt-get update and apt-get ugrade.

---

### Post by superm1 on 2008-02-06
> **Archmage said:**
> I'm sorry to bother, but the weekly builds leave a few questions open.

I had been noticed, that I'm now upgrading to 0.2**1**. After I did accept this, should I now switch from the 0.20.2 Fixes Builds to the MythTV Trunk builds in my sources.list?

Furthermore I did notice that MythVideo is not working anymore. Will this be fixed, when I switch to the MythTV Trunk  builds?
If you are on 0.21, then install the matching plugins.  They are on the same repos as the trunk builds, so yes switch over.  If you want to go back to 0.20.2, a backup of your database was automatically made before the upgrade happened.  You can find that backup in /var.  Once you find that backup, you will be able to drop the database, roll back the version of myth, and then reload the database using that backup.

---

### Post by superm1 on 2008-02-06
> **Nikas said:**
> I don't get any updates when running apt-get update and apt-get ugrade.
I just manually synced the US mirror from the PPA.  It should be on there no issues.

---

### Post by Nikas on 2008-02-06
> **superm1 said:**
> I just manually synced the US mirror from the PPA.  It should be on there no issues.

Okey. I'm using the UK-mirror. I'll change. :)

---

### Post by Nikas on 2008-02-06
MythWeb is buggy in the trunk build i got from apt-get.
I saw on trac that the problems was fixed yesterday.

Can i "install" the newer rev. of mythweb on my own or can we get a new build to the weeklys and install by apt-get?
I'm really new to this.

---

### Post by extasy on 2008-02-06
I second this request, the trunk version as it stands have some problems when it comes to both mythweb plug in and the recording/watching at the same time. After all this time waiting for a weekly it was a bit of a set back.

If the maintainer of this project wold take the time it requires to build a new weekly it would be appreciated a lot!

---

### Post by Nikas on 2008-02-07
Yes. New builds (trunk) would be really nice!

---

### Post by extasy on 2008-02-07
Don't know if this is a bug but it seems to be some problems with the plugin myth dvd and myth video. Only one of them can be installed at the same time. And if myth dvd is installed it does not work and the dvd option in media does not show.

So either it's a problem with the trunk or it's a problem with the build and its dependencies.

---

### Post by extasy on 2008-02-09
Bump

---

### Post by Nikas on 2008-02-10
Got some updates today but not for mythweb or the other plugins. I really need it. Mythweb have some bugs and i use it every day.

---

### Post by superm1 on 2008-02-10
Mythweb's build failed to build the first time around, but should be following sometime today.

---

### Post by Nikas on 2008-02-10
Thanks! Does that apply for the rest of the plugins too?

---

### Post by superm1 on 2008-02-10
> **Nikas said:**
> Thanks! Does that apply for the rest of the plugins too?
Yeah.  If you are on the US mirror, these should be there next time you update your package lists.

---

### Post by Henk Poley on 2008-02-11
Is mythshutdown broken in the current trunk build? I get:

```
2008-02-11 14:33:15.283 I'm idle now... shutdown will occur in 15 seconds.
2008-02-11 14:33:29.762 MainServer::HandleAnnounce Monitor
2008-02-11 14:33:29.772 adding: Oehoe as a client (events: 0)
2008-02-11 14:33:29.774 MainServer::HandleAnnounce Monitor
2008-02-11 14:33:29.774 adding: Oehoe as a client (events: 1)
2008-02-11 14:33:29.818 CheckShutdownServer returned - OK to shutdown
2008-02-11 14:33:29.825 Running the command to set the next scheduled wakeup time :-
						/usr/bin/sudo /usr/bin/mythshutdown --setwakeup 2008-02-11T18:42
mythshutdown: Could not initialize myth context. Exiting.
2008-02-11 14:33:30.143 Running the command to shutdown this computer :-
						/usr/bin/sudo /usr/bin/mythshutdown --shutdown
mythshutdown: Could not initialize myth context. Exiting.
2008-02-11 14:33:32.500 I'm idle now... shutdown will occur in 15 seconds.
```
Ad infinitum

---

### Post by Henk Poley on 2008-02-11
I found out that you now need to add the '-H' option to sudo so it sets the correct $HOME for mythshutdown.

```
/usr/bin/sudo -H /usr/bin/mythshutdown --setwakeup 2008-02-11T18:42
/usr/bin/sudo -H /usr/bin/mythshutdown --shutdown
```

---

### Post by Nikas on 2008-02-18
Just did apt-upgrade on my 7.10 machine (weekly trunk) and things updated but now mythweb does not work because mythweb was missing in the upgrade.

I get Incompatible protocol version (mythweb=39, backend=40).
Really need new builds.

Backend and frontend: 0.21.0~fixes16127-0ubuntu0~mythbuntu1
All the plugins: 0.20.99+trunk15878-0ubuntu0~mythbuntu2

apt-get upgrade cant install libmyth-perl. Tells me that libnet-upnp-perl are broken.

---

### Post by Archmage on 2008-02-19
I have two frontends and one backend.

After the upgrade the backend and one frontend are working, but on the other I'm getting the following information:

```

mythfrontend
2008-02-19 07:42:02.558 Using runtime prefix = /usr, libdir = /usr/lib
2008-02-19 07:42:02.990 XScreenSaver support enabled
2008-02-19 07:42:02.991 DPMS is active.
2008-02-19 07:42:02.992 Empty LocalHostName.
2008-02-19 07:42:02.992 Using localhost value of mythtv-test
2008-02-19 07:42:02.993 Testing network connectivity to 192.168.1.15
2008-02-19 07:42:03.026 New DB connection, total: 1
2008-02-19 07:42:03.036 Connected to database 'mythconverg' at host: 192.168.0.1
2008-02-19 07:42:03.040 Closing DB connection named 'DBManager0'
2008-02-19 07:42:03.040 Total desktop dim: 1600x1200, with 1 screen[s].
2008-02-19 07:42:03.054 Connected to database 'mythconverg' at host: 192.168.0.1
2008-02-19 07:42:03.057 Using screen 0, 1600x1200 at 0,0
2008-02-19 07:42:03.070 New DB connection, total: 2
2008-02-19 07:42:03.079 Connected to database 'mythconverg' at host: 192.168.0.1
2008-02-19 07:42:03.085 Unexpected DB Schema version.  Waiting to see if DB is being upgraded.
2008-02-19 07:42:08.103 Timed out waiting.
2008-02-19 07:42:08.103 This version of MythTV requires an updated database schema. Please run mythtv-setup or mythbackend to update your database.

```

I did restart all the machines, try to upgrade, but the problem still exist.

Is it possible that one of the machines receive a newer package that has been withdrawn later?

---

### Post by ian dobson on 2008-02-19
Hi,

Have you tried running mythtv-setup on your backend?

Regards
Ian Dobson

---

### Post by Archmage on 2008-02-19
> **ian dobson said:**
> Have you tried running mythtv-setup on your backend?

I can start mythtv-setup. However after leaving the program I still can't connect from my frontend on the backend.

---

### Post by dannyboy79 on 2008-02-20
> **Archmage said:**
> I have two frontends and one backend.

After the upgrade the backend and one frontend are working, but on the other I'm getting the following information:

```

mythfrontend
2008-02-19 07:42:02.558 Using runtime prefix = /usr, libdir = /usr/lib
2008-02-19 07:42:02.990 XScreenSaver support enabled
2008-02-19 07:42:02.991 DPMS is active.
2008-02-19 07:42:02.992 Empty LocalHostName.
2008-02-19 07:42:02.992 Using localhost value of mythtv-test
2008-02-19 07:42:02.993 Testing network connectivity to 192.168.1.15
2008-02-19 07:42:03.026 New DB connection, total: 1
2008-02-19 07:42:03.036 Connected to database 'mythconverg' at host: 192.168.0.1
2008-02-19 07:42:03.040 Closing DB connection named 'DBManager0'
2008-02-19 07:42:03.040 Total desktop dim: 1600x1200, with 1 screen[s].
2008-02-19 07:42:03.054 Connected to database 'mythconverg' at host: 192.168.0.1
2008-02-19 07:42:03.057 Using screen 0, 1600x1200 at 0,0
2008-02-19 07:42:03.070 New DB connection, total: 2
2008-02-19 07:42:03.079 Connected to database 'mythconverg' at host: 192.168.0.1
2008-02-19 07:42:03.085 Unexpected DB Schema version.  Waiting to see if DB is being upgraded.
2008-02-19 07:42:08.103 Timed out waiting.
2008-02-19 07:42:08.103 This version of MythTV requires an updated database schema. Please run mythtv-setup or mythbackend to update your database.

```

I did restart all the machines, try to upgrade, but the problem still exist.

Is it possible that one of the machines receive a newer package that has been withdrawn later?

what are the ip's of all the machines? the frontend isn't trying to connect to itself is it? normally 192.168.0.1 is your router's ip. also, you didn't accidentally put a backend on the frontend that isn't working did you? just throwing things out there to try to help.

---

### Post by Archmage on 2008-02-21
> **dannyboy79 said:**
> what are the ip's of all the machines? the frontend isn't trying to connect to itself is it? normally 192.168.0.1 is your router's ip. also, you didn't accidentally put a backend on the frontend that isn't working did you? just throwing things out there to try to help.

Sorry, this was a copy & paste problem. I did accidently insert the ip of my machine (192.168.1.15) into the quote. There should stand 192.168.0.1 as well.

My MythTV-Backend is also my router under the IP 192.168.0.1.

Question: Is it possibile that the AMD64 and the normal build have different versions? After a upgrade now also my other machine also can't connect to my backend anymore. :(

---

### Post by superm1 on 2008-02-21
The weekly builds: no.  The 8.04 Alpha2 images: yes.  They were built ~1 week apart.  You should be able to update both though and get up to a current version.

---

### Post by Archmage on 2008-02-22
I did solve the problem. The US-Mirror and UK-Mirror seem to have different versions at the time I did update. Therefore I received the different versions. Now everything is working.

---

### Post by Termina on 2008-03-03
I'm running Hardy 8.04 latest with all updates.

I have mythtv running on a 7.10 box. Other clients can use it (including a Mac OSX iBook) but not mine.

Hardy's mythfrontend is apparently unable to connect to older versions... which is pretty lame for a client. Is there a workaround?

I'm betting if I upgrade the backend to 8.04 OSX and 7.10 clients will break, so that isn't an option.

---

### Post by dannyboy79 on 2008-03-04
you can't mix and match mythtv versions. either upgrade all frontends and backends or NONE. that's what I have read on the mythtv mailing list plenty of times. there's a way to easily backup your database though, save it in a safe place, upgrade all mythtv machines, then on the new backend just use the backed up database and you should be golden. I think you'll have to reset up mythtv backend to point to where your recordings are IF it's different than /var/lib/mythtv/recordings/. you can google it and find the best way to upgrade mythtv

---

### Post by Archmage on 2008-03-04
(Again) I'm runing into some problems. :(

```
mythtv@2nd:~$ mythfrontend
2008-03-04 18:39:43.067 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-04 18:39:43.928 XScreenSaver support enabled
2008-03-04 18:39:43.929 DPMS is active.
2008-03-04 18:39:44.164 Empty LocalHostName.
2008-03-04 18:39:44.165 Using localhost value of 800
2008-03-04 18:39:44.647 New DB connection, total: 1
2008-03-04 18:39:44.957 Connected to database 'mythconverg' at host: 192.168.0.1
2008-03-04 18:39:44.964 Closing DB connection named 'DBManager0'
2008-03-04 18:39:44.965 Total desktop dim: 1280x1024, with 1 screen[s].
2008-03-04 18:39:45.143 Connected to database 'mythconverg' at host: 192.168.0.1
2008-03-04 18:39:45.179 Using screen 0, 1280x1024 at 0,0
Illegal instruction (core dumped)
myththv@2nd:~$
```

Anyone have an idea what this could be and how I could fix it?

---

### Post by SishGupta on 2008-03-12
> **Archmage said:**
> (Again) I'm runing into some problems. :(

```
mythtv@2nd:~$ mythfrontend
2008-03-04 18:39:43.067 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-04 18:39:43.928 XScreenSaver support enabled
2008-03-04 18:39:43.929 DPMS is active.
2008-03-04 18:39:44.164 Empty LocalHostName.
2008-03-04 18:39:44.165 Using localhost value of 800
2008-03-04 18:39:44.647 New DB connection, total: 1
2008-03-04 18:39:44.957 Connected to database 'mythconverg' at host: 192.168.0.1
2008-03-04 18:39:44.964 Closing DB connection named 'DBManager0'
2008-03-04 18:39:44.965 Total desktop dim: 1280x1024, with 1 screen[s].
2008-03-04 18:39:45.143 Connected to database 'mythconverg' at host: 192.168.0.1
2008-03-04 18:39:45.179 Using screen 0, 1280x1024 at 0,0
Illegal instruction (core dumped)
myththv@2nd:~$
```Anyone have an idea what this could be and how I could fix it?

I have this exact same problem. I am using 8.04 fully updated. I also had the isue in 7.10 when using mythtv 0.21.

The frustrating thing is that I am seemingly unable to find a solution from google or the mythtv site.

---

### Post by superm1 on 2008-03-12
Gah... another CPU that got bit by optimization?  Are you *sure* you have the most up to date build?  It's optimized to i686 which should cover a majority of the CPUs in use....

can you post /proc/cpuinfo?

---

### Post by SishGupta on 2008-03-12
```

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 4
model name      : AMD Athlon(TM)Processor
stepping        : 4
cpu MHz         : 1424.618
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow up
bogomips        : 2851.29
clflush size    : 32

```Thats my proc. But I am not sure that it matters.
It seems to be the nvidia proprietary drivers that are causing the problem. If i switch to nv, things work fine (except graphical things are sloooow)

> sishgupta@fxserver:~$ cat /etc/X11/xorg.conf.backup
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Tue Mar  4 20:24:34 UTC 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc101"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1024x768 +0+0"
EndSection
This is just the default xorg.conf that i get when installing the nvidia-glx-new driver through the restricted drivers manager.
This worked in the past but does not now with 0.21. I have whatever build is in the hardy repos.

Ive been working on this problem for like 4 hours and its way way later than i wanted to be up (its 4am).

Ill be back tomorrow.

---

### Post by superm1 on 2008-03-12
Hm crashing w/ nvidia-glx you say?

Try turning off OpenGL theme painter if it's on.  That might be taking you down.  Look for errors in your Xorg.0.log as well.

---

### Post by SishGupta on 2008-03-12
Thanks for your help superm1.

So I figured out eventually that while using the nvidia proprietary driver all ogl appls would get an illegal instruction.

This thread tells you why:
[http://www.nvnews.net/vbulletin/showthread.php?t=104914](http://www.nvnews.net/vbulletin/showthread.php?t=104914)

Summary:
Basically you need SSE to run the 169.xx series nvidia drivers. My old athlon was born in an age before AMD used the SSE instruction sets.

I am not sure why I had a problem with 0.21 on gutsy. I am not even sure what driver I was using then.

Anyway I am going to install nvidia 96.xx from envy and see how that plays out. 
Edit: Yeah, all is well now. =D

Sorry for gumming up this thread with a problem that is seemingly unrelated to mythtv.

---

### Post by sdavies9574 on 2008-04-01
> **SishGupta said:**
> I have this exact same problem. I am using 8.04 fully updated. I also had the isue in 7.10 when using mythtv 0.21.

The frustrating thing is that I am seemingly unable to find a solution from google or the mythtv site.

I am seeing this same thing, but I don't have NVidia graphics.  My system is a VIA epia mb with the onboard graphics (CLE266).  The system has chosen the openchrome driver for me and it seems to be working fine as far as I can tell.  I can't find any hints as to what this problem is in any logs, verbose output from mythfrontend, etc.


```
proc/cpuinfo:
processor	: 0
vendor_id	: CentaurHauls
cpu family	: 6
model		: 7
model name	: VIA Samuel 2
stepping	: 3
cpu MHz		: 399.000
cache size	: 64 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu de tsc msr cx8 mtrr pge mmx 3dnow up
bogomips	: 801.73
clflush size	: 32
```


```
xorg.conf:
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

---

### Post by jb5 on 2008-06-21
Is there a resource/web page that details what was fixed in the weekly build?

---

### Post by pelago on 2008-06-22
> **jb5 said:**
> Is there a resource/web page that details what was fixed in the weekly build?

Yes, I was about to post the exact same thing. Is there a changelog we can look at for each fixes release to see what's new/fixed?

---

### Post by sgunther on 2008-06-22
To see what is changing....

```
dpkg -s mythtv | grep Version
```

The latest as of today is;

> Version: 0.21.0+fixes17490-0ubuntu0+mythbuntu1

So in this case look for Changeset 17490.

Then in your web browser go to; [http://svn.mythtv.org/trac/timeline?from=06%2F22%2F08&daysback=10&changeset=on&milestone=on&wiki=on&update=Update](http://svn.mythtv.org/trac/timeline?from=06%2F22%2F08&daysback=10&changeset=on&milestone=on&wiki=on&update=Update)

You can see the change history.  Note: Some of the changes listed are for trunk and some are for the fixes-021 branch.  Depending on which weekly build you are syncing to look accordingly.

---

### Post by mat1t on 2008-07-07
I know this is an old thread, but it has the same title that I would have used so I figured re-using it would be the best! :)

What's the status of weekly builds on 21-fixes at the moment? I've recently purchased a freesat card, and there's a quite a few freesat fixes in the [latest revisions]("http://svn.mythtv.org/trac/changeset?old_path=%2Fbranches%2Frelease-0-21-fixes&old=17490&new_path=%2Fbranches%2Frelease-0-21-fixes&new=17724").

Are they stopped at the moment?

Thanks
Mat

---

### Post by mrand on 2008-07-07
> **mat1t said:**
> I know this is an old thread, but it has the same title that I would have used so I figured re-using it would be the best! :)

What's the status of weekly builds on 21-fixes at the moment? I've recently purchased a freesat card, and there's a quite a few freesat fixes in the [latest revisions]("http://svn.mythtv.org/trac/changeset?old_path=%2Fbranches%2Frelease-0-21-fixes&old=17490&new_path=%2Fbranches%2Frelease-0-21-fixes&new=17724").

Are they stopped at the moment?
Howdy Mat,

I did a fresh install on July 4th and it was at 17416.  Give them another week or three and I'll bet it will be past the version you need.

[INDENT]  Marc[/INDENT]

---

### Post by laga on 2008-07-07
I'm extremely busy at the moment and I'm usually not near the computer which has all the tools for the weekly builds. I'll try to get to it ASAP, but it might take another week.

---

### Post by mat1t on 2008-07-07
> **laga said:**
> I'm extremely busy at the moment and I'm usually not near the computer which has all the tools for the weekly builds. I'll try to get to it ASAP, but it might take another week.

That's ok, I was just wondering what the status of them was. Is it something that's likely to be a candidate for automation (such as integrating it with the PPA system on ubuntu) or is there a manual process with it?

Cheers,
Mat

---

### Post by Archmage on 2008-09-03
Thanks for the latest update. I was having problems, since the EIT-scan seems not to update in time, but after the update this seems to work (again).

If this hasn't anything to do with the update, I'm still happy with my Mythbutun. :)

---

