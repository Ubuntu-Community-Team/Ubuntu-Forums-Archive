---
title: "Why is current daily-live not current"
date: 2010-06-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by VMC on 2010-06-21
For the past several current daily-live ISO, I noticed that when I issue upgrade there is mega updates. 

I was under the impression that the current was in fact current. It's not. What's the point of making a current daily-live if it is not current.

Example: June21st, todays installed ISO shows 138mg of updates.

I guess my question is what are they updating from say the 20th to todays 21st ISO? Both show the same amount of updates.

```
The following packages will be upgraded:
  aisleriot anacron apport apport-gtk apt apt-transport-https apt-utils at-spi baobab binutils brltty brltty-x11 byobu
  coreutils couchdb-bin cpio empathy empathy-common evolution-webcal f-spot file-roller gcc-4.5-base gnome-dictionary
  gnome-games-common gnome-mahjongg gnome-panel gnome-panel-data gnome-screenshot gnome-search-tool gnome-sudoku
  gnome-system-log gnome-system-tools gnome-utils gnomine gnupg gnupg-curl gpgv grub-common grub-pc gtk2-engines-pixbuf
  hdparm indicator-applet indicator-applet-session indicator-me indicator-sound initramfs-tools initramfs-tools-bin
  iso-codes libanthy0 libarchive1 libatspi1.0-0 libbrlapi0.5 libdbusmenu-glib1 libdbusmenu-gtk1 libelf1 libgail-common
  libgail18 libgcc1 libgdict-1.0-6 libgl1-mesa-dri libgl1-mesa-glx libglib2.0-0 libglib2.0-data libglu1-mesa libgomp1
  libgpm2 libgtk-vnc-1.0-0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgweather-common libgweather1 libido-0.1-0
  libindicate-gtk2 libindicate4 libmission-control-plugins0 libncurses5 libncursesw5 liboobs-1-4 libpanel-applet2-0
  libpango1.0-0 libpango1.0-common libparted0debian1 libpci3 libpng12-0 libpoppler-glib4 libpoppler5 libsane libsmbclient
  libspectre1 libssl0.9.8 libstdc++6 libtelepathy-glib0 libtiff4 libusb-0.1-4 libwbclient0 libxdamage1 linux-generic
  linux-headers-generic linux-image-generic linux-libc-dev locales lupin-casper mobile-broadband-provider-info
  nautilus-sendto-empathy ncurses-base ncurses-bin ntpdate nvidia-current-modaliases openssl parted pciutils poppler-utils
  pptp-linux protobuf-compiler python-apport python-brlapi python-glade2 python-gobject python-gtk2 python-gtkspell
  python-indicate python-problem-report python-protobuf python-pyatspi python-pygoocanvas python-ubuntuone-client
  python-ubuntuone-storageprotocol python-xapian quadrapassel rdesktop rhythmbox rhythmbox-plugin-cdrecorder
  rhythmbox-plugins rsync samba-common samba-common-bin sane-utils screen smbclient software-center synaptic tar
  telepathy-gabble telepathy-mission-control-5 ttf-indic-fonts-core ttf-punjabi-fonts ubuntuone-client
  ubuntuone-client-gnome udisks usbutils x11-utils xscreensaver-data xscreensaver-gl
154 upgraded, 11 newly installed, 0 to remove and 1 not upgraded.
Need to get 138MB of archives.
```

---

### Post by kansasnoob on 2010-06-21
That's interesting. I hadn't updated mine with zsync since just after Alpha 1 until now. I'll try to remember to update every day and see how much the image changes from day to day.

---

### Post by VMC on 2010-06-21
Thanks.During the Lucid  cycle, zsyncing from day to day, it was kept current.

 I asked a question over at Launchpad. Awaiting for an answer. If I get one, I'll pass it along.

---

### Post by jerrylamos on 2010-06-21
If you look in the Maverick schedule you'll note that there are some freezes going on prior to Alpha 2.

Jerry

---

### Post by kansasnoob on 2010-06-21
> **jerrylamos said:**
> If you look in the Maverick schedule you'll note that there are some freezes going on prior to Alpha 2.

Jerry

In the past if things are "frozen" the daily just doesn't update. I've seen that many times.

I know VMC is not just a "looky-loo"! If VMC sees a problem then we should watch and see if it's a recurring problem.

If it's an intended change in how things work we should also know that so it can be well documented.

Based on my previous experiences with VMC this needs to be taken seriously!

---

### Post by kansasnoob on 2010-06-21
> **jerrylamos said:**
> If you look in the Maverick schedule you'll note that there are some freezes going on prior to Alpha 2.

Jerry

In the past if things are "frozen" the daily just doesn't update. I've seen that many times.

I know VMC is not just a "looky-loo"! If VMC sees a problem then we should watch and see if it's a recurring problem.

If it's an intended change in how things work we should also know that so it can be well documented.

Based on my previous experiences with VMC this needs to be taken seriously!

---

### Post by kansasnoob on 2010-06-21
> **jerrylamos said:**
> If you look in the Maverick schedule you'll note that there are some freezes going on prior to Alpha 2.

Jerry

In the past if things are "frozen" the daily just doesn't update. I've seen that many times.

I know VMC is not just a "looky-loo"! If VMC sees a problem then we should watch and see if it's a recurring problem.

If it's an intended change in how things work we should also know that so it can be well documented.

Based on my previous experiences with VMC this needs to be taken seriously!

---

### Post by kansasnoob on 2010-06-22
I have no idea why that multi-post happened.

Sorry. I've encountered some problems with Opera in Maverick.

---

### Post by wilee-nilee on 2010-06-22
> **kansasnoob said:**
> I have no idea why that multi-post happened.

Sorry. I've encountered some problems with Opera in Maverick.

Yow a triple post, I noticed servers slowing a few minutes ago, I had to do a firefox close when I had edited a post and it was just hanging, the edit was there when I opened it again.

---

### Post by kansasnoob on 2010-06-23
I noticed yesterday the daily stayed frozen at 06/21
but today there was a new 06/23:

> lance@lance-desktop:~$ cd Downloads
lance@lance-desktop:~/Downloads$ zsync [http://cdimage.ubuntu.com/daily-live/current/maverick-desktop-i386.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/maverick-desktop-i386.iso.zsync)
#################### 100.0% 288.2 kBps DONE     

reading seed file maverick-desktop-i386.iso: ***************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read maverick-desktop-i386.iso. **[COLOR="Red"]Target 72.7% complete.[/COLOR]**      
downloading from [http://cdimage.ubuntu.com/daily-live/current/maverick-desktop-i386.iso:](http://cdimage.ubuntu.com/daily-live/current/maverick-desktop-i386.iso:)
#################### 100.0% 575.0 kBps DONE      

verifying download...checksum matches OK
used 533471232 local, fetched 201376316


I probably won't have time to actually burn it though but I see it showed only 72.7% complete updating the iso from 06/21 so there were changes.

---

### Post by VMC on 2010-06-23
> **kansasnoob said:**
> I noticed yesterday the daily stayed frozen at 06/21
but today there was a new 06/23:



I probably won't have time to actually burn it though but I see it showed only 72.7% complete updating the iso from 06/21 so there were changes.

I noticed that too. It's the first time in several sessions that the % was less than 90%. After installation most all updates were included. So I guess my question has been answered. Probably the alternate was kept up to date, but I prefer to test the ubiquity installs.

The reason I even asked the question was during the previous 3 or 4 daily-live had very few updated included. I was wondering what was the reason for any new ISO's if the updates weren't included.

It's a moot point now (thanks Ranch Hand :)). I guess their back on track.

---

