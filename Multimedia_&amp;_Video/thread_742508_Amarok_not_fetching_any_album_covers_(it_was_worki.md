---
title: "Amarok not fetching any album covers (it was working yesterday)"
date: 2008-04-01
forum: Multimedia &amp; Video
---

### Post by liquid circuit on 2008-04-01
Amarok isn't fetching any cover art for any of my albums any more.  The albums I am searching for are tagged correctly.  It was working fine yesterday.  Late last night I switched from SQLite to MySQL, then when I searched for album art today, it doesn't find anything.  If I right click on the generic cover icon and try to fetch from Amazon, it looks like it is searching (I also see a spike in network activity), but nothing happens; no error message, no window pops up.  When I use the Cover Manager, the status bar indicates "Finished. Cover not found."  The Context browser is able to locate artist info still, so Amarok can connect to the net.

I am really not sure what is going on.  Any suggestions?

---

### Post by cecilx22 on 2008-04-01
Hey, I started having issues today as well (again, was working yeasterday), though I didn't make any configuration changes.  Perhaps Amazon changed something?

---

### Post by bbbaldie on 2008-04-02
Same issue here. I restarted X thinking something had gotten buggy, no go.

I think it's an Amarok issue, rather than Amazon, because if you tell it to go to amazon.ca, or amazon.co.uk, it still won't work.

---

### Post by kd70 on 2008-04-02
I also switched my Amazon source, but to no avail.

As to whether it's an Amarok issue: If I recall correctly the last update to my Amarok was in early March. In fact the Help->About gives the build-date as 11 Mar 08. What suddenly happened on Apr 1st to disable the Cover Fetch?

---

### Post by aeiah on 2008-04-02
this happened in the past and was to do with amazon changing something at their end. if this is happening to people who havent changed any settings, then i would certainly think amazon is to blame. updates to amazon.com's infrastructure is probably mirrored across amazon.co.uk, amazon.de etc.

just hang around on the amarok website and see if its a known issue, and see if it is being updated. it'll probably be fixed in a few days

---

### Post by aeiah on 2008-04-02
from here: [http://amarok.kde.org/forum/index.php/topic,15235.0.html](http://amarok.kde.org/forum/index.php/topic,15235.0.html)

"There's a fix in SVN for this, next version will restore this service again."

---

### Post by kd70 on 2008-04-02
Bang on!!

From the Amarok Help Forum : There's a fix in SVN for this, next version will restore this service again.

(See [http://amarok.kde.org/forum/index.php/topic,15235.msg22151.html#msg22151](http://amarok.kde.org/forum/index.php/topic,15235.msg22151.html#msg22151))

---

### Post by bbbaldie on 2008-04-02
Kewl. Nice work, all.

---

### Post by liquid circuit on 2008-04-02
Yay!  I didn't break it!  Well, thats one less thing I need to struggle with to try and fix.

I was getting the impression yesterday that this was somehow Amazon's twisted April Fool's joke to Linux users.:lolflag:

---

### Post by aeiah on 2008-04-02
exaile have fixed the problem already. what are amarok playing at? they havent fixed it after one day. pah, so slow ;)

---

### Post by Ni85 on 2008-04-02
> **kd70 said:**
> Bang on!!

From the Amarok Help Forum : There's a fix in SVN for this, next version will restore this service again.

(See [http://amarok.kde.org/forum/index.php/topic,15235.msg22151.html#msg22151](http://amarok.kde.org/forum/index.php/topic,15235.msg22151.html#msg22151))

which means we have to wait, right?

---

### Post by djrobthaman on 2008-04-03
So...

I've just discovered the same problem that you all are talking about here in this thread.  I also found [a page on the amarok web site that I think is giving the instructions on how to install the svn version]("http://amarok.kde.org/wiki/Amarok-svn").  Something on the page is a bit worrying thous.

"NOTE: I'm not responsible for any data loss etc. that can be blamed on this script. Use it at your own risk! (3.X has some code that might, but shouldn't, do bad things. See the ChangeLog for details.)"

So I figured before I dove into the deep end I'd ask... Does anyone have this version installed?  Any bad things happen to you because of it?

---

### Post by Jackrum on 2008-04-03
Meh. I'll wait. This is why I LOVE Ubuntu over other distros I've used. I noticed Amarok wasn't working, googled "Amarok not fetching covers" and BOOM - 3 seconds later I have an answer.  I'm paid to support Windows apps at my job, and let me tell you, trying to track down why the new e-learning app isn't playing nicely with certain Iexplorer versions can take all day.


(On a side note, anyone who says Windows is easier to install/recognize hardware I would bet money has never installed from a pure Windows Retail CD/DVD. Sure, the OEM disk that came with your PC probably works fine. Run your hiney down to 8est 8uy and pick up the raw install, then tell me how easy it is......)

---

### Post by timrobin on 2008-04-04
I crudely merged the SVN fix into the Gutsy source package and rebuilt.  

Steps:

Download the attached patch file 'coverfetcher.patch.txt'

```

apt-get source amarok
sudo apt-get build-dep amarok

```

Update 'amarok-1.4.7/debian/changelog' to avoid "upgrade" nagging (Optional)

```

cd amarok-1.4.7/amarok/src
patch < ../../../coverfetcher.patch.txt
cd ../../
dpkg-buildpackage -rfakeroot -b
sudo dpkg -i ../amarok*.deb

```

Start Amarok


Cover fetching working, nothing obviously broken.  Would have normally waited but I just rebuilt my collection and cant stand looking at that empty jewel case.

---

### Post by FrooziE on 2008-04-04
Anyway you could upload that .deb here or a link to it?

---

### Post by timrobin on 2008-04-04
i386 packages here ->  [http://tjr.homeip.net/~tim/amarok/](http://tjr.homeip.net/~tim/amarok/)

---

### Post by liquid circuit on 2008-04-05
Installed the .debs... its now retrieving covers (YAY!), and I haven't encountered any issues yet, but I haven't had a chance to really do extensive testing.  I don't expect any issues though.  Hopefully we'll soon have an official release in the repositories.  I'll post back here if I find anything strange with these .debs.

---

### Post by dasbooter on 2008-04-05
thanks for the info...muchly appreciated just noticed this now

---

### Post by havok1977 on 2008-04-06
@timrobin, thanks for posting the debs; you saved me some compiling time....

---

### Post by wiplash on 2008-04-06
EDIT: ignore me -- i didn't see timrobin's post.

how come no one's posted an ubuntu package yet ;-)

compiling from svn source is for those gentoo fanboys! camaan!

---

### Post by wiplash on 2008-04-06
oops, i'm blind.. thanks timrobin !

---

### Post by gwoodruff on 2008-04-06
Thanks much, Worked for Hardy 64bit. Amarok version is 1.4.8

Thanks, Gary

---

### Post by parkejr on 2008-04-07
probably the most helpful post I've read on here in a while..

one comment, despite following the instructions, I still needed to add fakeroot:

```
 sudo apt-get install fakeroot 
```

not sure why it wasn't part of my installation.

Thanks again,

Jeff.

---

### Post by unrater on 2008-04-08
sorry, but i didn't understand what to do. :\

what exactly i need to do? :S

and if i wait, how much time i'll need to have an update from ubuntu?

---

### Post by liquid circuit on 2008-04-09
First, you should probably close Amarok entirely.  Then download the 3 amarok .deb files to your Desktop (~/Desktop) from the link posted in [here.]("http://ubuntuforums.org/showpost.php?p=4653673&postcount=16")

Then open a terminal and run...
```
cd ~/Desktop
```

then run...
```
sudo dpkg -i amarok-engines_1.4.7-0ubuntu4_i386.deb amarok-xine_1.4.7-0ubuntu4_i386.deb amarok_1.4.7-0ubuntu4_i386.deb
```

Then re-open Amarok, and try and search for an album cover.  Hopefully it works.

---

### Post by elrond1337 on 2008-04-09
hi, where can i find the .deb files for amd64? When i try the i386 ones it returns: architecture does not fit. 
Thanks Pascal

---

### Post by troymcdavis on 2008-04-09
The .debs work in Hardy, if you also install [libgpod2]("http://packages.ubuntu.com/gutsy/i386/libgpod2/download") and [libmtp6]("http://packages.ubuntu.com/gutsy/i386/libmtp6/download"). Back-up your ~/.amarok directory, [EDIT: THE FOLLOWING TURNED OUT NOT TO BE TRUE. My .amarok directory magically came back, along with my playlists, tags, scores, and ratings, when I told it where my collection was. Still probably not a bad idea to back up your directory, though.] because it might wipe it (it got mine).

A quick:```
cp -r ~/.amarok ~/.amarok~YEARMODYTIME
```will do it, and then a:```
cp -r ~/.amarok~YEARMODYTIME ~/.amarok
```will restore your back up. However, I don't know if the .amarok directory you were first using in Hardy will be compatible (1.4.9) with the one packages here (1.4.7). However, I think if you are using beta software and willing to mix and match packages from different releases, you're already prepared for some risk. [END OF THINGS THAT ARE NOT NECESSARILY TRUE.]

Most importantly, it does work in Hardy, no problems.

---

### Post by elrond1337 on 2008-04-10
hi thanks for your reply.
Im using Gutsy so libgpod2 and libmtp6 can not be installed (Error: Wrong architecture 'i386'). Is there no way to get the debs for gutsy amd64?

Thanks Pascal

---

### Post by dylanologist on 2008-04-10
Like elrond1337 above, I'm having this problem and running Gutsy AMD64.  I'm wondering if there's a fix for this setup.

Also, I compiled Amarok (1.4.8) from source in order to include m4a/aac tag editing, and I'm wondering if that would affect any fixes coming down the line.  I really don't know much about compiling from source, so I just followed a detailed guide to the letter (I really needed that tag editing feature to make the transition from iTunes).  Does this mean my build of Amarok won't receive the regular updates through the Update Manager, and thus this problem won't magically disappear on its own someday?

---

### Post by pickarooney on 2008-04-13
Any way of getting this to work in Feisty? Not sure I feel like upgrading the whole OS to get the album covers back working again ;)

---

### Post by troymcdavis on 2008-04-13
For 64 Architectures:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/) is the Ubuntu Package search, where I found those two packages. I just searched for the package I wanted (libgpod2) and then clicked the best (or only) search result. Scroll way down where it says "Download *package x*" and click the architecture you want to use. Click one of the mirrors, and you're done.

(The only reason I clicked a particular architecture and linked the mirror page is because I find the UPS interface kind of confusing.)

It might work in Feisty; the only way to know is to download those patched amarok files and try to install them with dpkg, and then see if you can manually resolve any dependency problems that come up.

---

### Post by rune0077 on 2008-04-13
Just got home from a week long vacation, downloaded a whole bunch of updates, and voila, Amarok now fetches my covers like it used to. Problem should be fixed.

---

### Post by surfdoc on 2008-04-13
No update for gutsy yet though?

---

### Post by rune0077 on 2008-04-13
> **surfdoc said:**
> No update for gutsy yet though?

No? There should be, though you'd have to enable the backports in your software sources, so it's at your own risk. (to do it: System > Administration > Software Sources, then go to "Updates" and tick "Unsupported Updates (Gutsy-backports)").

---

### Post by surfdoc on 2008-04-13
Hmmm, well I have ...

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted

... in my sources.list file. I presume that's the same deal?

Latest version available is 2:1.4.8-0ubuntu3~gutsy1 (gutsy-backports)

---

### Post by rune0077 on 2008-04-13
> **surfdoc said:**
> Hmmm, well I have ...

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted

... in my sources.list file. I presume that's the same deal?

Latest version available is 2:1.4.8-0ubuntu3~gutsy1 (gutsy-backports)

From Amarok's website: 

> Amarok 1.4.9.1 - a we still love you release
April 12, 2008 - 18:12


and:

> For users of Kubuntu 7.10, packages are in gutsy-backports available from Adept Manager when you choose Unsupported Updates from the Updates tab of Manage Repositories.

Packages are also in the Hardy development version.

Well, it's brand new, and they probably ships it to Hardy first. I think they'll ship it for Gutsy once they have all the packages in order, so be patient.

---

### Post by surfdoc on 2008-04-13
> **rune0077 said:**
> Well, it's brand new, and they probably ships it to Hardy first. I think they'll ship it for Gutsy once they have all the packages in order, so be patient.

i concur

---

### Post by PetePete on 2008-04-19
very useful, but how do I update the changelog to avoid upgrade nag?





> **timrobin said:**
> I crudely merged the SVN fix into the Gutsy source package and rebuilt.  

Steps:

Download the attached patch file 'coverfetcher.patch.txt'

```

apt-get source amarok
sudo apt-get build-dep amarok

```

Update 'amarok-1.4.7/debian/changelog' to avoid "upgrade" nagging (Optional)

```

cd amarok-1.4.7/amarok/src
patch < ../../../coverfetcher.patch.txt
cd ../../
dpkg-buildpackage -rfakeroot -b
sudo dpkg -i ../amarok*.deb

```

Start Amarok


Cover fetching working, nothing obviously broken.  Would have normally waited but I just rebuilt my collection and cant stand looking at that empty jewel case.

---

### Post by Sabeeh on 2008-04-19
i also had to install python-qt3

> sudo apt-get install python-qt3

---

### Post by padams10001 on 2008-04-24
Anyone know how to fix this in feisty??

---

### Post by Ripfox on 2008-05-03
Erm...Exaile is not working on cover fetch. Any ideas for an Exaile user?

---

### Post by Ripfox on 2008-05-06
Same..no covers in exaile

---

### Post by notoriousdbp on 2008-05-08
I've just upgraded amarok using the gutsy backports and no joy with album covers - i tried rhythmbox too and that also failed to fetch album covers

---

### Post by Ohwii on 2008-05-21
Any luck with exaile ??

---

### Post by blom on 2008-05-22
I get a similar message when running from console for all searches:

xml.amazon.com /onca/xml3?t=webservices-20&dev-t=15VDQG80MCS2K1W2VRR2&mode=music&type=lite&locale=us&page=1&f=xml&KeywordSearch=Basement%20Jaxx
Invalid response received: 410

(When running exaile in a console/shell that is)

---

### Post by Vajk on 2008-05-26
> **liquid circuit said:**
> First, you should probably close Amarok entirely.  Then download the 3 amarok .deb files to your Desktop (~/Desktop) from the link posted in [here.]("http://ubuntuforums.org/showpost.php?p=4653673&postcount=16")

Then open a terminal and run...
```
cd ~/Desktop
```

then run...
```
sudo dpkg -i amarok-engines_1.4.7-0ubuntu4_i386.deb amarok-xine_1.4.7-0ubuntu4_i386.deb amarok_1.4.7-0ubuntu4_i386.deb
```

Then re-open Amarok, and try and search for an album cover.  Hopefully it works.

it works on gutsy, thanks

---

