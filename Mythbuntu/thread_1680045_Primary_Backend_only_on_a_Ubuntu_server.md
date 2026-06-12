---
title: "Primary Backend only on a Ubuntu server?"
date: 2011-02-01
forum: Mythbuntu
---

### Post by boondocks on 2011-02-01
Can you install and run the mythtv-backend (or the mythtv-backend-master) on Ubuntu server?
A Ubuntu **console-only** server that has no desktop environment like gnome, kde, lxde or xfce.

With no mythtv-frontend running on that Ubuntu server ...
Would the installation of the mythtv-backend trigger some kind of desktop environment as a dependency?
How would you run the "MythTV Backend Setup" and the "Mythbuntu Control Centre"?

---

### Post by can2002 on 2011-02-02
Hi there,

You need the base X libraries but you don't need a full desktop environment. If you install the mythtv-backend-master metapackage it will handle this for you (on a base server install, for example).  

You could then forward X through a SSH session to run mythtv-setup, although I finally settled on adding on XFCE and NX to my master backend.

Cheers,
Chris

---

### Post by boondocks on 2011-02-02
That is good to know.
Thanks.

---

### Post by nickrout on 2011-02-02
For the record, this is what my server says it will install:

> nick@server:~/LJ$ sudo aptitude install mythtv-backend-master
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following NEW packages will be installed:
  apache2-mpm-prefork{a} apport-gtk{a} apt-xapian-index{a} aspell{a} aspell-en{a} dictionaries-common{a} docbook-xml{a} gamin{a} gdb{a} gksu{a} gnome-keyring{a} gnome-mime-data{a} gvfs{a}
  gvfs-backends{a} hunspell-en-us{a} indicator-application{a} launchpad-integration{a} libapache2-mod-php5{a} libappindicator0{a} libarchive1{a} libart-2.0-2{a} libaspell15{a} libatasmart4{a}
  libavahi-glib1{a} libavc1394-0{a} libbluetooth3{a} libbonobo2-0{a} libbonobo2-common{a} libbonoboui2-0{a} libbonoboui2-common{a} libcairo-perl{a} libcdio-cdda0{a} libcdio-paranoia0{a} libcdio10{a}
  libdbusmenu-glib1{a} libdbusmenu-gtk1{a} libenchant1c2a{a} libgail18{a} libgamin0{a} libgcr0{a} libgdu0{a} libgksu2-0{a} libglade2-0{a} libglu1-mesa{a} libgnome-keyring0{a} libgnome2-0{a}
  libgnome2-canvas-perl{a} libgnome2-common{a} libgnome2-perl{a} libgnome2-vfs-perl{a} libgnomecanvas2-0{a} libgnomecanvas2-common{a} libgnomeui-0{a} libgnomeui-common{a} libgnomevfs2-0{a}
  libgnomevfs2-common{a} libgnomevfs2-extra{a} libgp11-0{a} libgstreamer0.10-0{a} libgtk2-perl{a} libgtop2-7{a} libgtop2-common{a} libgudev-1.0-0{a} libgvfscommon0{a} libhal-storage1{a} libhal1{a}
  libhtml-template-perl{a} libhunspell-1.2-0{a} libiec61883-0{a} libimobiledevice0{a} libindicator0{a} libjson-glib-1.0-0{a} liblaunchpad-integration1{a} liblzma1{a} libmagickcore2{a} libmagickwand2{a}
  libmath-round-perl{a} libmng1{a} libmyth-0.23-0{a} libmythtv-perl{a} libnet-upnp-perl{a} libnotify1{a} libntfs10{a} libopenobex1{a} libpam-gnome-keyring{a} libpango-perl{a} libphonon4{a} libplist1{a}
  libpolkit-agent-1-0{a} libproxy0{a} libqt4-dbus{a} libqt4-designer{a} libqt4-network{a} libqt4-opengl{a} libqt4-qt3support{a} libqt4-script{a} libqt4-sql{a} libqt4-sql-mysql{a} libqt4-webkit{a}
  libqt4-xml{a} libqt4-xmlpatterns{a} libqtcore4{a} libqtgui4{a} librarian0{a} libsexy2{a} libsgutils2-2{a} libsoup-gnome2.4-1{a} libsoup2.4-1{a} libstartup-notification0{a} libusbmuxd1{a} libvdpau1{a}
  libvte-common{a} libvte9{a} libwnck-common{a} libwnck22{a} libxaw7{a} libxcb-atom1{a} libxcb-aux0{a} libxcb-event1{a} libxmu6{a} libxres1{a} mtools{a} mysql-server mysql-server-5.1{a}
  mysql-server-core-5.1{a} mythtv-backend mythtv-backend-master mythtv-common{a} mythtv-database mythtv-transcode-utils{a} mythweb notification-daemon{a} ntfsprogs{a} ntp obex-data-server{a} php5{a}
  php5-common{a} php5-mysql{a} policykit-1-gnome{a} pwgen{a} python-cairo{a} python-debian{a} python-gconf{a} python-glade2{a} python-gtk2{a} python-vte{a} python-xapian{a} python-xdg{a}
  rarian-compat{a} scrollkeeper{a} sgml-data{a} software-properties-gtk{a} synaptic{a} ttf-droid{a} ttf-liberation{a} udisks{a} update-manager{a} update-notifier{a} usbmuxd{a} x11-utils{a} xbitmaps{a}
  xterm{a} zenity{a}
The following packages will be REMOVED:
  apache2-mpm-worker{a}
0 packages upgraded, 163 newly installed, 1 to remove and 22 not upgraded.
Need to get 86.8MB of archives. After unpacking 275MB will be used.
Do you want to continue? [Y/n/?]


---

