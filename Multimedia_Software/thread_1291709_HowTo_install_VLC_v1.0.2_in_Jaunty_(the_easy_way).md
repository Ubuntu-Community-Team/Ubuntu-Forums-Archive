---
title: "HowTo: install VLC v1.0.2 in Jaunty (the easy way)"
date: 2009-10-15
forum: Multimedia Software
---

### Post by linuxed on 2009-10-15
The latest version of VLC currently available in the repository for Jaunty users is v0.9.9.  If you're using Karmic however, the latest version is v1.0.2.  The guide below will walk you through the process of installing VLC v1.0.2 on Jaunty.
[list=1]
[*]Type the following.
```
sudo gedit /etc/apt/sources.list
```
[*]Copy the following and paste it at the very end of the file.
```

## karmic
deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse

```
[*]Click save and close gedit.
[*]Type the following:
```

sudo apt-get update
sudo apt-get install vlc

```
[*]Make sure that you don't perform any additional upgrades at this point other than whatever packages are mandatory for the new version of VLC to function properly.  As soon as the packages are installed type the following.
```

sudo gedit /etc/apt/sources.list

```
[*]Type a # sign in front of each of the entries that you previously added.
```

# deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
# deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
# deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb http://security.ubuntu.com/ubuntu karmic-security main restricted
# deb http://security.ubuntu.com/ubuntu karmic-security universe
# deb http://security.ubuntu.com/ubuntu karmic-security multiverse

```
[*]Click save and close gedit.
[*]Type the following.
```

sudo apt-get update

```
[*]At this point the libgcrypt11 package that you have installed is going to cause an error to occur in cups.  To fix this issue you will need to manually extract a couple of files to your /lib folder.  Download the libgcrypt11 v1.4.1 package ([32-bit users](http://packages.ubuntu.com/jaunty/i386/libgcrypt11/download) or [64-bit users](http://packages.ubuntu.com/jaunty/amd64/libgcrypt11/download)) to your Desktop and then type the following.
```

cd ~/Desktop
dpkg --extract libgcrypt11*.deb libgcrypt
sudo cp -P libgcrypt/lib/* /lib

```
[*]You can delete the libgcrypt folder and deb package on your desktop.  You might want to restart cups just to make sure everything's working.
```

sudo /etc/init.d/cups restart

```
[/list]

**If you upgrade to Karmic**
```

sudo apt-get install --reinstall libgcrypt11

```

---

### Post by defensorfedei on 2010-03-05
There is another easy way to do this, which is much safer.  I tried the above hack and it really screwed with my panel and caused frequent OAFID errors.  Another way to upgrade your vlc is as follows.

 1- Open /etc/apt/sources.list file and add this line to the bottom:

          deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) jaunty main  

**you can replace 'jaunty' with whatever version of Ubuntu you are using**

Save and close the file.

2-Then install GPG key using the following command:

          sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7613768D

3-Then type in terminal: sudo apt-get update

4-Then open up synaptic and navigate to vlc.  Then mark it for an upgrade and click apply.

This is much safer than installing packages that are not intended for you system. It also seems much easier than the originally posted method.

This link can provide more info: [http://www.ubuntugeek.com/howto-install-vlc-media-player-1-0-0-in-ubuntu.html](http://www.ubuntugeek.com/howto-install-vlc-media-player-1-0-0-in-ubuntu.html)

---

