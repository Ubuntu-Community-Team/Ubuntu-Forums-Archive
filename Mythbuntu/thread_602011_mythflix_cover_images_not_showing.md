---
title: "mythflix cover images not showing"
date: 2007-11-03
forum: Mythbuntu
---

### Post by supradrvr on 2007-11-03
I cant get the images to show up in mythflix. It just shows the html code in the description. Anyone else have this problem or a solution?

---

### Post by warp99 on 2007-11-11
Same problem here with Mythflix. No covers, only the html reference line. :confused:

---

### Post by wizard10000 on 2007-11-14
Far as I can tell this is an Ubuntu problem, not a problem with mythflix.

I had the same issue, uninstalled myth and compiled and installed from myth svn source - and the issue did not resolve.  Talked to someone else running the same version of myth compiled from the same location (but not running Ubuntu) and he doesn't have the problem.  I also had this problem in Feisty.

I bugged this yesterday but would still like a solution if anybody has one.

---

### Post by wizard10000 on 2007-11-14
Replying to my own post this is fixed in the trunk version of mythflix.  Here's a link to the closed bug report.

[http://cvs.mythtv.org/trac/ticket/3891](http://cvs.mythtv.org/trac/ticket/3891)

Don't know how long it'll be before the fix reaches Ubuntu repos, but it turns out we're not nuts  :)

---

### Post by road2elysium on 2007-11-14
> **warp99 said:**
> Same problem here with Mythflix. No covers, only the html reference line. :confused:

Same here.  Nice to know I'm not crazy ;)

---

### Post by road2elysium on 2007-11-14
> **wizard10000 said:**
> Replying to my own post this is fixed in the trunk version of mythflix.  Here's a link to the closed bug report.

[http://cvs.mythtv.org/trac/ticket/389](http://cvs.mythtv.org/trac/ticket/389)

Don't know how long it'll be before the fix reaches Ubuntu repos, but it turns out we're not nuts  :)

That ticket number looks like it got cut off because it refers to DVD auto-playing.  Do you perhaps mean this one?

[http://cvs.mythtv.org/trac/ticket/3891]("http://cvs.mythtv.org/trac/ticket/3891")

---

### Post by wizard10000 on 2007-11-15
Yeah - that's the one.  Thanks.

---

### Post by wizard10000 on 2007-11-16
If somebody wanted this fixed right now they could download source and apply the following changes:

[http://cvs.mythtv.org/trac/changeset/14386](http://cvs.mythtv.org/trac/changeset/14386)

---

### Post by barney_1 on 2007-12-02
I've applied the changes and am trying to compile the plugin but it keeps getting installed to the wrong directories.

make install is creating these directories:
```
/mythtv
/share/mythtv

```

Here is the method I'm using to compile the plugin:

```
./configure --prefix=/usr/share --disable-all --enable-mythflix
qmake mythplugins.pro
make
sudo make install
```

Here is the output of "sudo make install"

```
( [ -d mythflix ] && cd mythflix ; grep "^qmake_all:" Makefile && make -f Makefile qmake_all; ) || true
qmake_all: mythflix/$(MAKEFILE) i18n/$(MAKEFILE)
make[1]: Entering directory `/home/mike/compile/mythplugins-0.20.2/mythflix'
( [ -d mythflix ] && cd mythflix ; grep "^qmake_all:" Makefile && make -f Makefile qmake_all; ) || true
( [ -d i18n ] && cd i18n ; grep "^qmake_all:" Makefile && make -f Makefile qmake_all; ) || true
make[1]: Leaving directory `/home/mike/compile/mythplugins-0.20.2/mythflix'
( [ -d mythflix ] && cd mythflix ; make -f Makefile install; ) || true
make[1]: Entering directory `/home/mike/compile/mythplugins-0.20.2/mythflix'
( [ -d mythflix ] && cd mythflix ; grep "^qmake_all:" Makefile && make -f Makefile qmake_all; ) || true
( [ -d i18n ] && cd i18n ; grep "^qmake_all:" Makefile && make -f Makefile qmake_all; ) || true
( [ -d mythflix ] && cd mythflix ; make -f Makefile install; ) || true
make[2]: Entering directory `/home/mike/compile/mythplugins-0.20.2/mythflix/mythflix'
cp -f "libmythflix.so" "/mythtv/plugins/libmythflix.so"
cp -f "netflix-rss.xml" "/share/mythtv/mythflix/"
cp -f "images/news-info-bg.png" "/share/mythtv/themes/default/"
cp -f "images/title_netflix.png" "/share/mythtv/themes/default/"
cp -f "netflix_menu.xml" "/share/mythtv/"
cp -f "scripts/netflix.pl" "/share/mythtv/mythflix/scripts/"
cp -f "netflix-ui.xml" "/share/mythtv/themes/default/"
make[2]: Leaving directory `/home/mike/compile/mythplugins-0.20.2/mythflix/mythflix'
( [ -d i18n ] && cd i18n ; make -f Makefile install; ) || true
make[2]: Entering directory `/home/mike/compile/mythplugins-0.20.2/mythflix/i18n'
cp -f "mythflix_fi.qm" "/share/mythtv/i18n/"
cp -f "mythflix_es.qm" "/share/mythtv/i18n/"
cp -f "mythflix_sv.qm" "/share/mythtv/i18n/"
cp -f "mythflix_nl.qm" "/share/mythtv/i18n/"
cp -f "mythflix_et.qm" "/share/mythtv/i18n/"
cp -f "mythflix_nb.ts" "/share/mythtv/i18n/"
cp -f "mythflix_ru.qm" "/share/mythtv/i18n/"
make[2]: Leaving directory `/home/mike/compile/mythplugins-0.20.2/mythflix/i18n'
make[1]: Leaving directory `/home/mike/compile/mythplugins-0.20.2/mythflix'

```

How can I get this to install to the proper path?   Thanks!

---

### Post by barney_1 on 2007-12-02
I have successfully compiled my plugin.  I'll list how below.  

Problem:  Most DVD covers now show as they should, but the description still has the link address for the picture at the beginning of it.  I'm going to look around and see if there is a source fix for this problem as well.  I'll post back if I find one.

My solution for compiling my own mythflix:

-I downloaded the original package, and the ubuntu diff
-I manually changed mythflix.cpp and mythflixqueue.cpp for the cover art correction and the "move to top of queue" bug.
-I compiled as follows:
```
./configure --prefix=/usr --disable-all --enable-mythflix
qmake PREFIX=/usr mythplugins.pro
make
sudo make install.
```

Reboot and worked like a charm.

---

### Post by barney_1 on 2007-12-02
SOLVED:

I found a changeset that takes care of html in movie descriptions.  Now that I've figured these issues out, is there a way I can submit this for inclusion in an ubuntu update?  Basically everything but viewing what's in your queue is broken in the package that's currently in the repos.


If you want to do this yourself:
[COLOR="Red"]Don't even think about doing this unless you are already comfortable compiling from source.  I offer no support for this process.[/COLOR]

For Ubuntu 7.10 Gutsy Gibbon:

Make sure you enable downloading of source in your sources list.  I used synaptic to do this:
Settings --> Repositories --> "Ubuntu Software" tab --> check the "Source Code" box

Download the plugin source (ubuntu diffs will be automatically applied):
```
sudo apt-get update
apt-get source mythflix
```

Step up three directories to the mythflix source:
```
cd mythplugins-0.20.2/mythflix/mythflix
```

There are three files you will be patching, mythflix.cpp, mythflixqueue.cpp, and in the scripts directory: netflix.pl

Changesets:
Fix for "Move to Top of Queue": [http://cvs.mythtv.org/trac/ticket/3894](http://cvs.mythtv.org/trac/ticket/3894)
Fix for Adding a movie to Queue: [http://cvs.mythtv.org/trac/ticket/3576](http://cvs.mythtv.org/trac/ticket/3576)
Fix for Images not Downloading: [http://cvs.mythtv.org/trac/ticket/3891](http://cvs.mythtv.org/trac/ticket/3891)
Fix for Image HTML in descriptions: [http://cvs.mythtv.org/trac/ticket/3888](http://cvs.mythtv.org/trac/ticket/3888)

Download all of the .diff files from the four changesets and apply them using patch.  Here is an example of what I ran (my .diff files were located in ~/compile/patches):
```
patch mythflix.cpp ~/compile/patches/mythflix.cpp.imageFix.diff
```

You should apply 3 patches to mythflix.cpp, 3 to mythflixqueue.cpp and 1 to netflix.pl

Time to compile: (from the mythplugins-2.20.2 directory)
```
./configure --prefix=/usr --disable-all --enable-mythflix
qmake PREFIX=/usr mythplugins.pro
make
sudo make install
```

Reboot for good measure and you should be all fixed up.

If there are better practices that I could have used I'd love to hear about them.  Thanks!

---

### Post by ear9mrn on 2008-04-11
This did not work for me as the compile failed requesting source for mythtv.


I had to ...

sudo apt-get source mythtv

to download the source for mythtv. 

I then created a directory....

mkdir mythplugins-0.20.2/mythflix/mythtv

and copied the required files.
cp mythtv-0.20.2/libs/libmyth/* mythplugins-0.20.2/mythflix/mythtv

and the directory.
 
cp mythtv-0.20.2/libs/libmythui /mythplugins-0.20.2/mythflix/mythtv


Time to compile: (from the mythplugins-2.20.2 directory)
./configure --prefix=/usr --disable-all --enable-mythflix
qmake PREFIX=/usr mythplugins.pro
make
sudo make install

and then copied the compiled binary to the required directory (probably a good idea to back up the original just in case)

sudo cp mythplugins-0.20.2/mythflix/mythflix/libmythflix.so  /usr/lib/mythtv/plugins/

Work for me, did not even need to reboot.

---

### Post by danbaatar on 2008-08-02
Has this problem been addressed in Hardy yet?  I have mythplugins-0.21.0+fixes16838 and, although the descriptions and pictures are showing up just fine, none of the Queue editing commands (add to queue, move to top of queue, and remove from queue) are working.  I tried following the steps given here for my version of mythplugins (it was a long shot, but I though I'd give it a chance), and when applying the patch that is supposed to fix "move to top of queue" I received the error:

patching file mythflix/mythflix/mythflix.cpp
Hunk #1 FAILED at 416.
Hunk #2 FAILED at 450.
2 out of 2 hunks FAILED -- saving rejects to file mythflix/mythflix/mythflix.cpp.rej

I went ahead and compiled and installed the new version anyway, but there was no change.

---

