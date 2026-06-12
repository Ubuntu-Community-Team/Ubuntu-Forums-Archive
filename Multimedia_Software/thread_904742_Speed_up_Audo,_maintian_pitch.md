---
title: "Speed up Audo, maintian pitch????"
date: 2008-08-29
forum: Multimedia Software
---

### Post by toDIEisGAIN on 2008-08-29
Hey I'm trying to listen to some school related audio. I want to listen to it at a higher speed without changing the pitch from normal to Chipmunk. SMPlayer is great at speeding it up, but when I go to preferences and turn on the pitch maintainer the music stops and won't start. Is there any other program I might use? Or a fix for SMPlayer. Thanks guys.

---

### Post by rvm4000 on 2008-08-29
I guess this is because you're using an old mplayer. The option "High speed playback without altering the pitch" in the smplayer preferences, uses the mplayer scaletempo filter, which is not available in mplayer 1.0rc2.

To be sure, just take a look at the mplayer log (Options->View logs) after trying to play a file. You'll probably find this:
```

Couldn't find audio filter 'scaletempo'
[libaf] Couldn't create or open audio filter 'scaletempo'
Error at audio filter chain pre-init!

Exiting... (Fatal error)
```

You can find [here](http://sourceforge.net/project/showfiles.php?group_id=185512&package_id=260588) some deb packages for ubuntu with newer versions of mplayer, all of them with the scaletempo filter.

(If you have trouble with the installation, [take a look at this](http://smplayer.berlios.de/forums/viewtopic.php?pid=2691#p2691))

---

### Post by toDIEisGAIN on 2008-08-30
Thats exactly what it said. When i try to install any of the packages on either of the links i get the line..."Error: Dependency is not satisfiable: libconfhelper-perl" And on the forum posts I only saw the 64 version for hardy.

---

### Post by rvm4000 on 2008-08-30
libconfhelper-perl is not available in hardy, but it can be got from gutsy:

Add these lines to your /etc/apt/sources.list:
```
deb http://es.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb http://es.archive.ubuntu.com/ubuntu/ gutsy universe
```

And then run:
```

sudo apt-get install libconfhelper-perl/gutsy  liblogfile-rotate-perl/gutsy
```

Now you should be able to install the mplayer package.

---

### Post by toDIEisGAIN on 2008-08-30
So it won't work for Hardy at all? Or those will work for hardy?

---

### Post by rvm4000 on 2008-08-30
Yes, I think it should work. You only have to install libconfhelper-perl and liblogfile-rotate-perl from gutsy as explained before, to satisfy the mplayer dependencies. Then install mplayer.

---

### Post by toDIEisGAIN on 2008-08-31
How do I add the first two? (Sorry for the noob question)

---

### Post by rvm4000 on 2008-08-31
Open a console and type:

```
sudo nano /etc/apt/sources.list
```

(nano is a text editor, you can replace it with the one you like)

Add these lines somewhere in it:
```
deb http://es.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb http://es.archive.ubuntu.com/ubuntu/ gutsy universe
```

Save changes.

And now type:
```

sudo apt-get update
sudo apt-get install libconfhelper-perl/gutsy  liblogfile-rotate-perl/gutsy
```

That should download and install those two packages.

---

### Post by toDIEisGAIN on 2008-08-31
Damn. Still says it can't find the package.

---

### Post by rvm4000 on 2008-08-31
What's exactly the error?

Anyway I think you can download those packages directy from here:

[libconfhelper-perl_0.12.5_all.deb](http://es.archive.ubuntu.com/ubuntu/pool/universe/libc/libconfhelper-perl/libconfhelper-perl_0.12.5_all.deb)

[liblogfile-rotate-perl_1.04-4_all.deb](http://es.archive.ubuntu.com/ubuntu/pool/universe/libl/liblogfile-rotate-perl/liblogfile-rotate-perl_1.04-4_all.deb)

---

### Post by toDIEisGAIN on 2008-09-01
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Release 'gutsy' for 'libconfhelper-perl' was not found

After I downloaded the two.


Btw thanks so much for all your help.

---

### Post by rvm4000 on 2008-09-01
Try the following:

Delete the two lines you added to /etc/apt/sources.list.

Type in a console:
```
sudo apt-get update
```

Install the two packages:

```

cd *directory_where_you_downloaded_the_files*
sudo dpkg -i libconfhelper-perl_0.12.5_all.deb liblogfile-rotate-perl_1.04-4_all.deb
```

If everything's ok, install the new mplayer:
```

sudo dpkg -i mplayer_1.0rc2svn26030_i386.deb
```

---

### Post by Archmage on 2008-09-01
I know that mythtv has the option to play them faster, while not altering the pitch, but this would be a little to much to use this only for this.

---

### Post by toDIEisGAIN on 2008-09-03
Thanks for the help rvm. I appreciate it.

---

### Post by rvm4000 on 2008-09-08
I've just created a new deb package. This time it doesn't depend on old packages, so it should install without problems on Hardy:

[mplayer_1.0rc2svn27483_i386.deb](http://downloads.sourceforge.net/smplayer/mplayer_1.0rc2svn27483_i386.deb)

There's also the same package for amd64:
[mplayer_1.0rc2svn27483_amd64.deb](http://downloads.sourceforge.net/smplayer/mplayer_1.0rc2svn27483_amd64.deb)

---

### Post by Geremia on 2011-01-20
> **toDIEisGAIN said:**
> Hey I'm trying to listen to some school related audio. I want to listen to it at a higher speed without changing the pitch from normal to Chipmunk. SMPlayer is great at speeding it up, but when I go to preferences and turn on the pitch maintainer the music stops and won't start. Is there any other program I might use? Or a fix for SMPlayer. Thanks guys.
VLC does this.

---

