---
title: "flashplugin-nonfree doesn't work"
date: 2008-09-04
forum: Multimedia Software
---

### Post by bcrowell on 2008-09-04
Here's what I've done so far:

Enabled multiverse.

apt-get update && apt-get install flashplugin-nonfree

When I go to a page with flash content, it says I don't have the plugin installed.

Typing about:plugins in Firefox's url bar gives a bunch of java plugins, but no flash plugin.

I've seen people saying to make a symbolic link to /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so , but I don't have that file.

I've seen people saying to install nspluginwrapper, but the package doesn't seem to exist in any of the repos I have available (hardy, universe, multiverse).

This is all on hardy, 32-bit.

Can anyone help? Thanks in advance!

---

### Post by snowpine on 2008-09-04
Hi Bcrowell, at the risk of stating the obvious :) have you tried closing and restarting Firefox? You must restart your browser for the change to take effect.

---

### Post by Andrew B. on 2008-09-04
I think I might have the same problem.  With me, I found that the problem was with Firefox.  I am using Hardy 8.04 and I wanted to look at BBC iplayer, which requires the nonfree Flash player.  I tried all sorts of things and read lots of Forum threads.  In the end I installed Opera (from the Opera website, which had a self-explanatory installer) and then found that Flash was working fine.

I have no idea what the problem is but given that Flash works in Opera, and not in Firefox, I think it might be a problem with Firefox.

Does that help at all?  Is the problem you have related to looking at streaming video on websites?

---

### Post by wolfen69 on 2008-09-04
nspluginwrapper is used for 64bit hardy. the following worked for a friend of mine. ```
sudo apt-get purge flashplugin-nonfree
``` then ```
sudo apt-get clean
```then ```
sudo apt-get autoremove
``` then ```
sudo apt-get install flashplugin-nonfree
``` make sure firefox is closed during this procedure. for good measure also do ```
sudo apt-get install libflashsupport
```

---

### Post by Andrew B. on 2008-09-04
Wolfen, I tried the things you suggested and they haven't fixed my problem, but thank you anyway.

---

### Post by gandaran on 2008-09-04
> **bcrowell said:**
> Here's what I've done so far:

Enabled multiverse.

apt-get update && apt-get install flashplugin-nonfree

When I go to a page with flash content, it says I don't have the plugin installed.

Typing about:plugins in Firefox's url bar gives a bunch of java plugins, but no flash plugin.

I've seen people saying to make a symbolic link to /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so , but I don't have that file.

I've seen people saying to install nspluginwrapper, but the package doesn't seem to exist in any of the repos I have available (hardy, universe, multiverse).

This is all on hardy, 32-bit.

Can anyone help? Thanks in advance!

look the best way to install packages is using synaptic, open the synaptic package manager, scroll down to flashplugin-nonfree, check if the package is really installed,  if not mark for install and click the apply button.

if it's really installed, then one question, which firefox you running FF2 OR FF3?  and  check tools » addons » plugins, see if the flashplugin is enabled. 

another thing. you only need to install libflashsupport if you have any flash sound problems.

---

### Post by Andrew B. on 2008-09-04
Gandaran

In my installation, in Synaptic the Flashplayer nonfree is shown as installed.  In Firefox 3 addins, it is shown as installed (and the Gnash one is shown as disabled).  But still BBC iplayer does not work in Firefox but** does work** in Opera.

What can it be if it works in Opera and not in Firefox, do you think?

---

### Post by gandaran on 2008-09-04
> **Andrew B. said:**
> Gandaran

In my installation, in Synaptic the Flashplayer nonfree is shown as installed.  In Firefox 3 addins, it is shown as installed (and the Gnash one is shown as disabled).  But still BBC iplayer does not work in Firefox but** does work** in Opera.

What can it be if it works in Opera and not in Firefox, do you think?

I have answered you questions here [http://ubuntuforums.org/showthread.php?t=841613&page=3](http://ubuntuforums.org/showthread.php?t=841613&page=3)

---

### Post by aysiu on 2008-09-04
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

### Post by bcrowell on 2008-09-04
Hi, all,

Thanks for all the replies!

> Hi Bcrowell, at the risk of stating the obvious  have you tried closing and restarting Firefox? You must restart your browser for the change to take effect.

Yes, I did restart firefox.

Wolfen69, thanks for the suggestion, but that didn't help for me.

Gandaran, I'm running ff 2.0. I don't have a plugins under tools » addons, but if that's just a different way of getting to the about:plugins, as indicated in my original post, that page does *not* show the flash plugin as being installed, even after I install flashplugin-nonfree.

Here's the output from the commands aysiu asked for:

```
root@clifford:/home/bcrowell# uname -m
i686
root@clifford:/home/bcrowell# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
root@clifford:/home/bcrowell# cat /etc/apt/sources.list
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy universe multiverse
root@clifford:/home/bcrowell# ls /usr/lib/firefox/plugins
flashplugin-alternative.so
root@clifford:/home/bcrowell# dpkg -s flashplugin-nonfree
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
root@clifford:/home/bcrowell# dpkg -s mozilla-plugin-gnash
Package `mozilla-plugin-gnash' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
root@clifford:/home/bcrowell# dpkg -s swfdec-mozilla
Package `swfdec-mozilla' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
```

---

### Post by aysiu on 2008-09-04
I'm baffled. That all looks good to me.

i686. 8.04. Good sources.list. The Flash plugin is in the plugins folder. Adobe Flash is installed. None of the other Flash players are installed.

I'm stumped.

---

### Post by gandaran on 2008-09-05
bcrowell
       if you running FF2 on ubuntu hardy 8.04 32-bits, then you have to install flash manually, (won't work on 64-bits systems).
download the adobe tar.gz package to desktop here [http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/)
extract the package, drag or copy the **libflashplayer.so** file to the hidden home .mozilla/plugins folder (no plugins folder there? make one) thats all, it'll work.
if you have more than one user account, then copy the file to /usr/lib/mozilla/plugins or /usr/lib/firefox 2/plugins, this way flash installed in the root file system (you have to be root for this) can be used by all users, remove the flashplugin- nonfree, this manually installed flash will also be used by firefox 3.

---

### Post by bcrowell on 2008-09-07
Thanks, gandaran, that worked!

---

