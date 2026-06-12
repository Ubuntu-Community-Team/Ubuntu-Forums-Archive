---
title: "How-To: Compile Amarok 1.4.10 in Ubuntu 10.04 &quot;Lucid Lynx&quot;"
date: 2010-05-05
forum: Multimedia Software
---

### Post by Seegorkesolot on 2010-05-05
Hi everyone

As my previous thread about compiling the good old Amarok 1.4.10 for 9.10 and make it work properly again was well accepted, I post here the script for doing the same for the recent version 10.04.
In the old thread, there are some really great improvements like a better wiki-patch: [http://ubuntuforums.org/showthread.php?t=1307737](http://ubuntuforums.org/showthread.php?t=1307737)

```

#!/bin/sh

echo  '********************************************************************************************'
echo '*******This script will install amarok 1.4.10 with some recent  patches in Ubuntu 10.04**********'
echo  '********************************************************************************************'

sleep 3

echo
echo '*******************Installing dependencies*******************'
sleep 2
echo "Installing dependencies"
sudo apt-get install -q ruby-dev libtag1-dev qt4-dev-tools qt3-dev-tools kdelibs4-dev x-dev libxine-dev libgtk2-ruby libxine1-all-plugins

sleep 3

sudo apt-get install -q libdbus-qt-1-dev  libsqlite3-dev libtunepimp-dev libmysqlclient15-dev  libpq-dev libvisual-0.4-dev libsdl1.2-dev libifp-dev libusb-dev   libnjb-dev  x11proto-core-dev automake libtool  libxine1 libxine1-ffmpeg build-essential

sleep 3

sudo apt-get install ruby-dev libtag1-dev qt4-dev-tools qt3-dev-tools kdelibs4-dev x-dev libxine1

sleep 3

echo
echo '*******************Installing iPod Support  dependencies*******************'
sudo apt-get install libgpod-common libgpod4 libgpod-dev gtkpod
cd ~/Downloads
echo '*******************Dependencies installed!*******************'
sleep 2

echo
echo '*******************Fetching and applying  patches*******************'
sleep 2
wget  http://download.kde.org/stable/amarok/1.4.10/src/amarok-1.4.10.tar.bz2
tar -xvf amarok-1.4.10.tar.bz2
cd amarok-1.4.10

sleep 5

wget http://bugs.kde.org/attachment.cgi?id=32838 -O  amarok-1.4.10-gcc44.patch
patch -p1 < amarok-1.4.10-gcc44.patch

sleep 3

wget  http://mail.kde.org/pipermail/amarok/attachments/20090822/52116f4a/attachment-0001.dll  -O covermanager-fix.patch
patch -p1 < covermanager-fix.patch

sleep 3

wget  http://launchpadlibrarian.net/34885946/99_fix_wikipedia_lookup.patch -O  wikipedia-lookup.patch
patch -p1 < wikipedia-lookup.patch

sleep 3

sed 's/return " (band)";/return "";/g' amarok/src/contextbrowser.cpp  > amarok/src/contextbrowser.cpp.tmp
sed 's/return " (Band)";/return "";/g' amarok/src/contextbrowser.cpp.tmp  > amarok/src/contextbrowser.cpp

sed 's/return " (album)";/return "";/g' amarok/src/contextbrowser.cpp  > amarok/src/contextbrowser.cpp.tmp
mv amarok/src/contextbrowser.cpp.tmp amarok/src/contextbrowser.cpp

sed 's/return " (song)";/return "";/g' amarok/src/contextbrowser.cpp  > amarok/src/contextbrowser.cpp.tmp
mv amarok/src/contextbrowser.cpp.tmp amarok/src/contextbrowser.cpp
echo '*******************Patching DONE!*******************'
sleep 5

echo
echo '*******************Configuring..*******************'
sleep 2
./configure --without-arts
echo '*******************Configuring DONE!*******************'

sleep 5

echo
echo '*******************Building..*******************'
sleep 2
make
echo '*******************Building DONE!*******************'

sleep 5

echo
echo '*******************Installing..*******************'
sleep 2
sudo make install
echo '*******************Installing DONE!*******************'
 
sleep 5

echo
echo '*******************Cleaning up..*******************'
rm -r ~/Downloads/amarok*

sleep 2

echo
echo '*******************Everything done!*******************'

```The **~/** before Downloads makes sure, that you can run the  script from wherever you are in your system (stands for your home  directory). Further, omit the **checkinstall** line, as this is not  necessary in a script.. The sleep commands in between allow users to  check, if everything went fine before going to the next step.

I can confirm the above script is working and Amarok 1.4.10 is set up  correctly on a justsetup system.

And yes, I was to lazy too write a proper error handling^^

NOTE: I didn't perform any larger testing.. Open the program an playback  worked. My iPod worked also including artwork.
-------------------------------------

By the way: Because of self-compiling, a nice little extension program  is working again, **amarokFS** (FullScreen).
That's the way to install it:
```
cd ~/Downloads
wget  http://www.kde-apps.org/CONTENT/content-files/52641-amarokFS-0.5.tar.gz
tar -xvf 52641-amarokFS-0.5.tar.gz
cd amarokFS-0.5
make
sudo make install
```

Have fun and good luck!

If there are any issues, please feel free to mock about them ;-)

Greetz

---

### Post by lenticular on 2010-05-08
I've run the script you have so kindly provided, but can't figure out where the executable lives (or maybe I don't know what it is called).  Can you give me a pointer, please?

Thanks!

---

### Post by Seegorkesolot on 2010-05-09
Hi lenticular

The bin-file should be ```
/usr/bin/amarok
```A useful terminal command concerning your question is```
whereis nameofapplication
``````
~$ whereis amarok
amarok: /usr/bin/amarok

```You can start amarok in the terminal as well with the command ```
amarok
```

---

### Post by lenticular on 2010-05-09
Thanks! I will give that a shot.

---

### Post by jnbptst on 2010-05-12
Hey,

hasn't been working for me. during the script's execution i get an error message saying "amarok will not be built" but then it disappears under the new lines...

there used to be a repository with amarok 1.4 for jaunty, hasn't it been updated with lucid? it was a much easier process.

---

### Post by mc4man on 2010-05-12
> i get an error message saying "amarok will not be built" but...
You probably failed the configure for some reason.

While I have no use for amarok 1.4.10 (use a self built pana instead), did run the script to see (removed the make install section

Initially it failed, but only due to the presence of libmtp-dev, the lucid version is autodetected and too new.
Removing from build (--without-libmtp) allowed it to succeed just fine.

Personally I'd go with [the pana source]("https://launchpad.net/pana/+download") instead (atm use the .15) - easy to build and checkinstall or build as a debian package set.

As far as a pana ppa - here's a good one - though be aware that the ppa has other packages. If you leave enabled after installing pana and blindly run the update manager you may update something you don't wish ( though not that many atm for lucid - nvidia drivers being the most significant.

[https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra)

---

### Post by valentt on 2010-05-16
After installation typing amarok in bash doesn't start Amarok.

Where is bin file located? How to start it?

---

