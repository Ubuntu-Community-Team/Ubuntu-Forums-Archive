---
title: "problems with DVD playing"
date: 2010-05-13
forum: Multimedia Software
---

### Post by dcdano2007 on 2010-05-13
Greetings:  Running Ubuntu 9.10 on a Toshiba Portege' Laptop.  Just purchased a Samsung SE-S084C external DVD burner.  Computer/Ubuntu recognizes it and it works for writing data..etc.  It will not however play movies.  I have searched everywhere to figure out what to do...tried the instructions on [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Here is what I get in my terminal window:

dano@dano-laptop:~$  sudo apt-get install libdvdread4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 lsb-graphics lsb-desktop m4 ncurses-term libqt4-gui
  lsb pax lsb-core linux-headers-2.6.31-14-generic lsb-cxx
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
dano@dano-laptop:~$  sudo /usr/share/doc/libdvdread4/install-css.sh
Error parsing proxy URL wpad://: Unsupported scheme.
dano@dano-laptop:~$ 

Question:  what is this **Error parsing proxy URL wpad://:Unsupported scheme** and how do I get rid of it?  I have searched for this answer too...without luck.  

Any advice would be greatly appreciated.  Thanks.

---

### Post by lrcaballero on 2010-05-13
Try this and see if it helps you...

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Luis Caballero

---

### Post by dcdano2007 on 2010-05-13
Here are the results....

dano@dano-laptop:~$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
Error parsing proxy URL wpad://: Unsupported scheme.

dano@dano-laptop:~$ sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package app-install-data-medibuntu

dano@dano-laptop:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

dano@dano-laptop:~$ wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
Error parsing proxy URL wpad://: Unsupported scheme.

dano@dano-laptop:~$ sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
dpkg: error processing libdvdcss2_1.2.9-2medibuntu4_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libdvdcss2_1.2.9-2medibuntu4_i386.deb

dano@dano-laptop:~$

Any other thoughts???

---

### Post by dcdano2007 on 2010-05-14
Anything?  Anyone???

---

### Post by Alpha1Dash1 on 2010-05-14
Hi. I've just been through this process. I (luckily!) made some notes when I did the the same for a previous installation (taken from a website that I didn't make a note of, so I can't credit the real author). The 4 steps I followed were:

1)install the medibuntu repos (I think this is what is failing on your system) with:
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

2) install the decrypting libraries with:
sudo apt-get install libdvdcss2 libdvdread4 libdvdnav4

3)set the system up to use the css decrypting libs with:
sudo /usr/share/doc/libdvdread4/install-css.sh

4) delete the contents of the (hidden) folder ./dvdcss in your home folder.

Then try playing the dvd...

Note: you may also need to install extra codecs - I'd start with:
sudo apt-get install non-free-codecs

and if they don't work for a particular dvd, install gstreamer ones.

best of luck.

---

### Post by eltonw on 2010-05-14
> **dcdano2007 said:**
> Anything?  Anyone???

You can get more help if you state what MULTIMEDIA applications you have installed in the Sound and Video section. Have you installed / tried VLC for example? Be more specific: "does not play" means? doesn't load the DVD? no sound, or sound no video? are there any error messages? Have you UN-installed any libraries, for example?

Some more precise detail on what exactly happens when you install the DVD into the drive would help. 

The Samsung external DVD-R SE-S084C you need to _[COLOR="Sienna"]connect BOTH USB plugs to the computer[/COLOR]_, to properly power the device and for ***reliable*** USB i/o.
You can even burn disks with only ONE of the usb plugs connected, but the burn will not be 'correct' (try verifying after a burn, and you'll see).

.... [COLOR="Green"][FONT="Comic Sans MS"]your problem might be as simple as not _properly connecting_ the device [*see above*] to your laptop[/FONT][/COLOR].

HTH...

---

### Post by dcdano2007 on 2010-05-14
Alpha:  Step 1 loaded a few things.  Got same errors while doing step 2 and 3 listed...also no directory found from step 4.  I am showing hidden files/directories as well in the file viewer...

Elton:  both cables are plugged in.  No differences.  I am trying Movie Player, VLC Media Player, and Dragon Player.  Both Movie Player and VLC start up with an empty window then end and close out within 2 seconds.  Just the dvd icon with movie name appears on wallpaper screen.  Dragon starts up, and the cursor stays in 'busy' mode.  Nothing happens after that...stays busy...

That being said, I can view videos via hulu.com and youtube.  

What libraries should I be deleting?

Thanks for the help!!!

---

### Post by mc4man on 2010-05-14
you can always get libdvdcss2 directly - go here and pick the third listed if on a 64 bit install or fourth listed if a 32 bit install

[http://download.videolan.org/pub/libdvdcss/1.2.10/deb/](http://download.videolan.org/pub/libdvdcss/1.2.10/deb/)

> Error parsing proxy URL wpad://: Unsupported scheme.
A somewhat rare error - are you using a proxy or did you try to install ubuntu-restricted-extras and the install hung up on you? (most likely on ttf-mscorefonts...

---

### Post by 2hot6ft2 on 2010-05-14
This always worked for me in 9.10 and should still work unless they changed something.
Open a terminal
Applications > Accessories > Terminal
and run these commands one at a time and your password wont be shown when you type it in just type it in and hit enter.
This first one enables the medibuntu repository for restricted codecs and such
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
Remove any browser media player plugin you currently have installed (totem-mozilla is installed by default, but you may have installed mozilla-mplayer or mozilla-plugin-vlc) like this:
```
sudo apt-get remove totem-mozilla mozilla-mplayer mozilla-plugin-vlc
```
then for all the multimedia, mp3's, divx web player, and dvd playback
```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 gecko-mediaplayer
```
Oracle Java is part of the ubuntu-restricted-extras package so use your arrow keys and Tab key to select and Enter to accept or deny the Java terms of use depending on whether you want openjdk or sun java.
And to get rid of one package in the restricted extras that causes problems:
```
sudo apt-get purge ttf-mscorefonts-installer
```
ttf-mscorefonts-installer bug report
[https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217](https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217)
:popcorn:

---

