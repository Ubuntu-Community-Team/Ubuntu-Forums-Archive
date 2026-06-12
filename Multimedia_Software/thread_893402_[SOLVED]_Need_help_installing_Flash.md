---
title: "[SOLVED] Need help installing Flash"
date: 2008-08-18
forum: Multimedia Software
---

### Post by Sendress on 2008-08-18
even though Im a newbie for sure, iv been using ubuntu for a year now. I have scoured forums and websites trying to fix the flash on my system. iv tried everything except reinstalling the os. would someone please help me with flash. im about to scrap this whole thing. [email]steve.endress@earthlink.net[/email]

---

### Post by finer recliner on 2008-08-18
please give us more infomation: 

what version of ubuntu are you using?

are you using adobe's flash plugin, or an open-source alternative?

what version is the plugin?

what error do you get (if any)?

what happens when you try to view a website with flash in it?

---

### Post by Sendress on 2008-08-18
please give us more infomation:

what version of ubuntu are you using? 8.04 hardy heron

are you using adobe's flash plugin, or an open-source alternative? trying to use adobe not sure of other

what version is the plugin? 8, 9, 10. iv tried them all

what error do you get (if any)? no error, just doent work

what happens when you try to view a website with flash in it? youtube, metacafe, give me a white screen with no action.

---

### Post by finer recliner on 2008-08-18
what kind of firefox plugins do you have installed?

try disabling them one by one to see if one of them is blocking flash content (for example, noscript)

---

### Post by ajgreeny on 2008-08-18
Using ```
gksudo nautilus
``` navigate to /usr/lib/flashplugin-nonfree and rename the file** libflashplugin.so** to **libflashplugin.so~**.  Now using your downloaded tar.gz of flashplayer10, (which you must have already as you say you have tried v10), extract the archive, open the folder that is made and copy the **libflashplugin.so** file to /usr/lib/flashplugin-nonfree, where you have just renamed the original.

I have used this manual method for the last three updates of flash, through the two beta versions to the 10rc version, available now, and it has always worked without a problem.  Give it a try and good luck.

---

### Post by Sendress on 2008-08-18
sendress@Dell-D600:~$ gksudo nautilus
Initializing nautilus-share extension

** (nautilus:18251): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


i tried changing the icon in the same folder but its not an option either.

---

### Post by ajgreeny on 2008-08-18
Sorry it should be ```
gksu nautilus
```, my mistake.  Try that and see if it helps. 

EDIT:  If I use ```
gksudo nautilus
``` in the terminal I get a long error like you with the string of SSSSSSSSSSSSSSSSSSSs but nautilus still opens as root, and I can still use it OK.  If I use gksu nautilus the error messages are absent.  It makes no difference to my use of it though, and I understand that gksudo is just a linked command to gksu, anyway, so it should not make any difference to the outcome.

Sorry for any confusion this may cause you;  we're all still learning all through life!

---

### Post by Sendress on 2008-08-18
flash player ten wont install in the usr/lib/flashplugin directory only in the home/sendress/.mozilla and when i go to retrieve it to just drag and drop the .mozilla doesnt even exist. 

the terminal has an error message "note: please ask your administrator to remove the xpti.dat from the components directory of the mozilla netscape directory."

---

### Post by ajgreeny on 2008-08-19
> flash player ten wont install in the **usr/lib/flashplugin** directory only in the home/sendress/.mozilla and when i go to retrieve it to just drag and drop the .mozilla doesnt even exist.It's the **/usr/lib/flashplugin-nonfree** folder.  Try that and see if it helps.  If not then I am baffled. It has worked for me many times without problem.

---

### Post by gandaran on 2008-08-19
> **ajgreeny said:**
> It's the **/usr/lib/flashplugin-nonfree** folder.  Try that and see if it helps.  If not then I am baffled. It has worked for me many times without problem.

the /usr/lib/flashplugin-nonfree folder only exists if he has the synaptic adobe flash package installed.
for the adobe tarball, it's recommended to install in either home/user/.mozilla/plugins or /usr/lib/mozilla/plugins, flash will work in any of these folders, there's no deference at all if it's installed in the flashplugin-nonfree or the mozillas folders, it's the same, I recommend the home folder, no root permission needed here, if one flash version gives you problems you can easily delete and replace with another.

---

### Post by aysiu on 2008-08-19
Can you paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal) and paste the output back here? ```
uname -m
cat /etc/lsb-release
cat /etc/apt/sources.list
ls /usr/lib/firefox/plugins
dpkg -s flashplugin-nonfree
dpkg -s mozilla-plugin-gnash
dpkg -s swfdec-mozilla
```

---

### Post by Sendress on 2008-08-20
sendress@Dell-D600:~$ uname -m
i686
sendress@Dell-D600:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
sendress@Dell-D600:~$ cat /etc/apt/sources.list

## what i added on jan 28
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
sendress@Dell-D600:~$ ls /usr/lib/firefox/plugins
flashplugin-alternative.so
sendress@Dell-D600:~$ dpkg -s flashplugin-nonfree
Package: flashplugin-nonfree
Status: install ok installed
Priority: optional
Section: contrib/web
Installed-Size: 164
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 9.0.124.0ubuntu2
Replaces: flashplugin (<< 6)
Depends: debconf | debconf-2.0, fontconfig, libatk1.0-0, libc6, libcairo2, libexpat1, libfontconfig1, libfreetype6, libglib2.0-0, libgtk2.0-0, libice6, libpango1.0-0, libpng12-0, libsm6, libx11-6, libxau6, libxcursor1, libxdmcp6, libxext6, libxfixes3, libxi6, libxinerama1, libxrandr2, libxrender1, libxt6, wget, zlib1g
Suggests: firefox, firefox-3.0, konqueror-nsplugins, libflashsupport, msttcorefonts, ttf-bitstream-vera | ttf-dejavu, ttf-xfree86-nonfree, x-ttcidfont-conf, xfs (>= 1:1.0.1-5), xulrunner-1.9
Conflicts: flashplayer-mozilla, flashplugin (<< 6), xfs (<< 1:1.0.1-5)
Description: Adobe Flash Player plugin installer
 This package will download the Flash Player from Adobe.  It is a
 Netscape/Mozilla type plugin.  Any browser based on Netscape or Mozilla can
 use the Flash plugin.  This package currently supports the following browsers:
 Mozilla, Mozilla-Firefox, Firefox, Iceweasel, and Iceape.  Also Galeon and
 Epiphany can use the Flash plugin.  Konqueror can also use the Flash plugin if
 konqueror-nsplugins is installed.
 .
 WARNING: Installing this Ubuntu package causes the Adobe flash plugin to be
 downloaded from [www.adobe.com](www.adobe.com).  The distribution license of the Adobe flash
 plugin is available at [www.adobe.com](www.adobe.com).  Installing this Ubuntu package implies
 that you have accepted the terms of that license.
 .
  Homepage: [http://wiki.ubuntu.com/FlashPlayer9](http://wiki.ubuntu.com/FlashPlayer9)
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a, aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Adobe Flash Player (installer)
Original-Maintainer: Bart Martens <bartm@knars.be>
sendress@Dell-D600:~$ dpkg -s mozilla-plugin-gnash
Package: mozilla-plugin-gnash
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 308
Maintainer: Alexander Sack <asac@ubuntu.com>
Architecture: i386
Source: gnash
Version: 0.8.2-0ubuntu3
Depends: gnash (= 0.8.2-0ubuntu3), libc6 (>= 2.7-1), libgcc1 (>= 1:4.1.1-21), libstdc++6 (>= 4.2.1-4), libx11-6, libxi6
Description: free SWF movie player - Plugin for Mozilla and derivatives
 Gnash is a free Flash movie player, which works either standalone, or as
 plugin for Firefox/Mozilla or Konqueror.
 .
 This package includes the plugin for Firefox/Mozilla Web Browser.
 .
 Homepage: [http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/)
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384,92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a,aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Gnash SWF Player
Original-Maintainer: Miriam Ruiz <little_miry@yahoo.es>
sendress@Dell-D600:~$ dpkg -s swfdec-mozilla

---

### Post by aysiu on 2008-08-20
I think I know what the problem is, but can you post the output of ```
dpkg -s swfdec-mozilla
``` and also this command? ```
ls -l /usr/bin/firefox
```

---

### Post by Sendress on 2008-08-20
sendress@Dell-D600:~$ dpkg -s swfdec-mozilla

Package `swfdec-mozilla' is not installed and no info is available.

Use dpkg --info (= dpkg-deb --info) to examine archive files,

and dpkg --contents (= dpkg-deb --contents) to list their contents.





sendress@Dell-D600:~$ gksudo nautilus

Initializing nautilus-share extension



** (nautilus:6621): WARNING **: Unable to add monitor: Operation not supported

SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory

Please ask your system administrator to enable user sharing.

---

### Post by Sendress on 2008-08-20
sendress@Dell-D600:~$ dpkg -s swfdec-mozilla

Package `swfdec-mozilla' is not installed and no info is available.

Use dpkg --info (= dpkg-deb --info) to examine archive files,

and dpkg --contents (= dpkg-deb --contents) to list their contents.

sendress@Dell-D600:~$ 




sendress@Dell-D600:~$ ls -l /usr/bin/firefox

lrwxrwxrwx 1 root root 11 2008-07-31 10:57 /usr/bin/firefox -> firefox-3.0

sendress@Dell-D600:~$

---

### Post by aysiu on 2008-08-20
Okay. If you close Firefox, paste in this code ```
sudo apt-get remove mozilla-plugin-gnash gnash
``` and then start Firefox again, I think you should be good.

---

### Post by Sendress on 2008-08-21
that did the trick. an epic thank you

---

### Post by Flyingjester on 2008-08-21
The problem was you had two flash players installed the non-free, and gnash, they were creating a conflict.

---

