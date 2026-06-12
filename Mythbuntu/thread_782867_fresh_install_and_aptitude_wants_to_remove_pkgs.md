---
title: "fresh install and aptitude wants to remove pkgs"
date: 2008-05-05
forum: Mythbuntu
---

### Post by jackson on 2008-05-05
I did a clean Mythbuntu 8.04 install two days ago and now have things pretty much working well.  However, whenever I ssh in to my myth box to install something (e.g. nuvexport) aptitude tells me it is going to remove several packages including portmap and smbfs:

```
$sudo aptitude install nuvexport
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  libdebconfclient0 libevent1 libgssglue1 libnfsidmap2 librpcsecgss3 localechooser-data nfs-common portmap smbfs
The following packages have been automatically kept back:
  apport ffmpeg hal libavcodec1d libavformat1d libavutil1d libgtk2.0-0 libgtk2.0-common libhal-storage1 libhal1
  libpostproc1d libswscale1d python-apport python-problem-report
The following NEW packages will be automatically installed:
  libamrnb3 libamrwb3 libc6-dev libid3-3.8.3-dev libid3-3.8.3c2a libtwolame0 linux-libc-dev mencoder zlib1g-dev
The following packages have been kept back:
  apport-gtk mplayer
The following NEW packages will be installed:
  libamrnb3 libamrwb3 libc6-dev libid3-3.8.3-dev libid3-3.8.3c2a libtwolame0 linux-libc-dev mencoder nuvexport
  zlib1g-dev
0 packages upgraded, 10 newly installed, 9 to remove and 16 not upgraded.
Need to get 7779kB of archives. After unpacking 25.4MB will be used.
Do you want to continue? [Y/n/?] n
Abort.
```

I have always aborted b/c I don't want to mess things up, but this happens all the time.  Can I safely uninstall these packages?  I might want to share my myth box over nfs or smbfs, so it seems like I would lose that functionality if I remove the packages.

It's strange how this vanilla Mythbuntu 8.04 install wants to remove this stuff.

---

### Post by andrewc6l on 2008-05-05
I saw the same thing, and when I said "Ok, do it" I *did* lose smbfs support. The solution for me was to:

apt-get install smbfs

(and any other packages that I wanted to keep). Apt then marked them as "installed by user" or something like that. I did the install only for nfs-common, portmap and smbfs. Some of the others appear to be used only during the install process (localechooser-data, for instance).

---

### Post by jackson on 2008-05-05
Thanks very much.  That's what I'd figured I would do too, I was just curious if anyone else had seen this.  Thanks again!

---

### Post by capink on 2008-05-06
To prevent aptitude from removing any packages on your system, issue the following command:

```
sudo aptitude keep-all
```

---

