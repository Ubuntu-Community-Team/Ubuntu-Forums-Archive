---
title: "Where is minidlna package for Ubuntu 14.04"
date: 2014-04-18
forum: Multimedia Software
---

### Post by drpaneas on 2014-04-18
Hi there,

I want to install the mini-dlna 
link: [https://help.ubuntu.com/community/MiniDLNA](https://help.ubuntu.com/community/MiniDLNA)

but the:
```
drpaneas@ubuntupc:~$ sudo apt-get install minidlna
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package minidlna


```
doesn't do the job.

I did a quick search into the repos and...
```
drpaneas@ubuntupc:~$ sudo apt-cache search dlna
dleyna-renderer - DBus service to interact with DLNA Digital Media Renderers
dleyna-renderer-dbg - DBus service to interact with DLNA Digital Media Renderers (debug files)
dleyna-server - DBus service to interact with DLNA Digital Media Servers
dleyna-server-dbg - DBus service to interact with DLNA Digital Media Servers (debug files)
gir1.2-gupnpdlna-2.0 - GObject introspection data for the DLNA utility library for GUPnP
gnome-music - Music is the new GNOME music playing application
gupnp-dlna-tools - GObject-based library for GUPnP DLNA (tools)
kipi-plugins - image manipulation/handling plugins for KIPI aware programs
libdleyna-connector-dbus-1.0-1 - DBus connector module for the dLeyna services
libdleyna-connector-dbus-1.0-dbg - DBus connector module for the dLeyna services (debug files)
libdleyna-core-1.0-3 - Utility functions for higher level dLeyna components
libdleyna-core-1.0-dbg - Utility functions for higher level dLeyna components (debug files)
libdleyna-core-1.0-dev - Utility functions for higher level dLeyna components (development files)
libdlna-dev - development files for libdlna
libdlna0 - DLNA codec library
libgupnp-dlna-2.0-3 - DLNA utility library for GUPnP
libgupnp-dlna-2.0-dbg - DLNA utility library for GUPnP (debug symbols)
libgupnp-dlna-2.0-dev - DLNA utility library for GUPnP (development files)
libgupnp-dlna-doc - DLNA utility library for GUPnP (documentation)
librygel-core-2.0-1 - GNOME UPnP/DLNA services - core library
librygel-renderer-2.0-1 - GNOME UPnP/DLNA services - renderer library
librygel-renderer-gst-2.0-1 - GNOME UPnP/DLNA services - renderer library
librygel-server-2.0-1 - GNOME UPnP/DLNA services - server library
rygel - GNOME UPnP/DLNA services
rygel-2.0-dev - GNOME UPnP/DLNA services - plugin development files
rygel-dbg - GNOME UPnP/DLNA services
rygel-gst-launch - GNOME UPnP/DLNA services - gst-launch plugin
rygel-mediathek - GNOME UPnP/DLNA services - Mediathek plugin
rygel-playbin - GNOME UPnP/DLNA services - GStreamer Media Renderer plugin
rygel-preferences - GNOME UPnP/DLNA services - preferences tool
rygel-tracker - GNOME UPnP/DLNA services - Tracker plugin
totem-plugins-extra - Extra plugins for the Totem media player
upnp-inspector - Python UPnP framework analyser


```

it doesn't seem to be a dlna version of Ubuntu 14.04 so far. Do we know when will be available ?
At the Launchpad website the status seems to be "Deleted" ( chech this out: [https://launchpad.net/ubuntu/trusty/amd64/minidlna/1.0.24+dfsg-1](https://launchpad.net/ubuntu/trusty/amd64/minidlna/1.0.24+dfsg-1) )

Any ideas would be greatly appreciated.

Danke,
Panos

---

### Post by Clickbg on 2014-04-18
Hi I submitted a bug report for this one since in fact there is no practical workaround at the time. Please check in and mark that it also affects you - [https://bugs.launchpad.net/ubuntu/+source/minidlna/+bug/1309651](https://bugs.launchpad.net/ubuntu/+source/minidlna/+bug/1309651)

Here is a temporary fix. Please note that the package installation sequence is important:

```

  wget http://dk.archive.ubuntu.com/ubuntu/pool/universe/m/minidlna/minidlna_1.0.21+dfsg-1ubuntu1_amd64.deb
  wget http://security.ubuntu.com/ubuntu/pool/main/liba/libav/libavformat53_0.8.10-0ubuntu0.12.04.1_amd64.deb
  wget http://security.ubuntu.com/ubuntu/pool/main/liba/libav/libavcodec53_0.8.10-0ubuntu0.12.04.1_amd64.deb
  wget http://security.ubuntu.com/ubuntu/pool/main/liba/libav/libavutil51_0.8.10-0ubuntu0.12.04.1_amd64.deb


  dpkg -i libavutil51_0.8.10-0ubuntu0.12.04.1_amd64.deb
  dpkg -i libavcodec53_0.8.10-0ubuntu0.12.04.1_amd64.deb
  dpkg -i libavformat53_0.8.10-0ubuntu0.12.04.1_amd64.deb
  dpkg -i minidlna_1.0.21+dfsg-1ubuntu1_amd64.deb

```

Also remember that you will have to remove those packages after MiniDLNA is returned on the repo.

---

### Post by haraldgraeber on 2014-04-19
Hi Clickbg,


thanks a lot, you´re the hero! For my complete home media streaming I fully rely on MiniDLNA and I was terrified after I couldn´t find my MiniDLNA server after the upgrade to Lubuntu 14.04. The temp fix you provided works also for my i386 platform; I just replaced the string 'amd64' with 'i386' in all lines and it´s back up and running now just like before in 13.10.

As you suggested, I flagged your launchpad bug report that the bug also affects my and like to encourage other affected users to please do the same.

Cheers,

---

### Post by dummy76 on 2014-04-20
Hello,

i've tried to install it also, but one package was missing:

```
sudo dpkg -i minidlna_1.0.21+dfsg-1ubuntu1_i386.deb
Selecting previously unselected package minidlna.
(Reading database ... 91587 files and directories currently installed.)
Preparing to unpack minidlna_1.0.21+dfsg-1ubuntu1_i386.deb ...
Unpacking minidlna (1.0.21+dfsg-1ubuntu1) ...
dpkg: dependency problems prevent configuration of minidlna:
 minidlna depends on **libid3tag0 **(>= 0.15.1b); however:
  Package libid3tag0 is not installed.


dpkg: error processing package minidlna (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 minidlna

```

after install libid3tag0 then i was able to install minidlna.

my version:

```
lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04 LTS
Release:        14.04
Codename:       trusty

```

thanks for the install procedure :)

---

### Post by TaBaScO77 on 2014-04-20
I had the same problem.  Everyone in my family and all the TVs in my house connect to my Ubuntu server for DLNA video.  I love minidlna!  How frustrating.  Thankfully my server is a VM, and I took a snapshot just before I upgraded to 14.04.  I just now reverted to the old snapshot.  I'll just keep using Ubuntu 13 until they fix this problem.  I would rather just do that than mess with a workaround.  I'll definitely keep following this thread to find out when it's added to the 14.04 repos.

---

### Post by pablosquared on 2014-04-21
Thanks for the workaround, Clickbg.

This issue is really disappointing for such a high profile distribution, IMHO. I also use DLNA to stream media around the network - under Quantal, I used ps3mediaserver which doesn't work under Trusty because ffmpeg has been deprecated. And now I find minidlna, which I've also used in the past, doesn't yet have a Trusty version. 

I tried tvmobili, but it's a licensed product and the cost of a license isn't reaslistic (again, IMHO). So, when I want to stream media. I'm booting Quantal for the time being.

---

### Post by johnaaronrose on 2014-04-23
I've just done a clean install of Trusty 64 bit & also no minidlna. I've previously tried MediaTomb & it's far too complex for what I want to do: I want to play iPlayer .flv files downloaded by my iRecorder (Gambas GUI app) using get_iplayer. I've also subscribed to the Launchpad bug. Anybody know when Canonical are likely to fix this problem?

---

### Post by drpaneas on 2014-04-23
Eventually, I installed Plex and mini-dlna (thanks to the direct link for the deb packages)

I really recommend you to give Plex a try. It's an endeavour worthwhile. 
here is a guide I wrote: [https://forums.plex.tv/index.php/topic/106714-from-ubuntu-1404-to-nexus-7/](https://forums.plex.tv/index.php/topic/106714-from-ubuntu-1404-to-nexus-7/)  into their forums

---

### Post by urug on 2014-04-23
> **Clickbg said:**
> Hi I submitted a bug report for this one since in fact there is no practical workaround at the time. Please check in and mark that it also affects you - [https://bugs.launchpad.net/ubuntu/+source/minidlna/+bug/1309651](https://bugs.launchpad.net/ubuntu/+source/minidlna/+bug/1309651)

Here is a temporary fix. Please note that the package installation sequence is important:

```

  wget http://dk.archive.ubuntu.com/ubuntu/pool/universe/m/minidlna/minidlna_1.0.21+dfsg-1ubuntu1_amd64.deb
  wget http://security.ubuntu.com/ubuntu/pool/main/liba/libav/libavformat53_0.8.10-0ubuntu0.12.04.1_amd64.deb
  wget http://security.ubuntu.com/ubuntu/pool/main/liba/libav/libavcodec53_0.8.10-0ubuntu0.12.04.1_amd64.deb
  wget http://security.ubuntu.com/ubuntu/pool/main/liba/libav/libavutil51_0.8.10-0ubuntu0.12.04.1_amd64.deb


  dpkg -i libavutil51_0.8.10-0ubuntu0.12.04.1_amd64.deb
  dpkg -i libavcodec53_0.8.10-0ubuntu0.12.04.1_amd64.deb
  dpkg -i libavformat53_0.8.10-0ubuntu0.12.04.1_amd64.deb
  dpkg -i minidlna_1.0.21+dfsg-1ubuntu1_amd64.deb

```

Also remember that you will have to remove those packages after MiniDLNA is returned on the repo.

Thanks for the workaround. I had to complete one more step: installing libid3tag0.

```

wget http://dk.archive.ubuntu.com/ubuntu/pool/universe/m/minidlna/minidlna_1.0.21+dfsg-1ubuntu1_amd64.deb
wget http://security.ubuntu.com/ubuntu/pool/main/liba/libav/libavformat53_0.8.10-0ubuntu0.12.04.1_amd64.deb
wget http://security.ubuntu.com/ubuntu/pool/main/liba/libav/libavcodec53_0.8.10-0ubuntu0.12.04.1_amd64.deb
wget http://security.ubuntu.com/ubuntu/pool/main/liba/libav/libavutil51_0.8.10-0ubuntu0.12.04.1_amd64.deb

sudo dpkg -i libavutil51_0.8.10-0ubuntu0.12.04.1_amd64.deb
sudo dpkg -i libavcodec53_0.8.10-0ubuntu0.12.04.1_amd64.deb
sudo dpkg -i libavformat53_0.8.10-0ubuntu0.12.04.1_amd64.deb
sudo apt-get install libid3tag0
sudo dpkg -i minidlna_1.0.21+dfsg-1ubuntu1_amd64.deb

```

---

### Post by djart on 2014-04-26
Perhaps you'll want to keep an eye on the open bug report for this issue, located here: [https://bugs.launchpad.net/ubuntu/+source/minidlna/+bug/1309651](https://bugs.launchpad.net/ubuntu/+source/minidlna/+bug/1309651)

I've also created a PPA for 14.04 containing a fresh version of minidlna (thanks to work already maintained by Benoît Knecht), because I also heavily rely on MiniDLNA for TV viewing but didn't want to install older packages :-)

To install:
 sudo add-apt-repository ppa:djart/minidlna
sudo apt-get update
sudo apt-get install minidlna

---

### Post by piotrasbl on 2014-05-03
Thx,

Should anyone use 32bit(currently lubuntu 14.014) system - just like me, please mak sure u change amd64 into i386 in all mentioned files.

---

### Post by jiss2 on 2014-05-04
Plex wasnt picking up my folder eventhough i provided the permissions and added the plex user to all groups. Finally gave it up and gave rygel a try. Surprisingly good for my use cases. Just posting it here as another option for people missing minidlna till it comes to the repo(if it does)

---

### Post by m-dw on 2014-05-09
> **jiss2 said:**
> Plex wasnt picking up my folder eventhough i provided the permissions and added the plex user to all groups. Finally gave it up and gave rygel a try. Surprisingly good for my use cases. Just posting it here as another option for people missing minidlna till it comes to the repo(if it does)

Do we know whether miniDNLA is going to be put back in the repositories?  I'm looking for something light-weight to serve mpeg-2 transport stream (PVR recordingswith extension .ts) files from my headless Ubuntu server to my smart DVD..  The alternative (MediaTomb) seems a little bit over the top for my needs, although tempted to give it another go when I've got time to play about with it.

You know what ignore me.  I just installed it from djarts post further up this thread.  Not able to play back iPlayer .flv files, but everything else works.

---

### Post by rsjaffe on 2014-05-17
> **m-dw said:**
> Do we know whether miniDNLA is going to be put back in the repositories? 
It's back in Trusty. 

[FONT=courier new][/FONT][FONT=courier new]apt-cache show minidlna
[/FONT][FONT=courier new][/FONT][HR][/HR][FONT=courier new]Package: minidlna[/FONT]
[FONT=courier new]Priority: optional[/FONT]
[FONT=courier new]Section: universe/net[/FONT]
[FONT=courier new]Installed-Size: 471[/FONT]
[FONT=courier new]Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>[/FONT]
[FONT=courier new]Original-Maintainer: BenoÃ®t Knecht <benoit.knecht@fsfe.org>[/FONT]
[FONT=courier new]Architecture: amd64[/FONT]
[FONT=courier new]Version: 1.1.2+dfsg-1~ubuntu14.04.1[/FONT]
[FONT=courier new]Depends: adduser, initscripts (>= 2.88dsf-13.3), lsb-base, libavformat54 (>= 6:9.1-1), libavutil52 (>= 6:9.1-1), libc6 (>= 2.15), libexif12, libflac8 (>= 1.3.0), libid3tag0 (>= 0.15.1b), libjpeg8 (>= 8c), libogg0 (>= 1.0rc3), libsqlite3-0 (>= 3.5.9), libvorbis0a (>= 1.1.2)[/FONT]
[FONT=courier new]Filename: pool/universe/m/minidlna/minidlna_1.1.2+dfsg-1~ubuntu14.04.1_amd64.deb[/FONT]

---

### Post by johnaaronrose on 2014-05-19
It's now in the standard Ubuntu repos.

---

### Post by m-dw on 2014-05-20
I have it.... now  onto other issues... encoding vobs to streamable formats.

---

### Post by bapoumba on 2014-05-20
This thread has gone beyond the original purpose. So I am closing here, we won't support illegal activities : [http://ubuntuforums.org/misc.php?do=showrules](http://ubuntuforums.org/misc.php?do=showrules)

>  Material that suggests illegal activity or contains illegal content is also forbidden. We do not support circumventing TOS, EULA, etc here. Such threads will be closed

---

