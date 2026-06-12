---
title: "Totem (2.28.2) Plugin Mystery"
date: 2010-03-11
forum: Multimedia Software
---

### Post by n4lbl on 2010-03-11
When trying to play a DVD I get the message:  "_Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc.  Please install the necessary plugins and restart Totem to be able to play this media._"

I haven't played a DVD in a long time but believe that it used to work.  How do I determine which plugin(s) I need??

"Configure Plugins" shows only "BBC content viewer" and "YouTube Browser" enabled.  The others don't seem appropriate though.  This 9.10 system is up-to-date.

thanx,,,

---

### Post by n4lbl on 2010-03-11
Update: ran:
sudo apt-get install totem-gstreamer
[sudo] password for n4lbl: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
totem-gstreamer is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-16 linux-headers-2.6.31-16-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by n4lbl on 2010-03-12
Any ideas??  I'm lost.

thanx,,,

---

### Post by wojox on 2010-03-12
Did you try:

```
sudo apt-get install libdvdread4
```

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by n4lbl on 2010-03-12
Thank you.  It is working now.  

For the sake of completeness what happened was:

Before starting according to Synaptic Package M'gr I had 4.1.3-5ubuntu2 installed.

sudo apt-get install libdvdread4

Reading package lists... Done

Building dependency tree       

Reading state information... Done

libdvdread4 is already the newest version.

libdvdread4 set to manually installed.

The following packages were automatically installed and are no longer required:

  linux-headers-2.6.31-16 linux-headers-2.6.31-16-generic

Use 'apt-get autoremove' to remove them.

0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


sudo /usr/share/doc/libdvdread4/install-css.sh

--2010-03-12 09:12:31--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb)

Resolving packages.medibuntu.org... 88.191.82.11

Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.

HTTP request sent, awaiting response... 200 OK

Length: 36812 (36K) [application/x-debian-package]

Saving to: `/tmp/dvdcss-t6ovKA/libdvdcss.deb'



100%[======================================>] 36,812      48.2K/s   in 0.7s    



2010-03-12 09:12:32 (48.2 KB/s) - `/tmp/dvdcss-t6ovKA/libdvdcss.deb' saved [36812/36812]



Selecting previously deselected package libdvdcss2.

(Reading database ... 195583 files and directories currently installed.)

Unpacking libdvdcss2 (from .../dvdcss-t6ovKA/libdvdcss.deb) ...

Setting up libdvdcss2 (1.2.10-0.2medibuntu1) ...



Processing triggers for libc-bin ...

ldconfig deferred processing now taking place


That last line puzzled me.  I restarted Totem and:
Search for suitable plugin?
The required software to play this file is not installed. You need to install suitable plugins to play media files. Do you want to search for a plugin that supports the selected file?



The search will also include software which is not officially supported.

The requested plugins are:



GStreamer element dvdspu

The world is better!!  Many thanks.  How do I report this solved??

---

### Post by wojox on 2010-03-14
You're welcome.

---

