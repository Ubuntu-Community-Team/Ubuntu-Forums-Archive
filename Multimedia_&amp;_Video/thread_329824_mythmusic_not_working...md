---
title: "mythmusic not working.."
date: 2007-01-02
forum: Multimedia &amp; Video
---

### Post by eldragon on 2007-01-02
whenever i start mythfrontend, i get the following error:

2007-01-02 10:30:34.030 Registering Internal as a media playback plugin.
2007-01-02 10:30:34.064 Registering MythDVD DVD Media Handler as a media handler ext()
2007-01-02 10:30:34.065 Registering MythDVD VCD Media Handler as a media handler ext()
2007-01-02 10:30:34.086 Registering MythGallery Media Handler 1/2 as a media handler ext()
2007-01-02 10:30:34.086 Registering MythGallery Media Handler 2/2 as a media handler ext(gif,jpg,png)
libmp4ff.so.0: cannot open shared object file: No such file or directory
2007-01-02 10:30:34.088 MythPlugin::Init() dlerror: 
2007-01-02 10:30:34.088 Unable to initialize plugin 'mythmusic'.


i cant locate libmp4ff.so.0 anywhere in my system, i tried installing faad, which is already installed. and still nothing. everything else in mythtv works ok.

anyone got a clue? 

thanks

---

### Post by superm1 on 2007-01-03
> **eldragon said:**
> whenever i start mythfrontend, i get the following error:

2007-01-02 10:30:34.030 Registering Internal as a media playback plugin.
2007-01-02 10:30:34.064 Registering MythDVD DVD Media Handler as a media handler ext()
2007-01-02 10:30:34.065 Registering MythDVD VCD Media Handler as a media handler ext()
2007-01-02 10:30:34.086 Registering MythGallery Media Handler 1/2 as a media handler ext()
2007-01-02 10:30:34.086 Registering MythGallery Media Handler 2/2 as a media handler ext(gif,jpg,png)
libmp4ff.so.0: cannot open shared object file: No such file or directory
2007-01-02 10:30:34.088 MythPlugin::Init() dlerror: 
2007-01-02 10:30:34.088 Unable to initialize plugin 'mythmusic'.


i cant locate libmp4ff.so.0 anywhere in my system, i tried installing faad, which is already installed. and still nothing. everything else in mythtv works ok.

anyone got a clue? 

thanks
At this point, did you try to *reinstall* faad or just saw it was installed and move on?:
```
sudo apt-get install --reinstall libfaad2
```
It is supposed to have that file.  

Also, you didn't compile from source or anything right?

---

### Post by eldragon on 2007-01-03
no, i didnt compile it, just installed from repos.

tried libfaad2 and:

eldragon@emmet:~$ sudo apt-get install --reinstall libfaad2
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libfaad2


i did try to reinstall faad only, but it didnt fix it.

locate libmp4ff doesnt find anything.

which repo should have libfaad2?

---

### Post by superm1 on 2007-01-03
> **eldragon said:**
> no, i didnt compile it, just installed from repos.

tried libfaad2 and:

eldragon@emmet:~$ sudo apt-get install --reinstall libfaad2
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libfaad2


i did try to reinstall faad only, but it didnt fix it.

locate libmp4ff doesnt find anything.

which repo should have libfaad2?
My mistake,

its 

```
sudo apt-get install --reinstall libfaad2-0

```

I just glanced at the source package when I looked before and didn't catch the -0.

---

### Post by eldragon on 2007-01-04
ive already done that. not cutting it.


eldragon@emmet:~$ sudo apt-get install --reinstall libfaad2-0
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/176kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libfaad2-0
Install these packages without verification [y/N]? y
(Reading database ... 138060 files and directories currently installed.)
Preparing to replace libfaad2-0 2.0.0+cvs20060416-0.0 (using .../libfaad2-0_2.0.0+cvs20060416-0.0_i386.deb) ...
Unpacking replacement libfaad2-0 ...
Setting up libfaad2-0 (2.0.0+cvs20060416-0.0) ...

eldragon@emmet:~$ locate libmp4ff
eldragon@emmet:~$

---

### Post by superm1 on 2007-01-04
> **eldragon said:**
> ive already done that. not cutting it.


eldragon@emmet:~$ sudo apt-get install --reinstall libfaad2-0
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/176kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libfaad2-0
Install these packages without verification [y/N]? y
(Reading database ... 138060 files and directories currently installed.)
Preparing to replace libfaad2-0 2.0.0+cvs20060416-0.0 (using .../libfaad2-0_2.0.0+cvs20060416-0.0_i386.deb) ...
Unpacking replacement libfaad2-0 ...
Setting up libfaad2-0 (2.0.0+cvs20060416-0.0) ...

eldragon@emmet:~$ locate libmp4ff
eldragon@emmet:~$
Where is it getting this libfaad2-0?  The problem appears to be that you have a third party version?

```
apt-cache policy libfaad2-0
```
You need to install the one from ubuntu repositories, and then pin it to that version.

---

### Post by eldragon on 2007-01-04
ok, it was getting the libfaad2-0 from the cinelerra repos

i got rid of those,

did an apt-get update

then tried sudo apt-get install --reinstall libfaad2-0

and received:

eldragon@emmet:~$ sudo apt-get install --reinstall libfaad2-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of libfaad2-0 is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



btw: the apt-cache gave the following:

eldragon@emmet:~$ apt-cache policy libfaad2-0
libfaad2-0:
  Installed: 2.0.0+cvs20060416-0.0
  Candidate: 2.0.0+cvs20060416-0.0
  Version table:
 *** 2.0.0+cvs20060416-0.0 0
        500 [http://www.kiberpipa.org](http://www.kiberpipa.org) ./ Packages
        100 /var/lib/dpkg/status
     2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages

---

### Post by superm1 on 2007-01-04
> **eldragon said:**
> ok, it was getting the libfaad2-0 from the cinelerra repos

i got rid of those,

did an apt-get update

then tried sudo apt-get install --reinstall libfaad2-0

and received:

eldragon@emmet:~$ sudo apt-get install --reinstall libfaad2-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of libfaad2-0 is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



btw: the apt-cache gave the following:

eldragon@emmet:~$ apt-cache policy libfaad2-0
libfaad2-0:
  Installed: 2.0.0+cvs20060416-0.0
  Candidate: 2.0.0+cvs20060416-0.0
  Version table:
 *** 2.0.0+cvs20060416-0.0 0
        500 [http://www.kiberpipa.org](http://www.kiberpipa.org) ./ Packages
        100 /var/lib/dpkg/status
     2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages

Okay, you can open up synaptic and search for libfaad2-0.  Press ctrl-e and it will let you force a version.  

Also you might be able to force it using aptitude instead of apt-get, but i've always had trouble with it.

---

### Post by eldragon on 2007-01-05
that did it! thanks a lot!

now, only problem is it removed cinelerra.....well, i'll figure that out later :D

---

### Post by superm1 on 2007-01-05
> **eldragon said:**
> that did it! thanks a lot!

now, only problem is it removed cinelerra.....well, i'll figure that out later :D
If mythmusic was the only thing that broke by using this library, I can help you work out rebuilding mythmusic using the cinelerra library locally.  This is a bit of work though, so your call :)

---

### Post by eldragon on 2007-01-05
thanks a lot, but its ok, didnt use cinelerra anyway.

i much rather keep the ubuntu version. much more compatible for the future :)

oh, and i didnt realize mythmusic sucked this bad, well. now i know

---

### Post by Fisslefink on 2007-03-31
Encountered the same error after a dist-upgrade from Edgy to Feisty with mythmusic version 0.20-svn20070122-0.0ubuntu2 (upgraded automatically).

I fixed it by downloading the faad2 rpm from this site:
[ftp://rpmfind.net/linux/freshrpms/fedora/linux/5/faad2/faad2-2.0-8.fc5.i386.rpm](ftp://rpmfind.net/linux/freshrpms/fedora/linux/5/faad2/faad2-2.0-8.fc5.i386.rpm)

and converting it to a .deb package using alien, then decompressing this package and copying the files in "/data/usr/lib" to my /usr/lib folder:

libfaad.so.0
libfaad.so.0.0.0
libmp4ff.so.0
libmp4ff.so.0.0.0
libmp4v2.so.0
libmp4v2.so.0.0.0

I have attached these files as a .tar archive to make this easier on the next person.  Simply decompress the .tar and copy the files to /usr/lib.

Restarting mythfrontend solved the problem right away, no reboot needed.

Hope that helps.

Fisslefink

---

### Post by superm1 on 2007-03-31
> **Fisslefink said:**
> Encountered the same error after a dist-upgrade from Edgy to Feisty with mythmusic version 0.20-svn20070122-0.0ubuntu2 (upgraded automatically).

I fixed it by downloading the faad2 rpm from this site:
[ftp://rpmfind.net/linux/freshrpms/fedora/linux/5/faad2/faad2-2.0-8.fc5.i386.rpm](ftp://rpmfind.net/linux/freshrpms/fedora/linux/5/faad2/faad2-2.0-8.fc5.i386.rpm)

and converting it to a .deb package using alien, then decompressing this package and copying the files in "/data/usr/lib" to my /usr/lib folder:

libfaad.so.0
libfaad.so.0.0.0
libmp4ff.so.0
libmp4ff.so.0.0.0
libmp4v2.so.0
libmp4v2.so.0.0.0

I have attached these files as a .tar archive to make this easier on the next person.  Simply decompress the .tar and copy the files to /usr/lib.

Restarting mythfrontend solved the problem right away, no reboot needed.

Hope that helps.

Fisslefink
Going to the feisty version of all packages shouldn't require this.  If you had to convert a faad2 from an rpm based distro, there are existing issues with your packages.  It's a much much better solution to install the version on the feisty mirrors.

---

### Post by skralljt on 2007-07-03
What an idiotic problem, I have this problem of xmms not being able to decode m4a files.  I had a libfaad2.5 version installed from rarewares or marillat's repo, 2.5, that didn't have the mp4f:

libmp4ff.so.0: cannot open shared object file: No such file or directory

error, so then I forced the ubuntu repo version, libfaad2.0, and now xmms works all of a sudden!  aacgain doesn't, but better to be able to listen to music than not at all....

If anyone is having the problem of xmms not opening aac/mp4/m4a files, and you are using multiverse packages, make sure you try rolling back to libfaad2.0, it worked for me!

---

### Post by 4embrey on 2007-10-14
</quote>and converting it to a .deb package using alien, then decompressing this package and copying the files in "/data/usr/lib" to my /usr/lib folder:

libfaad.so.0
libfaad.so.0.0.0
libmp4ff.so.0
libmp4ff.so.0.0.0
libmp4v2.so.0
libmp4v2.so.0.0.0

I have attached these files as a .tar archive to make this easier on the next person. Simply decompress the .tar and copy the files to /usr/lib.

Restarting mythfrontend solved the problem right away, no reboot needed.

Hope that helps.

Fisslefink</quote>

Fix it ... Thank you !

---

