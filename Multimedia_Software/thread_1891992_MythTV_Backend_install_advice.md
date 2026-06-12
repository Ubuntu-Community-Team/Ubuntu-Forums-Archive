---
title: "MythTV Backend install advice"
date: 2011-12-07
forum: Multimedia Software
---

### Post by sirgad on 2011-12-07
Hi,

I have a laptop running Ubuntu 11.10 Server (64-bit).  It is essentially headless and managed entirely over SSH.  My plan is to attach a USB digital TV tuner and serve live TV to my local network machines running OS X 10.6.8 and iOS5.  I'd also need to be able to perform remote scheduling of recordings.

I don't have a great deal of space on the laptop (whilst it currently runs on a 80GB HDD, I'll eventually be migrating it to a 16 or 32GB USB flash drive), so I'm trying to keep a tight rein on what gets installed.  I'm also trying to keep a tight rein on running services in order to keep power requirements down (UK energy companies are raising prices all the time).

I've found several How-Tos regarding MythTV, and this seems like a good solution.  However, I'm not entirely satisfied with the number of dependencies that are installed by *apt-get*, and would like to cherry-pick only the truly required packages for my needs.

For example, a How-To from 3 years ago [_here on the Ubuntu website_]("https://help.ubuntu.com/community/MythTV/Install/Server/Backend") tells me to start by installing *xmltv*.  This is what I get:
```
The following NEW packages will be installed
  libarchive-zip-perl libclass-inspector-perl libclass-load-perl
  libclass-methodmaker-perl libclass-singleton-perl libconvert-binhex-perl
  libdate-manip-perl libdatetime-format-strptime-perl libdatetime-locale-perl
  libdatetime-perl libdatetime-timezone-perl libdigest-hmac-perl
  libemail-address-perl libemail-find-perl libemail-valid-perl
  libexporter-lite-perl libfcgi-perl libfile-slurp-perl libhtml-fromtext-perl
  libhtml-tableextract-perl libhttp-cache-transparent-perl
  libhttp-server-simple-perl libio-stringy-perl liblingua-preferred-perl
  liblist-moreutils-perl liblog-tracemessages-perl libmath-round-perl
  libmime-tools-perl libnet-dns-perl libnet-domain-tld-perl libnet-ip-perl
  libossp-uuid-perl libossp-uuid16 libparams-validate-perl
  libparse-recdescent-perl libregexp-common-perl libsoap-lite-perl
  libtask-weaken-perl libterm-progressbar-perl libterm-readkey-perl
  libtext-bidi-perl libtie-ixhash-perl libtk-tablematrix-perl
  libunicode-string-perl libwww-mechanize-perl libxml-dom-perl
  libxml-libxml-perl libxml-libxslt-perl libxml-namespacesupport-perl
  libxml-parser-perl libxml-perl libxml-regexp-perl libxml-sax-expat-perl
  libxml-sax-perl libxml-twig-perl libxml-writer-perl libxml-xpath-perl
  libxmltv-perl libyaml-syck-perl perl-tk xmltv xmltv-gui xmltv-util
0 upgraded, 63 newly installed, 0 to remove and 0 not upgraded.
Need to get 13.2 MB of archives.
After this operation, 78.7 MB of additional disk space will be used.
```
It seems like a heck of a lot to install just so that I can grab TV schedules from the web.

Similarly, when it comes to the core MythTV packages, the How-To recommends installing *mysql-server*, *mythtv-backend* and *mythtv-database*.  What I get is this:
```
The following NEW packages will be installed
  libasyncns0 libaudio2 libavc1394-0 libdbd-mysql-perl libdbi-perl libflac8
  libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglu1-mesa libiec61883-0
  libjson0 liblcms1 libllvm2.9 libmng1 libmp3lame0 libmysqlclient16
  libmyth-0.24-0 libmyth-python libmythtv-perl libnet-daemon-perl
  libnet-upnp-perl libplrpc-perl libpulse0 libqt4-dbus libqt4-declarative
  libqt4-designer libqt4-network libqt4-opengl libqt4-qt3support libqt4-script
  libqt4-sql libqt4-sql-mysql libqt4-xml libqt4-xmlpatterns libqtcore4
  libqtgui4 libqtwebkit4 libraw1394-11 libsdl1.2debian libsdl1.2debian-alsa
  libsndfile1 libutempter0 libvdpau1 libvorbisenc2 libxaw7 libxcb-shape0
  libxmu6 libxpm4 libxtst6 libxv1 libxxf86dga1 libxxf86vm1 mysql-client-5.1
  mysql-client-core-5.1 mysql-common mysql-server mysql-server-5.1
  mysql-server-core-5.1 mythtv-backend mythtv-common mythtv-database
  mythtv-transcode-utils pwgen python-lxml python-mysqldb python-support qdbus
  ttf-dejavu ttf-dejavu-extra ttf-droid ttf-liberation x11-utils xbitmaps
  xterm zenity zenity-common
0 upgraded, 77 newly installed, 0 to remove and 0 not upgraded.
Need to get 91.9 MB/92.8 MB of archives.
After this operation, 261 MB of additional disk space will be used.
```
I actually discussed this with some of the devs on the mythtv IRC channel, who confirmed my suspicions that many of the packages listed above were not, in fact, necessary for a MythTV-Backend setup.  However, because they do not officially support a backend/frontend setup split between different machines, they were unable to help me further.

If someone could advise me how to go about installing only the precise packages required for my needs, I'd be grateful.

Many thanks,

S.

---

### Post by sirgad on 2011-12-10
I eventually got some good advice on the mythtv mailing list.: I should use _[tvheadend]("https://www.lonelycoder.com/hts/tvheadend_overview.html")_.  It's part of HTS and is purpose-designed to share a single TV tuner across a network. It even has a very user-friendly webGUI for config etc.

Unfortunately I may have run into a bug in the driver for my tuner (dib7000; Nova-T) so I'm still dead in the water.

But perhaps others will have more luck.

---

### Post by BicyclerBoy on 2011-12-10
The mythbackend storage requirements dictate a big disk..

Can need 5GB/hr per each channel. LiveTV is buffered as a full length temp recording.
Most mythtv users never use live tv except for debugging & 1TB HDD is considered small.

What are the nova-t driver bugs you refer ?
I assume USB nova-t stick..

That xml bloat also affects (even worse) the alsa source code package..

---

### Post by sirgad on 2011-12-11
> What are the nova-t driver bugs you refer ?
I assume USB nova-t stick..

Yes, Nova-T USB.  The bug appears to have manifested in kernel 3.  The error in the log is as follows:

```
dib0700: tx buffer length is larger than 4. Not supported.
```

Searching for this term reveals many have the same issue, with my exact tuner and all in kernel 3.  Oddly, some have the same log message in kernel 2.6.* even though their tuner works fine, so it may be unrelated.  All I know for sure is that, even though I know the tuner works just fine with EyeTV 3.5.* on my Mac, *tvheadend* simply reports "no signal" when scanning for services.  I've confirmed I've chosen the correct transmitter, and the device is properly recognised by the software.

I should add that I made a live USB (with persistence) of Ubuntu 11.04 Desktop, which has kernel 2.6.39, and installed *tvheadend* on that, but still received the same error.

S.

EDIT: [Kernel 3.0 Breaks DVB-T]("http://forums.opensuse.org/english/get-technical-help-here/tumbleweed/464128-kernel-3-0-breaks-dvb-t.html")

---

### Post by BicyclerBoy on 2011-12-11
Hope that does not effect the PCI version (dual USB on a PCI card) or spread to any other devices.

That bug sounds like an i2c error 'inside' the USB device..

Why not use 10.04.3 ?
Or try the ubuntu kernel team ppa..

---

### Post by sirgad on 2011-12-13
Just FYI: I've now tried the same tuner with a live USB (with persistence) of 10.04.3 Desktop, and it still doesn't work.  Research suggests this shouldn't be the case, so maybe there's something else at play.

---

### Post by BicyclerBoy on 2011-12-13
You do have the linux-firmware package installed ?
dmesg | grep firmware
dmesg | grep dvb

---

### Post by sirgad on 2011-12-14
Those greps don't throw up any results, but running:

```
apt-cache policy linux-firmware
```

Gives the following:

```
linux-firmware:
  Installed: 1.60
  Candidate: 1.60
  Version table:
 *** 1.60 0
        500 http://gb.archive.ubuntu.com/ubuntu/ oneiric/main amd64 Packages
        100 /var/lib/dpkg/status
```

Make of that what you will.  Personally, I've no clue what it means :)

---

### Post by BicyclerBoy on 2011-12-14
I would just run synaptic package manager & search for firmware..

I believe synaptic GUI has been left out of 11.10 but it still works when installed.

Read thru' dmesg to see what happens during boot..

---

### Post by sirgad on 2011-12-14
I haven't got a clue what you're talking about. Which firmware? Why?  You're going to have to give me a little more to work on than this.

---

### Post by BicyclerBoy on 2011-12-14
A lot of PC cards/gadgets have firmware loaded by drivers as detected.
This include most tuner cards & wifi adapters etc.
The nova-t stick requires firmware..

Some firmware is provided & some is extracted from windows drivers & is non-free.

Synaptic is the GUI package management tool used in ubuntu..it has been left out of the latest release..

Trying in a terminal:
gksudo synaptic
search for 'firmware'
mark for install:
- linux-firmware
- linux-firmware-nonfree
click apply

Unplug & replug tuner stick
dmesg | tail

---

### Post by sirgad on 2011-12-15
Hi,

As I indicated, linux-firmware 1.6 is currently already installed.  Oh, and I'm not using a GUI - I indicated that in my first post when I said all my interaction was over SSH with a headless server.

I may look into the non-free firmwares as you suggest.  I'll get back to you.

S.

---

### Post by BicyclerBoy on 2011-12-15
Sorry no GUI. just use aptitude or apt-get..

simulated dummy run:
apt-get -s install linux-firmware*

hint: hit the 'tab' twice to auto complete command..

Real install
sudo apt-get install linux-firm.....etc

---

### Post by sirgad on 2012-02-09
Hi,

Just to close the thread:

I eventually got recommended [TVHeadend]("https://www.lonelycoder.com/tvheadend/"), which is just what I was looking for and trumps the MythTV backend idea completely.  Highly recommended to anyone.

---

### Post by BicyclerBoy on 2012-02-11
Good that you found a solution.

TVHeadEnd is nothing like MythTV..The PVR is a paradigm shift in TV consumption.

If TVHeadend works with your tuner card then mythtv should have.
The tuner errors must have been of little consequence.

---

