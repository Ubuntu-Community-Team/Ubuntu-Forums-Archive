---
title: "How-To: Compile Amarok 1.4.10 in Ubuntu 9.10 &quot;Karmic Koala&quot;"
date: 2009-10-31
forum: Multimedia Software
---

### Post by Seegorkesolot on 2009-10-31
Well, I'm new to the forum, but I thought, that this howto may be worth being posted.

As a huge fan of Amarok I was a little distraced in Jaunty by the changes that the new Amarok 2 and so on implied and switched back to 1.4

In Karmic, I decided to give Amarok 2.2 a try but stated, that there's still a lot to do until the program reaches the quality of 1.4.10.

Which meant, that I installed the old version again. In order to avoid any foreign ppa, I compiled it from source. This is how I did this:

NOTE: An existing Installation of amarok 2 will be broken after the following steps, so backup you data!
----------------------------------

(Start a terminal)

**First**: Satisfy dependencies (I'm not sure, if all of them are really necessary)

```
sudo apt-get install kdelibs4-dev libxine-dev libdbus-qt-1-dev libtag1-dev libsqlite3-dev libtunepimp-dev libmysqlclient15-dev libpq-dev libvisual-0.4-dev libsdl1.2-dev libifp-dev
libusb-dev  libnjb-dev ruby ruby1.8-dev  x11proto-core-dev automake libtool
[COLOR=Black]libxine1 libxine1-ffmpeg[/COLOR] build-essential checkinstall
```For iPod support:
```

sudo apt-get install libgpod-common libgpod4 libgpod-dev gtkpod

```[B]
Second[/B]: Download and install the source code to a directory you wish. I used here my Downloads Folder and enter the folder
```
cd Downloads
wget http://download.kde.org/stable/amarok/1.4.10/src/amarok-1.4.10.tar.bz2
tar -xvf amarok-1.4.10.tar.bz2
cd amarok-1.4.10
```[B]

Third[/B]: Well, the source and the 4.4 Version of the GNU C/#/++-Compilers do not work that well and amarok 1.4 isn't maintained anymore. So we have to apply a patch which will change the code to an up-to-date state (the one who wants can apply here a patch for the non-functioning cover-fetcher as well).

```

wget http://bugs.kde.org/attachment.cgi?id=32838 -O amarok-1.4.10-gcc44.patch
patch -p1 < amarok-1.4.10-gcc44.patch

```(covermanager-fix:
```

wget http://mail.kde.org/pipermail/amarok/attachments/20090822/52116f4a/attachment-0001.dll -O covermanager-fix.patch
patch -p1 < covermanager-fix.patch 

```)

**Fourth**: Wikipedia-Fix
Getting the Wikipedia infos is broken in the origin code. So we'll patch it with a solution provided on launchpad ([https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/316140/](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/316140/))

```
wget http://launchpadlibrarian.net/34885946/99_fix_wikipedia_lookup.patch -O wikipedia-lookup.patch
patch -p1 < wikipedia-lookup.patch
```I wasn't that satisfied with the search results. It was looked for "artist (band)" etc. which resulted in almost no success. So I changed two lines in the code with the following two commands to look for just the artist and so improve the results of wikipedia search.

```
sed 's/return " (band)";/return "";/g' amarok/src/contextbrowser.cpp > amarok/src/contextbrowser.cpp.tmp
sed 's/return " (Band)";/return "";/g' amarok/src/contextbrowser.cpp.tmp > amarok/src/contextbrowser.cpp

sed 's/return " (album)";/return "";/g' amarok/src/contextbrowser.cpp > amarok/src/contextbrowser.cpp.tmp
mv amarok/src/contextbrowser.cpp.tmp amarok/src/contextbrowser.cpp

sed 's/return " (song)";/return "";/g' amarok/src/contextbrowser.cpp > amarok/src/contextbrowser.cpp.tmp
mv amarok/src/contextbrowser.cpp.tmp amarok/src/contextbrowser.cpp
```[B]

Fifth[/B]: Compile and install the source code
Since I'm under ***gnome*** I need to use the ./configure script with a flag, otherwise the KDE SoundSystem will not be found..
```
./configure --without-arts
make
```For ***Kubuntu*** the flag isn't necessary (hopefully ;-))
```
./configure
make
```This should run through without errors, otherwise something isn't set up correctly yet!

Now for installing:
If you want a .deb package created use checkinstall
Probably, there will be error messages during the install and nothing is installed, but the package is created anyway
```
sudo checkinstall --pkgname amarok1410 --pkgversion 1.0
```For finally installing use make install
```
sudo make install
```And then you're done!

NOTE: I didn't perform any larger testing.. Open the program an playback worked. My iPod worked also including artwork.
-------------------------------------

By the way: Because of self-compiling, a nice little extension program is working again, **amarokFS** (FullScreen).
That's the way to install it:
```
cd ~/Downloads
wget http://www.kde-apps.org/CONTENT/content-files/52641-amarokFS-0.5.tar.gz
tar -xvf 52641-amarokFS-0.5.tar.gz
cd amarokFS-0.5
make
sudo make install
```Have fun and good luck! ;)

See

---

### Post by wattz3 on 2009-11-10
Thank you very much! Worked great for me!

The only thing I would add, is after running the command checkinstall, modify the "Package" and "Provides" fields. 
This will prevent package manager from trying to upgrade to version 2.x automatically.


```

# checkinstall

This package will be built according to these values: 

0 -  Maintainer: [ root@baaam ]
1 -  Summary: [ Amarok 1.4.10 - ubuntu 9.10 compile ]
2 -  Name:    [ amarok1410 ]
3 -  Version: [ 1.4.10 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ amarok-1.4.10 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ amarok1410 ]
```

---

### Post by andrew.46 on 2009-11-10
Hi wattz3,

> **wattz3 said:**
> The only thing I would add, is after running the command checkinstall, modify the "Package" and "Provides" fields. 
This will prevent package manager from trying to upgrade to version 2.x automatically.

Better than doing it *after* running the checkinstall command is perhaps to add it in with the actual checkinstall command line:

```
$ sudo checkinstall --pkgname xxxxx --pkgversion xxxxx
```

With a careful look at the naming conventions used by Ubuntu and the amarok package you should be able to easily defeat your version being overwritten by the repository.

Andrew

---

### Post by Seegorkesolot on 2009-11-11
Thanks to both of you for this simple and obvious but elegant solution!

However, with make install, I hadn't any problems with Update Manager trying to upgrade. But creating a proper and functioning .deb is the nicer way of doing this, of course ;)

---

### Post by weazie on 2009-11-14
checking for kde-config... not found
configure: error: The important program kde-config was not found!
Please check whether you installed KDE correctly.

Where to find the package kde-config?
I have KDE installed with amarok 2.2, which I removed.

weazie

EDIT:

Ok it was just a tip of the iceberg of missing dependecies...
I gave up.

---

### Post by Seegorkesolot on 2009-11-14
Hi weazie

Please check if you have installed the package kdebase-dev. If not, try to compile it again with the installed dev-files for KDE.

Otherwise install Amarok 2 again and try to compile 1.4.10 without removing the new version.

Good luck! And if there are still problems, please don't hesitate to bring them up!

---

### Post by weazie on 2009-11-14
Hi,

Thanks for help.
What I did was that I googled every error and installed the missing packages with synaptic.
got pretty far with that..

I ran out of patience with this:

>checking for KDE... configure: error:
>in the prefix, you've chosen, are no KDE libraries installed. This will >fail.
>So, check this please and use another prefix!
 [http://www.fedoraforum.org/forum/archive/index.php/t-18389.html](http://www.fedoraforum.org/forum/archive/index.php/t-18389.html)

Maybe someone will continue from that...

Thanks again.

---

### Post by Seegorkesolot on 2009-11-15
Yeah, that's pretty much the same thing as I did, as I wrote this howto.
Well, the problem with this is that I missed the dependencies that were already installed on my system.
I'm sorry for this inconvenience.

So, according to your problem:
Check, if following package is installed

```

kdelibs4-dev

```

Such development packages are essential for building packages from source. Missing dev packages lead to the paradox situation, that although KDE is installed and running, such an error can occur during configure.

See

---

### Post by mc4man on 2009-11-15
nice job with the patches and overall.

The build deps seems a bit incomplete and has 2 packages that don't exist ( xlibs-dev, devtools 

This may be a bit more suitable and adds a check for decent build tools, some who use this may not have built anything before ( blue are needed runtime deps

```
sudo apt-get install kdelibs4-dev libxine-dev libdbus-qt-1-dev libtag1-dev libsqlite3-dev \
libtunepimp-dev libmysqlclient15-dev libpq-dev libvisual-0.4-dev libsdl1.2-dev libifp-dev \
libusb-dev  libnjb-dev ruby ruby1.8-dev  x11proto-core-dev automake libtool \
[COLOR="Blue"]libxine1 libxine1-ffmpeg[/COLOR] build-essential checkinstall
```

plus ipod packages as you noted if desired

---

### Post by Seegorkesolot on 2009-11-15
Hi mc4man

Thanks a lot for your input, that's just about that, what I had planned to find out next ;-)

However, with your posted command everything should be fine! I wasn't aware, that the two packages you mentioned don't exist.

See

---

### Post by mc4man on 2009-11-15
One was long gone, don't think the other ever existed, though you picked up some needed deps with the  dependency package you had (ruby-dev) and the dummy (x-dev). I substituted the actual ones there.

I'm all for keeping amarok 1.4 going as long as possible, hopefully good to go for the 10.04  LTS.

while amarok2 has some interesting features as far as a music player it doesn't match 1.4 (plus they removed some commands, options I find useful

note: the above deps can install close to 100 packages - tested on a livecd but forgot the note the actual total

---

### Post by andrewkk on 2009-11-16
> **Seegorkesolot said:**
> In order to avoid any foreign ppa, I compiled it from source.

If I knew of a PPA for this I would never have considered compiling from source &#8211; but I don't know very much about this kind of thing. What are your reasons for avoiding a PPA? Is there just not one available, or do you distrust them?

Thanks for the awesome writeup.

---

### Post by Nick Brohman on 2009-11-16
G'day

As a [COLOR=Red]***new use***[/COLOR]r, I would like to know if I add the cover manager patch, will that be added to my amarok14 installation automatically?

I, like everyone here, do not like the new Amarok & much prefer the 1.4... that I had with Hardy & would like to be able to get what covers I can with ease

This is how I got my version (from a bloke with a sense of humour) :-

[Ok, I'm gonna rewite the instructions in Brohmanese. :)

Step 1: Get rid of any amarok packages that you may have installed.

- Go to System->Administration->Synaptic Package Manager and enter your password when prompted.
- Type amarok into the quick search box and press ENTER.
- Look in the results for any packages with the word 'amarok' in them that also has a green status box next to it indicating that it is currently installed.
- For each that you find, right-click and select 'Mark for complete removal'.
- When you're done, click the big green 'Apply' checkmark in the toolbar.
- Close Synaptic Package Manager.


Step 2: Add repositories to /etc/apt/sources.list

- Open up a console terminal then copy & paste the following two line into it one at a time, entering your password when prompted:

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
gksudo gedit /etc/apt/sources.list

- The first command makes a backup of the file we're about to edit.
- The second command bring the file up for editing in the gedit text editor.
- You'll be presented with a copy of your /etc/apt/sources.list file ready for editing. This file contails the internet addresses for all of the respositories of packages that the update manager uses to keep your system up to date.
- If you added any lines to this file in your previous amarok installation attempt then delete them now.
- Next copy & paste the following two lines to the end of the file:

deb [http://ppa.launchpad.net/bogdanb/amarok14/ubuntu](http://ppa.launchpad.net/bogdanb/amarok14/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bogdanb/amarok14/ubuntu](http://ppa.launchpad.net/bogdanb/amarok14/ubuntu) jaunty main

- Save the file and exit from gedit.
- Go back to a terminal and copy & paste the following three lines into it one at a time, entering your password if prompted:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AE74AE63
sudo apt-get update
sudo apt-get install amarok14

- The first command add the security key for the new repository to your keyring.
- The second command refreshes the ist of respositories.
- The third command installs amarok 1.4 and all of its dependencies.

That's it! You should now have a new entry for amarok in Applications->Sound & Video. Just click on it and have a go.]

I had to learn copy & paste first, didn't do things correctly first time but have now used the command lines several times with success.

I say several because this [COLOR=Red]***new user***[/COLOR] is very good at mucking up his system without intent.

***Should I get the Karmic or keep the Jaunty version ?*** Jaunty is working for me, but not having the covers makes it look untidy.

My understanding is that I would **change jaunty to karmic **when pasting the lines to gedit but I'm *[COLOR=Red]unsure of when/where to insert[/COLOR]* the cover command.

Any help & advice is much appreciated.

Cheers...Nicko  :)

---

### Post by mc4man on 2009-11-16
> I would like to know if I add the cover manager patch, will that be added to my amarok14 installation automatically?


No, the patch must be applied to the source before compiling.

> do you distrust them
Can't speak for the OP, but in  terms of this ppa (bogdanb/amarok14) it is fine and quite safe to use.
You won't get the adv. of the patches posted here, otherwise works fine.

In general I almost never use/add a ppa, though occasionally download a package from one.
It's best to view them (ppa's) as a means to get something specific, and not add or leave them enabled without knowing what's in them.

ppa's that contain multiple apps should never be left enabled, or an update thru the update manager may install/update things you don't wish or worse.

---

### Post by andrewkk on 2009-11-16
For those interested in installing Amarok 1.4 from a PPA, there appear to currently be two options:

[LIST=1]
[*]The [PPA for KDE3.5 Maintainers]("https://launchpad.net/~kde3-maintainers/+archive/ppa") is an attempt to keep all of KDE3.5 "a viable Ubuntu desktop environment" and contains a package of Amarok 1.4 for Karmic. I would trust this PPA to be maintained for longer than any individual contributor's PPA.
[*]Bogdan Butnaru's [PPA for Amarok 1.4 series]("https://launchpad.net/~bogdanb/+archive/amarok14") appears to be giving Amarok more special attention than the KDE3.5 Maintainers’ PPA is. While I can't speak for its availability in the long term, it may be the better PPA to use for now.

[/LIST]
> **Nick Brohman said:**
> deb [http://ppa.launchpad.net/bogdanb/amarok14/ubuntu](http://ppa.launchpad.net/bogdanb/amarok14/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bogdanb/amarok14/ubuntu](http://ppa.launchpad.net/bogdanb/amarok14/ubuntu) jaunty main
...
My understanding is that I would **change jaunty to karmic **when pasting the lines to gedit but I'm unsure of when/where to insert the cover command.
[INDENT]Nick, this PPA does not appear to currently have a build of Amarok 1.4 for Karmic, but its maintainer has suggested using the Jaunty build instead:
[QUOTE=Bogdan Butnaru]The Jaunty version of Amarok14 works on Karmic Koala too. If you're already using it on Jaunty you can safely update to Karmic, and it will keep working. If you have a new Karmic installation, you can add the Jaunty PPA and install. I won't do a Karmic release until I have the time to add a patch for the Amazon cover fetching bug that many of you reported.[/QUOTE]

If a Karmic version is added to the PPA, the Apt line will look like:
```
deb http://ppa.launchpad.net/bogdanb/amarok14/ubuntu karmic main
deb-src http://ppa.launchpad.net/bogdanb/amarok14/ubuntu karmic main
```[/INDENT]


mc4man, thanks for the explanation.

---

### Post by Nick Brohman on 2009-11-16
G'day mc4man & andrewkk,

Many thanks for the info, I'll just have to forego the cover art for now.

As for the Karmic version, I'm not disappointed as I find my version to be very good.

Cheers...Nicko

---

### Post by Nick Brohman on 2009-11-17
mc4man & andrewkk, 

I was between a rock & a hard place this morning so I just gleaned that I could not do what I had asked was possible.

I wish to thank you both for your considered replies, both have taught me more than you realise.

I also wish to acknowledge tgeer43 for his original instructions as he is the one responsible for me getting amarok14 in the first instance (& copy & paste).

I shall now study the OP & work out how it is done.

One is never too old to learn & I don't want to stop doing that...I know that there are many who will appreciate this thread as much as myself.

Many thanks...I'll see you in the sunshine.....Nicko

ps I don't understand a lot of what is being said in this thread but for me, it is a great learning tool & for that I'm very grateful.

---

### Post by andrewharvey on 2009-11-20
EDIT: I just installed kdelibs4-dev, and let it remove the other packages. Things seem fine. I then proceded to install Amarok successfully with
```
./configure --prefix=`kde-config --prefix` --without-arts --enable-postgresql --enable-mysql
make
sudo make install
```however even with libvisual-0.4-dev, libvisual-0.4-0 and libvisual-0.4-plugins neither --enable-libvisual or --with-libvisual or just left out entirelly at the ./configure line did I manage to get libvisual visualisations working. Not a big deal though because I don't use them anyway.

original message:

>  I'm using the ppa [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu)
and i have kdelibs5-dev (from the ppa) installed. if i try to install kdelibs4-dev it says that kde-devel, kdebase-workspace-dev, kdelibs5-dev and libkonq5-dev need to be removed.

oh and running ./configure gives
```
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE libraries installed. This will fail.
So, check this please and use another prefix!

```any ideas on what i can do to get around this...?

i'm using 32bit karmic.

---

### Post by Castor68 on 2009-11-22
**Seegorkesolot**: thank you for this thread. It worked perfect for me. I love Amarok and I was very sad because 2.2.0 didn't work in Karmic Koala.

In order to avoid mistakes writing the commands in the terminal, I put all of them in a batch file. This means, I made some of copy+past.

Here is:

```
#!/bin/sh

sudo apt-get install kdelibs4-dev libxine-dev libdbus-qt-1-dev libtag1-dev libsqlite3-dev \
libtunepimp-dev libmysqlclient15-dev libpq-dev libvisual-0.4-dev libsdl1.2-dev libifp-dev \
libusb-dev  libnjb-dev ruby ruby1.8-dev  x11proto-core-dev automake libtool \
libxine1 libxine1-ffmpeg build-essential checkinstall

sudo apt-get install ruby-dev libtag1-dev qt4-dev-tools qt3-dev-tools xlibs-dev kdelibs4-dev x-dev devtools libxine1
sudo apt-get install libgpod-common libgpod4 libgpod-dev gtkpod
cd Downloads

wget [http://download.kde.org/stable/amarok/1.4.10/src/amarok-1.4.10.tar.bz2](http://download.kde.org/stable/amarok/1.4.10/src/amarok-1.4.10.tar.bz2)
tar -xvf amarok-1.4.10.tar.bz2
cd amarok-1.4.10

wget [http://bugs.kde.org/attachment.cgi?id=32838](http://bugs.kde.org/attachment.cgi?id=32838) -O amarok-1.4.10-gcc44.patch
patch -p1 < amarok-1.4.10-gcc44.patch

wget [http://mail.kde.org/pipermail/amarok/attachments/20090822/52116f4a/attachment-0001.dll](http://mail.kde.org/pipermail/amarok/attachments/20090822/52116f4a/attachment-0001.dll) -O covermanager-fix.patch
patch -p1 < covermanager-fix.patch

wget [http://launchpadlibrarian.net/34885946/99_fix_wikipedia_lookup.patch](http://launchpadlibrarian.net/34885946/99_fix_wikipedia_lookup.patch) -O wikipedia-lookup.patch
patch -p1 < wikipedia-lookup.patch

sed 's/return " (band)";/return "";/g' amarok/src/contextbrowser.cpp > amarok/src/contextbrowser.cpp.tmp
sed 's/return " (Band)";/return "";/g' amarok/src/contextbrowser.cpp.tmp > amarok/src/contextbrowser.cpp

sed 's/return " (album)";/return "";/g' amarok/src/contextbrowser.cpp > amarok/src/contextbrowser.cpp.tmp
mv amarok/src/contextbrowser.cpp.tmp amarok/src/contextbrowser.cpp

sed 's/return " (song)";/return "";/g' amarok/src/contextbrowser.cpp > amarok/src/contextbrowser.cpp.tmp
mv amarok/src/contextbrowser.cpp.tmp amarok/src/contextbrowser.cpp

./configure --without-arts
make

sudo checkinstall

sudo make install
```

---

### Post by zenkaon on 2009-11-26
awesome - I love amarok 1.4

Ever since wikipedia and album lookup stopped working I've been playing with other things like:

amarok2 - We're all of the same opinion

rhythembox - terrible, If I can't understand the playlist/library there is no way my wife can (she can't by the way)

Exaile - A very good attempt at a gnome amarok14 - but not quite there yet  

I often ssh into my media PC from my laptop and do everything on the command line with mplayer * commands from an albums directory.

Anyways, I thought I'd add another package to the massive list. This enables MTP support for el-crappo Tesco mp3 players like mine
```

sudo apt-get install libmtp-dev

```

:guitar: :guitar: :guitar: :guitar: :guitar: :guitar: :guitar:

---

### Post by Seegorkesolot on 2009-11-27
Hi everyone

Thank you all for much thinking and trying out for improve my original post. Especially the "summary" posted as shell script posted by Castor68 is helpful for many new users not experienced with self-compiling.

Here are some improvment suggestions:

```

#!/bin/sh

echo '********************************************************************************************'
echo '*******This script will install amarok 1.4.10 with some recent patches in Ubuntu 9.10**********'
echo '********************************************************************************************'

sleep 3

echo
echo '*******************Installing dependencies*******************'
sleep 2
sudo apt-get install kdelibs4-dev libxine-dev libdbus-qt-1-dev libtag1-dev libsqlite3-dev libtunepimp-dev libmysqlclient15-dev libpq-dev libvisual-0.4-dev libsdl1.2-dev libifp-dev libusb-dev  libnjb-dev ruby ruby1.8-dev  x11proto-core-dev automake libtool libxine1 libxine1-ffmpeg build-essential 

sleep 3

sudo apt-get install ruby-dev libtag1-dev qt4-dev-tools qt3-dev-tools xlibs-dev kdelibs4-dev x-dev devtools libxine1

sleep 3

echo
echo '*******************Installing iPod Support dependencies*******************'
sudo apt-get install libgpod-common libgpod4 libgpod-dev gtkpod
cd ~/Downloads
echo '*******************Dependencies installed!*******************'
sleep 2

echo
echo '*******************Fetching and applying patches*******************'
sleep 2
wget http://download.kde.org/stable/amarok/1.4.10/src/amarok-1.4.10.tar.bz2
tar -xvf amarok-1.4.10.tar.bz2
cd amarok-1.4.10

sleep 5

wget http://bugs.kde.org/attachment.cgi?id=32838 -O amarok-1.4.10-gcc44.patch
patch -p1 < amarok-1.4.10-gcc44.patch

sleep 3

wget http://mail.kde.org/pipermail/amarok/attachments/20090822/52116f4a/attachment-0001.dll -O covermanager-fix.patch
patch -p1 < covermanager-fix.patch

sleep 3

wget http://launchpadlibrarian.net/34885946/99_fix_wikipedia_lookup.patch -O wikipedia-lookup.patch
patch -p1 < wikipedia-lookup.patch

sleep 3

sed 's/return " (band)";/return "";/g' amarok/src/contextbrowser.cpp > amarok/src/contextbrowser.cpp.tmp
sed 's/return " (Band)";/return "";/g' amarok/src/contextbrowser.cpp.tmp > amarok/src/contextbrowser.cpp

sed 's/return " (album)";/return "";/g' amarok/src/contextbrowser.cpp > amarok/src/contextbrowser.cpp.tmp
mv amarok/src/contextbrowser.cpp.tmp amarok/src/contextbrowser.cpp

sed 's/return " (song)";/return "";/g' amarok/src/contextbrowser.cpp > amarok/src/contextbrowser.cpp.tmp
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

```The **~/** before Downloads makes sure, that you can run the script from wherever you are in your system (stands for your home directory). Further, omit the **checkinstall** line, as this is not necessary in a script.. The sleep commands in between allow users to check, if everything went fine before going to the next step.

I can confirm the above script is working and amarok 1.4.10 is set up correctly on a justsetup system.


To the PPA-subject: Well, it's not that I distrust the mentioned ppa's, I used them in jaunty for instance and read that this ppa is also working for karmic, before I wrote this howto. I just do not like to be dependend of anything I can't manage;)

And of course, as mc4man already mentioned, I really aimed to fix things  with the patches that didn't work anymore.

@andrewharvey: Yes, the really necessary dependencies is one thing I'm still wondering about. But anyway, I don't think you will get everything to run as amarok is based on kde3-libs and there are maybe some things that will not work without heavy source editing.. But it's still worth a try of course;)

---

### Post by zenkaon on 2009-12-10
Hello,

You may have noticed that in post-KDE3 environments like karmic, when you build amarok 1.4 the artist icons are missing in the left hand column - it's clear that they are missing - you get some default "cannot find icon" icon.

I have a tarball of the needed icons, with instructions at this website:
[http://pprc.qmul.ac.uk/~jmorris/personal/amarok/](http://pprc.qmul.ac.uk/~jmorris/personal/amarok/)

Basically you download and unpack the tarball in the correct directory and restart amarok and you have working icons.

Everything looks better. Enjoy!

---

### Post by Seegorkesolot on 2009-12-11
Ok, I never realized they were missing ;) But as I copied them and restarted amarok, I just had to say "Ahh!":P

Thanks for the input:popcorn:

---

### Post by mc4man on 2009-12-11
While possibly a bit premature, I'd like to see amarok 1.4 available for those that wish in lucid.
There  be an issue or 2 building based on some extensive patching of kdelibs4c2a in lucid though obviously alpha1 1 is a bit early to form definite conclusions. (and possibly the lucid gcc may also come into play

A couple of quick tests builds failed, fixed the first cause, the 2nd seemed directly related to kdelibs4c2a and haven't pursued as of yet.

In any event I took a package built on karmic and installed in lucid A1 to test. Atm works fine, though it appears aac decoding (thru libfaad) has been removed from libxine1-ffmpeg and not enabled otherwise as of yet for xine based players.
( also tested aac on xine-ui, no go 

Have restored aac for xine in lucid by rebuilding the libxine1-ffmpeg package, what the intentions are in lucid in this regard are unclear ( at least to me.

---

### Post by Jp81 on 2009-12-21
> **Seegorkesolot said:**
> 
**Fourth**: Wikipedia-Fix
Getting the Wikipedia infos is broken in the origin code. So we'll patch it with a solution provided on launchpad ([https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/316140/](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/316140/))

```
wget http://launchpadlibrarian.net/34885946/99_fix_wikipedia_lookup.patch -O wikipedia-lookup.patch
patch -p1 < wikipedia-lookup.patch
```I wasn't that satisfied with the search results. It was looked for "artist (band)" etc. which resulted in almost no success. So I changed two lines in the code with the following two commands to look for just the artist and so improve the results of wikipedia search.

```
sed 's/return " (band)";/return "";/g' amarok/src/contextbrowser.cpp > amarok/src/contextbrowser.cpp.tmp
sed 's/return " (Band)";/return "";/g' amarok/src/contextbrowser.cpp.tmp > amarok/src/contextbrowser.cpp

sed 's/return " (album)";/return "";/g' amarok/src/contextbrowser.cpp > amarok/src/contextbrowser.cpp.tmp
mv amarok/src/contextbrowser.cpp.tmp amarok/src/contextbrowser.cpp

sed 's/return " (song)";/return "";/g' amarok/src/contextbrowser.cpp > amarok/src/contextbrowser.cpp.tmp
mv amarok/src/contextbrowser.cpp.tmp amarok/src/contextbrowser.cpp
```
I recommend to use the patch below instead of wikipedia-lookup.patch and those sed commands. With that patch Amarok looks first for "artist (band)". If that fails, Amarok looks for "artist".

```
--- a/amarok/src/contextbrowser.cpp	2009-12-21 18:50:18.000000000 +0200
+++ b/amarok/src/contextbrowser.cpp	2009-12-21 18:33:08.000000000 +0200
@@ -4120,7 +4120,7 @@
          m_wiki = QString::fromUtf8( storedJob->data().data(), storedJob->data().size() );
     }
 
-    if( m_wiki.find( "var wgArticleId = 0" ) != -1 )
+    if( m_wiki.find( "wgArticleId=0," ) != -1 )
     {
         debug() << "Article not found." << endl;
         
@@ -4170,13 +4170,15 @@
     }
 
     // Ok lets remove the top and bottom parts of the page
-    m_wiki = m_wiki.mid( m_wiki.find( "<h1 class=\"firstHeading\">" ) );
+    m_wiki = m_wiki.mid( m_wiki.find( "<h1 " ) );
     m_wiki = m_wiki.mid( 0, m_wiki.find( "<div class=\"printfooter\">" ) );
     // Adding back license information
     m_wiki += copyright;
     m_wiki.append( "</div>" );
     m_wiki.replace( QRegExp("<h3 id=\"siteSub\">[^<]*</h3>"), QString::null );
-
+    m_wiki.replace( QRegExp("<div id=\"jump-to-nav\">Jump to: "
+			    "<a href=\"#column-one\">navigation</a>, "
+			    "<a href=\"#searchInput\">search</a></div>"), QString::null );
     m_wiki.replace( QRegExp( "<span class=\"editsection\"[^>]*>[^<]*<[^>]*>[^<]*<[^>]*>[^<]*</span>" ), QString::null );
 
     m_wiki.replace( QRegExp( "<a href=\"[^\"]*\" class=\"new\"[^>]*>([^<]*)</a>" ), "\\1" );
```

See [http://forum.kde.org/viewtopic.php?f=115&t=81926#p130302](http://forum.kde.org/viewtopic.php?f=115&t=81926#p130302)

---

### Post by Maxei on 2010-01-03
Hi, I want to thank you people for bringing this usefull information. I got tired of using Amarok 2.2 and Rythmbox:  The main reason is because I have the impression of hearing the same songs all the time. This is because (I suppose) these two programs don't have the 'perfect random play' that Amarok 1.4 has (anyone can say the contrary but I know what I'm talking about).

So, I have one little question. How to use the shell script that is proposed to install 1.4? Sorry but never done that kind of thing.

A detailed info for newbies on how to use the shell script will be greatly appreciated. Thanks.

---

### Post by Marrkk on 2010-01-04
you dont need really to compile amarok 1.4 to use un karmic
just do this .. only takes a couple of minutes..

[http://www.ubuntugeek.com/howto-install-amarok-1-4-in-ubuntu-jaunty.html](http://www.ubuntugeek.com/howto-install-amarok-1-4-in-ubuntu-jaunty.html)

---

### Post by dentaku65 on 2010-01-05
Thanks Seegorkesolot!
Your post really rocks!
I've compiled and everything went ok; finally I get back amarok that works after the big delusion of amarok2; thanks to zenkaon too for the icons...
maybe it's time to create a PPA for the real amarok.

:guitar:

---

### Post by boubbin on 2010-01-12
Hi,

Im on a Karmic Kubuntu kde3 remix, so im using kde3 in Karmic Koala.
i cant satisfy all the deps:
```
boubbin@supervisor:~/amarok-kde3-1.4.10$ sudo apt-get install kdelibs4-dev libxine-dev libdbus-qt-1-dev libtag1-dev libsqlite3-dev libtunepimp-dev libmysqlclient15-dev libpq-dev libvisual-0.4-dev libsdl1.2-dev libifp-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
libxine-dev is already the newest version.
libdbus-qt-1-dev is already the newest version.
libtag1-dev is already the newest version.
libsqlite3-dev is already the newest version.
libsqlite3-dev set to manually installed.
libtunepimp-dev is already the newest version.
libmysqlclient15-dev is already the newest version.
libpq-dev is already the newest version.
libvisual-0.4-dev is already the newest version.
libsdl1.2-dev is already the newest version.
libifp-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdelibs4-dev: Depends: kdelibs4c2a (= 4:3.5.10.dfsg.1-2ubuntu7.2) but it is not going to be installed
E: Broken packages
```

and amarok wont compile:
```
make[4]: Entering directory `/home/boubbin/amarok-kde3-1.4.10/amarok/src/amarokcore'
/bin/bash ../../../libtool --silent --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../../.. -I../../../amarok/src -I../../../amarok/src/amarokcore -I../../../amarok/src -I../../../amarok/src/engine -I../../../amarok/src/plugin -I../../../amarok/src/statusbar -I../../../amarok/src/mediadevice -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION  -MT amarokdcophandler.lo -MD -MP -MF .deps/amarokdcophandler.Tpo -c -o amarokdcophandler.lo amarokdcophandler.cpp
In file included from /usr/include/kdecore_export.h:24,
                 from /usr/include/kurl.h:25,
                 from ../../../amarok/src/amarok.h:9,
                 from amarokdcophandler.cpp:22:
In file included from ../../../amarok/src/amarok.h:9,
                 from amarokdcophandler.cpp:22:
/usr/include/kurl.h:27:27: error: QtCore/QVariant: No such file or directory
/usr/include/kurl.h:28:23: error: QtCore/QUrl: No such file or directory
/usr/include/kurl.h:29:23: error: QtCore/QMap: No such file or directory
In file included from amarokdcophandler.cpp:22:
../../../amarok/src/amarok.h:10:38: error: kprocio.h: No such file or directory
In file included from ../../../amarok/src/amarok.h:11,
                 from amarokdcophandler.cpp:22:
/usr/include/kio/netaccess.h:26:26: error: QtCore/QObject: No such file or directory
/usr/include/kio/netaccess.h:27:26: error: QtCore/QString: No such file or directory
In file included from /usr/include/kio/netaccess.h:28,
                 from ../../../amarok/src/amarok.h:11,
                 from amarokdcophandler.cpp:22:
/usr/include/kio/global.h:25:24: error: QtCore/QHash: No such file or directory
/usr/include/kio/global.h:27:24: error: QtCore/QList: No such file or directory
In file included from /usr/include/kio/global.h:30,
                 from /usr/include/kio/netaccess.h:28,
                 from ../../../amarok/src/amarok.h:11,
                 from amarokdcophandler.cpp:22:
/usr/include/kiconloader.h:26:30: error: QtCore/QStringList: No such file or directory
In file included from /usr/include/kiconloader.h:29,
                 from /usr/include/kio/global.h:30,
                 from /usr/include/kio/netaccess.h:28,
                 from ../../../amarok/src/amarok.h:11,
                 from amarokdcophandler.cpp:22:
/usr/include/kglobal.h:23:33: error: QtCore/QAtomicPointer: No such file or directory
In file included from /usr/include/kio/netaccess.h:28,
                 from ../../../amarok/src/amarok.h:11,
                 from amarokdcophandler.cpp:22:
/usr/include/kio/global.h:31:45: error: QtGui/QPixmap: No such file or directory
In file included from /usr/include/kio/global.h:36,
                 from /usr/include/kio/netaccess.h:28,
                 from ../../../amarok/src/amarok.h:11,
                 from amarokdcophandler.cpp:22:
/usr/include/kjob.h:27:24: error: QtCore/QPair: No such file or directory
In file included from /usr/include/kio/netaccess.h:29,
                 from ../../../amarok/src/amarok.h:11,
                 from amarokdcophandler.cpp:22:
/usr/include/kio/udsentry.h:27:30: error: QtCore/QSharedData: No such file or directory
In file included from /usr/include/kio/netaccess.h:31,
                 from ../../../amarok/src/amarok.h:11,
                 from amarokdcophandler.cpp:22:
/usr/include/kio/jobclasses.h:26:30: error: QtCore/QLinkedList: No such file or directory
In file included from /usr/include/kconfig.h:27,
                 from /usr/include/ksharedconfig.h:25,
                 from /usr/include/kcoreconfigskeleton.h:29,
                 from /usr/include/kconfigskeleton.h:28,
                 from amarokconfig.h:8,
                 from amarokdcophandler.cpp:23:
/usr/include/kconfigbase.h:29:27: error: QtCore/QtGlobal: No such file or directory
In file included from /usr/include/ksharedconfig.h:25,
                 from /usr/include/kcoreconfigskeleton.h:29,
                 from /usr/include/kconfigskeleton.h:28,
                 from amarokconfig.h:8,
                 from amarokdcophandler.cpp:23:
/usr/include/kconfig.h:33:29: error: QtCore/QByteArray: No such file or directory
In file included from /usr/include/ksharedconfig.h:26,
                 from /usr/include/kcoreconfigskeleton.h:29,
                 from /usr/include/kconfigskeleton.h:28,
                 from amarokconfig.h:8,
                 from amarokdcophandler.cpp:23:
/usr/include/ksharedptr.h:30:47: error: QtCore/QExplicitlySharedDataPointer: No such file or directory
In file included from /usr/include/kconfiggroup.h:714,
                 from /usr/include/kcoreconfigskeleton.h:30,
                 from /usr/include/kconfigskeleton.h:28,
                 from amarokconfig.h:8,
                 from amarokdcophandler.cpp:23:
/usr/include/conversion_check.h:26:24: error: QtGui/QColor: No such file or directory
/usr/include/conversion_check.h:27:23: error: QtGui/QFont: No such file or directory
/usr/include/conversion_check.h:28:24: error: QtCore/QDate: No such file or directory
/usr/include/conversion_check.h:29:25: error: QtCore/QPoint: No such file or directory
/usr/include/conversion_check.h:30:24: error: QtCore/QSize: No such file or directory
/usr/include/conversion_check.h:31:24: error: QtCore/QRect: No such file or directory
In file included from amarokconfig.h:9,
                 from amarokdcophandler.cpp:23:
/usr/include/kdebug.h:27:25: error: QtCore/QDebug: No such file or directory
In file included from amarokdcophandler.h:24,
                 from amarokdcophandler.cpp:24:
amarokdcopiface.h:23:24: error: dcopobject.h: No such file or directory
In file included from ../../../amarok/src/app.h:24,
                 from amarokdcophandler.cpp:25:
/usr/include/kapplication.h:44:30: error: QtGui/QApplication: No such file or directory
/usr/include/kapplication.h:49:26: error: QtGui/QX11Info: No such file or directory
In file included from ../../../amarok/src/clicklineedit.h:24,
                 from ../../../amarok/src/contextbrowser.h:12,
                 from amarokdcophandler.cpp:28:
/usr/include/klineedit.h:33:27: error: QtGui/QLineEdit: No such file or directory
In file included from /usr/include/kcompletion.h:24,
                 from /usr/include/klineedit.h:35,
                 from ../../../amarok/src/clicklineedit.h:24,
                 from ../../../amarok/src/contextbrowser.h:12,
                 from amarokdcophandler.cpp:28:
/usr/include/kglobalsettings.h:25:26: error: QtGui/QPalette: No such file or directory
In file included from /usr/include/kcompletion.h:26,
                 from /usr/include/klineedit.h:35,
                 from ../../../amarok/src/clicklineedit.h:24,
                 from ../../../amarok/src/contextbrowser.h:12,
                 from amarokdcophandler.cpp:28:
/usr/include/kshortcut.h:33:28: error: QtCore/QMetaType: No such file or directory
/usr/include/kshortcut.h:34:30: error: QtGui/QKeySequence: No such file or directory
In file included from /usr/include/klineedit.h:35,
                 from ../../../amarok/src/clicklineedit.h:24,
                 from ../../../amarok/src/contextbrowser.h:12,
                 from amarokdcophandler.cpp:28:
/usr/include/kcompletion.h:32:27: error: QtCore/QPointer: No such file or directory
In file included from ../../../amarok/src/contextbrowser.h:15,
                 from amarokdcophandler.cpp:28:
/usr/include/ktabwidget.h:27:28: error: QtGui/QTabWidget: No such file or directory
In file included from amarokdcophandler.cpp:28:
../../../amarok/src/contextbrowser.h:16:28: error: ktoolbarbutton.h: No such file or directory
In file included from /usr/include/klocale.h:26,
                 from ../../../amarok/src/metabundle.h:16,
                 from ../../../amarok/src/enginecontroller.h:18,
                 from amarokdcophandler.cpp:31:
/usr/include/klocalizedstring.h:25:24: error: QtCore/QChar: No such file or directory
/usr/include/klocalizedstring.h:26:30: error: QtCore/QLatin1Char: No such file or directory
In file included from amarokdcophandler.cpp:32:
../../../amarok/src/equalizersetup.h:22:25: error: kdialogbase.h: No such file or directory
In file included from /usr/include/khtml_events.h:22,
                 from ../../../amarok/src/htmlview.h:9,
                 from amarokdcophandler.cpp:33:
/usr/include/kparts/event.h:23:27: error: QtGui/QKeyEvent: No such file or directory
In file included from /usr/include/khtml_part.h:32,
                 from ../../../amarok/src/htmlview.h:10,
                 from amarokdcophandler.cpp:33:
/usr/include/kparts/part.h:24:25: error: QtCore/QEvent: No such file or directory
/usr/include/kparts/part.h:25:37: error: QtCore/QSharedDataPointer: No such file or directory
/usr/include/kparts/part.h:26:45: error: QtXml/QDomElement: No such file or directory
In file included from /usr/include/kguiitem.h:28,
                 from /usr/include/kdialog.h:33,
                 from /usr/include/kfind.h:24,
                 from /usr/include/khtml_part.h:35,
                 from ../../../amarok/src/htmlview.h:10,
                 from amarokdcophandler.cpp:33:
/usr/include/kicon.h:24:23: error: QtGui/QIcon: No such file or directory
In file included from /usr/include/kfind.h:24,
                 from /usr/include/khtml_part.h:35,
                 from ../../../amarok/src/htmlview.h:10,
                 from amarokdcophandler.cpp:33:
/usr/include/kdialog.h:35:25: error: QtGui/QDialog: No such file or directory
In file included from ../../../amarok/src/htmlview.h:10,
                 from amarokdcophandler.cpp:33:
/usr/include/khtml_part.h:39:26: error: QtCore/QRegExp: No such file or directory
In file included from ../../../amarok/src/htmlview.h:11,
                 from amarokdcophandler.cpp:33:
/usr/include/khtmlview.h:32:29: error: QtGui/QScrollArea: No such file or directory
In file included from ../../../amarok/src/browserToolBar.h:14,
                 from ../../../amarok/src/mediabrowser.h:12,
                 from amarokdcophandler.cpp:34:
/usr/include/ktoolbar.h:30:26: error: QtGui/QToolBar: No such file or directory
In file included from /usr/include/kservice.h:27,
                 from ../../../amarok/src/pluginmanager.h:21,
                 from ../../../amarok/src/mediabrowser.h:16,
                 from amarokdcophandler.cpp:34:
/usr/include/klibloader.h:26:27: error: QtCore/QLibrary: No such file or directory
/usr/include/klibloader.h:27:27: error: QtCore/QtPlugin: No such file or directory
In file included from /usr/include/kpluginfactory.h:31,
                 from /usr/include/klibloader.h:29,
                 from /usr/include/kservice.h:27,
                 from ../../../amarok/src/pluginmanager.h:21,
                 from ../../../amarok/src/mediabrowser.h:16,
                 from amarokdcophandler.cpp:34:
/usr/include/kexportplugin.h:24:32: error: QtCore/QPluginLoader: No such file or directory
In file included from /usr/include/kservice.h:30,
                 from ../../../amarok/src/pluginmanager.h:21,
                 from ../../../amarok/src/mediabrowser.h:16,
                 from amarokdcophandler.cpp:34:
/usr/include/ksycocaentry.h:26:30: error: QtCore/QDataStream: No such file or directory
In file included from amarokdcophandler.cpp:34:
../../../amarok/src/mediabrowser.h:22:41: error: klistview.h: No such file or directory
In file included from amarokdcophandler.cpp:36:
../../../amarok/src/osd.h:20:21: error: kpixmap.h: No such file or directory
In file included from ../../../amarok/src/playlistbrowseritem.h:14,
                 from ../../../amarok/src/playlistbrowser.h:14,
                 from amarokdcophandler.cpp:38:
../../../amarok/src/podcastbundle.h:9:22: error: krfcdate.h: No such file or directory
In file included from ../../../amarok/src/playlistbrowser.h:17,
                 from amarokdcophandler.cpp:38:
/usr/include/kaction.h:33:31: error: QtGui/QWidgetAction: No such file or directory
In file included from ../../../amarok/src/playlistbrowser.h:19,
                 from amarokdcophandler.cpp:38:
/usr/include/kpushbutton.h:23:29: error: QtGui/QPushButton: No such file or directory
In file included from /usr/include/kpagewidgetmodel.h:25,
                 from /usr/include/kpagewidget.h:25,
                 from /usr/include/kpagedialog.h:29,
                 from /usr/include/kconfigdialog.h:24,
                 from ../../../amarok/src/lastfm.h:28,
                 from amarokdcophandler.cpp:44:
/usr/include/kpagemodel.h:27:37: error: QtCore/QAbstractItemModel: No such file or directory
In file included from /usr/include/kpagewidget.h:27,
                 from /usr/include/kpagedialog.h:29,
                 from /usr/include/kconfigdialog.h:24,
                 from ../../../amarok/src/lastfm.h:28,
                 from amarokdcophandler.cpp:44:
/usr/include/kpageview.h:27:25: error: QtGui/QWidget: No such file or directory
amarokdcophandler.cpp:48:24: error: dcopclient.h: No such file or directory
In file included from amarokdcophandler.cpp:50:
/usr/include/kstartupinfo.h:32:30: error: QtCore/QChildEvent: No such file or directory
/usr/include/kstartupinfo.h:33:29: error: QtGui/QWidgetList: No such file or directory
In file included from ../../../amarok/src/amarok.h:9,
                 from amarokdcophandler.cpp:22:
/usr/include/kurl.h:112: error: expected class-name before '{' token
/usr/include/kurl.h:114: error: expected ';' before '<' token
/usr/include/kurl.h:125: error: expected template-name before '<' token
/usr/include/kurl.h:125: error: expected '{' before '<' token
/usr/include/kurl.h:125: error: expected unqualified-id before '<' token
In file included from /usr/include/c++/4.4/new:40,
                 from /usr/include/c++/4.4/ext/new_allocator.h:33,
                 from /usr/include/c++/4.4/i486-linux-gnu/bits/c++allocator.h:34,
                 from /usr/include/c++/4.4/bits/allocator.h:48,
                 from /usr/include/c++/4.4/vector:62,
                 from ../../../amarok/src/enginebase.h:14,
                 from amarokdcophandler.cpp:30:
/usr/include/c++/4.4/exception:35: error: expected '}' before end of line
/usr/include/c++/4.4/exception:35: error: expected unqualified-id before end of line
/usr/include/c++/4.4/exception:35: error: expected declaration before end of line
make[4]: *** [amarokdcophandler.lo] Error 1
make[4]: Leaving directory `/home/boubbin/amarok-kde3-1.4.10/amarok/src/amarokcore'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/boubbin/amarok-kde3-1.4.10/amarok/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/boubbin/amarok-kde3-1.4.10/amarok'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/boubbin/amarok-kde3-1.4.10'
make: *** [all] Error 2


```
If i look at the errors occured in make i get this feeling it has something to do with qt? dunno.

---

### Post by koshari on 2010-01-12
why dont you just use the bogdan deb?

it works in 9.10 as well as 9.04

[http://thedaneshproject.com/posts/install-amarok-14-on-ubuntu-904/](http://thedaneshproject.com/posts/install-amarok-14-on-ubuntu-904/)

---

### Post by boubbin on 2010-01-12
> **koshari said:**
> why dont you just use the bogdan deb?
because is need to compile amarok against new libgpod (1.0.6 or something).

---

### Post by dentaku65 on 2010-01-13
> **koshari said:**
> why dont you just use the bogdan deb?

it works in 9.10 as well as 9.04

[http://thedaneshproject.com/posts/install-amarok-14-on-ubuntu-904/](http://thedaneshproject.com/posts/install-amarok-14-on-ubuntu-904/)

I think because does not have all the patches like wikipedia and covermanager

---

### Post by Jp81 on 2010-01-13
> **boubbin said:**
> Hi,

Im on a Karmic Kubuntu kde3 remix, so im using kde3 in Karmic Koala.
i cant satisfy all the deps:
[...]

The following packages have unmet dependencies:
  kdelibs4-dev: Depends: kdelibs4c2a (= 4:3.5.10.dfsg.1-2ubuntu7.2) but it is not going to be installed
E: Broken packages[/CODE]

and amarok wont compile:
[...]
If i look at the errors occured in make i get this feeling it has something to do with qt? dunno.
sudo apt-get install kdelibs4-kde3-dev libqt4-dev

---

### Post by boubbin on 2010-01-14
> **Jp81 said:**
> sudo apt-get install kdelibs4-kde3-dev libqt4-dev

boubbin@supervisor:~$ sudo apt-get install kdelibs4-kde3-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
kdelibs4-kde3-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.

---

### Post by dentaku65 on 2010-01-14
I've created the PPA with this and based on Bogdan PPA, compiled correctly for Jaunty series but not for Karmic series (there something that going wrong in the remote PPA make); anyway the jaunty packages works fine in karmic too.
[https://launchpad.net/~dentaku65/+archive/amarok1410](https://launchpad.net/~dentaku65/+archive/amarok1410)

I've applied the patches:
[LIST]
[*]Wikipedia
[*]GCC4
[*]Covermanager (last.fm)
[*]MTP support
[/LIST]
Plus I've add the icon set suggested by zenkaon on post #22 :-)

Please consider this PPA packages really experimental, do not spread them so much... if someone that knows very well  PPA and deb compiling and want to correct them please contact me.

---

### Post by Jp81 on 2010-01-14
> **boubbin said:**
> boubbin@supervisor:~$ sudo apt-get install kdelibs4-kde3-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
kdelibs4-kde3-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.

Just install libqt4-dev and then try to run make again.

---

### Post by boubbin on 2010-01-14
> **Jp81 said:**
> Just install libqt4-dev and then try to run make again.

boubbin@supervisor:~$ sudo apt-get install libqt4-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
libqt4-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.

---

### Post by Jp81 on 2010-01-14
And make still complains about missing Qt files? Those files are part of the libqt4-dev package.

Edit. It seems that you have to install kdelibs4-dev package:
> **boubbin said:**
> 
and amarok wont compile:
```

../../../amarok/src/amarok.h:10:38: error: kprocio.h: No such file or directory
[...] 
amarokdcopiface.h:23:24: error: dcopobject.h: No such file or directory
[...]
../../../amarok/src/mediabrowser.h:22:41: error: klistview.h: No such file or directory
[...]
../../../amarok/src/osd.h:20:21: error: kpixmap.h: No such file or directory
[...]
../../../amarok/src/podcastbundle.h:9:22: error: krfcdate.h: No such file or directory
[...]
amarokdcophandler.cpp:48:24: error: dcopclient.h: No such file or directory
```

```

:~$ for i in /{kprocio.h,dcopobject.h,klistview.h,kpixmap.h,krfcdate.h,dcopclient.h}; do 
> apt-file search $i
> done
kdelibs4-dev: /usr/include/kde/kprocio.h
kdelibs4-dev: /usr/include/kde/dcopobject.h
kdelibs4-dev: /usr/include/kde/klistview.h
kdelibs4-dev: /usr/include/kde/kpixmap.h
kdelibs4-dev: /usr/include/kde/krfcdate.h
kdelibs4-dev: /usr/include/kde/dcopclient.h
```

---

### Post by boubbin on 2010-01-14
> **Jp81 said:**
> And make still complains about missing Qt files? Those files are part of the libqt4-dev package.
Edit. It seems that you have to install kdelibs4-dev package:


boubbin@supervisor:~/amarok-kde3-1.4.10$ for i in {kprocio.h,dcopobject.h,klistview.h,kpixmap.h,krfcdate.h,dcopclient.h}; do apt-file search $i; done
kdelibs4-dev: /usr/include/kde/kprocio.h
kdelibs4-dev: /usr/include/kde/dcopobject.h
kdelibs4-dev: /usr/include/kde/kmediaplayer/playerdcopobject.h
kdelibs4-dev: /usr/include/kde/klistview.h
kdelibs4-dev: /usr/include/kde/kpixmap.h
lazarus-doc: /usr/share/doc/lazarus/lcl/interfacebase/twidgetset.loadstockpixmap.html
lazarus-doc: /usr/share/doc/lazarus/lcl/lclintf/loadstockpixmap.html
libgtk2.0-dev: /usr/include/gtk-2.0/gdk/gdkpixmap.h
libgtk2.0-dev: /usr/include/gtk-2.0/gtk/gtkpixmap.h
python-gtk2-doc: /usr/share/gtk-doc/html/pygtk/class-gdkpixmap.html
kdelibs4-dev: /usr/include/kde/krfcdate.h
kdelibs4-dev: /usr/include/kde/dcopclient.h

```
boubbin@supervisor:~/amarok-kde3-1.4.10$ sudo apt-get install kdelibs4-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdelibs4-dev: Depends: kdelibs4c2a (= 4:3.5.10.dfsg.1-2ubuntu7.2) but it is not going to be installed
E: Broken packages

```

---

### Post by Jp81 on 2010-01-14
Sorry. I forgot you are using KDE 3 remix. Install kdelibs4-kde3-dev instead.

---

### Post by boubbin on 2010-01-14
> **Jp81 said:**
> Sorry. I forgot you are using KDE 3 remix. Install kdelibs4-kde3-dev instead.

```
boubbin@supervisor:~/amarok-kde3-1.4.10$ sudo apt-get install kdelibs4-kde3-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
kdelibs4-kde3-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
```

---

### Post by Jp81 on 2010-01-14
And still getting those make errors? You seem to have all dependencies installed. Maybe you should run ./configure again and then "make clean" and "make".

---

### Post by boubbin on 2010-01-14
> **Jp81 said:**
> And still getting those make errors? You seem to have all dependencies installed. Maybe you should run ./configure again and then "make clean" and "make".

yeah, i ran ./configure then make clean and then make:

```
boubbin@supervisor:~/amarok-kde3-1.4.10$ make
Makefile:994: warning: overriding commands for target `clean-bcheck'
Makefile:972: warning: ignoring old commands for target `clean-bcheck'
Makefile:999: warning: overriding commands for target `bcheck-am'
Makefile:977: warning: ignoring old commands for target `bcheck-am'
Makefile:1031: warning: overriding commands for target `clean-bcheck'
Makefile:994: warning: ignoring old commands for target `clean-bcheck'
Makefile:1036: warning: overriding commands for target `bcheck-am'
Makefile:999: warning: ignoring old commands for target `bcheck-am'
make  all-recursive
make[1]: Entering directory `/home/boubbin/amarok-kde3-1.4.10'
Makefile:994: warning: overriding commands for target `clean-bcheck'
Makefile:972: warning: ignoring old commands for target `clean-bcheck'
Makefile:999: warning: overriding commands for target `bcheck-am'
Makefile:977: warning: ignoring old commands for target `bcheck-am'
Makefile:1031: warning: overriding commands for target `clean-bcheck'
Makefile:994: warning: ignoring old commands for target `clean-bcheck'
Makefile:1036: warning: overriding commands for target `bcheck-am'
Makefile:999: warning: ignoring old commands for target `bcheck-am'
Making all in amarok
make[2]: Entering directory `/home/boubbin/amarok-kde3-1.4.10/amarok'
Making all in src
make[3]: Entering directory `/home/boubbin/amarok-kde3-1.4.10/amarok/src'
Making all in amarokcore
make[4]: Entering directory `/home/boubbin/amarok-kde3-1.4.10/amarok/src/amarokcore'
/opt/kde3/bin/kconfig_compiler ./amarok.kcfg ./amarokconfig.kcfgc; ret=$?; \
        if test "$ret" != 0; then rm -f amarokconfig.h ; exit $ret ;  fi
/usr/share/qt3/bin/moc ./amarokdcophandler.h -o amarokdcophandler.moc
/bin/bash ../../../libtool --silent --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../../.. -I../../../amarok/src -I../../../amarok/src/amarokcore -I../../../amarok/src -I../../../amarok/src/engine -I../../../amarok/src/plugin -I../../../amarok/src/statusbar -I../../../amarok/src/mediadevice -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION  -MT amarokdcophandler.lo -MD -MP -MF .deps/amarokdcophandler.Tpo -c -o amarokdcophandler.lo amarokdcophandler.cpp
In file included from /usr/include/kdecore_export.h:24,
                 from /usr/include/kurl.h:25,
                 from ../../../amarok/src/amarok.h:9,
                 from amarokdcophandler.cpp:22:
/usr/include/kdemacros.h:162:29: error: QtCore/qglobal.h: No such file or directory
In file included from ../../../amarok/src/amarok.h:9,
                 from amarokdcophandler.cpp:22:
/usr/include/kurl.h:27:27: error: QtCore/QVariant: No such file or directory
/usr/include/kurl.h:28:23: error: QtCore/QUrl: No such file or directory
/usr/include/kurl.h:29:23: error: QtCore/QMap: No such file or directory
In file included from amarokdcophandler.cpp:22:
../../../amarok/src/amarok.h:10:38: error: kprocio.h: No such file or directory
In file included from ../../../amarok/src/amarok.h:11,
                 from amarokdcophandler.cpp:22:
/usr/include/kio/netaccess.h:26:26: error: QtCore/QObject: No such file or directory
/usr/include/kio/netaccess.h:27:26: error: QtCore/QString: No such file or directory
In file included from /usr/include/kio/netaccess.h:28,
                 from ../../../amarok/src/amarok.h:11,
                 from amarokdcophandler.cpp:22:
/usr/include/kio/global.h:25:24: error: QtCore/QHash: No such file or directory
/usr/include/kio/global.h:27:24: error: QtCore/QList: No such file or directory
In file included from /usr/include/kio/global.h:30,
                 from /usr/include/kio/netaccess.h:28,
                 from ../../../amarok/src/amarok.h:11,
                 from amarokdcophandler.cpp:22:
/usr/include/kiconloader.h:26:30: error: QtCore/QStringList: No such file or directory
In file included from /usr/include/kiconloader.h:29,
                 from /usr/include/kio/global.h:30,
                 from /usr/include/kio/netaccess.h:28,
                 from ../../../amarok/src/amarok.h:11,
                 from amarokdcophandler.cpp:22:
/usr/include/kglobal.h:23:33: error: QtCore/QAtomicPointer: No such file or directory
In file included from /usr/include/kio/netaccess.h:28,
                 from ../../../amarok/src/amarok.h:11,
                 from amarokdcophandler.cpp:22:
/usr/include/kio/global.h:31:45: error: QtGui/QPixmap: No such file or directory
In file included from /usr/include/kio/global.h:36,
                 from /usr/include/kio/netaccess.h:28,
                 from ../../../amarok/src/amarok.h:11,
                 from amarokdcophandler.cpp:22:
/usr/include/kjob.h:27:24: error: QtCore/QPair: No such file or directory
In file included from /usr/include/kio/netaccess.h:29,
                 from ../../../amarok/src/amarok.h:11,
                 from amarokdcophandler.cpp:22:
/usr/include/kio/udsentry.h:27:30: error: QtCore/QSharedData: No such file or directory
In file included from /usr/include/kio/netaccess.h:31,
                 from ../../../amarok/src/amarok.h:11,
                 from amarokdcophandler.cpp:22:
/usr/include/kio/jobclasses.h:26:30: error: QtCore/QLinkedList: No such file or directory
In file included from /usr/include/kconfig.h:27,
                 from /usr/include/ksharedconfig.h:25,
                 from /usr/include/kcoreconfigskeleton.h:29,
                 from /usr/include/kconfigskeleton.h:28,
                 from amarokconfig.h:8,
                 from amarokdcophandler.cpp:23:
/usr/include/kconfigbase.h:29:27: error: QtCore/QtGlobal: No such file or directory
In file included from /usr/include/ksharedconfig.h:25,
                 from /usr/include/kcoreconfigskeleton.h:29,
                 from /usr/include/kconfigskeleton.h:28,
                 from amarokconfig.h:8,
                 from amarokdcophandler.cpp:23:
/usr/include/kconfig.h:33:29: error: QtCore/QByteArray: No such file or directory
In file included from /usr/include/ksharedconfig.h:26,
                 from /usr/include/kcoreconfigskeleton.h:29,
                 from /usr/include/kconfigskeleton.h:28,
                 from amarokconfig.h:8,
                 from amarokdcophandler.cpp:23:
/usr/include/ksharedptr.h:30:47: error: QtCore/QExplicitlySharedDataPointer: No such file or directory
In file included from /usr/include/kconfiggroup.h:714,
                 from /usr/include/kcoreconfigskeleton.h:30,
                 from /usr/include/kconfigskeleton.h:28,
                 from amarokconfig.h:8,
                 from amarokdcophandler.cpp:23:
/usr/include/conversion_check.h:26:24: error: QtGui/QColor: No such file or directory
/usr/include/conversion_check.h:27:23: error: QtGui/QFont: No such file or directory
/usr/include/conversion_check.h:28:24: error: QtCore/QDate: No such file or directory
/usr/include/conversion_check.h:29:25: error: QtCore/QPoint: No such file or directory
/usr/include/conversion_check.h:30:24: error: QtCore/QSize: No such file or directory
/usr/include/conversion_check.h:31:24: error: QtCore/QRect: No such file or directory
In file included from amarokconfig.h:9,
                 from amarokdcophandler.cpp:23:
/usr/include/kdebug.h:27:25: error: QtCore/QDebug: No such file or directory
In file included from amarokdcophandler.h:24,
                 from amarokdcophandler.cpp:24:
amarokdcopiface.h:23:24: error: dcopobject.h: No such file or directory
In file included from ../../../amarok/src/app.h:24,
                 from amarokdcophandler.cpp:25:
/usr/include/kapplication.h:44:30: error: QtGui/QApplication: No such file or directory
/usr/include/kapplication.h:49:26: error: QtGui/QX11Info: No such file or directory
In file included from ../../../amarok/src/clicklineedit.h:24,
                 from ../../../amarok/src/contextbrowser.h:12,
                 from amarokdcophandler.cpp:28:
/usr/include/klineedit.h:33:27: error: QtGui/QLineEdit: No such file or directory
In file included from /usr/include/kcompletion.h:24,
                 from /usr/include/klineedit.h:35,
                 from ../../../amarok/src/clicklineedit.h:24,
                 from ../../../amarok/src/contextbrowser.h:12,
                 from amarokdcophandler.cpp:28:
/usr/include/kglobalsettings.h:25:26: error: QtGui/QPalette: No such file or directory
In file included from /usr/include/kcompletion.h:26,
                 from /usr/include/klineedit.h:35,
                 from ../../../amarok/src/clicklineedit.h:24,
                 from ../../../amarok/src/contextbrowser.h:12,
                 from amarokdcophandler.cpp:28:
/usr/include/kshortcut.h:33:28: error: QtCore/QMetaType: No such file or directory
/usr/include/kshortcut.h:34:30: error: QtGui/QKeySequence: No such file or directory
In file included from /usr/include/klineedit.h:35,
                 from ../../../amarok/src/clicklineedit.h:24,
                 from ../../../amarok/src/contextbrowser.h:12,
                 from amarokdcophandler.cpp:28:
/usr/include/kcompletion.h:32:27: error: QtCore/QPointer: No such file or directory
In file included from ../../../amarok/src/contextbrowser.h:15,
                 from amarokdcophandler.cpp:28:
/usr/include/ktabwidget.h:27:28: error: QtGui/QTabWidget: No such file or directory
In file included from amarokdcophandler.cpp:28:
../../../amarok/src/contextbrowser.h:16:28: error: ktoolbarbutton.h: No such file or directory
In file included from /usr/include/klocale.h:26,
                 from ../../../amarok/src/metabundle.h:16,
                 from ../../../amarok/src/enginecontroller.h:18,
                 from amarokdcophandler.cpp:31:
/usr/include/klocalizedstring.h:25:24: error: QtCore/QChar: No such file or directory
/usr/include/klocalizedstring.h:26:30: error: QtCore/QLatin1Char: No such file or directory
In file included from amarokdcophandler.cpp:32:
../../../amarok/src/equalizersetup.h:22:25: error: kdialogbase.h: No such file or directory
In file included from /usr/include/khtml_events.h:22,
                 from ../../../amarok/src/htmlview.h:9,
                 from amarokdcophandler.cpp:33:
/usr/include/kparts/event.h:23:27: error: QtGui/QKeyEvent: No such file or directory
In file included from /usr/include/khtml_part.h:32,
                 from ../../../amarok/src/htmlview.h:10,
                 from amarokdcophandler.cpp:33:
/usr/include/kparts/part.h:24:25: error: QtCore/QEvent: No such file or directory
/usr/include/kparts/part.h:25:37: error: QtCore/QSharedDataPointer: No such file or directory
/usr/include/kparts/part.h:26:45: error: QtXml/QDomElement: No such file or directory
In file included from /usr/include/kguiitem.h:28,
                 from /usr/include/kdialog.h:33,
                 from /usr/include/kfind.h:24,
                 from /usr/include/khtml_part.h:35,
                 from ../../../amarok/src/htmlview.h:10,
                 from amarokdcophandler.cpp:33:
/usr/include/kicon.h:24:23: error: QtGui/QIcon: No such file or directory
In file included from /usr/include/kfind.h:24,
                 from /usr/include/khtml_part.h:35,
                 from ../../../amarok/src/htmlview.h:10,
                 from amarokdcophandler.cpp:33:
/usr/include/kdialog.h:35:25: error: QtGui/QDialog: No such file or directory
In file included from ../../../amarok/src/htmlview.h:10,
                 from amarokdcophandler.cpp:33:
/usr/include/khtml_part.h:39:26: error: QtCore/QRegExp: No such file or directory
In file included from ../../../amarok/src/htmlview.h:11,
                 from amarokdcophandler.cpp:33:
/usr/include/khtmlview.h:32:29: error: QtGui/QScrollArea: No such file or directory
In file included from ../../../amarok/src/browserToolBar.h:14,
                 from ../../../amarok/src/mediabrowser.h:12,
                 from amarokdcophandler.cpp:34:
/usr/include/ktoolbar.h:30:26: error: QtGui/QToolBar: No such file or directory
In file included from /usr/include/kservice.h:27,
                 from ../../../amarok/src/pluginmanager.h:21,
                 from ../../../amarok/src/mediabrowser.h:16,
                 from amarokdcophandler.cpp:34:
/usr/include/klibloader.h:26:27: error: QtCore/QLibrary: No such file or directory
/usr/include/klibloader.h:27:27: error: QtCore/QtPlugin: No such file or directory
In file included from /usr/include/kpluginfactory.h:31,
                 from /usr/include/klibloader.h:29,
                 from /usr/include/kservice.h:27,
                 from ../../../amarok/src/pluginmanager.h:21,
                 from ../../../amarok/src/mediabrowser.h:16,
                 from amarokdcophandler.cpp:34:
/usr/include/kexportplugin.h:24:32: error: QtCore/QPluginLoader: No such file or directory
In file included from /usr/include/kservice.h:30,
                 from ../../../amarok/src/pluginmanager.h:21,
                 from ../../../amarok/src/mediabrowser.h:16,
                 from amarokdcophandler.cpp:34:
/usr/include/ksycocaentry.h:26:30: error: QtCore/QDataStream: No such file or directory
In file included from amarokdcophandler.cpp:34:
../../../amarok/src/mediabrowser.h:22:41: error: klistview.h: No such file or directory
In file included from amarokdcophandler.cpp:36:
../../../amarok/src/osd.h:20:21: error: kpixmap.h: No such file or directory
In file included from ../../../amarok/src/playlistbrowseritem.h:14,
                 from ../../../amarok/src/playlistbrowser.h:14,
                 from amarokdcophandler.cpp:38:
../../../amarok/src/podcastbundle.h:9:22: error: krfcdate.h: No such file or directory
In file included from ../../../amarok/src/playlistbrowser.h:17,
                 from amarokdcophandler.cpp:38:
/usr/include/kaction.h:33:31: error: QtGui/QWidgetAction: No such file or directory
In file included from ../../../amarok/src/playlistbrowser.h:19,
                 from amarokdcophandler.cpp:38:
/usr/include/kpushbutton.h:23:29: error: QtGui/QPushButton: No such file or directory
In file included from /usr/include/kpagewidgetmodel.h:25,
                 from /usr/include/kpagewidget.h:25,
                 from /usr/include/kpagedialog.h:29,
                 from /usr/include/kconfigdialog.h:24,
                 from ../../../amarok/src/lastfm.h:28,
                 from amarokdcophandler.cpp:44:
/usr/include/kpagemodel.h:27:37: error: QtCore/QAbstractItemModel: No such file or directory
In file included from /usr/include/kpagewidget.h:27,
                 from /usr/include/kpagedialog.h:29,
                 from /usr/include/kconfigdialog.h:24,
                 from ../../../amarok/src/lastfm.h:28,
                 from amarokdcophandler.cpp:44:
/usr/include/kpageview.h:27:25: error: QtGui/QWidget: No such file or directory
amarokdcophandler.cpp:48:24: error: dcopclient.h: No such file or directory
In file included from amarokdcophandler.cpp:50:
/usr/include/kstartupinfo.h:32:30: error: QtCore/QChildEvent: No such file or directory
/usr/include/kstartupinfo.h:33:29: error: QtGui/QWidgetList: No such file or directory
In file included from ../../../amarok/src/amarok.h:9,
                 from amarokdcophandler.cpp:22:
/usr/include/kurl.h:112: error: expected class-name before '{' token
/usr/include/kurl.h:114: error: expected ';' before '<' token
/usr/include/kurl.h:125: error: expected template-name before '<' token
/usr/include/kurl.h:125: error: expected '{' before '<' token
/usr/include/kurl.h:125: error: expected unqualified-id before '<' token
In file included from /usr/include/c++/4.4/new:40,
                 from /usr/include/c++/4.4/ext/new_allocator.h:33,
                 from /usr/include/c++/4.4/i486-linux-gnu/bits/c++allocator.h:34,
                 from /usr/include/c++/4.4/bits/allocator.h:48,
                 from /usr/include/c++/4.4/vector:62,
                 from ../../../amarok/src/enginebase.h:14,
                 from amarokdcophandler.cpp:30:
/usr/include/c++/4.4/exception:35: error: expected '}' before end of line
/usr/include/c++/4.4/exception:35: error: expected unqualified-id before end of line
/usr/include/c++/4.4/exception:35: error: expected declaration before end of line
make[4]: *** [amarokdcophandler.lo] Error 1
make[4]: Leaving directory `/home/boubbin/amarok-kde3-1.4.10/amarok/src/amarokcore'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/boubbin/amarok-kde3-1.4.10/amarok/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/boubbin/amarok-kde3-1.4.10/amarok'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/boubbin/amarok-kde3-1.4.10'
make: *** [all] Error 2

```

---

### Post by Jp81 on 2010-01-14
I tried to compile amarok 1.4.10 while using Kubuntu Karmic Kde 3 remix and ./configure failed with error message "in the prefix, you've chosen, are no KDE libraries installed. This will fail." I ran command "export KDEDIR=/opt/kde3". After that ./configure run without errors and I was able to compile amarok.

So run "export KDEDIR=/opt/kde3" before running ./configure.

If you get an error related to libmtp, apply following patch: [http://bugs.debian.org/cgi-bin/bugreport.cgi?msg=5;filename=amarok_1.4.10-2_1.4.10-2.1.diff;att=1;bug=516557](http://bugs.debian.org/cgi-bin/bugreport.cgi?msg=5;filename=amarok_1.4.10-2_1.4.10-2.1.diff;att=1;bug=516557)

---

### Post by dentaku65 on 2010-01-15
> **boubbin said:**
> yeah, i ran ./configure then make clean and then make:

```
boubbin@supervisor:~/amarok-kde3-1.4.10$ make
Makefile:994: warning: overriding commands for target `clean-bcheck'
Makefile:972: warning: ignoring old commands for target `clean-bcheck'
Makefile:999: warning: overriding commands for target `bcheck-am'
Makefile:977: warning: ignoring old commands for target `bcheck-am'
Makefile:1031: warning: overriding commands for target `clean-bcheck'
Makefile:994: warning: ignoring old commands for target `clean-bcheck'
Makefile:1036: warning: overriding commands for target `bcheck-am'
Makefile:999: warning: ignoring old commands for target `bcheck-am'
make  all-recursive
make[1]: Entering directory `/home/boubbin/amarok-kde3-1.4.10'
Makefile:994: warning: overriding commands for target `clean-bcheck'
Makefile:972: warning: ignoring old commands for target `clean-bcheck'
Makefile:999: warning: overriding commands for target `bcheck-am'
Makefile:977: warning: ignoring old commands for target `bcheck-am'
Makefile:1031: warning: overriding commands for target `clean-bcheck'
Makefile:994: warning: ignoring old commands for target `clean-bcheck'
Makefile:1036: warning: overriding commands for target `bcheck-am'
Makefile:999: warning: ignoring old commands for target `bcheck-am'
Making all in amarok
make[2]: Entering directory `/home/boubbin/amarok-kde3-1.4.10/amarok'
Making all in src
make[3]: Entering directory `/home/boubbin/amarok-kde3-1.4.10/amarok/src'
Making all in amarokcore
make[4]: Entering directory `/home/boubbin/amarok-kde3-1.4.10/amarok/src/amarokcore'
/opt/kde3/bin/kconfig_compiler ./amarok.kcfg ./amarokconfig.kcfgc; ret=$?; \
        if test "$ret" != 0; then rm -f amarokconfig.h ; exit $ret ;  fi
/usr/share/qt3/bin/moc ./amarokdcophandler.h -o amarokdcophandler.moc
/bin/bash ../../../libtool --silent --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../../.. -I../../../amarok/src -I../../../amarok/src/amarokcore -I../../../amarok/src -I../../../amarok/src/engine -I../../../amarok/src/plugin -I../../../amarok/src/statusbar -I../../../amarok/src/mediadevice -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION  -MT amarokdcophandler.lo -MD -MP -MF .deps/amarokdcophandler.Tpo -c -o amarokdcophandler.lo amarokdcophandler.cpp
In file included from /usr/include/kdecore_export.h:24,
                 from /usr/include/kurl.h:25,
                 from ../../../amarok/src/amarok.h:9,
                 from amarokdcophandler.cpp:22:
/usr/include/kdemacros.h:162:29: error: QtCore/qglobal.h: No such file or directory
In file included from ../../../amarok/src/amarok.h:9,
                 from amarokdcophandler.cpp:22:
/usr/include/kurl.h:27:27: error: QtCore/QVariant: No such file or directory
/usr/include/kurl.h:28:23: error: QtCore/QUrl: No such file or directory
/usr/include/kurl.h:29:23: error: QtCore/QMap: No such file or directory
In file included from amarokdcophandler.cpp:22:
../../../amarok/src/amarok.h:10:38: error: kprocio.h: No such file or directory
In file included from ../../../amarok/src/amarok.h:11,
                 from amarokdcophandler.cpp:22:
/usr/include/kio/netaccess.h:26:26: error: QtCore/QObject: No such file or directory
/usr/include/kio/netaccess.h:27:26: error: QtCore/QString: No such file or directory
In file included from /usr/include/kio/netaccess.h:28,
                 from ../../../amarok/src/amarok.h:11,
                 from amarokdcophandler.cpp:22:
/usr/include/kio/global.h:25:24: error: QtCore/QHash: No such file or directory
/usr/include/kio/global.h:27:24: error: QtCore/QList: No such file or directory
In file included from /usr/include/kio/global.h:30,
                 from /usr/include/kio/netaccess.h:28,
                 from ../../../amarok/src/amarok.h:11,
                 from amarokdcophandler.cpp:22:
/usr/include/kiconloader.h:26:30: error: QtCore/QStringList: No such file or directory
In file included from /usr/include/kiconloader.h:29,
                 from /usr/include/kio/global.h:30,
                 from /usr/include/kio/netaccess.h:28,
                 from ../../../amarok/src/amarok.h:11,
                 from amarokdcophandler.cpp:22:
/usr/include/kglobal.h:23:33: error: QtCore/QAtomicPointer: No such file or directory
In file included from /usr/include/kio/netaccess.h:28,
                 from ../../../amarok/src/amarok.h:11,
                 from amarokdcophandler.cpp:22:
/usr/include/kio/global.h:31:45: error: QtGui/QPixmap: No such file or directory
In file included from /usr/include/kio/global.h:36,
                 from /usr/include/kio/netaccess.h:28,
                 from ../../../amarok/src/amarok.h:11,
                 from amarokdcophandler.cpp:22:
/usr/include/kjob.h:27:24: error: QtCore/QPair: No such file or directory
In file included from /usr/include/kio/netaccess.h:29,
                 from ../../../amarok/src/amarok.h:11,
                 from amarokdcophandler.cpp:22:
/usr/include/kio/udsentry.h:27:30: error: QtCore/QSharedData: No such file or directory
In file included from /usr/include/kio/netaccess.h:31,
                 from ../../../amarok/src/amarok.h:11,
                 from amarokdcophandler.cpp:22:
/usr/include/kio/jobclasses.h:26:30: error: QtCore/QLinkedList: No such file or directory
In file included from /usr/include/kconfig.h:27,
                 from /usr/include/ksharedconfig.h:25,
                 from /usr/include/kcoreconfigskeleton.h:29,
                 from /usr/include/kconfigskeleton.h:28,
                 from amarokconfig.h:8,
                 from amarokdcophandler.cpp:23:
/usr/include/kconfigbase.h:29:27: error: QtCore/QtGlobal: No such file or directory
In file included from /usr/include/ksharedconfig.h:25,
                 from /usr/include/kcoreconfigskeleton.h:29,
                 from /usr/include/kconfigskeleton.h:28,
                 from amarokconfig.h:8,
                 from amarokdcophandler.cpp:23:
/usr/include/kconfig.h:33:29: error: QtCore/QByteArray: No such file or directory
In file included from /usr/include/ksharedconfig.h:26,
                 from /usr/include/kcoreconfigskeleton.h:29,
                 from /usr/include/kconfigskeleton.h:28,
                 from amarokconfig.h:8,
                 from amarokdcophandler.cpp:23:
/usr/include/ksharedptr.h:30:47: error: QtCore/QExplicitlySharedDataPointer: No such file or directory
In file included from /usr/include/kconfiggroup.h:714,
                 from /usr/include/kcoreconfigskeleton.h:30,
                 from /usr/include/kconfigskeleton.h:28,
                 from amarokconfig.h:8,
                 from amarokdcophandler.cpp:23:
/usr/include/conversion_check.h:26:24: error: QtGui/QColor: No such file or directory
/usr/include/conversion_check.h:27:23: error: QtGui/QFont: No such file or directory
/usr/include/conversion_check.h:28:24: error: QtCore/QDate: No such file or directory
/usr/include/conversion_check.h:29:25: error: QtCore/QPoint: No such file or directory
/usr/include/conversion_check.h:30:24: error: QtCore/QSize: No such file or directory
/usr/include/conversion_check.h:31:24: error: QtCore/QRect: No such file or directory
In file included from amarokconfig.h:9,
                 from amarokdcophandler.cpp:23:
/usr/include/kdebug.h:27:25: error: QtCore/QDebug: No such file or directory
In file included from amarokdcophandler.h:24,
                 from amarokdcophandler.cpp:24:
amarokdcopiface.h:23:24: error: dcopobject.h: No such file or directory
In file included from ../../../amarok/src/app.h:24,
                 from amarokdcophandler.cpp:25:
/usr/include/kapplication.h:44:30: error: QtGui/QApplication: No such file or directory
/usr/include/kapplication.h:49:26: error: QtGui/QX11Info: No such file or directory
In file included from ../../../amarok/src/clicklineedit.h:24,
                 from ../../../amarok/src/contextbrowser.h:12,
                 from amarokdcophandler.cpp:28:
/usr/include/klineedit.h:33:27: error: QtGui/QLineEdit: No such file or directory
In file included from /usr/include/kcompletion.h:24,
                 from /usr/include/klineedit.h:35,
                 from ../../../amarok/src/clicklineedit.h:24,
                 from ../../../amarok/src/contextbrowser.h:12,
                 from amarokdcophandler.cpp:28:
/usr/include/kglobalsettings.h:25:26: error: QtGui/QPalette: No such file or directory
In file included from /usr/include/kcompletion.h:26,
                 from /usr/include/klineedit.h:35,
                 from ../../../amarok/src/clicklineedit.h:24,
                 from ../../../amarok/src/contextbrowser.h:12,
                 from amarokdcophandler.cpp:28:
/usr/include/kshortcut.h:33:28: error: QtCore/QMetaType: No such file or directory
/usr/include/kshortcut.h:34:30: error: QtGui/QKeySequence: No such file or directory
In file included from /usr/include/klineedit.h:35,
                 from ../../../amarok/src/clicklineedit.h:24,
                 from ../../../amarok/src/contextbrowser.h:12,
                 from amarokdcophandler.cpp:28:
/usr/include/kcompletion.h:32:27: error: QtCore/QPointer: No such file or directory
In file included from ../../../amarok/src/contextbrowser.h:15,
                 from amarokdcophandler.cpp:28:
/usr/include/ktabwidget.h:27:28: error: QtGui/QTabWidget: No such file or directory
In file included from amarokdcophandler.cpp:28:
../../../amarok/src/contextbrowser.h:16:28: error: ktoolbarbutton.h: No such file or directory
In file included from /usr/include/klocale.h:26,
                 from ../../../amarok/src/metabundle.h:16,
                 from ../../../amarok/src/enginecontroller.h:18,
                 from amarokdcophandler.cpp:31:
/usr/include/klocalizedstring.h:25:24: error: QtCore/QChar: No such file or directory
/usr/include/klocalizedstring.h:26:30: error: QtCore/QLatin1Char: No such file or directory
In file included from amarokdcophandler.cpp:32:
../../../amarok/src/equalizersetup.h:22:25: error: kdialogbase.h: No such file or directory
In file included from /usr/include/khtml_events.h:22,
                 from ../../../amarok/src/htmlview.h:9,
                 from amarokdcophandler.cpp:33:
/usr/include/kparts/event.h:23:27: error: QtGui/QKeyEvent: No such file or directory
In file included from /usr/include/khtml_part.h:32,
                 from ../../../amarok/src/htmlview.h:10,
                 from amarokdcophandler.cpp:33:
/usr/include/kparts/part.h:24:25: error: QtCore/QEvent: No such file or directory
/usr/include/kparts/part.h:25:37: error: QtCore/QSharedDataPointer: No such file or directory
/usr/include/kparts/part.h:26:45: error: QtXml/QDomElement: No such file or directory
In file included from /usr/include/kguiitem.h:28,
                 from /usr/include/kdialog.h:33,
                 from /usr/include/kfind.h:24,
                 from /usr/include/khtml_part.h:35,
                 from ../../../amarok/src/htmlview.h:10,
                 from amarokdcophandler.cpp:33:
/usr/include/kicon.h:24:23: error: QtGui/QIcon: No such file or directory
In file included from /usr/include/kfind.h:24,
                 from /usr/include/khtml_part.h:35,
                 from ../../../amarok/src/htmlview.h:10,
                 from amarokdcophandler.cpp:33:
/usr/include/kdialog.h:35:25: error: QtGui/QDialog: No such file or directory
In file included from ../../../amarok/src/htmlview.h:10,
                 from amarokdcophandler.cpp:33:
/usr/include/khtml_part.h:39:26: error: QtCore/QRegExp: No such file or directory
In file included from ../../../amarok/src/htmlview.h:11,
                 from amarokdcophandler.cpp:33:
/usr/include/khtmlview.h:32:29: error: QtGui/QScrollArea: No such file or directory
In file included from ../../../amarok/src/browserToolBar.h:14,
                 from ../../../amarok/src/mediabrowser.h:12,
                 from amarokdcophandler.cpp:34:
/usr/include/ktoolbar.h:30:26: error: QtGui/QToolBar: No such file or directory
In file included from /usr/include/kservice.h:27,
                 from ../../../amarok/src/pluginmanager.h:21,
                 from ../../../amarok/src/mediabrowser.h:16,
                 from amarokdcophandler.cpp:34:
/usr/include/klibloader.h:26:27: error: QtCore/QLibrary: No such file or directory
/usr/include/klibloader.h:27:27: error: QtCore/QtPlugin: No such file or directory
In file included from /usr/include/kpluginfactory.h:31,
                 from /usr/include/klibloader.h:29,
                 from /usr/include/kservice.h:27,
                 from ../../../amarok/src/pluginmanager.h:21,
                 from ../../../amarok/src/mediabrowser.h:16,
                 from amarokdcophandler.cpp:34:
/usr/include/kexportplugin.h:24:32: error: QtCore/QPluginLoader: No such file or directory
In file included from /usr/include/kservice.h:30,
                 from ../../../amarok/src/pluginmanager.h:21,
                 from ../../../amarok/src/mediabrowser.h:16,
                 from amarokdcophandler.cpp:34:
/usr/include/ksycocaentry.h:26:30: error: QtCore/QDataStream: No such file or directory
In file included from amarokdcophandler.cpp:34:
../../../amarok/src/mediabrowser.h:22:41: error: klistview.h: No such file or directory
In file included from amarokdcophandler.cpp:36:
../../../amarok/src/osd.h:20:21: error: kpixmap.h: No such file or directory
In file included from ../../../amarok/src/playlistbrowseritem.h:14,
                 from ../../../amarok/src/playlistbrowser.h:14,
                 from amarokdcophandler.cpp:38:
../../../amarok/src/podcastbundle.h:9:22: error: krfcdate.h: No such file or directory
In file included from ../../../amarok/src/playlistbrowser.h:17,
                 from amarokdcophandler.cpp:38:
/usr/include/kaction.h:33:31: error: QtGui/QWidgetAction: No such file or directory
In file included from ../../../amarok/src/playlistbrowser.h:19,
                 from amarokdcophandler.cpp:38:
/usr/include/kpushbutton.h:23:29: error: QtGui/QPushButton: No such file or directory
In file included from /usr/include/kpagewidgetmodel.h:25,
                 from /usr/include/kpagewidget.h:25,
                 from /usr/include/kpagedialog.h:29,
                 from /usr/include/kconfigdialog.h:24,
                 from ../../../amarok/src/lastfm.h:28,
                 from amarokdcophandler.cpp:44:
/usr/include/kpagemodel.h:27:37: error: QtCore/QAbstractItemModel: No such file or directory
In file included from /usr/include/kpagewidget.h:27,
                 from /usr/include/kpagedialog.h:29,
                 from /usr/include/kconfigdialog.h:24,
                 from ../../../amarok/src/lastfm.h:28,
                 from amarokdcophandler.cpp:44:
/usr/include/kpageview.h:27:25: error: QtGui/QWidget: No such file or directory
amarokdcophandler.cpp:48:24: error: dcopclient.h: No such file or directory
In file included from amarokdcophandler.cpp:50:
/usr/include/kstartupinfo.h:32:30: error: QtCore/QChildEvent: No such file or directory
/usr/include/kstartupinfo.h:33:29: error: QtGui/QWidgetList: No such file or directory
In file included from ../../../amarok/src/amarok.h:9,
                 from amarokdcophandler.cpp:22:
/usr/include/kurl.h:112: error: expected class-name before '{' token
/usr/include/kurl.h:114: error: expected ';' before '<' token
/usr/include/kurl.h:125: error: expected template-name before '<' token
/usr/include/kurl.h:125: error: expected '{' before '<' token
/usr/include/kurl.h:125: error: expected unqualified-id before '<' token
In file included from /usr/include/c++/4.4/new:40,
                 from /usr/include/c++/4.4/ext/new_allocator.h:33,
                 from /usr/include/c++/4.4/i486-linux-gnu/bits/c++allocator.h:34,
                 from /usr/include/c++/4.4/bits/allocator.h:48,
                 from /usr/include/c++/4.4/vector:62,
                 from ../../../amarok/src/enginebase.h:14,
                 from amarokdcophandler.cpp:30:
/usr/include/c++/4.4/exception:35: error: expected '}' before end of line
/usr/include/c++/4.4/exception:35: error: expected unqualified-id before end of line
/usr/include/c++/4.4/exception:35: error: expected declaration before end of line
make[4]: *** [amarokdcophandler.lo] Error 1
make[4]: Leaving directory `/home/boubbin/amarok-kde3-1.4.10/amarok/src/amarokcore'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/boubbin/amarok-kde3-1.4.10/amarok/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/boubbin/amarok-kde3-1.4.10/amarok'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/boubbin/amarok-kde3-1.4.10'
make: *** [all] Error 2

```

This error seems that you did not applied the first patch as indicated in post #1

---

### Post by boubbin on 2010-01-15
> **dentaku65 said:**
> This error seems that you did not applied the first patch as indicated in post #1

I started all over again and went with the guide step by step.
The make runs a long time (like 3mins), then i get this:


```
/usr/share/qt3/include/qimage.h: In member function 'bool QImageTextKeyLang::operator<(const QImageTextKeyLang&) const':
/usr/share/qt3/include/qimage.h:61: warning: suggest parentheses around '&&' within '||'
/usr/include/libmtp.h: In member function 'virtual MediaItem* MtpMediaDevice::copyTrackToDevice(const MetaBundle&)':
/usr/include/libmtp.h:541: error: too many arguments to function 'int LIBMTP_Send_Track_From_File(LIBMTP_mtpdevice_t*, const char*, LIBMTP_track_t*, int (*)(uint64_t, uint64_t, const void*), const void*)'
mtpmediadevice.cpp:302: error: at this point in file
mtpmediadevice.cpp: In member function 'uint32_t MtpMediaDevice::getDefaultParentId()':
mtpmediadevice.cpp:383: warning: deprecated conversion from string constant to 'char*'
/usr/include/libmtp.h: In member function 'LIBMTP_album_t* MtpMediaDevice::getOrCreateAlbum(QPtrList<MediaItem>*)':
/usr/include/libmtp.h:591: error: too many arguments to function 'int LIBMTP_Create_New_Album(LIBMTP_mtpdevice_t*, LIBMTP_album_t*)'
mtpmediadevice.cpp:532: error: at this point in file
/usr/include/libmtp.h: In member function 'uint32_t MtpMediaDevice::createFolder(const char*, uint32_t)':
/usr/include/libmtp.h:564: error: too few arguments to function 'uint32_t LIBMTP_Create_Folder(LIBMTP_mtpdevice_t*, char*, uint32_t, uint32_t)'
mtpmediadevice.cpp:611: error: at this point in file
/usr/include/libmtp.h: In member function 'void MtpMediaDevice::playlistFromItem(MtpMediaItem*)':
/usr/include/libmtp.h:578: error: too many arguments to function 'int LIBMTP_Create_New_Playlist(LIBMTP_mtpdevice_t*, LIBMTP_playlist_t*)'
mtpmediadevice.cpp:916: error: at this point in file
make[5]: *** [mtpmediadevice.lo] Error 1
make[5]: Leaving directory `/home/boubbin/amarok/amarok-1.4.10/amarok/src/mediadevice/mtp'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/boubbin/amarok/amarok-1.4.10/amarok/src/mediadevice'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/boubbin/amarok/amarok-1.4.10/amarok/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/boubbin/amarok/amarok-1.4.10/amarok'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/boubbin/amarok/amarok-1.4.10'
make: *** [all] Error 2

```

---

### Post by boubbin on 2010-01-15
> **Jp81 said:**
> 
So run "export KDEDIR=/opt/kde3" before running ./configure.


I did that export thingy and got the same error...

> **Jp81 said:**
> 
If you get an error related to libmtp, apply following patch: [http://bugs.debian.org/cgi-bin/bugreport.cgi?msg=5;filename=amarok_1.4.10-2_1.4.10-2.1.diff;att=1;bug=516557](http://bugs.debian.org/cgi-bin/bugreport.cgi?msg=5;filename=amarok_1.4.10-2_1.4.10-2.1.diff;att=1;bug=516557)

I do get error related to libmtp but i dont know how to apply that patch

---

### Post by boubbin on 2010-01-15
Ok i applied the diff patch manually and make went thru now.
I got amarok installed correctly.
Thanks everyone for help.

Amarok FS addon still gives me an error:

```
boubbin@supervisor:~/Downloads/amarokFS-0.5$ make
qmake -o Makefile amarokFS-xml.pro
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/kde -I/usr/local/include/kde -I/usr/include -I/opt/kde3/include -I/opt/kde/include -I/usr/kde/3.5/include -I/usr/include/qt3 -o main.o main.cpp
In file included from /usr/include/kdecore_export.h:24,
                 from /usr/include/kdeversion.h:30,
                 from /usr/include/kapplication.h:25,
                 from main.cpp:22:
/usr/include/kdemacros.h:162:29: error: QtCore/qglobal.h: No such file or directory
In file included from main.cpp:22:
/usr/include/kapplication.h:44:30: error: QtGui/QApplication: No such file or directory
In file included from /usr/include/kconfig.h:27,
                 from /usr/include/ksharedconfig.h:25,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from main.cpp:22:
/usr/include/kconfigbase.h:29:27: error: QtCore/QtGlobal: No such file or directory
In file included from /usr/include/ksharedconfig.h:25,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from main.cpp:22:
/usr/include/kconfig.h:31:26: error: QtCore/QString: No such file or directory
/usr/include/kconfig.h:32:27: error: QtCore/QVariant: No such file or directory
/usr/include/kconfig.h:33:29: error: QtCore/QByteArray: No such file or directory
/usr/include/kconfig.h:34:24: error: QtCore/QList: No such file or directory
In file included from /usr/include/ksharedconfig.h:26,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from main.cpp:22:
/usr/include/ksharedptr.h:30:47: error: QtCore/QExplicitlySharedDataPointer: No such file or directory
/usr/include/ksharedptr.h:31:33: error: QtCore/QAtomicPointer: No such file or directory
In file included from main.cpp:22:
/usr/include/kapplication.h:49:26: error: QtGui/QX11Info: No such file or directory
In file included from /usr/include/klocale.h:26,
                 from /usr/include/kaboutdata.h:27,
                 from main.cpp:23:
/usr/include/klocalizedstring.h:25:24: error: QtCore/QChar: No such file or directory
/usr/include/klocalizedstring.h:26:30: error: QtCore/QLatin1Char: No such file or directory
/usr/include/klocalizedstring.h:27:30: error: QtCore/QStringList: No such file or directory
In file included from main.cpp:23:
/usr/include/kaboutdata.h:30:37: error: QtCore/QSharedDataPointer: No such file or directory
In file included from main.cpp:24:
/usr/include/kcmdlineargs.h:23:24: error: QtCore/QBool: No such file or directory
main.cpp:25:31: error: kaboutapplication.h: No such file or directory
In file included from /usr/include/kurlrequester.h:22,
                 from amarokfs_config.h:15,
                 from amfs-xml.h:7,
                 from main.cpp:28:
/usr/include/keditlistbox.h:25:27: error: QtGui/QGroupBox: No such file or directory
/usr/include/keditlistbox.h:26:34: error: QtGui/QStringListModel: No such file or directory
In file included from /usr/include/kurlrequester.h:23,
                 from amarokfs_config.h:15,
                 from amfs-xml.h:7,
                 from main.cpp:28:
/usr/include/kfile.h:21:23: error: QtCore/QDir: No such file or directory
In file included from /usr/include/kurlrequester.h:24,
                 from amarokfs_config.h:15,
                 from amfs-xml.h:7,
                 from main.cpp:28:
/usr/include/kpushbutton.h:23:29: error: QtGui/QPushButton: No such file or directory
In file included from /usr/include/kpushbutton.h:25,
                 from /usr/include/kurlrequester.h:24,
                 from amarokfs_config.h:15,
                 from amfs-xml.h:7,
                 from main.cpp:28:
/usr/include/kstandardguiitem.h:24:24: error: QtCore/QPair: No such file or directory
In file included from /usr/include/kicontheme.h:32,
                 from /usr/include/kguiitem.h:27,
                 from /usr/include/kstandardguiitem.h:26,
                 from /usr/include/kpushbutton.h:25,
                 from /usr/include/kurlrequester.h:24,
                 from amarokfs_config.h:15,
                 from amfs-xml.h:7,
                 from main.cpp:28:
/usr/include/kiconloader.h:27:26: error: QtCore/QObject: No such file or directory
In file included from /usr/include/kguiitem.h:28,
                 from /usr/include/kstandardguiitem.h:26,
                 from /usr/include/kpushbutton.h:25,
                 from /usr/include/kurlrequester.h:24,
                 from amarokfs_config.h:15,
                 from amfs-xml.h:7,
                 from main.cpp:28:
/usr/include/kicon.h:24:23: error: QtGui/QIcon: No such file or directory
In file included from /usr/include/kurlrequester.h:25,
                 from amarokfs_config.h:15,
                 from amfs-xml.h:7,
                 from main.cpp:28:
/usr/include/kurl.h:28:23: error: QtCore/QUrl: No such file or directory
/usr/include/kurl.h:29:23: error: QtCore/QMap: No such file or directory
In file included from /usr/include/kurlrequester.h:26,
                 from amarokfs_config.h:15,
                 from amfs-xml.h:7,
                 from main.cpp:28:
/usr/include/khbox.h:24:24: error: QtGui/QFrame: No such file or directory
In file included from main.cpp:28:
amfs-xml.h:29:26: error: dcopclient.h: No such file or directory
In file included from /usr/include/kconfig.h:27,
                 from /usr/include/ksharedconfig.h:25,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from main.cpp:22:
/usr/include/kconfigbase.h:66: error: âWriteConfigFlagsâ has not been declared
/usr/include/kconfigbase.h:71: error: expected â;â before âvirtualâ
/usr/include/kconfigbase.h:112: error: âWriteConfigFlagsâ has not been declared
/usr/include/kconfigbase.h:113: error: âWriteConfigFlagsâ has not been declared
/usr/include/kconfigbase.h:114: error: âWriteConfigFlagsâ has not been declared
/usr/include/kconfigbase.h:171: error: âWriteConfigFlagsâ has not been declared
/usr/include/kconfigbase.h:180: error: expected constructor, destructor, or type conversion before â(â token
In file included from /usr/include/ksharedconfig.h:25,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from main.cpp:22:
/usr/include/kconfig.h:99: error: âOpenFlagsâ has not been declared
/usr/include/kconfig.h:126: error: expected â;â before âexplicitâ
/usr/include/kconfig.h:157: error: âOpenFlagsâ has not been declared
/usr/include/kconfig.h:376: error: âWriteConfigFlagsâ has not been declared
/usr/include/kconfig.h:396: error: expected â;â before âQ_DECLARE_PRIVATEâ
/usr/include/kconfig.h:397: error: expected â;â before â}â token
/usr/include/kconfig.h:398: error: expected constructor, destructor, or type conversion before â(â token
In file included from /usr/include/ksharedconfig.h:26,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from main.cpp:22:
/usr/include/ksharedptr.h:197: error: expected constructor, destructor, or type conversion before âboolâ
/usr/include/ksharedptr.h:203: error: expected constructor, destructor, or type conversion before âboolâ
/usr/include/ksharedptr.h:209: error: expected constructor, destructor, or type conversion before âvoidâ
/usr/include/ksharedptr.h:220: error: expected constructor, destructor, or type conversion before âvoidâ
In file included from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from main.cpp:22:
/usr/include/ksharedconfig.h:41: error: expected class-name before â{â token
/usr/include/ksharedconfig.h:69: error: âOpenFlagsâ has not been declared
/usr/include/ksharedconfig.h:97: error: âOpenFlagsâ has not been declared
/usr/include/ksharedconfig.h:106: error: âOpenFlagsâ has not been declared
In file included from /usr/include/kapplication.h:45,
                 from main.cpp:22:
/usr/include/kcomponentdata.h:25: error: using typedef-name âQByteArrayâ after âclassâ
/usr/include/qt3/qcstring.h:119: error: âQByteArrayâ has a previous declaration here
In file included from main.cpp:22:
/usr/include/kapplication.h:400: error: expected â:â before âQ_SLOTSâ
/usr/include/kapplication.h:406: error: âQ_SCRIPTABLEâ was not declared in this scope
/usr/include/kapplication.h:406: error: expected â;â before âvoidâ
/usr/include/kapplication.h:409: error: expected â;â before âvoidâ
/usr/include/kapplication.h:410: error: expected â;â before âvoidâ
/usr/include/kapplication.h:440: error: expected primary-expression before âvoidâ
/usr/include/kapplication.h:440: error: expected â;â before âvoidâ
/usr/include/kapplication.h:475: error: âdâ is not a type
/usr/include/kapplication.h:476: error: expected â;â before âQ_PRIVATE_SLOTâ
/usr/include/kapplication.h:478: error: expected â;â before â}â token
In file included from /usr/include/klocale.h:26,
                 from /usr/include/kaboutdata.h:27,
                 from main.cpp:23:
/usr/include/klocalizedstring.h:429: error: âqlonglongâ has not been declared
/usr/include/klocalizedstring.h:429: error: âKLocalizedString KLocalizedString::subs(int, int, int, const QChar&) constâ cannot be overloaded
/usr/include/klocalizedstring.h:369: error: with âKLocalizedString KLocalizedString::subs(int, int, int, const QChar&) constâ
/usr/include/klocalizedstring.h:444: error: âqulonglongâ has not been declared
/usr/include/klocalizedstring.h:444: error: âKLocalizedString KLocalizedString::subs(int, int, int, const QChar&) constâ cannot be overloaded
/usr/include/klocalizedstring.h:369: error: with âKLocalizedString KLocalizedString::subs(int, int, int, const QChar&) constâ
/usr/include/klocalizedstring.h:370: error: âQLatin1Charâ was not declared in this scope
/usr/include/klocalizedstring.h:385: error: âQLatin1Charâ was not declared in this scope
/usr/include/klocalizedstring.h:400: error: âQLatin1Charâ was not declared in this scope
/usr/include/klocalizedstring.h:415: error: âQLatin1Charâ was not declared in this scope
/usr/include/klocalizedstring.h:430: error: âQLatin1Charâ was not declared in this scope
/usr/include/klocalizedstring.h:445: error: âQLatin1Charâ was not declared in this scope
/usr/include/klocalizedstring.h:461: error: âQLatin1Charâ was not declared in this scope
/usr/include/klocalizedstring.h:474: error: âQLatin1Charâ was not declared in this scope
/usr/include/klocalizedstring.h:487: error: âQLatin1Charâ was not declared in this scope
In file included from /usr/include/kaboutdata.h:27,
                 from main.cpp:23:
/usr/include/klocale.h:566: error: âDateTimeFormatOptionsâ has not been declared
/usr/include/klocale.h:578: error: expected â;â before âQStringâ
/usr/include/klocale.h:1400: error: expected constructor, destructor, or type conversion before â(â token
In file included from main.cpp:23:
/usr/include/kaboutdata.h:248: error: default argument for parameter of type âconst QByteArray&â has type âconst char [20]â
/usr/include/kaboutdata.h:867: error: expected â;â before â<â token
In file included from main.cpp:24:
/usr/include/kcmdlineargs.h:30: error: using typedef-name âQByteArrayâ after âclassâ
/usr/include/qt3/qcstring.h:119: error: âQByteArrayâ has a previous declaration here
/usr/include/kcmdlineargs.h:269: error: âStdCmdLineArgsâ has not been declared
/usr/include/kcmdlineargs.h:288: error: expected â;â before âstaticâ
/usr/include/kcmdlineargs.h:311: error: âStdCmdLineArgsâ has not been declared
/usr/include/kcmdlineargs.h:330: error: âStdCmdLineArgsâ has not been declared
/usr/include/kcmdlineargs.h:311: error: âStdCmdLineArgsâ was not declared in this scope
/usr/include/kcmdlineargs.h:330: error: âStdCmdLineArgsâ was not declared in this scope
/usr/include/kcmdlineargs.h:656: error: expected constructor, destructor, or type conversion before â(â token
In file included from main.cpp:26:
/usr/include/qt3/qimage.h: In member function âbool QImageTextKeyLang::operator<(const QImageTextKeyLang&) constâ:
/usr/include/qt3/qimage.h:61: warning: suggest parentheses around â&&â within â||â
In file included from /usr/include/kurlrequester.h:22,
                 from amarokfs_config.h:15,
                 from amfs-xml.h:7,
                 from main.cpp:28:
/usr/include/keditlistbox.h: At global scope:
/usr/include/keditlistbox.h:46: error: expected class-name before â{â token
/usr/include/keditlistbox.h:49: error: âButtonsâ has not been declared
/usr/include/keditlistbox.h:53: error: expected â;â before âpublicâ
/usr/include/keditlistbox.h:75: error: expected â;â before â*â token
/usr/include/keditlistbox.h:78: error: expected â;â before â}â token
/usr/include/keditlistbox.h:78: error: expected â;â before â}â token
/usr/include/keditlistbox.h:93: error: âButtonsâ has not been declared
/usr/include/keditlistbox.h:98: error: expected â;â before âexplicitâ
/usr/include/keditlistbox.h:125: error: âButtonsâ has not been declared
/usr/include/keditlistbox.h:136: error: âButtonsâ has not been declared
/usr/include/keditlistbox.h:152: error: âButtonsâ has not been declared
/usr/include/keditlistbox.h:223: error: âButtonsâ does not name a type
/usr/include/keditlistbox.h:228: error: âButtonsâ has not been declared
/usr/include/keditlistbox.h:267: error: expected primary-expression before âvoidâ
/usr/include/keditlistbox.h:267: error: expected â;â before âvoidâ
/usr/include/keditlistbox.h:281: error: expected â:â before âQ_SLOTSâ
/usr/include/keditlistbox.h:282: error: expected primary-expression before âvoidâ
/usr/include/keditlistbox.h:282: error: expected â;â before âvoidâ
/usr/include/keditlistbox.h:286: error: expected â,â or â...â before â&â token
/usr/include/keditlistbox.h:289: error: expected â:â before âQ_SLOTSâ
/usr/include/keditlistbox.h:290: error: expected primary-expression before âvoidâ
/usr/include/keditlistbox.h:290: error: expected â;â before âvoidâ
/usr/include/keditlistbox.h:297: error: expected â;â before â}â token
/usr/include/keditlistbox.h:297: error: expected â;â before â}â token
/usr/include/keditlistbox.h:299: error: expected constructor, destructor, or type conversion before â(â token
In file included from /usr/include/ksharedconfig.h:26,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from main.cpp:22:
/usr/include/ksharedptr.h: In destructor âKSharedPtr<T>::~KSharedPtr() [with T = KSharedConfig]â:
/usr/include/klocale.h:91:   instantiated from here
/usr/include/ksharedptr.h:90: error: âclass KSharedConfigâ has no member named ârefâ
make: *** [main.o] Error 1
```

---

### Post by Jp81 on 2010-01-15
> **boubbin said:**
> I did that export thingy and got the same error...
Errors mentioned in your posts #43 and #46 are not the same. 

> **boubbin said:**
> Ok i applied the diff patch manually and make went thru now.
I got amarok installed correctly.
Thanks everyone for help.

Amarok FS addon still gives me an error:

```
boubbin@supervisor:~/Downloads/amarokFS-0.5$ make
[..]
amfs-xml.h:29:26: error: dcopclient.h: No such file or directory

```
It seems that make did not find KDE headers. Try to run the aforementioned export command and *make clean* before running *./configure* and *make*.

---

### Post by boubbin on 2010-01-15
> **Jp81 said:**
> Errors mentioned in your posts #43 and #46 are not the same. 
It seems that make did not find KDE headers. Try to run the aforementioned export command and *make clean* before running *./configure* and *make*.
theres no configure in amarokFS and export with make clean and make are giving me an error

```
boubbin@supervisor:~/Downloads/amarokFS-0.5$ !ex
export KDEDIR=/opt/kde3
boubbin@supervisor:~/Downloads/amarokFS-0.5$ make clean
rm -f moc_amfs-xml.o moc_cb.o moc_label-command.o moc_amarokfs_config.o moc_label-pixmap.o
rm -f moc_amfs-xml.cpp moc_cb.cpp moc_label-command.cpp moc_amarokfs_config.cpp moc_label-pixmap.cpp
rm -f main.o amfs-xml.o cb.o label-command.o amarokfs_config.o label-pixmap.o
rm -f *~ core *.core
boubbin@supervisor:~/Downloads/amarokFS-0.5$ make
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/kde -I/usr/local/include/kde -I/usr/include -I/opt/kde3/include -I/opt/kde/include -I/usr/kde/3.5/include -I/usr/include/qt3 -o main.o main.cpp
In file included from /usr/include/kdecore_export.h:24,
                 from /usr/include/kdeversion.h:30,
                 from /usr/include/kapplication.h:25,
                 from main.cpp:22:
/usr/include/kdemacros.h:162:29: error: QtCore/qglobal.h: No such file or directory
In file included from main.cpp:22:
/usr/include/kapplication.h:44:30: error: QtGui/QApplication: No such file or directory
In file included from /usr/include/kconfig.h:27,
                 from /usr/include/ksharedconfig.h:25,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from main.cpp:22:
/usr/include/kconfigbase.h:29:27: error: QtCore/QtGlobal: No such file or directory
In file included from /usr/include/ksharedconfig.h:25,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from main.cpp:22:
/usr/include/kconfig.h:31:26: error: QtCore/QString: No such file or directory
/usr/include/kconfig.h:32:27: error: QtCore/QVariant: No such file or directory
/usr/include/kconfig.h:33:29: error: QtCore/QByteArray: No such file or directory
/usr/include/kconfig.h:34:24: error: QtCore/QList: No such file or directory
In file included from /usr/include/ksharedconfig.h:26,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from main.cpp:22:
/usr/include/ksharedptr.h:30:47: error: QtCore/QExplicitlySharedDataPointer: No such file or directory
/usr/include/ksharedptr.h:31:33: error: QtCore/QAtomicPointer: No such file or directory
In file included from main.cpp:22:
/usr/include/kapplication.h:49:26: error: QtGui/QX11Info: No such file or directory
In file included from /usr/include/klocale.h:26,
                 from /usr/include/kaboutdata.h:27,
                 from main.cpp:23:
/usr/include/klocalizedstring.h:25:24: error: QtCore/QChar: No such file or directory
/usr/include/klocalizedstring.h:26:30: error: QtCore/QLatin1Char: No such file or directory
/usr/include/klocalizedstring.h:27:30: error: QtCore/QStringList: No such file or directory
In file included from main.cpp:23:
/usr/include/kaboutdata.h:30:37: error: QtCore/QSharedDataPointer: No such file or directory
In file included from main.cpp:24:
/usr/include/kcmdlineargs.h:23:24: error: QtCore/QBool: No such file or directory
main.cpp:25:31: error: kaboutapplication.h: No such file or directory
In file included from /usr/include/kurlrequester.h:22,
                 from amarokfs_config.h:15,
                 from amfs-xml.h:7,
                 from main.cpp:28:
/usr/include/keditlistbox.h:25:27: error: QtGui/QGroupBox: No such file or directory
/usr/include/keditlistbox.h:26:34: error: QtGui/QStringListModel: No such file or directory
In file included from /usr/include/kurlrequester.h:23,
                 from amarokfs_config.h:15,
                 from amfs-xml.h:7,
                 from main.cpp:28:
/usr/include/kfile.h:21:23: error: QtCore/QDir: No such file or directory
In file included from /usr/include/kurlrequester.h:24,
                 from amarokfs_config.h:15,
                 from amfs-xml.h:7,
                 from main.cpp:28:
/usr/include/kpushbutton.h:23:29: error: QtGui/QPushButton: No such file or directory
In file included from /usr/include/kpushbutton.h:25,
                 from /usr/include/kurlrequester.h:24,
                 from amarokfs_config.h:15,
                 from amfs-xml.h:7,
                 from main.cpp:28:
/usr/include/kstandardguiitem.h:24:24: error: QtCore/QPair: No such file or directory
In file included from /usr/include/kicontheme.h:32,
                 from /usr/include/kguiitem.h:27,
                 from /usr/include/kstandardguiitem.h:26,
                 from /usr/include/kpushbutton.h:25,
                 from /usr/include/kurlrequester.h:24,
                 from amarokfs_config.h:15,
                 from amfs-xml.h:7,
                 from main.cpp:28:
/usr/include/kiconloader.h:27:26: error: QtCore/QObject: No such file or directory
In file included from /usr/include/kguiitem.h:28,
                 from /usr/include/kstandardguiitem.h:26,
                 from /usr/include/kpushbutton.h:25,
                 from /usr/include/kurlrequester.h:24,
                 from amarokfs_config.h:15,
                 from amfs-xml.h:7,
                 from main.cpp:28:
/usr/include/kicon.h:24:23: error: QtGui/QIcon: No such file or directory
In file included from /usr/include/kurlrequester.h:25,
                 from amarokfs_config.h:15,
                 from amfs-xml.h:7,
                 from main.cpp:28:
/usr/include/kurl.h:28:23: error: QtCore/QUrl: No such file or directory
/usr/include/kurl.h:29:23: error: QtCore/QMap: No such file or directory
In file included from /usr/include/kurlrequester.h:26,
                 from amarokfs_config.h:15,
                 from amfs-xml.h:7,
                 from main.cpp:28:
/usr/include/khbox.h:24:24: error: QtGui/QFrame: No such file or directory
In file included from main.cpp:28:
amfs-xml.h:29:26: error: dcopclient.h: No such file or directory
In file included from /usr/include/kconfig.h:27,
                 from /usr/include/ksharedconfig.h:25,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from main.cpp:22:
/usr/include/kconfigbase.h:66: error: âWriteConfigFlagsâ has not been declared
/usr/include/kconfigbase.h:71: error: expected â;â before âvirtualâ
/usr/include/kconfigbase.h:112: error: âWriteConfigFlagsâ has not been declared
/usr/include/kconfigbase.h:113: error: âWriteConfigFlagsâ has not been declared
/usr/include/kconfigbase.h:114: error: âWriteConfigFlagsâ has not been declared
/usr/include/kconfigbase.h:171: error: âWriteConfigFlagsâ has not been declared
/usr/include/kconfigbase.h:180: error: expected constructor, destructor, or type conversion before â(â token
In file included from /usr/include/ksharedconfig.h:25,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from main.cpp:22:
/usr/include/kconfig.h:99: error: âOpenFlagsâ has not been declared
/usr/include/kconfig.h:126: error: expected â;â before âexplicitâ
/usr/include/kconfig.h:157: error: âOpenFlagsâ has not been declared
/usr/include/kconfig.h:376: error: âWriteConfigFlagsâ has not been declared
/usr/include/kconfig.h:396: error: expected â;â before âQ_DECLARE_PRIVATEâ
/usr/include/kconfig.h:397: error: expected â;â before â}â token
/usr/include/kconfig.h:398: error: expected constructor, destructor, or type conversion before â(â token
In file included from /usr/include/ksharedconfig.h:26,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from main.cpp:22:
/usr/include/ksharedptr.h:197: error: expected constructor, destructor, or type conversion before âboolâ
/usr/include/ksharedptr.h:203: error: expected constructor, destructor, or type conversion before âboolâ
/usr/include/ksharedptr.h:209: error: expected constructor, destructor, or type conversion before âvoidâ
/usr/include/ksharedptr.h:220: error: expected constructor, destructor, or type conversion before âvoidâ
In file included from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from main.cpp:22:
/usr/include/ksharedconfig.h:41: error: expected class-name before â{â token
/usr/include/ksharedconfig.h:69: error: âOpenFlagsâ has not been declared
/usr/include/ksharedconfig.h:97: error: âOpenFlagsâ has not been declared
/usr/include/ksharedconfig.h:106: error: âOpenFlagsâ has not been declared
In file included from /usr/include/kapplication.h:45,
                 from main.cpp:22:
/usr/include/kcomponentdata.h:25: error: using typedef-name âQByteArrayâ after âclassâ
/usr/include/qt3/qcstring.h:119: error: âQByteArrayâ has a previous declaration here
In file included from main.cpp:22:
/usr/include/kapplication.h:400: error: expected â:â before âQ_SLOTSâ
/usr/include/kapplication.h:406: error: âQ_SCRIPTABLEâ was not declared in this scope
/usr/include/kapplication.h:406: error: expected â;â before âvoidâ
/usr/include/kapplication.h:409: error: expected â;â before âvoidâ
/usr/include/kapplication.h:410: error: expected â;â before âvoidâ
/usr/include/kapplication.h:440: error: expected primary-expression before âvoidâ
/usr/include/kapplication.h:440: error: expected â;â before âvoidâ
/usr/include/kapplication.h:475: error: âdâ is not a type
/usr/include/kapplication.h:476: error: expected â;â before âQ_PRIVATE_SLOTâ
/usr/include/kapplication.h:478: error: expected â;â before â}â token
In file included from /usr/include/klocale.h:26,
                 from /usr/include/kaboutdata.h:27,
                 from main.cpp:23:
/usr/include/klocalizedstring.h:429: error: âqlonglongâ has not been declared
/usr/include/klocalizedstring.h:429: error: âKLocalizedString KLocalizedString::subs(int, int, int, const QChar&) constâ cannot be overloaded
/usr/include/klocalizedstring.h:369: error: with âKLocalizedString KLocalizedString::subs(int, int, int, const QChar&) constâ
/usr/include/klocalizedstring.h:444: error: âqulonglongâ has not been declared
/usr/include/klocalizedstring.h:444: error: âKLocalizedString KLocalizedString::subs(int, int, int, const QChar&) constâ cannot be overloaded
/usr/include/klocalizedstring.h:369: error: with âKLocalizedString KLocalizedString::subs(int, int, int, const QChar&) constâ
/usr/include/klocalizedstring.h:370: error: âQLatin1Charâ was not declared in this scope
/usr/include/klocalizedstring.h:385: error: âQLatin1Charâ was not declared in this scope
/usr/include/klocalizedstring.h:400: error: âQLatin1Charâ was not declared in this scope
/usr/include/klocalizedstring.h:415: error: âQLatin1Charâ was not declared in this scope
/usr/include/klocalizedstring.h:430: error: âQLatin1Charâ was not declared in this scope
/usr/include/klocalizedstring.h:445: error: âQLatin1Charâ was not declared in this scope
/usr/include/klocalizedstring.h:461: error: âQLatin1Charâ was not declared in this scope
/usr/include/klocalizedstring.h:474: error: âQLatin1Charâ was not declared in this scope
/usr/include/klocalizedstring.h:487: error: âQLatin1Charâ was not declared in this scope
In file included from /usr/include/kaboutdata.h:27,
                 from main.cpp:23:
/usr/include/klocale.h:566: error: âDateTimeFormatOptionsâ has not been declared
/usr/include/klocale.h:578: error: expected â;â before âQStringâ
/usr/include/klocale.h:1400: error: expected constructor, destructor, or type conversion before â(â token
In file included from main.cpp:23:
/usr/include/kaboutdata.h:248: error: default argument for parameter of type âconst QByteArray&â has type âconst char [20]â
/usr/include/kaboutdata.h:867: error: expected â;â before â<â token
In file included from main.cpp:24:
/usr/include/kcmdlineargs.h:30: error: using typedef-name âQByteArrayâ after âclassâ
/usr/include/qt3/qcstring.h:119: error: âQByteArrayâ has a previous declaration here
/usr/include/kcmdlineargs.h:269: error: âStdCmdLineArgsâ has not been declared
/usr/include/kcmdlineargs.h:288: error: expected â;â before âstaticâ
/usr/include/kcmdlineargs.h:311: error: âStdCmdLineArgsâ has not been declared
/usr/include/kcmdlineargs.h:330: error: âStdCmdLineArgsâ has not been declared
/usr/include/kcmdlineargs.h:311: error: âStdCmdLineArgsâ was not declared in this scope
/usr/include/kcmdlineargs.h:330: error: âStdCmdLineArgsâ was not declared in this scope
/usr/include/kcmdlineargs.h:656: error: expected constructor, destructor, or type conversion before â(â token
In file included from main.cpp:26:
/usr/include/qt3/qimage.h: In member function âbool QImageTextKeyLang::operator<(const QImageTextKeyLang&) constâ:
/usr/include/qt3/qimage.h:61: warning: suggest parentheses around â&&â within â||â
In file included from /usr/include/kurlrequester.h:22,
                 from amarokfs_config.h:15,
                 from amfs-xml.h:7,
                 from main.cpp:28:
/usr/include/keditlistbox.h: At global scope:
/usr/include/keditlistbox.h:46: error: expected class-name before â{â token
/usr/include/keditlistbox.h:49: error: âButtonsâ has not been declared
/usr/include/keditlistbox.h:53: error: expected â;â before âpublicâ
/usr/include/keditlistbox.h:75: error: expected â;â before â*â token
/usr/include/keditlistbox.h:78: error: expected â;â before â}â token
/usr/include/keditlistbox.h:78: error: expected â;â before â}â token
/usr/include/keditlistbox.h:93: error: âButtonsâ has not been declared
/usr/include/keditlistbox.h:98: error: expected â;â before âexplicitâ
/usr/include/keditlistbox.h:125: error: âButtonsâ has not been declared
/usr/include/keditlistbox.h:136: error: âButtonsâ has not been declared
/usr/include/keditlistbox.h:152: error: âButtonsâ has not been declared
/usr/include/keditlistbox.h:223: error: âButtonsâ does not name a type
/usr/include/keditlistbox.h:228: error: âButtonsâ has not been declared
/usr/include/keditlistbox.h:267: error: expected primary-expression before âvoidâ
/usr/include/keditlistbox.h:267: error: expected â;â before âvoidâ
/usr/include/keditlistbox.h:281: error: expected â:â before âQ_SLOTSâ
/usr/include/keditlistbox.h:282: error: expected primary-expression before âvoidâ
/usr/include/keditlistbox.h:282: error: expected â;â before âvoidâ
/usr/include/keditlistbox.h:286: error: expected â,â or â...â before â&â token
/usr/include/keditlistbox.h:289: error: expected â:â before âQ_SLOTSâ
/usr/include/keditlistbox.h:290: error: expected primary-expression before âvoidâ
/usr/include/keditlistbox.h:290: error: expected â;â before âvoidâ
/usr/include/keditlistbox.h:297: error: expected â;â before â}â token
/usr/include/keditlistbox.h:297: error: expected â;â before â}â token
/usr/include/keditlistbox.h:299: error: expected constructor, destructor, or type conversion before â(â token
In file included from /usr/include/ksharedconfig.h:26,
                 from /usr/include/kcomponentdata.h:23,
                 from /usr/include/kapplication.h:45,
                 from main.cpp:22:
/usr/include/ksharedptr.h: In destructor âKSharedPtr<T>::~KSharedPtr() [with T = KSharedConfig]â:
/usr/include/klocale.h:91:   instantiated from here
/usr/include/ksharedptr.h:90: error: âclass KSharedConfigâ has no member named ârefâ
make: *** [main.o] Error 1

```

---

### Post by Jp81 on 2010-01-15
> **boubbin said:**
> theres no configure in amarokFS [...]

Then you have to modify the Makefile with text editor. Find a line that begins with string "INCPATH =" and change it to look like this: ```

INCPATH  = -I/opt/kde3/include/kde -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/kde -I/usr/local/include/kde -I/usr/include -I/opt/kde3/include -I/opt/kde/include -I/usr/kde/3.5/include -I/usr/include/qt3
```

---

### Post by surja on 2010-01-23
I installed all the deps as instructed but i get this error during make:

```
Making all in audible
make[5]: Entering directory `/home/surja/Downloads/amarok-1.4.10/amarok/src/metadata/audible'
make[6]: Entering directory `/home/surja/Downloads/amarok-1.4.10/amarok/src/metadata/audible'
/bin/bash ../../../../libtool --silent --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../../../.. -I/usr/include/kde -I/usr/share/qt3/include -I.  -I/usr/include/taglib    -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION  -MT audibleproperties.lo -MD -MP -MF .deps/audibleproperties.Tpo -c -o audibleproperties.lo audibleproperties.cpp
audibleproperties.cpp: In member function 'void TagLib::Audible::Properties::readAudibleProperties(FILE*, int)':
audibleproperties.cpp:77: error: 'fseek' was not declared in this scope
audibleproperties.cpp:78: error: 'fread' was not declared in this scope
make[6]: *** [audibleproperties.lo] Error 1
make[6]: Leaving directory `/home/surja/Downloads/amarok-1.4.10/amarok/src/metadata/audible'
make[5]: *** [all-recursive] Error 1
make[5]: Leaving directory `/home/surja/Downloads/amarok-1.4.10/amarok/src/metadata/audible'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/surja/Downloads/amarok-1.4.10/amarok/src/metadata'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/surja/Downloads/amarok-1.4.10/amarok/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/surja/Downloads/amarok-1.4.10/amarok'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/surja/Downloads/amarok-1.4.10'
make: *** [all] Error 2
```

---

### Post by mael on 2010-02-03
> **dentaku65 said:**
> I've created the PPA with this and based on Bogdan PPA, compiled correctly for Jaunty series but not for Karmic series (there something that going wrong in the remote PPA make); anyway the jaunty packages works fine in karmic too.
[https://launchpad.net/~dentaku65/+archive/amarok1410](https://launchpad.net/~dentaku65/+archive/amarok1410)

I've applied the patches:
[LIST]
[*]Wikipedia
[*]GCC4
[*]Covermanager (last.fm)
[*]MTP support
[/LIST]
Plus I've add the icon set suggested by zenkaon on post #22 :-)

Please consider this PPA packages really experimental, do not spread them so much... if someone that knows very well  PPA and deb compiling and want to correct them please contact me.

**AWESOME!!! ** Thanks a lot!
Hint: The PPA holds the deb packages alright and they work great, but it's not possible to install them using apt, i had to download and install them manually, because the "Packages" file is empty. at least for i386.

Covermanager works! WP works! didn't try MTP

---

### Post by mael on 2010-02-06
i switched to Pana now, a new fork of Amarok 1.4 :)

[http://pana.bunnies.net/](http://pana.bunnies.net/)

---

### Post by Maxei on 2010-02-09
Hi Mael,

Can you please explain the steps to install Pana on Ubuntu Karmic. Thanks a lot. Did you get any issues? I tried to install the package from the bogdan ppa but it didnt work in my case, so I would like to try the Pana option. Thanks for help.

---

### Post by mael on 2010-02-10
hi,
i created a deb package and a mini-howto:
[http://pana.bunnies.net/2010/02/04/pana-1-4-13-released/#comments](http://pana.bunnies.net/2010/02/04/pana-1-4-13-released/#comments)
see if this helps :)

it's working very well here :)

---

### Post by Nick Brohman on 2010-02-17
G'day mael,

I've been to your link but need some clarification, please.

I have very limited experience and would like to install Pana in lieu of my bogdanb ppa.

On that page, you say that it is a deb package but some of it will conflict with my version of Amarok.

I should first remove Amarok14, that I can then download the deb pkge but that is where I'm stumped.

**Do I then use dpkg mgr to install Pana ?**

If not, I'll have to wait for it.

Love the old Amarok, it was the first music player that I had with Sabayon 3.5 and it is my player of choice.

**Are there any issues by not having PA as a sound server ?**

BTW if I have to compile from source, I can do so with step by step instructions.

I wish to thank everyone involved in keeping Amarok14 alive as it is the only player that this silly old b can use to it's full extent.

Thank you...

---

### Post by mael on 2010-02-17
hi
first remove amarok14 (don't use "purge"!!!):
> sudo apt-get remove amarok14
then install Pana:
> sudo dpkg -i pana_1.4.13-1_i386.deb
Then follow this guide to transfer your setttings:
[http://pana.bunnies.net/wiki/doku.php?id=converting_amarok_config](http://pana.bunnies.net/wiki/doku.php?id=converting_amarok_config)

about PA: i kicked it out a long time ago, i'm completely using ALSA. on Karmic this means doing some workarounds eg. manually configuring the multimedia keys on my keyboard but PA really upset me. I do have a script which calibrates my 7.1 speaker system for different occasions like listening to music, watching 5.1 movies, watching stereo movies etc. and this didn't work on Karmic with PA.
Let me know if you need further assistance.

---

### Post by Nick Brohman on 2010-02-17
G'day mael,

Thanks for your reply.

I'll remove Amarok via Synaptic. As I don't use anything but 2.1 speakers, I should be right there as i have my sound card set up reasonably well.

Like you I found PA to be a PITA...and ALSA is my choice for sound...we won't go into that here...PITA starts with pain....you'll know what i mean.

I don't need to transfer any other stuff as i use the playlist abilities, i.e., 'never played' or ... use the right click on artists, albums or songs for my playlists.

I was talking to a mate of mine with Skype, wishing him Happy Birthday for his 56th when you posted your reply.....so I haven't followed your yet guide but will do so now.

I really appreciate all that has been done to keep this great player going...it's a boon to me because the player operates on the KISS principle.

There are too many people to thank by name, I would like to thank all of you who have helped me....two I will mention tho' are bogdanb and tgeer43...for my original install of A14...and those who originally gave me the link to bogdanb's ppa.....

As long as I can have full screen, I use an 81cm HD TV, can get covers and ProjectM, I'll be a happy chappy.

I'll go and make a pizza, crack another Coopers Sparkling Ale and get rockin' with the best music player going....did I mention that I didn't start computing 'til I could put a Linux OS on box....no..well now I have.

It will take me about an hour or so before I can tell you of my success.....

The only wish for me is that I'd really like to import a lot of music from my Sony mimi-disc stereo to my library with ease... the Sony software doesn't work very well with wine...actually didn't work for me but that could be because of my inexperience...Dreams Are Made Of This..**.just read the post again, just two command line......that's even better....shows to go that one must be diligent, eh? **

---

### Post by Nick Brohman on 2010-02-17
Please ignore this post, I'll work it out soon

---

### Post by Nick Brohman on 2010-02-17
Thanks mael, 

I'm having problems with this install as i really don't understand all that I have to do.

I think that some of those probs started with a failed remastersys back-up last November.

Since then, all updates I've accepted haven't updated the box.....poco a poco is what I am but every step I take puts me 5 m further from my goal....

My lack o' knowledge started back in '68 when I refused to get involved with those humungous IBM installations that had to run at a preciise 74.5 F...not good for a bloke who is allergic to air-conditioning

Thanks again and I really do appreciate your efforts to help me, I know that this new version of Amarok is appreciated by many, I will be one of them...just not at present....I was going to add the results of the first two commands but it seems I didn't save them....when I'm sure I did....Oh Well Part 2...

When I put the 2nd command in terminal, i should then go to that link and copy/paste the commands... line by line + enter or in the whole of each separate set of commands ?

Having been a middle distance runner, i'm used to getting to the finish post in The Long Run

Viva Pana! keeparokkin' & I will let you know of my success in the future..  your advice will give me knowledge & comprehension...

Cheers

---

### Post by lwh77 on 2010-02-22
I am working on a Pana PPA for Karmic, it's taking a while as I am guessing package names for the dependencies then trying to rebuild it each time. Once I finish it should be easy to release a new PPA with each verstion. 

Do any of you use NMM or Helix as the engine?

---

### Post by mastermindg on 2010-02-22
Does anybody know if it's possible to use Amarok 1.4 with the new iPhone libraries for KK? I've got it working with my iPhone and RhythmBox using the following post:
[URL="http://maketecheasier.com/sync-iphone-with-rhythmbox/2010/02/13"]
http://maketecheasier.com/sync-iphone-with-rhythmbox/2010/02/13[/URL]

I'm able to mount my iPhone under /mnt/ipod and am able to use it with gtkpod. But Amarok is giving me an error that it can't create the lock file. Anybody have any ideas?

---

### Post by Nick Brohman on 2010-02-22
> **lwh77 said:**
> I am working on a Pana PPA for Karmic, it's taking a while as I am guessing package names for the dependencies then trying to rebuild it each time. Once I finish it should be easy to release a new PPA with each verstion. 

Do any of you use NMM or Helix as the engine?

Thank you, lwh77,

Myself, I have[COLOR=Red]** xine **[/COLOR]as my engine on my PC,  no Pulse, just ALSA. We won't talk about my new laptop here..it's just 9.10 oh! oh! oh! with **P**it**A.**

I'd like to be able to help in these 'builds' but my knowledge is very, very limited... 

**I am prepared to help with testing the build **tho'...if I can help in that way, just let me know 'cos I've been amarokkin14 tonight and don't want any other player.

For instance, I used the 'never played' playlist tonight and 13,000 odd songs loaded within 30 seconds, probably less, it was just quick.

I would need a package that I can install using **dpkg.**

If I have to install by using **Terminal**, I'd **need clear and precise **directions as to what I do with each command ...just like a recipe for your favourite meal...or one you'd like to try for the first time.


For this ol' hippy/surfer, Amarok 1.4 was just so easy to use, bogdanb's PPA has been great, but I'm just missing the original..missing my Covers, full screen and ProjectM of 6 months ago.

An old maxim....**'If It Ain't Broke, Don't Fix It'...**remains true....I'm not interested in the new Amarok as it's too complicated for me.

---

### Post by mc4man on 2010-02-22
If you wish to build pana in the meantime it's very easy, full instr.'s here
[http://ubuntuforums.org/showthread.php?t=1400314&page=2](http://ubuntuforums.org/showthread.php?t=1400314&page=2)

---

### Post by lwh77 on 2010-02-22
I have a working PPA now, I'm just dealing with some upload problems actually getting it on launchpad. Should be fixed later today.

---

### Post by lwh77 on 2010-02-22
I finished the PPA, but it has no extra stuff turned on: [https://launchpad.net/~lwh/+archive/pana](https://launchpad.net/~lwh/+archive/pana)

---

### Post by wall0159 on 2010-03-31
The libxine in Karmic contains a bug that breaks the playback of 24-bit FLACs. I was able to get around this by 
1. Removing all instances of libxine from synaptic (I don't use it for anything else, your mileage may vary)
2. going to
[http://www.xine-project.org/releases](http://www.xine-project.org/releases)
and downloading xine-lib 1.1.18.1 
3. configure/make/make install it 
4. install amarok as discussed in this thread.

Hope this is useful to someone - I think this is an easier way to get 24bit FLAC support in amarok than the sources.list trickery I've seen elsewhere on the web (eg. [http://microsoft_rules.ubuntuforums.org/showthread.php?p=8867313](http://microsoft_rules.ubuntuforums.org/showthread.php?p=8867313))

---

