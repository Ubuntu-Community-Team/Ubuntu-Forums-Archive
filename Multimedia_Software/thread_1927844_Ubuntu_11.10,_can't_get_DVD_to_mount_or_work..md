---
title: "Ubuntu 11.10, can't get DVD to mount or work."
date: 2012-02-18
forum: Multimedia Software
---

### Post by rrtobin on 2012-02-18
Here is what I tried and what I get.  Nothing can see dvd media in drive.  music CD seems to work ok, but DVD no working.

Thanks for the help.

*-cdrom
                description: DVD writer
                product: DVD Writer 740b
                vendor: HP
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: HI24
                serial: [
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc

sudo mount /dev/dvd dvd
mount: no medium found on /dev/sr0

---

### Post by garvinrick4 on 2012-02-18
Just a thought:
Did you install "libdvdcss2" so as to be able to play DVD's.
Not in 11.10 right now,  always used to be in medibuntu repository:

Look under ppa tab and click on your 11.10 version and install ppa as instructed:

[http://www.ubuntuupdates.org/ppas](http://www.ubuntuupdates.org/ppas)

Then:
```
sudo apt-get install libdvdcss2
```

---

### Post by rrtobin on 2012-02-19
Thanks for the reply.  I cant seem to find the ppa in that link.

Here is what I tried and the response I received.

sudo apt-get install libdvdcss2

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libdvdcss2' has no installation candidate

Thanks for the help and suggestions.

---

### Post by rrtobin on 2012-02-19
I also tried to just install Mplayer to get it to work. Here are my results.

> sudo apt-get update

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

> sudo apt-get install mplayer

Reading package lists... Done
Building dependency tree       
Reading state information... Done
mplayer is already the newest version.
mplayer set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by garvinrick4 on 2012-02-19
```
gksudo gedit /etc/apt/sources.list
```Now put a # (comment mark) in front of two offending lines below and hit save. This will take them
out of play.

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/p...source/Sources]("http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/source/Sources")  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/p...-i386/Packages]("http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages")  404  Not Found

Now go to this web site and then hit ppa tab and go down to medibuntu and add by clicking
on version of Ubuntu you are using and follow instructions for medibuntu free.
[http://www.ubuntuupdates.org/ppas](http://www.ubuntuupdates.org/ppas)

If they ask for a key to the medibuntu ppa after installing open terminal and copy and paste these two lines.
```
gpg --keyserver keyserver.ubuntu.com --recv 2EBC26B60C5A2783
``````
gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -
```Then add your libdvdcss2:
```
sudo apt-get install libdvdcss2
```

---

### Post by garvinrick4 on 2012-02-19
> mplayer is already the newest version.It showed already installed when you tried to install mplayer.
Type 
```
totem
```
in terminal and see what opens.

---

### Post by garvinrick4 on 2012-02-19
Open "software sources" and you will see ppa's added. Can use check marks also to add
or "comment out" so they do not come in play. click on screenshots.

---

### Post by garvinrick4 on 2012-02-20
For those whom prefer to put new line sources.list for repository:
Add lets say medibuntu to:
Open a editor as per below in root so as to be able to add and save (not read only)
```
gksudo gedit /etc/apt/sources.list
```Add line to bottom of sources.list then hit save (gksudo in previous command gave root powers)
```
deb http://packages.medibuntu.org/ oneiric free non-free
```Add key in terminal. 

```
gpg --keyserver keyserver.ubuntu.com --recv 2EBC26B60C5A2783
``````
gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -
``````
sudo apt-get update
```Done

##If added a ppa and cannot find it in sources list look in directory.
 /etc/apt/sources.list.d

##There are 3 or more ways to add a ppa to your repo list. I believe the easiest is adding
by instructions at ppa site (do not forget key if shows. Then use "Software Sources" to
add or remove ppa's use with simple checkmark and a sudo apt-get update.
Use which one makes you comfortable. Nice to learn multiple ways to install ppa's and their keys. 

#If any new user has any questions please ask.

#If using the version in Alpha or Beta 12.04 will be know "precise 12.04" medibuntu repo open. Will be a oneiric if wanted for "precise 12.04". 
  That is true of most if not all ppa's do not have available until version is released.

---

