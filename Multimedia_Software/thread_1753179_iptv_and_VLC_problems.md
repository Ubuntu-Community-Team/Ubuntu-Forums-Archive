---
title: "iptv and VLC problems"
date: 2011-05-08
forum: Multimedia Software
---

### Post by rodtud on 2011-05-08
Hi,
I'm trying to view TPG's iptv but get the message:
"The installed VLC software and web browser plugin are too old.

This indicates a problem with the software that will require you
upgrade to the latest version in order to watch TPG IPTV.

Click OK to continue viewing this page with errors,
or Cancel to take you to the download page for the software."

If I click OK it wants to search for plugins, and wants:

"RTP protocol source"

If I click Cancel, it takes me to the VLC download page to download version 1.1.9 which I already have installed.

I have just upgraded to 'Natty'.

Has anyone managed to overcome these problems?

Sorry if this has already been answered, but I couldn't find it.

Rod

---

### Post by labinnsw on 2011-06-22
I place the attached script in my home directory, set it to open with vlc,  and create a launcher. (My launcher is placed on cairo dock, but feel free to put yours on the desktop, the menu of your desktop manager or the panel you use.)

Still trying to figure out how to install the vlc rtp protocol source plugin.

N.B. File must be extracted.

---

### Post by Yellow Pasque on 2011-06-22
VLC has to be built with liblivemedia-dev for live555 (rtp) support. See: [http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

---

### Post by labinnsw on 2011-06-25
> **Temüjin said:**
> VLC has to be built with liblivemedia-dev for live555 (rtp) support. See: [http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

Thanks for your help.
I couldn't get past the second command in the link you posted.

```
labinnsw@UbuntuLTS:~$ sudo apt-get -y install build-essential git-core checkinstall automake yasm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.

git-core is already the newest version.
checkinstall is already the newest version.
automake is already the newest version.
yasm is already the newest version.
The following packages were automatically installed and are no longer required:
  libopenal1 libva-x11-1 dvgrab swh-plugins nspluginwrapper libsox-fmt-mp3 libbluray0 libsox-fmt-pulse transcode-doc iw libx11-xcb1 libqjson0 kdenlive-data libdirac-decoder0 mplayer-skins libmatroska0
  lsdvd audacity-data liblzo2-2 sox libvdpau1 xine-ui chromium-browser-inspector libvamp-hostsdk3 libebml0 libxcb-randr0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
labinnsw@UbuntuLTS:~$ sudo apt-get -y install liba52-0.7.4-dev libaa1-dev libasound2-dev libass-dev libavahi-client-dev libcaca-dev libcairo2-dev libcddb2-dev libcdio-dev libdca-dev libdirac-dev libdvbpsi-dev libdvdnav-dev libdvdread-dev libebml-dev libfaad-dev libflac-dev libfluidsynth-dev libfreetype6-dev libfribidi-dev libgcrypt11-dev libggi2-dev libgl1-mesa-dev libglib2.0-0 libgnomevfs2-dev libgnutls-dev libhal-dev libid3tag0-dev libjack-dev libkate-dev liblircclient-dev liblua5.1-0-dev libmad0-dev libmatroska-dev libmodplug-dev libmpcdec-dev libmpeg2-4-dev libmtp-dev libncursesw5-dev libnotify-dev libogg-dev liboggkate-dev libpango1.0-dev libpng12-dev libprojectm-dev libprojectm-qt-dev libproxy-dev libpulse-dev libqt4-dev libraw1394-dev librsvg2-dev libschroedinger-dev libsdl-image1.2-dev libsdl1.2-dev libshout3-dev libsmbclient-dev libspeex-dev libsqlite3-dev libsvga1-dev libsysfs-dev libtag1-dev libtar-dev libgme-dev libtheora-dev libtool libtwolame-dev libudev-dev libupnp3-dev libv4l-dev libva-dev libvcdinfo-dev libvorbis-dev libvpx-dev libx11-dev libx11-xcb-dev libxcb-composite0-dev libxcb-keysyms1-dev libxcb-randr0-dev libxcb-shm0-dev libxcb-xv0-dev libxcb-xvmc0-dev libxcb1-dev libxext-dev libxml2-dev libxpm-dev libxt-dev libxv-dev libzvbi-dev lua5.1 qt4-qtconfig xulrunner-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
liba52-0.7.4-dev is already the newest version.
libaa1-dev is already the newest version.
libasound2-dev is already the newest version.
libass-dev is already the newest version.
libavahi-client-dev is already the newest version.
libcaca-dev is already the newest version.
libcairo2-dev is already the newest version.
libcairo2-dev set to manually installed.
libcddb2-dev is already the newest version.
libcdio-dev is already the newest version.
libdca-dev is already the newest version.
E: Couldn't find package libdvbpsi-dev
labinnsw@UbuntuLTS:~$
```

Trying to solve it with instructions from [this link]("http://ubuntuforums.org/showpost.php?p=10654297&postcount=2") just produces another error:

```
labinnsw@UbuntuLTS:~$ dget -ux https://launchpad.net/ubuntu/+archive/primary/+files/libdvbpsi_0.1.7-1.dsc
dget: retrieving https://launchpad.net/ubuntu/+archive/primary/+files/libdvbpsi_0.1.7-1.dsc
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
103  1975  103  1975    0     0    492      0  0:00:04  0:00:04 --:--:--  6114
dget: using existing libdvbpsi_0.1.7.orig.tar.gz
dget: using existing libdvbpsi_0.1.7-1.diff.gz
dpkg-source: info: extracting libdvbpsi in libdvbpsi-0.1.7
dpkg-source: info: unpacking libdvbpsi_0.1.7.orig.tar.gz
dpkg-source: info: applying libdvbpsi_0.1.7-1.diff.gz
labinnsw@UbuntuLTS:~$ cd libdvbpsi_0.1.7
bash: cd: libdvbpsi_0.1.7: No such file or directory
labinnsw@UbuntuLTS:~$ 

```

Googling > No such file or directory "libdvbpsi_0 1.7"
[yeilds one result]("http://www.google.com.au/search?q=No+such+file+or+directory+%22libdvbpsi_0+1.7%22&hl=en&num=10&lr=&ft=i&cr=&safe=images&tbs=") which leads to [this]("http://osdir.com/ml/debian-bugs-closed/2011-05/msg01126.html") and I can't make head or tail of that.

---

### Post by Yellow Pasque on 2011-06-25
> E: Couldn't find package libdvbpsi-dev
That's odd. This package is in standard natty repos.
> No such file or directory "libdvbpsi_0 1.7" 
You didn't type the directory name correctly. Use autocomplete (Hit 'Tab' twice).

---

### Post by labinnsw on 2011-06-25
> **Temüjin said:**
> That's odd. This package is in standard natty repos.

You didn't type the directory name correctly. Use autocomplete (Hit 'Tab' twice).

I am using 64 bit Lucid and I didn't type, I copied and paste. I have double checked the instructions and I can't see where I made an error. Do you know what the correct directory name should be?

Tabbing twice only produces a beep. (twice)

---

### Post by Yellow Pasque on 2011-06-25
Oh, for Lucid:
```
sudo apt-get install libdvbpsi5-dev
```

---

### Post by labinnsw on 2011-06-27
I accidentally discovered just today, that it works with the [nightly build of firefox]("https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa"). Not sure if any of the other stuff helped because I have been installing them as well.

---

