---
title: "How-To: Compile Amarok 1.4.10 in Ubuntu 10.04"
date: 2010-08-23
forum: Multimedia Software
---

### Post by dentaku65 on 2010-08-23
I'm a big user of old Amarok and I still using in Lucid; here the how-to compile from source; based on this post [http://ubuntuforums.org/showthread.php?t=1307737](http://ubuntuforums.org/showthread.php?t=1307737) (thx Seegorkesolot) with some new hints and modified patches.

This works on Ubuntu (Gnome version) without the official repository version of Amarok installed.

**INSTALL DEPENDENCIES**
```
sudo apt-get install libgpod-common libgpod-dev libgpod4 kdelibs4-dev libxine-dev libdbus-qt-1-dev libtag1-dev libsqlite3-dev libtunepimp-dev libmysqlclient15-dev libpq-dev libvisual-0.4-dev libsdl1.2-dev libifp-dev libxine1 libxine1-ffmpeg build-essential checkinstall ruby ruby-dev libruby libltdl-dev
```
**DOWNLOAD AMAROK SOURCE**
```
cd ~/Downloads
wget http://download.kde.org/stable/amarok/1.4.10/src/amarok-1.4.10.tar.bz2
tar -xvf amarok-1.4.10.tar.bz2
cd amarok-1.4.10
```
**PATCH FIX THE CODE (fix for GCC, Cover Manager and Wikipedia lookup)**
```
wget http://yep.it/savedpatch/amarok-1.4.10-gcc44.patch -O amarok-1.4.10-gcc44.patch
patch -p1 < amarok-1.4.10-gcc44.patch

```
```
wget http://yep.it/savedpatch/amarok-1.4.10-covermanager-fix.patch -O amarok-1.4.10-covermanager-fix.patch
patch -p1 < amarok-1.4.10-covermanager-fix.patch
```
```
wget http://yep.it/savedpatch/amarok-1.4.10-wikipedia.patch -O amarok-1.4.10-wikipedia.patch
patch -p1 < amarok-1.4.10-wikipedia.patch
```
**COMPILE & INSTALL THE APP**
```
./configure --without-arts
make
sudo make install
```
**RESTORE ORIGINAL APP ICONS** (thx zenkaon)
```
cd ~/Downloads
wget http://pprc.qmul.ac.uk/~jmorris/personal/amarok/amarok.icons.__usr.share.icons__.tar.gz -O amarok.icons.__usr.share.icons__.tar.gz
sudo cp ~/Downloads/amarok.icons.__usr.share.icons__.tar.gz /usr/share/icons
cd /usr/share/icons
sudo tar zxvf amarok.icons.__usr.share.icons__.tar.gz
```

Done! You can now launch Amarok ;)

**NICE TO HAVE (Install when Amarok is executed)**

UltraLyricwiki, working script for lyrics: 
> [http://kde-apps.org/content/show.php/ultraLyricWiki?content=116725](http://kde-apps.org/content/show.php/ultraLyricWiki?content=116725)

Notify OSD for Ubuntu integration: 
> [http://kde-apps.org/content/show.php/Amarok+Notify-osd+-+critical+update?content=104506](http://kde-apps.org/content/show.php/Amarok+Notify-osd+-+critical+update?content=104506)

My favourite theme: 
> under Amarok - Configure Amarok - Appareance - Download theme, then search for 3Dintegrity

---

### Post by Seegorkesolot on 2010-09-06
Hi

I just randomly googled the topic to check if my script still is in use  anywhere and it is in fact ;)  Nice work and thx for keeping it alive :p

Greetz

---

### Post by sharkindustries on 2010-09-11
Hi.. thanks to dentaku65 and Seegorkesolot for making my fav linux audio app (and it's right version.. lol) available in 10.04!! 

INSTALLATION: I followed instructions as per the first post; I ran into troubles, which i fixed :P  by installing the following:
1) ruby, ruby1.8 and ruby1.8-dev
2) libltdl-dev

REMARKS: I don't know if this case applies to everyone! But *better to check if the above packages are installed before installing amarok*.

---

### Post by mc4man on 2010-09-11
It will also build and run fine on 10.10 w/ a few minor changes, there's also the pana clone
Atm have both installed, haven't decided which to keep.

---

### Post by dentaku65 on 2010-09-25
Thx all,
I've updated the dependencies and did some screenshots 

bye

---

### Post by ubfu on 2010-10-20
Problem start at compiling
> ./configure --without-arts
make
sudo make install
having the problem compiling giving some error about ruby programming language which I am not sure which lib to install.

[http://pastebin.com/TjgDkmhR](http://pastebin.com/TjgDkmhR)

Thanks hope for solution :)

---

### Post by mc4man on 2010-10-20
> I am not sure which lib to install.
You need ruby, ruby1.8-dev, and their deps.
run this
```
sudo apt-get install ruby ruby-dev libruby
```
or
```
sudo apt-get install ruby ruby1.8-dev libruby1.8
```

 /usr/bin/ruby must link to ruby1.8, at least at build time

Edit - what release of ubuntu are you using - assuming lucid?

---

### Post by dentaku65 on 2010-10-20
mmm...
changed the dependencies of ruby in the #1 switched from ruby-8 to ruby; should the distribution now choose the version...

---

### Post by ubfu on 2010-10-20
> **mc4man said:**
> You need ruby, ruby1.8-dev, and their deps.
run this
```
sudo apt-get install ruby ruby-dev libruby
```
or
```
sudo apt-get install ruby ruby1.8-dev libruby1.8
```

(if you have ruby1.9.X-dev installed amarok will not build and /usr/bin/ruby must link to ruby1.8, at least at build time

Edit - what release of ubuntu are you using - assuming lucid?



Forgot to mention, using maverick right now (dual boot with hardy)

 I had uninstall version  1.9 ruby at synaptic but I still having some error during installation on ./configure --without-arts
Here's the pastebin , The error seem like I need a xine library , and again , which library should I install ?
[http://pastebin.com/PNb4YiVQ](http://pastebin.com/PNb4YiVQ)

Thanks :)

---

### Post by mc4man on 2010-10-20
> which library should I install 
Well I built amarok 1.4 on maverick about 6 wks. ago, all went well. Rebuilding today a few things have changed, haven't the time to look into.
(shouldn't be a concern if you don't need mtp support, should be a solution, note pana config

you need libxine1 and libxine-dev (the 1.18.X ver.
There is also a dev that's not available in maverick - whether it's needed not sure, when I first built on maverick I installed the lucid libs, a build without today showed no ill effect that I've seen  - libdbus-qt-1-dev

So a reasonable dep check would be to run this (obviously most are installed
```
sudo apt-get install libgpod-common libgpod-dev libgpod4 kdelibs4-dev libxine-dev \
libtag1-dev libsqlite3-dev libtunepimp-dev libmysqlclient-dev libpq-dev \
libvisual-0.4-dev libsdl1.2-dev libifp-dev libxine1 libxine1-ffmpeg build-essential \
checkinstall ruby ruby-dev libruby libltdl-dev libmp4v2-dev

```

Current plugin list from amarok 1.4 configure - using this
./configure --without-arts --with-mp4v2 --without-libmtp

> ===  Amarok - PLUGINS  ========================================================
 ==========================
 =
 = The following extra functionality will NOT be included:
 =   - NMM-engine
 =   - Helix-engine
 =   - yauap-engine
 =   - MySql Support
 =   - Postgresql Support
 =   - Konqueror Sidebar
 =   - MTP Device Support
 =   - Rio Karma Support
 =
 = The following extra functionality will be included:
 =   + xine-engine
 =   + libvisual Support
 =   + MusicBrainz Support
 =   + MP4/AAC Tag Write Support
 =   + iPod Support
 =   + iRiver iFP Support
 =   + Creative Nomad Jukebox Support
 =   + DAAP Music Sharing Support


Now as a comparison - recent Debian package set build of pana - from build log

> ===  Pana - PLUGINS  ========================================================
 ==========================
 =
 = The following extra functionality will NOT be included:
 =   - NMM-engine
 =   - Helix-engine
 =   - yauap-engine
 =   - Konqueror Sidebar
 =   - Rio Karma Support
 =
 = The following extra functionality will be included:
 =   + xine-engine
 =   + libvisual Support
 =   + MySql Support
 =   + Postgresql Support
 =   + MusicBrainz Support
 =   + MP4/AAC Tag Write Support
 =   + iPod Support
 =   + iRiver iFP Support
 =   + Creative Nomad Jukebox Support
 =   + MTP Device Support
 =   + DAAP Music Sharing Support

For install I prefer checkinstall for amarok14 - a simple command -
```
sudo checkinstall --pkgname amarok14 --pkgversion 1.4 --backup=no --default \
--deldoc=yes --deldesc=yes --delspec=yes --fstrans=no 

```

Ot
I use ruby 1.9.2 - amarok 1.4 seems to run fine when it is the default ruby, but as mentioned won't build unless 1.8 is the default (/usr/bin/ruby) at compile time.

---

### Post by theozzlives on 2010-10-20
I just install amarok14 from the PPA and it runs fine. I also have to install the missing dependancy (libmysqlclient15off_5.0.32-7etch12_amd64.deb). I'm running Maverick.

```
http://ppa.launchpad.net/bogdanb/amarok14/ubuntu jaunty main
```

Key:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0x1d7e9dd033e89ba781e32a24b9f1c432ae74ae63
```

Update and do:

```
sudo apt-get install amarok14
```

---

### Post by mc4man on 2010-10-20
> mmm...
changed the dependencies of ruby in the #1 switched from ruby-8 to ruby; should the distribution now choose the version...
I think it's fine specifying the dependency packages - atm 1.8 is the default for all recent ubuntu releases so your orig. was good also.

I'd mentioned to prev. poster using the dep packages just in case he'd used a higher version or outside ppa packages.

There now is a ppa for mav. that offers the 1.9.2 as an 'alternative' which is quite convenient 
So for Ex.
> doug@doug-laptop:~$ sudo update-alternatives --config ruby
There are 2 choices for the alternative ruby (providing /usr/bin/ruby).

  Selection    Path                Priority   Status
------------------------------------------------------------
  0            /usr/bin/ruby1.9.2   400       auto mode
  1            /usr/bin/ruby1.8     200       manual mode
* 2            /usr/bin/ruby1.9.2   400       manual mode
Press enter to keep the current choice[*], or type selection number:
 Before building I switch back to 1.8 - the various dev's and libs themselves can coexist, if amarok or pana had an issue running w/ 1.9.2 then I'd keep 1.8 as default and switch to 1.9.2 as needed...

---

### Post by dentaku65 on 2010-10-20
> **theozzlives said:**
> I just install amarok14 from the PPA and it runs fine. I also have to install the missing dependancy (libmysqlclient15off_5.0.32-7etch12_amd64.deb). I'm running Maverick.

```
http://ppa.launchpad.net/bogdanb/amarok14/ubuntu jaunty main
```

Key:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0x1d7e9dd033e89ba781e32a24b9f1c432ae74ae63
```

Update and do:

```
sudo apt-get install amarok14
```

Hi ozz,
but on this version there are some crucial aspects that does not work, like wikipedia and lastfm; that's why the sources must be patched.

---

### Post by dentaku65 on 2010-10-20
> **mc4man said:**
> I think it's fine specifying the dependency packages - atm 1.8 is the default for all recent ubuntu releases so your orig. was good also.

I'd mentioned to prev. poster using the dep packages just in case he'd used a higher version or outside ppa packages.

There now is a ppa for mav. that offers the 1.9.2 as an 'alternative' which is quite convenient 
So for Ex.

 Before building I switch back to 1.8 - the various dev's and libs themselves can coexist, if amarok or pana had an issue running w/ 1.9.2 then I'd keep 1.8 as default and switch to 1.9.2 as needed...

Thx macman,
actually I don't use Mav at the moment, again thanks for sharing :KS

---

### Post by aphlar on 2010-11-29
Muchas gracias - Thank you so much

---

### Post by mc4man on 2010-11-29
Small note - for lyrics I've found this plugin script to work quite well with amarok 1.4
[http://kde-apps.org/content/show.php/ultraLyricWiki?content=116725](http://kde-apps.org/content/show.php/ultraLyricWiki?content=116725)

Just dl and put in Documents folder, no need to extract
amarok - tools - script manager - Install Script will find and install, Then just highlight and click 'run'.

---

### Post by mc4man on 2010-12-01
Just a note on 11.04 and amarok14 - 
While a bit early to say it definitely can be used, atm amarok builds and works fine.
Unity is very incomplete so was a bit of a hassle to get pinned. 
There is no notification (systray) area, how that will shake out don't know.

On the positive side everything I tried so far works, the osd works and amarok keeps it's taskbar instead of ending up on the static one at top of screen like alot of other media players (whatever that thing is called.
Was able to add an application icon, though when using amarok the one below w/ no icon shows up (amarokapp). Amarok will minimize to unity thru that icon.

Basically same build instructions though one small change to source was needed
In amarok-1.4.10/amarok/src/osd.h this line (40), needed the red removed
```
void show( const QString &text, QImage newImage = QImage[COLOR="DarkRed"]::QImage[/COLOR]() );
```

So atm have 2 oldies still going well, totem-xine and amarok 1.4, though i fear the end for either one or both may be approaching..

Edit: gave the 'classic' desktop a try in natty - atm far superior for multimedia use

---

### Post by mc4man on 2011-10-21
This is a modified version from what's on pg.1 to be used on **11.10 (Oneiric**
It will require using 5 packages from natty that are no longer available in 11.10, for the MP4/AAC tag write support there will be 4 additional packages needed, that's optional & not required to use Amarok

To prevent broken packages when installing the natty packages the build-dep list is much larger, some may already be installed, doesn't matter, run the full list
Should work fine if ALL the steps are carefully followed, the 2 gcc patches are absolutely required as is the fix header, don't skip

This is set up to use the same terminal for all, only command not included is the cd to folder holding the downloaded packages

So install the build-deps - 

```
sudo apt-get install libgpod-common libgpod-dev libgpod4  libxine-dev \
libtag1-dev libsqlite3-dev libtunepimp-dev libmysqlclient-dev libpq-dev \
libvisual-0.4-dev libsdl1.2-dev libifp-dev libxine1 libxine1-ffmpeg \
build-essential checkinstall ruby ruby-dev libruby libltdl-dev libxmu-dev \
libjpeg-dev libmng-dev libcups2-dev libart-2.0-dev libacl1-dev libattr1-dev libaspell-dev \
libbz2-dev libjasper-dev libopenexr-dev libpcre3-dev liblualib50-dev \
libsasl2-dev libtiff4-dev libxml2-dev  gettext-kde libxslt1-dev  kdelibs5-data \
libavahi-common-dev qt3-dev-tools python-scour pkg-kde-tools kdesdk-scripts
```

Get the required natty packages - 

Go to each one of these 5 links, pick your arch at the bottom of the page, (or all deb on 1) & download, put all the .debs in an empty folder
**You must get all 5**

[http://packages.ubuntu.com/natty/kdelibs4c2a](http://packages.ubuntu.com/natty/kdelibs4c2a)
[http://packages.ubuntu.com/natty/kdelibs4-dev](http://packages.ubuntu.com/natty/kdelibs4-dev)
[http://packages.ubuntu.com/natty/kdelibs-data](http://packages.ubuntu.com/natty/kdelibs-data)
[http://packages.ubuntu.com/natty/libavahi-qt3-dev](http://packages.ubuntu.com/natty/libavahi-qt3-dev)
[http://packages.ubuntu.com/natty/libavahi-qt3-1](http://packages.ubuntu.com/natty/libavahi-qt3-1)

Optional for MP4/AAC Tag Write Support (not required
If using then as above, place in same folder

[http://packages.ubuntu.com/natty/libmp4v2-0](http://packages.ubuntu.com/natty/libmp4v2-0)
[http://packages.ubuntu.com/natty/libmp4v2-dev](http://packages.ubuntu.com/natty/libmp4v2-dev)
[http://packages.ubuntu.com/natty/libmpeg4ip-dev](http://packages.ubuntu.com/natty/libmpeg4ip-dev)
[http://packages.ubuntu.com/natty/libmpeg4ip-0](http://packages.ubuntu.com/natty/libmpeg4ip-0)

Then cd to the folder containing the downloaded packages in the terminal & run
```
sudo dpkg -i *.deb
```
There should be no issues, if for some reason there are then that **must be resolved** before continuing

Get the amarok source
```
cd; mkdir amarok_build; cd amarok_build
```
```
wget http://download.kde.org/stable/amarok/1.4.10/src/amarok-1.4.10.tar.bz2 && \
tar -xvf amarok-1.4.10.tar.bz2 && \
cd amarok-1.4.10
```

PATCH FIX THE CODE (fix for GCC, Cover Manager and Wikipedia lookup)

```
wget http://yep.it/savedpatch/amarok-1.4.10-gcc44.patch -O amarok-1.4.10-gcc44.patch && \
patch -p1 < amarok-1.4.10-gcc44.patch

```

```
wget http://yep.it/savedpatch/amarok-1.4.10-covermanager-fix.patch -O amarok-1.4.10-covermanager-fix.patch && \
patch -p1 < amarok-1.4.10-covermanager-fix.patch

```


```
wget http://yep.it/savedpatch/amarok-1.4.10-wikipedia.patch -O amarok-1.4.10-wikipedia.patch && \
patch -p1 < amarok-1.4.10-wikipedia.patch
```

Additional ggc-4.6 Patch
Attached below is a new **required** patch, download, extract & place in the amarok-1.4.10 folder, then 
```
patch -p1 < gcc46-fix.patch
```

All patches should & **must complete without error**

Fix a header - 

In the same terminal (still @ the amarok-1.4.10$ prompt
```
cd amarok/src; sed -i -e 's/QImage::QImage/QImage/g' osd.h
```

```
cd ../..
```

Configure
Pre-configure ruby check
In 11.10 one can have both ruby-1.8 & ruby-1.9 installed. When building amarok the default ruby must be set to 1.8, it likely will run with either
To check & set if need be
```
sudo update-alternatives --config ruby
```
If it returns no alternatives then you are fine. If it returns a list make sure it's set to 1.8, either manual or auto, no matter
Ex.
> sudo update-alternatives --config ruby
[sudo] password for doug: 
There are 2 choices for the alternative ruby (providing /usr/bin/ruby).

  Selection    Path                Priority   Status
------------------------------------------------------------
  0            /usr/bin/ruby1.8     50        auto mode
* 1            /usr/bin/ruby1.8     50        manual mode
  2            /usr/bin/ruby1.9.1   10        manual mode

Press enter to keep the current choice[*], or type selection number: 

In this case it's good, i'd press enter and proceed

Edit: 
MTP support is not avail., if libmtp-dev is installed amarok will try to enable & the build **will fail**. Make sure it's not installed or if it is a --without-libmtp needs to be in the configure before the LDFlags=


If NOT using the MP4 packages then use this
```
./configure --without-arts --enable-mysql LDFLAGS='-lkdecore -lDCOP -lkdefx -lkparts'
```

If using the MP4 packages then use this instead
```
./configure --without-arts --with-mp4v2 --enable-mysql LDFLAGS='-lkdecore -lDCOP -lkdefx -lkparts'

```

After a good configure then build
```
make
```

Install with checkinstall, (the new terminal behavior in 11.10 is to stop the cursor from blinking after about 12  seconds - checkinstall will pause at least once - just wait &  let it finish
 ```
sudo checkinstall --pkgname amarok14 --pkgversion 1.4 --backup=no \
--default --deldoc=yes --deldesc=yes --delspec=yes --fstrans=no

```

EDIT: -forgot something- 
Best to run this after install
```
sudo ldconfig
```


Systray icon in unity
Amarok works best with a systray icon, in unity 'Amarok' must be added to the systray whitelist
This can be done thru a gsettings command or in dconf-editor
For dconf-editor install
```
sudo apt-get install dconf-tools
```
Then start with
dconf-editor

Can be found under desktop > unity > panel
To add click in the edit box until it turns white, then at end of string add
```
,'Amarok' 
```
To set Do Not click out with mouse, press enter on the keyboard
A restart of unity will add
The systray icon is less than ideal, I don't know how to fix, needs a trans background. If any finds how to, either pre or post build, that would be great

There are some additional scripts, ect. at the end of post 1, refer to
Have checked this on both i386 & amd64, should be fine, am going to do a fresh install tonight & will d. check

---

### Post by masavini on 2012-01-14
hi,
i installed amarok on ubuntu 10.10 following the procedure of the first post...
it seems fine, but i can't get musicbrainz plugin to work properly: i installed the libtunepimp5-mp3 library, but if i click on "fill-in tags using musicbrainz" it gets stuck on "generating audio fingerprint" and the cpu goes 100%.

can anybody help me?

---

### Post by dentaku65 on 2012-04-03
Hi mc4man,

what about to use Trinity Desktop packages for Oneiric?
[http://www.trinitydesktop.org/installation.php#ubuntu](http://www.trinitydesktop.org/installation.php#ubuntu)

I'm waiting them with Precise version in order to start again the "resurrection" of Amarok 1.4 

Unfortunately their version of Amarok 1.4 (amarok-trinity) do not have the precious patches proposed here, so we need to compile it from the sources.


> **mc4man said:**
> 
snip
[http://packages.ubuntu.com/natty/kdelibs4c2a](http://packages.ubuntu.com/natty/kdelibs4c2a)
[http://packages.ubuntu.com/natty/kdelibs4-dev](http://packages.ubuntu.com/natty/kdelibs4-dev)
[http://packages.ubuntu.com/natty/kdelibs-data](http://packages.ubuntu.com/natty/kdelibs-data)
[http://packages.ubuntu.com/natty/libavahi-qt3-dev](http://packages.ubuntu.com/natty/libavahi-qt3-dev)
[http://packages.ubuntu.com/natty/libavahi-qt3-1](http://packages.ubuntu.com/natty/libavahi-qt3-1)

Optional for MP4/AAC Tag Write Support (not required
If using then as above, place in same folder

[http://packages.ubuntu.com/natty/libmp4v2-0](http://packages.ubuntu.com/natty/libmp4v2-0)
[http://packages.ubuntu.com/natty/libmp4v2-dev](http://packages.ubuntu.com/natty/libmp4v2-dev)
[http://packages.ubuntu.com/natty/libmpeg4ip-dev](http://packages.ubuntu.com/natty/libmpeg4ip-dev)
[http://packages.ubuntu.com/natty/libmpeg4ip-0](http://packages.ubuntu.com/natty/libmpeg4ip-0)
snip


---

### Post by mc4man on 2012-04-08
> **dentaku65 said:**
> Hi mc4man,

what about to use Trinity Desktop packages for Oneiric?
[http://www.trinitydesktop.org/installation.php#ubuntu](http://www.trinitydesktop.org/installation.php#ubuntu)

I'm waiting them with Precise version in order to start again the "resurrection" of Amarok 1.4 

Unfortunately their version of Amarok 1.4 (amarok-trinity) do not have the precious patches proposed here, so we need to compile it from the sources.

I don't have a 11.10 install anymore - I know I tried out trinity - can't quite remember why I decided to go with Ubuntu/Debian libs

As far as 12.04 - there are several things to take into consideration & maybe at the end of the day the trinity or trinity source files **may** be the best direction
(ATM the trinity packages are not installable in 12.04, certainly not without some help..

The 1st. thing to deal with is libtunepimp.. is not in precise & it's not simply a matter of providing

The 2nd issue may revolve around libjpeg, precise's dev is a dep package to the 8 version, but at least one of the kde deps requires libjpeg62

Anyway to check out I just today put in a new 12.04 install so used my 11.10 method.
I had to remove libtunepimp-dev from the pre-installs & add 2 packages
(libjpeg62 libidn11-dev

Then proceeded as laid out, was curious to see what would happen about libjpeg62 & libjpeg-dev (libjpeg8-dev

Actually the build, install & running went fine, all seems ok with amarok though I've only done a short test.
As far as libjpeg it's using the 8 version with no apparent ill effect (not to say there won't be, What's it used for?

Seen here - 
> 
ldd /usr/bin/amarok
	linux-gate.so.1 =>  (0xb779d000)
	libkdecore.so.4 => /usr/lib/libkdecore.so.4 (0xb7595000)
	libqt-mt.so.3 => /usr/lib/libqt-mt.so.3 (0xb6e30000)
	libkdeui.so.4 => /usr/lib/libkdeui.so.4 (0xb6b8d000)
	libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xb6a91000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb68eb000)
	libDCOP.so.4 => /usr/lib/libDCOP.so.4 (0xb68b9000)
	libart_lgpl_2.so.2 => /usr/lib/libart_lgpl_2.so.2 (0xb68a2000)
	libidn.so.11 => /usr/lib/i386-linux-gnu/libidn.so.11 (0xb686d000)
	libkdefx.so.4 => /usr/lib/libkdefx.so.4 (0xb6844000)
	libSM.so.6 => /usr/lib/i386-linux-gnu/libSM.so.6 (0xb683b000)
	libICE.so.6 => /usr/lib/i386-linux-gnu/libICE.so.6 (0xb6821000)
	libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xb66ed000)
	libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0xb66d6000)
	libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xb66d1000)
	libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xb66a5000)
	libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xb6687000)
	libfontconfig.so.1 => /usr/lib/i386-linux-gnu/libfontconfig.so.1 (0xb6653000)
	libaudio.so.2 => /usr/lib/i386-linux-gnu/libaudio.so.2 (0xb6639000)
	[COLOR="Blue"]libjpeg.so.8 => /usr/lib/i386-linux-gnu/libjpeg.so.8 (0xb65e3000)[/COLOR]
	libpng12.so.0 => /lib/i386-linux-gnu/libpng12.so.0 (0xb65b9000)
	libXi.so.6 => /usr/lib/i386-linux-gnu/libXi.so.6 (0xb65a9000)
	libXrender.so.1 => /usr/lib/i386-linux-gnu/libXrender.so.1 (0xb659f000)
	libXrandr.so.2 => /usr/lib/i386-linux-gnu/libXrandr.so.2 (0xb6595000)
	libXcursor.so.1 => /usr/lib/i386-linux-gnu/libXcursor.so.1 (0xb658a000)
	libXinerama.so.1 => /usr/lib/i386-linux-gnu/libXinerama.so.1 (0xb6586000)
	libXft.so.2 => /usr/lib/i386-linux-gnu/libXft.so.2 (0xb6570000)
	libfreetype.so.6 => /usr/lib/i386-linux-gnu/libfreetype.so.6 (0xb64d6000)
	libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xb64c3000)
	libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xb64a8000)
	/lib/ld-linux.so.2 (0xb779e000)
	libuuid.so.1 => /lib/i386-linux-gnu/libuuid.so.1 (0xb64a2000)
	libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xb6481000)
	libexpat.so.1 => /lib/i386-linux-gnu/libexpat.so.1 (0xb6456000)
	libXt.so.6 => /usr/lib/i386-linux-gnu/libXt.so.6 (0xb63fa000)
	libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xb63f6000)
	libXfixes.so.3 => /usr/lib/i386-linux-gnu/libXfixes.so.3 (0xb63f0000)
	libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xb63e9000)

A continuing minor issue is the systray icon without transparency

As far as a unity launcher icon if desired to open  amarok - I altered the Exec= in the .desktop from Exec=amarok to Exec=amarokapp
This way a pinned icon opens amarok without a 2nd icon opening. 
(maybe could develop some quicklists, dunno yet

If you want to go trinity source, either as is or when they do a precise set let me know...

---

### Post by dentaku65 on 2012-04-09
I've tried your method on Precise, but I'm stuck with this error on make command

> grep: /usr/lib/libgnutls.la: No such file or directory
/bin/sed: can't read /usr/lib/libgnutls.la: No such file or directory
libtool: link: `/usr/lib/libgnutls.la' is not a valid libtool archive
make[5]: *** [libamarok_ipod-mediadevice.la] Error 1
make[5]: Leaving directory `/home/sava/Source/amarok-1.4.10/amarok/src/mediadevice/ipod'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/sava/Source/amarok-1.4.10/amarok/src/mediadevice'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/sava/Source/amarok-1.4.10/amarok/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/sava/Source/amarok-1.4.10/amarok'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sava/Source/amarok-1.4.10'
make: *** [all] Error 2


---

### Post by mc4man on 2012-04-09
Are you on a 64 bit bit install?
(didn't have a chance to try that yet & there have been all these multiarch changes

Tonight maybe I'll do a 64 bit install & see if that's what you have (or anyway to see

Edit - have a few minutes so tried on a Fresh 64 bit - went fine - maybe run a make distclean, run a new configure & post

Attached complete build log from **64 bit**, maybe some use, maybe not

Otherwise only diff from 11.10
```
sudo apt-get install libgpod-common libgpod-dev libgpod4  libxine-dev \
libtag1-dev libsqlite3-dev libmysqlclient-dev libpq-dev \
libvisual-0.4-dev libsdl1.2-dev libifp-dev libxine1 libxine1-ffmpeg \
build-essential checkinstall ruby ruby-dev libruby libltdl-dev libxmu-dev \
libjpeg-dev libmng-dev libcups2-dev libart-2.0-dev libacl1-dev libattr1-dev \
libaspell-dev libbz2-dev libjasper-dev libopenexr-dev libpcre3-dev liblualib50-dev \
libsasl2-dev libtiff4-dev libxml2-dev  gettext-kde libxslt1-dev  kdelibs5-data \
libavahi-common-dev qt3-dev-tools python-scour pkg-kde-tools kdesdk-scripts \
libjpeg62 libidn11-dev
```

add. packages - 
```
$ ls /home/doug/Desktop/ama_deps 
kdelibs4c2a_3.5.10.dfsg.1-5ubuntu2_amd64.deb   libmp4v2-0_1.6dfsg-0.2ubuntu9_amd64.deb
kdelibs4-dev_3.5.10.dfsg.1-5ubuntu2_amd64.deb  libmp4v2-dev_1.6dfsg-0.2ubuntu9_amd64.deb
kdelibs-data_3.5.10.dfsg.1-5ubuntu2_all.deb    libmpeg4ip-0_1.6dfsg-0.2ubuntu9_amd64.deb
libavahi-qt3-1_0.6.30-0ubuntu2_amd64.deb       libmpeg4ip-dev_1.6dfsg-0.2ubuntu9_amd64.deb
libavahi-qt3-dev_0.6.30-0ubuntu2_amd64.deb
```

---

### Post by dentaku65 on 2012-04-09
> **mc4man said:**
> Are you on a 64 bit bit install?
(didn't have a chance to try that yet & there have been all these multiarch changes

Tonight maybe I'll do a 64 bit install & see if that's what you have (or anyway to see

Edit - have a few minutes so tried on a Fresh 64 bit - went fine - maybe run a make distclean, run a new configure & post

Attached complete build log from **64 bit**, maybe some use, maybe not

Otherwise only diff from 11.10
```
sudo apt-get install libgpod-common libgpod-dev libgpod4  libxine-dev \
libtag1-dev libsqlite3-dev libmysqlclient-dev libpq-dev \
libvisual-0.4-dev libsdl1.2-dev libifp-dev libxine1 libxine1-ffmpeg \
build-essential checkinstall ruby ruby-dev libruby libltdl-dev libxmu-dev \
libjpeg-dev libmng-dev libcups2-dev libart-2.0-dev libacl1-dev libattr1-dev \
libaspell-dev libbz2-dev libjasper-dev libopenexr-dev libpcre3-dev liblualib50-dev \
libsasl2-dev libtiff4-dev libxml2-dev  gettext-kde libxslt1-dev  kdelibs5-data \
libavahi-common-dev qt3-dev-tools python-scour pkg-kde-tools kdesdk-scripts \
libjpeg62 libidn11-dev
```

add. packages - 
```
$ ls /home/doug/Desktop/ama_deps 
kdelibs4c2a_3.5.10.dfsg.1-5ubuntu2_amd64.deb   libmp4v2-0_1.6dfsg-0.2ubuntu9_amd64.deb
kdelibs4-dev_3.5.10.dfsg.1-5ubuntu2_amd64.deb  libmp4v2-dev_1.6dfsg-0.2ubuntu9_amd64.deb
kdelibs-data_3.5.10.dfsg.1-5ubuntu2_all.deb    libmpeg4ip-0_1.6dfsg-0.2ubuntu9_amd64.deb
libavahi-qt3-1_0.6.30-0ubuntu2_amd64.deb       libmpeg4ip-dev_1.6dfsg-0.2ubuntu9_amd64.deb
libavahi-qt3-dev_0.6.30-0ubuntu2_amd64.deb
```

I did a make distclean and configure again
```
./configure --without-arts  LDFLAGS='-lkdecore -lDCOP -lkdefx -lkparts'
```
But during the make I get this error again
> grep: /usr/lib/libgnutls.la: No such file or directory
/bin/sed: can't read /usr/lib/libgnutls.la: No such file or directory
libtool: link: `/usr/lib/libgnutls.la' is not a valid libtool archive
make[5]: *** [libamarok_ipod-mediadevice.la] Error 1
make[5]: Leaving directory `/home/sava/Source/amarok-1.4.10/amarok/src/mediadevice/ipod'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/sava/Source/amarok-1.4.10/amarok/src/mediadevice'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/sava/Source/amarok-1.4.10/amarok/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/sava/Source/amarok-1.4.10/amarok'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sava/Source/amarok-1.4.10'
make: *** [all] Error 2


Runing xubuntu precise 32bit

---

### Post by mc4man on 2012-04-09
> **dentaku65 said:**
> I did a make distclean and configure again
```
./configure --without-arts  LDFLAGS='-lkdecore -lDCOP -lkdefx -lkparts'
```
But during the make I get this error again


Runing xubuntu precise 32bit
Unfortunately I tend to resolve such things thru trial & error (attempted logically) rather than any grand knowledge - 
Give me a hr or 2 & I'll try on a live xubuntu session, should have enough ram to do

Is libgnutls-dev installed (should be), & is there a /usr/lib/i386-linux-gnu/libgnutls.a & a /usr/lib/i386-linux-gnu/pkgconfig/gnutls.pc

I guess the first thing I'd try is adding it to the configure though don't think it's exactly proper

```
./configure --without-arts  LDFLAGS='-lkdecore -lDCOP -lkdefx -lkparts -lgnutls'

```
(Though for that build, no mp4v2, I still use --enable-mysql

Have you built any related packages like gpod or installed  non-repo packages?

If unresolvable maybe some of the talented people in the dev/compiling sub-forum would know

As seen here the plugin does link on my various ubuntu builds

ldd  /usr/lib/kde3/libamarok_ipod-mediadevice.so
.....clipped
libgnutls.so.26 => /usr/lib/i386-linux-gnu/libgnutls.so.26 (0xb4c28000)

The other thing you could do is **after** a ./configure attach here the makefile from amarok/src/mediadevice/ipod

---

### Post by mc4man on 2012-04-09
Booted to todays Xubuntu image & did the build in the live session
Other then I've never used Xubuntu all went fine
Used my posted ./configure & the same without mysql, both went fine & amarok is up & running

So I guess you could spend some time to try to figure what's gone south with your install or at some point copy out anything of interest & do a fresh install
I'd go for the latter, dev installs can go bad & sometimes best to abandon & start fresh
You could ck. that those files I mentioned are installed, maybe purge libgnutls-dev & re-install it & whatever else gets removed.
(also re-run  the apt-get, then the dpkg -i *.deb

---

### Post by dentaku65 on 2012-04-10
> **mc4man said:**
> Booted to todays Xubuntu image & did the build in the live session
Other then I've never used Xubuntu all went fine
Used my posted ./configure & the same without mysql, both went fine & amarok is up & running

So I guess you could spend some time to try to figure what's gone south with your install or at some point copy out anything of interest & do a fresh install
I'd go for the latter, dev installs can go bad & sometimes best to abandon & start fresh
You could ck. that those files I mentioned are installed, maybe purge libgnutls-dev & re-install it & whatever else gets removed.
(also re-run  the apt-get, then the dpkg -i *.deb

Thx mac4man for your support,

I've tried everything from the begininng but I still have the same issue 
> /bin/bash ../../../../libtool --silent --tag=CXX   --mode=link g++  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION  -avoid-version -module -no-undefined -Wl,--no-undefined -Wl,--allow-shlib-undefined -R /usr/lib -R /usr/lib -R /usr/lib  -pthread -L/usr/local/lib -lgpod -lgdk_pixbuf-2.0 -limobiledevice -lgobject-2.0 -lplist -lusbmuxd -lgthread-2.0 -lrt -lgnutls -ltasn1 -lglib-2.0    -lkdecore -lDCOP -lkdefx -lkparts -lgnutls -o libamarok_ipod-mediadevice.la -rpath /usr/lib/kde3 ipodmediadevice.lo ../../../../amarok/src/libamarok.la 
grep: /usr/lib/libgnutls.la: No such file or directory
/bin/sed: can't read /usr/lib/libgnutls.la: No such file or directory
libtool: link: `/usr/lib/libgnutls.la' is not a valid libtool archive
make[5]: *** [libamarok_ipod-mediadevice.la] Error 1
make[5]: Leaving directory `/home/sava/Source/amarok-1.4.10/amarok/src/mediadevice/ipod'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/sava/Source/amarok-1.4.10/amarok/src/mediadevice'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/sava/Source/amarok-1.4.10/amarok/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/sava/Source/amarok-1.4.10/amarok'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sava/Source/amarok-1.4.10'
make: *** [all] Error 2


I've also tried to find libgnutls.la and does not exist on my box
```
sudo updatedb && locate libgnutls.la
```

I think that the issue is derived somehow because I did a version upgrade (from Lucid to Precise); of course the libgnutls-dev is installed.
:confused:

---

### Post by mc4man on 2012-04-10
> **dentaku65 said:**
> Thx mac4man for your support,

I've tried everything from the begininng but I still have the same issue 


I've also tried to find libgnutls.la and does not exist on my box
```
sudo updatedb && locate libgnutls.la
```

I think that the issue is derived somehow because I did a version upgrade (from Lucid to Precise); of course the libgnutls-dev is installed.
:confused:
Well it can't find because it doesn't exist in 12.04 but did in 10.04

I'd try a purge. & re-install (maybe even restart/ldconfig in between

If still no go then it's worthy of a bug report

[http://packages.ubuntu.com/lucid/libgnutls-dev/filelist](http://packages.ubuntu.com/lucid/libgnutls-dev/filelist)

[http://packages.ubuntu.com/precise/libgnutls-dev/filelist](http://packages.ubuntu.com/precise/libgnutls-dev/filelist)

Edit maybe also re-install libtool libltdl-dev ?

---

### Post by jamesdeser on 2012-04-10
I guess you could spend some time to try to figure what's gone south with your install or at some point copy out anything of interest & do a fresh install I'd go for the latter, dev installs can go bad & sometimes best to abandon & start fresh You could ck. that those files I mentioned are installed, maybe purge libgnutls-dev & re-install it & whatever else gets removed.

---

### Post by dentaku65 on 2012-04-10
> **mc4man said:**
> Well it can't find because it doesn't exist in 12.04 but did in 10.04

I'd try a purge. & re-install (maybe even restart/ldconfig in between

If still no go then it's worthy of a bug report

[http://packages.ubuntu.com/lucid/libgnutls-dev/filelist](http://packages.ubuntu.com/lucid/libgnutls-dev/filelist)

[http://packages.ubuntu.com/precise/libgnutls-dev/filelist](http://packages.ubuntu.com/precise/libgnutls-dev/filelist)

Edit maybe also re-install libtool libltdl-dev ?

I confirm, this file do not exist in Precise
[http://packages.ubuntu.com/search?suite=precise&arch=i386&searchon=contents&keywords=libgnutls.la](http://packages.ubuntu.com/search?suite=precise&arch=i386&searchon=contents&keywords=libgnutls.la)

---

### Post by dentaku65 on 2012-04-10
Ok, in a very bad manner, I think I solved the problem.

1) follow all the guide of mc4man

Then
```
./configure --without-arts [COLOR="Red"]--without-gnutls[/COLOR] LDFLAGS='-lkdecore -lDCOP -lkdefx -lkparts [COLOR="Red"]-lgnutls[/COLOR]'
```

Then
```
make
```

Then
```
sudo make install
```

Then
```
sudo apt-get install libmusicbrainz4-dev libvorbis-dev libflac-dev libogg-dev libmad0-dev libmpcdec-dev libcurl4-gnutls-dev libofa0-dev libcurl4-gnutls-dev libmusicbrainz3-dev 
```

Then
Download (your arch)
[http://packages.ubuntu.com/oneiric/libtunepimp5](http://packages.ubuntu.com/oneiric/libtunepimp5)
[http://packages.ubuntu.com/oneiric/libtunepimp-dev](http://packages.ubuntu.com/oneiric/libtunepimp-dev)

Then
```
sudo dpkg -i libtunepimp5_0.5.3-7.4ubuntu1_i386.deb libtunepimp-dev_0.5.3-7.4ubuntu1_i386.deb
```

Then
```
sudo ln -s /usr/lib/libmusicbrainz3.so.6 /usr/lib/libmusicbrainz.so.4
```

Finaly got Amarok 1.4 to works!

---

### Post by mc4man on 2012-04-10
> **dentaku65 said:**
> 
1) follow all the guide of mc4man
Then
```
./configure --without-arts [COLOR="Red"]--without-gnutls[/COLOR] LDFLAGS='-lkdecore -lDCOP -lkdefx -lkparts [COLOR="Red"]-lgnutls[/COLOR]'
```


The --without-gnutls would only be possibly needed for upgraders to 12.04, not fresh installs
Maybe this weekend I'll put up a 10.04, upgrade & see what's up.

If you have the chance - how did you do the upgrade, thru update-manager or something else?

---

### Post by dentaku65 on 2012-04-11
> **mc4man said:**
> The --without-gnutls would only be possibly needed for upgraders to 12.04, not fresh installs
Maybe this weekend I'll put up a 10.04, upgrade & see what's up.

If you have the chance - how did you do the upgrade, thru update-manager or something else?

Yes, update-manager -d

---

