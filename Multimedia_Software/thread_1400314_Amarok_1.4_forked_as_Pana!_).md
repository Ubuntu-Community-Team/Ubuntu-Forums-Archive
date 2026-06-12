---
title: "Amarok 1.4 forked as Pana! :)"
date: 2010-02-06
forum: Multimedia Software
---

### Post by mael on 2010-02-06
my friends with taste in good music players! Amarok 1.4 has a new fork called Pana! 
Homepage: [http://pana.bunnies.net/](http://pana.bunnies.net/) 
PPA: [https://launchpad.net/~lwh/+archive/pana](https://launchpad.net/~lwh/+archive/pana)



Current build with visualization support (which is not enabled in the build from the PPA). 
[http://rapidshare.com/files/420212152/pana_1.4.17-99-1_i386.deb.html](http://rapidshare.com/files/420212152/pana_1.4.17-99-1_i386.deb.html)


please also install these packages:

> libvisual-0.4-0
libvisual-0.4-plugins
libvisual-projectm

ProjectM has very cool visualizations!

Current Pana Changelog:
> May 16th, 2010

Pana 1.4.17

    - Cleaned up build process
    - Added new splash screen
    - Removed old svn scripts that don't work at all with Pana's repository
    - Moved some Ruby files to a pana14 subdir to avoid conflict with Amarok and Pana1.5
    - Branched 1.5

May 9, 2010

Pana 1.4.16
    - Added logo thanks to Christopher Stark [http://christopherstark.de/](http://christopherstark.de/)
    - Renamed helixconfig.kcfg to panahelixconfig.kcfg to avoid conflict with Amarok 1.4
    - Renamed nmm_kdeconfig.kcfg to pananmm_kdeconfig.kcfg to avoid conflict with Amarok 1.4

February 21, 2010

Pana 1.4.15
    - Wikipedia fix from here [http://ubuntuforums.org/showpost.php?p=8537150](http://ubuntuforums.org/showpost.php?p=8537150)
    - Renamed xinecfg.kcfg to panaxinecfg.kcfg to avoid conflict with Amarok 1.4
    - Default to --without-arts
    - Other languages translation files fixed to have Pana name in them and work again. Thanks to Florian Schröck for the script to automate it.
    

February 6th , 2010

Pana 1.4.14

    - Did a license check on everything. Reverted a few more files with "GPLv3 or later" back to "GPLv2 or later". 

February 4th, 2010

Pana 1.4.13
    - Fixed up English docs, some more Amarok -> Pana corrections, and the odd Amarok -> Pana ones. (i.e. in (c) or credits)
    - Made clean target clean translation files.
    - Fixed a bug in ipod device Makefile that broke compilation. Thanks to Florian Schröck for the report.
    - Fixed mp4v2 code to build with newer g++
    - Fixed license - some files don't say "any later" or "or later" so we must default to  GPLv2 #516822
    - Fixed player id for audioscrobbler so Pana stops showing as Amarok on Last.fm.
    - Tested more configure options for hardware we don't have ...

January 23rd, 2010

Pana 1.4.11
    First release, mainly the name change.
    This is Amarok 1.4.10 with fixes:

    - Last.fm instead of Amazon for covers thanks to Benjamin Johnson <obeythepenguin@users.sourceforge.net>
    - Wikipedia search is fixed 
    - Audible bugs fixed thanks to Rafael Laboissiere <rafael@debian.org>
    - Last.fm player id changed , Pana registered as a player.
    - MTP compile errors fixed


---

### Post by Yellow Pasque on 2010-02-07
That is awesome. Maybe some of the KDE 3.5.x holdouts will upgrade now.

---

### Post by dentaku65 on 2010-02-10
Really nice!
At last someone did it!
I'm so happy... I compiled correctly from the source (I will produce an how-to as soon as I can); but we must inform the author to fix the Wikipedia with the correct patch (here the code [http://ubuntuforums.org/showpost.php?p=8537150&postcount=25](http://ubuntuforums.org/showpost.php?p=8537150&postcount=25)), the one that I used for my PPA (here the file)

---

### Post by mael on 2010-02-10
i told him in IRC

---

### Post by lwh77 on 2010-02-10
Thanks, I added it it will be in the next one, 1.4.15

---

### Post by dartmusic on 2010-02-11
This is quite exciting...thanks for taking this on!

One question (for now): I haven't had a chance to load Pana yet, but I did notice on the website that you note that there is no MySQL support.  Does this mean that Pana ONLY uses SQLite?  Any plans to bring back MySQL?

---

### Post by mael on 2010-02-11
> **dartmusic said:**
> This is quite exciting...thanks for taking this on!

One question (for now): I haven't had a chance to load Pana yet, but I did notice on the website that you note that there is no MySQL support.  Does this mean that Pana ONLY uses SQLite?  Any plans to bring back MySQL?

no, MySQL support is still available. i was just too lazy to include it when i compiled it :)
 currently you would have to compile it yourself if you want a MySQL DB

---

### Post by dentaku65 on 2010-02-12
..waiting for 1.4.15 version... :D

---

### Post by mael on 2010-02-20
i created a new deb for Ubuntu Karmic including yet unofficial updates of ALL language files: [http://rapidshare.com/files/353065811/pana_1.4.14-1_i386.deb](http://rapidshare.com/files/353065811/pana_1.4.14-1_i386.deb)

configure options i used:

> ./configure -prefix=`kde-config -prefix` -disable-debug -disable-warnings -without-arts -with-mp4v2 -with-libmtp -enable-mysql -enable-postgresql

==========================
=== Pana – PLUGINS ========================================================
==========================
=
= The following extra functionality will NOT be included:
= – NMM-engine
= – Helix-engine
= – yauap-engine
= – Konqueror Sidebar
= – Rio Karma Support
=
= The following extra functionality will be included:
= + xine-engine
= + libvisual Support
= + MySql Support
= + Postgresql Support
= + MusicBrainz Support
= + MP4/AAC Tag Write Support
= + iPod Support
= + iRiver iFP Support
= + Creative Nomad Jukebox Support
= + MTP Device Support
= + DAAP Music Sharing Support
=
===============================================================================

---

### Post by SuperSonic4 on 2010-02-20
Interesting, what are the dependencies?

---

### Post by dentaku65 on 2010-02-21
Pana 1.4.15 has been released; if you wish you can compile by yourself (in Karmic):
Go in your downloads directory
```
cd ~/Downloads
```
Get the libraries stuff:
```
sudo apt-get install kdelibs4-dev libxine-dev libdbus-qt-1-dev libtag1-dev libsqlite3-dev \
libtunepimp-dev libmysqlclient15-dev libpq-dev libvisual-0.4-dev libsdl1.2-dev libifp-dev \
libusb-dev  libnjb-dev ruby ruby1.8-dev  x11proto-core-dev automake libtool \
libxine1 libxine1-ffmpeg build-essential checkinstall libgpod-common libgpod4 libgpod-dev
```
Get Pana source:
```
wget http://launchpad.net/pana/trunk/1.4.15/+download/pana-1.4.15.tar.bz
```
Compile:
```
tar xvf pana-1.4.15.tar.bz
cd pana-1.4.15
./configure --prefix=`kde-config --prefix` --disable-debug --disable-warnings --without-arts
make
sudo make install
```

Done!

---

### Post by mc4man on 2010-02-21
Also works (atm) in lucid.  
Installing here with checkinstall, something like this will suffice (one could add a provides and or conflicts if desired, no real need to. - the fstrans=no is redundant in karmic and lucid, doesn't hurt

```
sudo checkinstall -D --pakdir "$HOME/Desktop"  --pkgname pana --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default --pkgversion 1.4.15 --fstrans=no 
```

---

### Post by lwh77 on 2010-02-22
Thanks , your dependency list helped me fix my PPA :)

---

### Post by lwh77 on 2010-02-22
The PPA is done but it's not built with any options, do people normally make a different one for each possible set? I.e. one for MySQL, one for Postgres, etc etc. 

[https://launchpad.net/~lwh/+archive/pana](https://launchpad.net/~lwh/+archive/pana)

---

### Post by dentaku65 on 2010-02-22
> **lwh77 said:**
> The PPA is done but it's not built with any options, do people normally make a different one for each possible set? I.e. one for MySQL, one for Postgres, etc etc. 

[https://launchpad.net/~lwh/+archive/pana](https://launchpad.net/~lwh/+archive/pana)

IMHO, I figure that configure just pass only --without-arts 
at least with amarok14; thus that at first load the user can choose the preferred db

---

### Post by Maxei on 2010-02-24
Pana is one option, but I just realized that two chaps,  	 davidsansome john.maguire are using amarok 1.4 as the base for Clementine. So it seems this is more like a fork than Pana, which has only changed the name. I will give it a go. If I well understood, there is a deb package but you can also build it yourself. here is the link:

[http://code.google.com/p/clementine-player/](http://code.google.com/p/clementine-player/)

---

### Post by mc4man on 2010-02-25
> are using amarok 1.4 as the base for Clementine

Atm it seems very bare bones, certainly not up to pana/amarok 1.4 yet (or ever..?

Some of reasons I use pana/amarok is for the commands - load, play, append, queue, which are missing in Clementine and one that's also missing in amark2 - cdplay

I like to be able to put a cd in any of my drives (2 internal, 1 external) and have the player open, load the cd and start playing without any interaction on my part, pana/amarok 1.4 is one of the few that can do that from multiple drives

(made a 2nd .desktop for pana to do that

---

### Post by Yellow Pasque on 2010-02-25
> **lwh77 said:**
> The PPA is done but it's not built with any options, do people normally make a different one for each possible set? I.e. one for MySQL, one for Postgres, etc etc. 

[https://launchpad.net/~lwh/+archive/pana](https://launchpad.net/~lwh/+archive/pana)
If the options conflict and you want to offer different versions, yes. You can name them differently (pana-mysql... pana-postgres..)

---

### Post by Maxei on 2010-03-06
Thanks Dentaku for your instructions. It worked just fine for me. Now I can listen to my collection of music in complete true randomness. The SHUFFLE function is the one that I appreciate the most in Amarok 1.4/Pana. No other player compare to it in this aspect. I was tired of hearing the same songs pretty often, despite of my relatively large collection, with the version 2 or Rhythmbox. I don't care much about wikipedia information or to watch the CD covers (I don't dislike them though).
I hope that Pana/Amarok14 will continue to be supported for quite some time in the future. WHo needs another music player or additional functions when this software is (IMO) in top shape?

---

### Post by Kadai on 2010-03-08
Well, I'm going to say this: "Yay for forks! <3"

Amarok1.4 is, by far, the best player that is around... and now that there are some people doing forks, those are good news.

The player can be pulished, updated and optimized, but as long it keeps it simple and beautiful nature... it will be a jewel by itself.

I'm now a fan out of this, and putting an eye on this.

---

### Post by Nick Brohman on 2010-03-11
G'day to all of you who have contributed to this Amarok14/Pana1.4.5......I'm in awe of you after watching my Pana install.....

Thank you all, I've now to load some music so that I can start utilising Pana.....

---

### Post by Nick Brohman on 2010-03-11
G'day all, 

This is basically the first time I've installed something by using CLI....I'm rapt as I thought i'd made a mistake with the last lines....I have Pana playing now....I'm for voting this Pana/Amarok version as the best music player available....[COLOR=Red]***Thanks to everyone who put this together..***[/COLOR]

---

### Post by wkulecz on 2010-03-11
PLEASE!

Get this in the repos for 10.04!  My wife will kill me if I update her 8.04 system and Amarok is gone!  Amarok 2 is dreck.

--wally.

---

### Post by Kadai on 2010-03-11
> **wkulecz said:**
> PLEASE!

Get this in the repos for 10.04!  My wife will kill me if I update her 8.04 system and Amarok is gone!  Amarok 2 is dreck.

--wally.

This going onto repos is kinda hard at this point, except if this reach popular acclaim by actually thousand peoples.

Now, despite what it does appear, installing Amarok1.4 is easy in any system post 8.04, but you need to be a little tricky.

First, all you need is to download the three packages (*.deb) from here (download them in any folder you want... preferred empty) :
For 32Bits:
```
https://launchpad.net/~dentaku65/+archive/amarok1410/+build/1444229
```

For 64Bits:
```
https://launchpad.net/~dentaku65/+archive/amarok1410/+build/1444228
```

For lpia (?)
```
https://launchpad.net/~dentaku65/+archive/amarok1410/+build/1444230
```

After (or while you wait) in a console window, remove the old Amarok, and its common files:
```
sudo apt-get remove amarok amarok-common amarok-utils
```

Later, moving inside the folder where you downloaded the deb files (inside the console using the "cd" command -no quotes-, or with Dolphin, pressing F4 when on the folder to open a Terminal there) execute the next in the console:
```
sudo dpkg -i *.deb
```
It will install the three deb files on the system, and by the way, an updated Amarok1.4 with several bugfixes (all listed in this thread).

Run it, configure it... and enjoy it.

---

### Post by MonsterTrimble on 2010-03-19
Has anyone successfully tried adding the Pana repository to the sources.list? I want to install Pana on my Lubuntu 9.10 laptop and want to do it repository style. :P

On a side note, somebody should add Pana to the Amarok Wikipedia entry under 'Forks'.

---

### Post by mael on 2010-03-19
the official pana PPA is still not working
you can get the older version 1.4.14 here (my build): [http://rapidshare.com/files/353065811/pana_1.4.14-1_i386.deb](http://rapidshare.com/files/353065811/pana_1.4.14-1_i386.deb)

i'll release an unofficial build with the current version 1.4.15 next week

---

### Post by mael on 2010-03-19
> **MonsterTrimble said:**
> 
On a side note, somebody should add Pana to the Amarok Wikipedia entry under 'Forks'.

Good idea, i added it

---

### Post by Kadai on 2010-03-19
> **mael said:**
> the official pana PPA is still not working
you can get the older version 1.4.14 here (my build): [http://rapidshare.com/files/353065811/pana_1.4.14-1_i386.deb](http://rapidshare.com/files/353065811/pana_1.4.14-1_i386.deb)

i'll release an unofficial build with the current version 1.4.15 next week

Thanks for the Link.
Now, I hope that Pana just have not got abandoned, specially because it has not been updated on a month, and that the PPA has not been updated.

---

### Post by philip5 on 2010-03-19
If you guys are eager for Pana 1.4.15 then you can find packages of it in my PPA on Launchpad but only for Karmic. Follow the link in my signature and you'll find it... :)

Hope it's of use and have fun!

---

### Post by WildeBeest on 2010-03-19
Nothing for Jaunty?

---

### Post by philip5 on 2010-03-19
> **WildeBeest said:**
> Nothing for Jaunty?
As you asked so politely I added a build for Jaunty too... ;)

---

### Post by WildeBeest on 2010-03-19
You da man!!! :p

---

### Post by mael on 2010-03-23
since the PPA isn’t working yet, i created a new pana-1.4.15 deb package for Ubuntu Lucid 10.04. Could someone please test this, also on older versions of Ubuntu?
[http://rapidshare.com/files/367255629/pana_1.4.15-1_i386.deb](http://rapidshare.com/files/367255629/pana_1.4.15-1_i386.deb)

==========================
=== Pana – PLUGINS ========================================================
==========================
=
= The following extra functionality will NOT be included:
= – NMM-engine
= – Helix-engine
= – yauap-engine
= – Konqueror Sidebar
=
= The following extra functionality will be included:
= + xine-engine
= + libvisual Support
= + MySql Support
= + Postgresql Support
= + MusicBrainz Support
= + MP4/AAC Tag Write Support
= + iPod Support
= + iRiver iFP Support
= + Creative Nomad Jukebox Support
= + MTP Device Support
= + Rio Karma Support
= + DAAP Music Sharing Support
=
===============================================================================

---

### Post by wkulecz on 2010-03-23
> Now, I hope that Pana just have not got abandoned, specially because it has not been updated on a month, and that the PPA has not been updated

I hope Pana will not try to "improve".  That is what killed Amarok 2.0, IMHO, "improved" it to the point its more trouble that its worth.  Amarok 1.4 in 8.04 is missing *nothing* as far as I'm concerned.  Keeping it as is, dealing only with the underlying system software changes (10.04, 10.10 etc.) to keep it PPA installable and working would be great service to those of us mature enough to know that different is not better, better is better, and better is the enemy of good enough.  Once you get to "good enough" point, further changes quickly become counter productive.

--wally.

---

### Post by stafio on 2010-03-23
> since the PPA isn’t working yet, i created a new pana-1.4.15 deb package for Ubuntu Lucid 10.04. Could someone please test this, also on older versions of Ubuntu?

I tested the package on Karmic and got the following error when trying to run Pana:
```
Pana: [Loader] Starting panaapp..
Pana: [Loader] Don't run gdb, valgrind, etc. against this binary! Use panaapp.
panaapp: error while loading shared libraries: libtunepimp.so.5: cannot open shared object file: No such file or directory

```

---

### Post by mc4man on 2010-03-24
> got the following error
make sure you have libtunepimp installed

Have pana up and running well on lucid, builds just as in karmic.

Can also, for those not wishing to build on jaunty and karmic, recommend [philip5's]("https://launchpad.net/~philip5/+archive/extra") ppa builds - they are quite well done. (used a modified copy of his .diff to build pana on lucid

For some, depending on usage, having the yauap engine available may also be useful - gstreamer in lucid has been improved. The current gstreamer plugins are also available for [karmic here ]("https://launchpad.net/~gstreamer-developers/+archive/ppa")

( I use  the xine engine with xine-libs 1.18 which has improvements, bugs fixes over the 1.16 and 1.17 now in ubuntu

small note on philip5's ppa - there are quite a number of packages there, if enabling one might consider installing pana and or whatever else and then disabling the ppa till such time you want to grab an update or something else

(though a quick glance suggests there is nothing there that would be an issue if it got updated inadvertently, just generally a good practice if using a ppa with numerous packages

---

### Post by stafio on 2010-03-27
I have Pana working now. I had to install libtunepimp5 and libxine1-all-plugins. Now I have a problem when the player changes songs. An error message comes up ```
The script 'Default' exited with error code: 127. 
Details: /usr/bin/env: ruby: No such file or directory
```. I'm sure there's something else I need to install to stop this, but I don't know what it is.

---

### Post by philip5 on 2010-03-27
> **stafio said:**
> I have Pana working now. I had to install libtunepimp5 and libxine1-all-plugins. Now I have a problem when the player changes songs. An error message comes up ```
The script 'Default' exited with error code: 127. 
Details: /usr/bin/env: ruby: No such file or directory
```. I'm sure there's something else I need to install to stop this, but I don't know what it is.
Are you using the Pana packages from my PPA or something else? Just so I know if it could be something at my end but I don't think that would be something connected to my packages that gives that error...

---

### Post by mael on 2010-03-28
stafio try installing:
ruby ruby1.8 libruby1.8

---

### Post by captaincrook on 2010-03-29
Any way to get this app to draw from QTCurve in Karmic, or to better fit into KDE 4.4?

---

### Post by stafio on 2010-03-31
> Are you using the Pana packages from my PPA or something else?
No, I'm using the deb from mael in #33 above.

> stafio try installing:
ruby ruby1.8 libruby1.8

I installed these and now I'm not getting any errors! Thanks all.

---

### Post by Robertjm on 2010-04-03
I remember there were issues with running both Amarok 1.4 and 2.0 on the same machine. Currently, I'm trying to use A2, but am inclined to installed Pana since I'm more comfortable with the old 1.4 interface.

Will I have any immediate issues with them installed on the same machine, or do I have to do anything special for accomplish that feat?

BTW: Since Songbird has now announced they're dropping support for linux, perhaps they can replace it in the Maverick Meerkat's repos?

Robert

---

### Post by mael on 2010-04-03
it should be no problem - i haven't tried it though. pana uses its own preferences/db/profile directory.

---

### Post by Robertjm on 2010-04-03
Thanks! I installed it, but I'm having issues.

I had a couple of files I had to install, even though they weren't listed in the dependencies, which finally allowed me to run Pana (sorry I didn't write them down, but they were listed in the thread here already).

I chose the MySQL database option. When I finally launched Pana there was an immediate MySQL error, however, the error pop-up disappeared too fast for me to see what it was. The program did launch and I went to a sample .mp3 file located on my desktop. I was able to play it, but then I got another error msg. I installed the missing ruby files mentioned earlier in this thread and then restarted Pana.

Now, when I launch the program I get some type of a dcopserver error (screenshot attached). When I click OK, it launches Pana. However, I had to go back through and set up my database again.

I played the .mp3 that gave me errors before with no problems and then closed Pana down. Then I tried opening the program again and got the same dcop error, and it asked me to go into the Setup Wizard again!

BTW: totally unrelated, but I can't see to play the .ogg file that was included in the package, even though Rythmbox. I went to Wikipedia and downloaded a totally different .ogg file, which played just fine.

Robert

---

### Post by Maxei on 2010-04-12
I have some albums without covers. When I click the cover manager and try to fetch them, I get a message saying that "you have seen all the covers that last.fm returned using the query below"... The truth is that nothing can be fetched by changing the query. Is this a bug or is there something in the settings that can be adjusted? Or is just the script that is now obsolete? which scripts you guys use for cover fetching, lyrics etc? Please post,it may help more than one user. Thanks.

PS. Otherwise, Pana is working great. :-)

---

### Post by mael on 2010-04-13
i have seen some problems with the coverfetcher, too. eg. if you search just for "elvis" nothing is returned.

Maxel make sure you have the latest version 1.4.15. i just tried your scenario and it worked, i got some covers where i had none before.

---

### Post by wkulecz on 2010-05-01
> **Kadai said:**
> This going onto repos is kinda hard at this point, except if this reach popular acclaim by actually thousand peoples.

Now, despite what it does appear, installing Amarok1.4 is easy in any system post 8.04, but you need to be a little tricky.

First, all you need is to download the three packages (*.deb) from here (download them in any folder you want... preferred empty) :
For 32Bits:
```
https://launchpad.net/~dentaku65/+archive/amarok1410/+build/1444229
```

For 64Bits:
```
https://launchpad.net/~dentaku65/+archive/amarok1410/+build/1444228
```

For lpia (?)
```
https://launchpad.net/~dentaku65/+archive/amarok1410/+build/1444230
```

After (or while you wait) in a console window, remove the old Amarok, and its common files:
```
sudo apt-get remove amarok amarok-common amarok-utils
```

Later, moving inside the folder where you downloaded the deb files (inside the console using the "cd" command -no quotes-, or with Dolphin, pressing F4 when on the folder to open a Terminal there) execute the next in the console:
```
sudo dpkg -i *.deb
```
It will install the three deb files on the system, and by the way, an updated Amarok1.4 with several bugfixes (all listed in this thread).

Run it, configure it... and enjoy it.


Thanks, these are very clear instructions, although the link for the 64-bit version only has two deb files, not three.  Didn't take me long to figure out the missing "common" deb was linked off the 32-bit page.

Unfortunately while the dpkg install seemed to work, when I open amarok via the menu selection installed, it flashes up a splash screen I can barely see before it dies.

Starting it in a terminal I see:

```
amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
amarokapp: error while loading shared libraries: libmysqlclient.so.15: cannot open shared object file: No such file or directory
```

Seems 10.04 release uses libmysqlclient16 :(

Any ideas for a quick fix?

--wally.

---

### Post by Kadai on 2010-05-01
> **wkulecz said:**
> Thanks, these are very clear instructions, although the link for the 64-bit version only has two deb files, not three.  Didn't take me long to figure out the missing "common" deb was linked off the 32-bit page.

Unfortunately while the dpkg install seemed to work, when I open amarok via the menu selection installed, it flashes up a splash screen I can barely see before it dies.

Starting it in a terminal I see:

```
amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
amarokapp: error while loading shared libraries: libmysqlclient.so.15: cannot open shared object file: No such file or directory
```Seems 10.04 release uses libmysqlclient16 :(

Any ideas for a quick fix?

--wally.

Hopefully you figured out the common package thing (it is labeled as -for all systems- but no idea why it does not shows then under other arquitectures).

Now, there are two ways you can try to solve this issue.
First, if you have already installed any libmysqlclient, you can search for it on /usr/lib.
For that, you need to open a console window (or terminal window), and there, type "cd /usr/lib" (no quotes), and then this:
```
ls -al libmysqlclient*
```If it shows "libmysqlclient.so.16" in a green color, we are in the half good way. That one is a symbolic link, so, to make it work for amarok, we need to copy it:
```
sudo cp libmysqlclient.so.16 libmysqlclient.so.15
```Thismay ask for your password. That command should make the trick, we just copy the link with a different name, so amarok can use it.

The second way is a bit more risky, but you can try to install the next package on your system:
[http://packages.ubuntu.com/jaunty-updates/libmysqlclient15off](http://packages.ubuntu.com/jaunty-updates/libmysqlclient15off)
But it is not all recommended, unless you know what you are doing.

Hope it helps.

---

### Post by wkulecz on 2010-05-03
> **Kadai said:**
> Hopefully you figured out the common package thing (it is labeled as -for all systems- but no idea why it does not shows then under other arquitectures).

Now, there are two ways you can try to solve this issue.
First, if you have already installed any libmysqlclient, you can search for it on /usr/lib.
For that, you need to open a console window (or terminal window), and there, type "cd /usr/lib" (no quotes), and then this:
```
ls -al libmysqlclient*
```If it shows "libmysqlclient.so.16" in a green color, we are in the half good way. That one is a symbolic link, so, to make it work for amarok, we need to copy it:
```
sudo cp libmysqlclient.so.16 libmysqlclient.so.15
```Thismay ask for your password. That command should make the trick, we just copy the link with a different name, so amarok can use it.

The second way is a bit more risky, but you can try to install the next package on your system:
[http://packages.ubuntu.com/jaunty-updates/libmysqlclient15off](http://packages.ubuntu.com/jaunty-updates/libmysqlclient15off)
But it is not all recommended, unless you know what you are doing.

Hope it helps.

The copy to new name operation still doesn't let it run.  Same error message:
```
amarokapp: /usr/lib/libmysqlclient.so.15: version `libmysqlclient_15' not found (required by /usr/lib/libamarok.so.0)
```

I didn't try the second method.

--wally.

---

### Post by proggy on 2010-05-03
> **mael said:**
> i created a new deb for Ubuntu Karmic including yet unofficial updates of ALL language files: [http://rapidshare.com/files/353065811/pana_1.4.14-1_i386.deb](http://rapidshare.com/files/353065811/pana_1.4.14-1_i386.deb)

configure options i used:
:( no 64 bit version?

---

### Post by Kadai on 2010-05-03
> **wkulecz said:**
> The copy to new name operation still doesn't let it run.  Same error message:
```
amarokapp: /usr/lib/libmysqlclient.so.15: version `libmysqlclient_15' not found (required by /usr/lib/libamarok.so.0)
```I didn't try the second method.

--wally.

Too bad, in such case try installing the deb on the link.
That is the way I do have Amarok installed, because it does complained hard on not having certain packages installed (and when I do tried, libmysqlclient was just not present on repos)

The system shouldn't have any true problem running with that package, or at least I have not got any problem myself.

---

### Post by mael on 2010-05-04
> **proggy said:**
> :( no 64 bit version?

sorry, i don't have a 64 bit ubuntu system

@Kadai and @wkulecz:
i have successfully compiled pana on lucid with libmysqlclient-dev and libmysqlclient16 5.1.41-3ubuntu12 - no need for "hacks" (but i use the sqlite backend)
try this:
[http://rapidshare.com/files/367255629/pana_1.4.15-1_i386.deb](http://rapidshare.com/files/367255629/pana_1.4.15-1_i386.deb)

---

### Post by wkulecz on 2010-05-08
> Too bad, in such case try installing the deb on the link.

Adding the [http://packages.ubuntu.com/jaunty-up...sqlclient15off](http://packages.ubuntu.com/jaunty-up...sqlclient15off) deb file to the three and doing the dpkg -i *.deb got me a working amarok 1.4.

I don't see the risk you mentioned, no conflicts from dpkg or after loading synaptic.

Thanks!

--wally.

---

### Post by lwh77 on 2010-05-09
> **Kadai said:**
> Thanks for the Link.
Now, I hope that Pana just have not got abandoned, specially because it has not been updated on a month, and that the PPA has not been updated.


It's not abandoned I'm just busy :)

---

### Post by lwh77 on 2010-05-09
> **wkulecz said:**
> I hope Pana will not try to "improve".  That is what killed Amarok 2.0, IMHO, "improved" it to the point its more trouble that its worth.  Amarok 1.4 in 8.04 is missing *nothing* as far as I'm concerned.  Keeping it as is, dealing only with the underlying system software changes (10.04, 10.10 etc.) to keep it PPA installable and working would be great service to those of us mature enough to know that different is not better, better is better, and better is the enemy of good enough.  Once you get to "good enough" point, further changes quickly become counter productive.

--wally.

For 1.4 I am trying to leave it as-is , I really just want Amarok 1.4 to keep working on current OSes, I tried so many other players after Amarok 2 came out and didn't like any. There are many parts of 1.4.10 that are broken which may make sense to remove but even that - I am doing that in a 1.5 branch.

---

### Post by lwh77 on 2010-05-15
I finally got a working PPA for karmic, it works on lucid a few people report. It's here:
[https://launchpad.net/~lwh/+archive/pana](https://launchpad.net/~lwh/+archive/pana)

---

### Post by Thoralyon on 2010-05-30
Is there a working script that shows coverimages on the desktop for pana?

---

### Post by hcaleman on 2010-06-02
> **Thoralyon said:**
> Is there a working script that shows coverimages on the desktop for pana?

Also interested in this and adding another question, when I compile what do I need to do to enable mp4/aac tagging?  I can't seem to ge it work with the flags I'm using, wouldn't --with-mp4v2 be what I need?

---

### Post by mael on 2010-06-03
> **Thoralyon said:**
> Is there a working script that shows coverimages on the desktop for pana?

is there one for amarok 1.4? if so, try this: [http://pana.bunnies.net/wiki/doku.php?id=edit_amarok_scripts_to_work_with_pana](http://pana.bunnies.net/wiki/doku.php?id=edit_amarok_scripts_to_work_with_pana)

---

### Post by mael on 2010-06-03
> **hcaleman said:**
> Also interested in this and adding another question, when I compile what do I need to do to enable mp4/aac tagging?  I can't seem to ge it work with the flags I'm using, wouldn't --with-mp4v2 be what I need?

please make sure you have these packages installed (I'm not sure which one is the right one):
* libtag1-dev
* libmp4v2-dev
* libfaac-dev
* libtagc0-dev

---

### Post by Thoralyon on 2010-06-03
I tried that, for the multimediakeys it worked, for the desktop script it didn't, bur probably not due to my bad editing, but due to missing packages.

The script I used was this [http://kde-apps.org/content/show.php?content=20293](http://kde-apps.org/content/show.php?content=20293) one.
The problem is that even under gnome using amarok I had problems getting it to work the last time around.
So does someone know if there is a newer version of that script, or which exact dependencies it has, I dont want to install everything with qt in its name just to get it to work

---

### Post by mael on 2010-06-03
unfortunately i don't know how to proceed on this, i don't know any python. maybe contact the original author.

if you want random coverimages on your GNOME desktop, i can provide a BASH script, which i use to display my photo collection

---

### Post by kung fu buntu on 2010-06-22
**mael**
thank you so much for keeping the best music player alive.
I had lost hope a long time ago and that is why I kept using KDE3 for so long. I just updated some weeks ago at home and at work I'm still using KDE3.
I got really happy when I found about this one and tried it... and it works!!! :D
Even more because even with Amarok 2.3.1 the thing sucks really bad with constant crashes :(




I looked here for some info, but didn't find it...
[http://pana.bunnies.net/wiki/doku.php?id=howtos](http://pana.bunnies.net/wiki/doku.php?id=howtos)

How can I import my old amarok 1.4 database?


BTW, I think you and clementine and cuberok devs should really talk to each other in joining forces.
That will make the Rebel force stronger in order to defeat the Empire ;)

---

### Post by mael on 2010-06-24
first of thank you, but i'm not the developer, lwh77 (Luke) is :)

the documentation how to update is here: [http://pana.bunnies.net/wiki/doku.php?id=converting_amarok_config](http://pana.bunnies.net/wiki/doku.php?id=converting_amarok_config)

---

### Post by kung fu buntu on 2010-06-27
> mysqldump -uuser -p amarokDB > panaDB 
Enter password:                                                                                                                                             
mysqldump: Got error: 1045: Access denied for user 'user'@'localhost' (using password: NO) when trying to connect      
:( any help?

I have already upgraded my DB to amarok2, since I installed it before I discovered Pana.

---

### Post by mael on 2010-06-28
i don't know a way to convert an amarok 2 DB back. the only way i can think of is take a look at the program which converts the DB from amarok 1 to amarok 2 and revert the changes

maybe you have an old backup of your amarok 1 DB?

PS: in that statement you have to replace "user" with your own username.

---

### Post by mael on 2010-09-20
Current build with visualization support (which is not enabled in the build from the PPA). 
[http://rapidshare.com/files/420212152/pana_1.4.17-99-1_i386.deb.html](http://rapidshare.com/files/420212152/pana_1.4.17-99-1_i386.deb.html)


please also install these packages:

> libvisual-0.4-0
libvisual-0.4-plugins
libvisual-projectm

ProjectM has very cool visualizations!

---

### Post by MonsterTrimble on 2010-09-21
I thought Amarok 1.4 already had the Project M ability.

Are there any further releases coming? Development seems to have stalled.

---

### Post by Richard85 on 2010-10-01
Another Amarok 1.4 fork
[http://www.clementine-player.org/](http://www.clementine-player.org/)

---

