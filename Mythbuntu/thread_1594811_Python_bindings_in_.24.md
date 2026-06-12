---
title: "Python bindings in .24"
date: 2010-10-12
forum: Mythbuntu
---

### Post by joshoekstra on 2010-10-12
I've been having trouble getting metadata pulled in after I accidentally reset my metadata when moving disks.
Now I'd like to add the data again but I don't get any metadata via the frontend. If I press W on the movie Spider I get:
Using it via frontend gives this:
```
2010-10-11 16:45:15.155 Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l nl -M spider
2010-10-11 16:45:16.582 No results found for spider 0 0 

```
After a simple ls /usr/share/mythtv/metadata I discovered I don't have a Movie dir or tmdb.py installed, after pulling that from trac I get the same resulta but now manually I get this:
```
/usr/share/mythtv/metadata/Movie/tmdb.py -l nl -M spider
9613:Spider (2002)
40039:Spiders (2000)
and so on.... 
```

According to Robert McNamara and Raymond Wagner this is because the python bindings are not installed correctly.
I updated from .23.1 to .24 via mythbuntu-repos and checked if libmyth-python is installed, which it is.

Is there something I'm missing or is there something missing from the packages?

---

### Post by superm1 on 2010-10-12
Between these two commits I think it should hopefully be solved with tonight's autobuilds.

[http://bazaar.launchpad.net/~mythbuntu/mythtv/mythtv-trunk/revision/337](http://bazaar.launchpad.net/~mythbuntu/mythtv/mythtv-trunk/revision/337)
[http://bazaar.launchpad.net/~mythbuntu/mythtv/mythtv-trunk/revision/336](http://bazaar.launchpad.net/~mythbuntu/mythtv/mythtv-trunk/revision/336)

Please let us know tomorrow if the problem persist after upgrading to tonight's builds!

---

### Post by joshoekstra on 2010-10-13
Since I'm on the other side of the pond I guess after trunk26766?
Movies and stuff seems to be working now, thanks :)

---

### Post by superm1 on 2010-10-13
Yeah 26766 or newer. Glad it fixed the problem.

---

### Post by Herman Gerritsen on 2010-10-30
Hi there,

I seem to have the same problem.
I am using mythbuntu-repos .24 (27009) Updated from 23.1 on a Ubuntu 10.04 OS.

After the update I started using this metadata grabbing, so I am not sure it ever worked for me.

From the Frontend logs I see this:
```
2010-10-30 22:38:17.307 Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M The Matrix
2010-10-30 22:38:17.341 No results found for The Matrix 0 0

```When I run tmdb.py manually (from /usr/share/mythtv/metadata/Movie/) it returns this error:
```
me@be:/usr/share/mythtv/metadata/Movie$ ./tmdb.py -l en -M The Matrix

The subdirectory "tmdb" containing the modules tmdb_api.py (v0.1.3 or greater), tmdb_ui.py,
tmdb_exceptions.py must have been installed with the MythTV python bindings.
Error:(No module named lxml.etree)
```When I investigate the /usr/share/pyshared/Mythtv/tmdb directory on my backend the requested modules are there.

I am lost from here, are there any pointers?

Thanks,
Herman

---

### Post by joshoekstra on 2010-10-31
Try [http://www.gossamer-threads.com/lists/mythtv/users/455819](http://www.gossamer-threads.com/lists/mythtv/users/455819)
Also, try to determine if mythpython is available(just run mythpython in terminal)
Check if libmyth-python is installed in the same version as the rest.
Here it works like this and before it was solved I had the same errors...

---

### Post by Herman Gerritsen on 2010-10-31
> **joshoekstra said:**
> Try [http://www.gossamer-threads.com/lists/mythtv/users/455819](http://www.gossamer-threads.com/lists/mythtv/users/455819)
Also, try to determine if mythpython is available(just run mythpython in terminal)
 It is there
> **joshoekstra said:**
> 
Check if libmyth-python is installed in the same version as the rest.
Here it works like this and before it was solved I had the same errors...

This is where thing go wrong I think.
This is the result of "sudo apt-cache show libmyth-python":

```

me@be:~$ sudo apt-cache show libmyth-python
Package: libmyth-python
Source: mythtv
Priority: optional
Section: libs
Installed-Size: 580
Maintainer: MythTV Ubuntu Maintainers <ubuntu-mythtv@lists.ubuntu.com>
Architecture: all
Version: 0.24.0+fixes27009-0ubuntu0+mythbuntu1
Replaces: mythtv-common (<< 0.20.98)
Depends: python, python-support (>= 0.90.0), python-mysqldb
Conflicts: mythtv-common (<< 0.20.98)
Filename: pool/main/m/mythtv/libmyth-python_0.24.0+fixes27009-0ubuntu0+mythbuntu1_all.deb
Size: 126728
MD5sum: 74164f241080ec9f2a12933bb4382d8a
SHA1: 562ae6a05937b28091482f4c3a544d51690a58a5
Description: A python library to access some MythTV features
 MythTV provides a unified graphical interface for recording and viewing
 television programs. Refer to the mythtv package for more information.
 .
 This package contains files needed for some python MythTV add-ons.

Package: libmyth-python
Priority: optional
Section: universe/libs
Installed-Size: 692
Maintainer: MythTV Ubuntu Maintainers <ubuntu-mythtv@lists.ubuntu.com>
Architecture: all
Source: mythtv
Version: 0.23.0+fixes24158-0ubuntu2
Replaces: mythtv-common (<< 0.20.98)
Depends: python-mysqldb
Conflicts: mythtv-common (<< 0.20.98)
Filename: pool/universe/m/mythtv/libmyth-python_0.23.0+fixes24158-0ubuntu2_all.deb
Size: 180316
MD5sum: d6080bd47eccd3df343fedda83ceb827
SHA1: f2605e63eddf5645bfdd3ebdf2bb0d6c678f24d6
SHA256: 3626a18173638720ce80bfb9842fdb51a5fddd5315b4287da743efb8377a9eff
Description: A python library to access some MythTV features
 MythTV provides a unified graphical interface for recording and viewing
 television programs. Refer to the mythtv package for more information.
 .
 This package contains files needed for some python MythTV add-ons.
Homepage: http://www.mythtv.org
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Task: mythbuntu-backend-master, mythbuntu-backend-slave, mythbuntu-desktop, mythbuntu-frontend
```It says myth 0.24.0+fixes27009-0ubuntu0+mythbuntu1 is installed but the libmyth-python bindings are version 0.23.0+fixes24158-0ubuntu2

But "sudo apt-get remove libmyth-python" says nothing to remove

So I definently got a messed up upgrade...
Now I must get all the packages back in line.

If you can help me with getting rid of the old version without removing the whole installation I would like to hear. :)

Thanks so far.

Herman

---

### Post by Herman Gerritsen on 2010-10-31
> **joshoekstra said:**
> Try [http://www.gossamer-threads.com/lists/mythtv/users/455819](http://www.gossamer-threads.com/lists/mythtv/users/455819)
This thread does not get me anywhere.

I think I now have all my mythbuntu pakages in line:
"sudo dpkg --list | grep -i myth" gives me this:
```

ii  libmyth-0.24-0                       0.24.0+fixes27009-0ubuntu0+mythbuntu1           Common library code for MythTV and add-on mo
ii  libmyth-python                       0.24.0+fixes27009-0ubuntu0+mythbuntu1           A python library to access some MythTV featu
ii  libmythtv-perl                       0.24.0+fixes27009-0ubuntu0+mythbuntu1           A PERL library to access some MythTV feature
ii  mythbuntu-repos                      8.7-0ubuntu0+mythbuntu~auto20101030003223       Mythbuntu repos installer
ii  mythtv-backend                       0.24.0+fixes27009-0ubuntu0+mythbuntu1           A personal video recorder application (serve
ii  mythtv-common                        0.24.0+fixes27009-0ubuntu0+mythbuntu1           A personal video recorder application (commo
ii  mythtv-database                      0.24.0+fixes27009-0ubuntu0+mythbuntu1           A personal video recorder application (datab
ii  mythtv-transcode-utils               0.24.0+fixes27009-0ubuntu0+mythbuntu1           Utilities used for transcoding MythTV tasks
ii  mythweb                              0.24.0+fixes27009-0ubuntu0+mythbuntu1           Web interface add-on module for MythTV

```Stil I cannot reproduce the lines you get below:
[FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black]```
Manually: 
/usr/share/mythtv/metadata/Movie/tmdb.py -l nl -M spider 
9613:Spider (2002) 
40039:Spiders (2000) 
and so on.... 
```[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]I have also tried this with getting the tmdb.py from "svn -r 27009 co http://svn.mythtv.org/svn/trunk/". Also tried it with the /usr/share/pyshared/Mythtv/tmdb/*.py files from the svn version.
They all give me the same problem.
It still feels like the same problem you had though but the gossamer thread stops where things get interresting.

So still lost :( hope someone can give me some pointers from here.

Thanks,
Herman

---

### Post by joshoekstra on 2010-11-01
> **Herman Gerritsen said:**
> It is there


This is where thing go wrong I think.
This is the result of "sudo apt-cache show libmyth-python":


I got the same result, those packages are after all still cached on disk.

> **Herman Gerritsen said:**
> This thread does not get me anywhere.

I think I now have all my mythbuntu pakages in line:
"sudo dpkg --list | grep -i myth" gives me this:
```

ii  libmyth-0.24-0                       0.24.0+fixes27009-0ubuntu0+mythbuntu1           Common library code for MythTV and add-on mo
ii  libmyth-python                       0.24.0+fixes27009-0ubuntu0+mythbuntu1           A python library to access some MythTV featu
ii  libmythtv-perl                       0.24.0+fixes27009-0ubuntu0+mythbuntu1           A PERL library to access some MythTV feature
ii  mythbuntu-repos                      8.7-0ubuntu0+mythbuntu~auto20101030003223       Mythbuntu repos installer
ii  mythtv-backend                       0.24.0+fixes27009-0ubuntu0+mythbuntu1           A personal video recorder application (serve
ii  mythtv-common                        0.24.0+fixes27009-0ubuntu0+mythbuntu1           A personal video recorder application (commo
ii  mythtv-database                      0.24.0+fixes27009-0ubuntu0+mythbuntu1           A personal video recorder application (datab
ii  mythtv-transcode-utils               0.24.0+fixes27009-0ubuntu0+mythbuntu1           Utilities used for transcoding MythTV tasks
ii  mythweb                              0.24.0+fixes27009-0ubuntu0+mythbuntu1           Web interface add-on module for MythTV

```Stil I cannot reproduce the lines you get below:
[FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black]```
Manually: 
/usr/share/mythtv/metadata/Movie/tmdb.py -l nl -M spider 
9613:Spider (2002) 
40039:Spiders (2000) 
and so on.... 
```[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

You shouldn't, it's indicative for wrong bindings...
You should get something like:
```
 /usr/share/mythtv/metadata/Movie/tmdb.py -l nl -M spider
<?xml version='1.0' encoding='UTF-8'?>
<metadata>
  <item>
    <language>en</language>
    <title>Spiders</title>
    <inetref>40039</inetref>
    <imdb>0203940</imdb>
    <userrating>8.0</userrating>
    <description>A DNA experiment on a rare breed of spider is taking place on a NASA space shuttle, when a freak meteor shower engulfs the shuttle, causing everything to go horribly wrong. One survivor is found on the ship and watched over in a secret location deep in the California desert. The problem continues, as the survivor isn't alone, as another deadly spiders climbs out of him and goes on a rampage around the ship. Curious reporter Marci Eyre must now survive, escape and warn everyone before the spider reaches outside the desert.</description>
    <releasedate>2000-01-01</releasedate>
    <images>
      <image type="coverart" url="http://hwcdn.themoviedb.org/posters/46f/4c59c1155e73d63a6e00046f/spiders-original.jpg" width="666" height="949" thumb="http://hwcdn.themoviedb.org/posters/46f/4c59c1155e73d63a6e00046f/spiders-cover.jpg"/>
    </images>
    <lastupdated>Wed, 18 Aug 2010 22:52:15 GMT</lastupdated>
  </item>
  <item>
    <language>en</language>
    <title>Spider</title>
    <inetref>9613</inetref>
    <imdb>0278731</imdb>
    <userrating>7.6</userrating>
    <description>A brilliant and powerful psychological thriller about a deeply disturbed boy, Spider, who âseesâ his father brutally murder his mother and replace her with a prostitute. Convinced they plan to murder him next, Spider hatches an insane plan, which he carries through to tragic effect. Years later, his delusional account of his past begins to unravel and Spider spirals into fresh madness.</description>
    <releasedate>2002-05-21</releasedate>
    <images>
      <image type="coverart" url="http://hwcdn.themoviedb.org/posters/f8c/4bc9278a017a3c57fe00ff8c/spider-original.jpg" width="1000" height="1500" thumb="http://hwcdn.themoviedb.org/posters/f8c/4bc9278a017a3c57fe00ff8c/spider-cover.jpg"/>
      <image type="fanart" url="http://hwcdn.themoviedb.org/backdrops/566/4c9664d35e73d63a76000566/spider-original.jpg" width="1280" height="720" thumb="http://hwcdn.themoviedb.org/backdrops/566/4c9664d35e73d63a76000566/spider-thumb.jpg"/>
    </images>
    <lastupdated>Wed, 22 Sep 2010 00:28:11 GMT</lastupdated>
  </item>
ending with:
</metadata>

```
> 
I have also tried this with getting the tmdb.py from "svn -r 27009 co http://svn.mythtv.org/svn/trunk/". Also tried it with the /usr/share/pyshared/Mythtv/tmdb/*.py files from the svn version.
They all give me the same problem.
It still feels like the same problem you had though but the gossamer thread stops where things get interresting.

So still lost :( hope someone can give me some pointers from here.

Thanks,
Herman

I was using trunk before and had to uninstall and reinstall after switch to .24-fixes happened to reïnstall libmyth-python if I'm not mistaken. This didn't interfere with any settings and recordings I had made.
Do you still have the .23 version installed as well? If that doesn;t help I'm at a loss as well concerning the cause of your trouble.

---

### Post by Herman Gerritsen on 2010-11-01
> **joshoekstra said:**
> Do you still have the .23 version installed as well? If that doesn;t help I'm at a loss as well concerning the cause of your trouble.

I think I have succefully removed anything from older version. At least I think "dpkg --list" gives a list of all installed packages (and not cached) but I am not 100% sure.

> **joshoekstra said:**
> I was using trunk before and had to  uninstall and reinstall after switch to .24-fixes happened to reïnstall  libmyth-python if I'm not mistaken. This didn't interfere with any  settings and recordings I had made.

Should I fully remove myth? and than after a mythbuntu reconfigure to .24 reinstall myth?
Think I will try that in one of the comming days when I have some time to spare.

Thanks,
Herman

---

### Post by joshoekstra on 2010-11-01
> **Herman Gerritsen said:**
> I think I have succefully removed anything from older version. At least I think "dpkg --list" gives a list of all installed packages (and not cached) but I am not 100% sure.



Should I fully remove myth? and than after a mythbuntu reconfigure to .24 reinstall myth?
Think I will try that in one of the comming days when I have some time to spare.

Thanks,
Herman
It helped me past the bump of libmyth 0.23 :)
I hope a dev drops by here who's more knowledgeable ;)

---

### Post by joshoekstra on 2010-11-03
> **joshoekstra said:**
> It helped me past the bump of libmyth 0.23 :)
I hope a dev drops by here who's more knowledgeable ;)

Can we conclude everything is working for you as well?

---

### Post by Herman Gerritsen on 2010-11-09
> **joshoekstra said:**
> Can we conclude everything is working for you as well?
Sadly not :(
 
I have reinstalled myth on front and backend. And still can't do the metadata grabbing from my frontend (I have a sperate front and backend)
 
I tried installing a frontend on my backend server. If I do the metagrabbing from that frontend everything goes fine.
 
So In short, I can only grab from a frontend that is installed on my backend server.
Everything that is grabbed will show up on all my other frontends, just can't do any updating there. (I suppose grabbing from frontends should be possible though.)
 
So the problem is partly solved :)...
 
I will keep updating any new mythbuntu packages and hope it works someday ;)
If I really have some time to spare I could try to look deeper, but right now I would not know where to start.
 
Greetings,
Herman

---

### Post by iitywygms on 2010-11-16
Any update?
I am in the exact same boat. :(
And why marked solved?

---

### Post by extasy on 2010-11-17
I've got the exact same problem with .24 with fixes update. Installed a updated set of mythtv today so I should have the most current. But still the problem is there.

---

### Post by Herman Gerritsen on 2010-11-19
Hi There,

Today I have upgraded my frontend (not yet my backend).
My grabbing problems are now solved. :)

I upgraded through the commandline (sudo apt-get update && sudo apt-get upgrade)
Now I have  this version:

MythTV Version   : 27280
MythTV Branch    : branches/release-0-24-fixes
Network Protocol : 63
Library API      : 0.24.20101028-1
QT Version       : 4.6.2


Thanks to all, Hope everybody has the same results with the newest version.
Herman

---

