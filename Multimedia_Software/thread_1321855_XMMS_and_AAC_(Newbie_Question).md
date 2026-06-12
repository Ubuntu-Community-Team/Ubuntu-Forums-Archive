---
title: "XMMS and AAC? (Newbie Question)"
date: 2009-11-10
forum: Multimedia Software
---

### Post by The Soul Man on 2009-11-10
Does anybody know how to play AAC files with XMMS?
The only matches i got when i googled it was for older versions of Ubuntu. i.e 7.04...
I'm running XMMS under Ubuntu 9.04 64 bit and 9.10 32 bit.

So... could anyone help a newbie like me?

---

### Post by The Soul Man on 2009-11-13
Not to be inpatient, but could anyone help me?

---

### Post by mc4man on 2009-11-13
Had xmms running on a hardy install, haven't bothered since using karmic.

As I remember I added some plugins,-  flac, wma, and the mp4 one as far as audio

You can ck. in the dapper repo or possibly the old-release repo for maybe gutsy..? (or fiesty, forget when xmms was dropped) and see if the plugin will install cleanly. 

It probably won't, in that case you'll need to build the source on your current install (if it fails solely on the libfaad ver. , maybe  a workaround
Or search and see if someone has packaged various plugin's as .debs

As I remember not all of the plugins I installed worked perfectly, though a number  did


[http://packages.ubuntu.com/en/dapper-updates/xmms-mp4](http://packages.ubuntu.com/en/dapper-updates/xmms-mp4)

---

### Post by The Soul Man on 2009-11-14
> **mc4man said:**
> Had xmms running on a hardy install, haven't bothered since using karmic.

As I remember I added some plugins,-  flac, wma, and the mp4 one as far as audio

You can ck. in the dapper repo or possibly the old-release repo for maybe gutsy..? (or fiesty, forget when xmms was dropped) and see if the plugin will install cleanly. 

It probably won't, in that case you'll need to build the source on your current install (if it fails solely on the libfaad ver. , maybe  a workaround
Or search and see if someone has packaged various plugin's as .debs

As I remember not all of the plugins I installed worked perfectly, though a number  did


[http://packages.ubuntu.com/en/dapper-updates/xmms-mp4](http://packages.ubuntu.com/en/dapper-updates/xmms-mp4)

It didnt work to look in the repos... :(

i'll search for a .deb.

but anyway
Thanks for answer!

---

### Post by mc4man on 2009-11-14
> It didnt work to look in the repos

My memory of this is returning a bit, try this one instead


[https://launchpad.net/ubuntu/hardy/i386/xmms-mp4/2.6-1](https://launchpad.net/ubuntu/hardy/i386/xmms-mp4/2.6-1)

.......................................................................

these can be self built from source  and the relevant .so's pasted into ~/.xmms/Plugins/  (with xmms not running
or gotten here

possibly for some wma
[http://www.box.net/shared/nt0gtp2e4s](http://www.box.net/shared/nt0gtp2e4s)

for flac
[http://www.box.net/shared/hvj75mnlnn](http://www.box.net/shared/hvj75mnlnn)

---

### Post by The Soul Man on 2009-11-14
> **mc4man said:**
> My memory of this is returning a bit, try this one instead

[https://launchpad.net/ubuntu/hardy/i386/xmms-mp4/2.6-1](https://launchpad.net/ubuntu/hardy/i386/xmms-mp4/2.6-1)



Didnt work... :(

The package installer refused to install it..
(See attachment)

but thanks for helping !

---

### Post by mc4man on 2009-11-14
Maybe there is a little confusion here - do you mean xmms (no longer avail in ubuntu) or xmms2  ..?

If xmms, while I'm not sure of the value, it's certainly doable 

quickly did this on karmic
added this repo (don't have time to build and gather deps

[http://www.pvv.ntnu.no/~knuta/xmms/](http://www.pvv.ntnu.no/~knuta/xmms/)

then in terminal installed
> doug@doug-laptop:~$ sudo apt-get install xmms
........
The following extra packages will be installed:
  libglib1.2ldbl libgtk1.2 libgtk1.2-common libmikmod2
The following NEW packages will be installed:
  libglib1.2ldbl libgtk1.2 libgtk1.2-common libmikmod2 xmms
0 upgraded, 5 newly installed, 0 to remove and 7 not upgraded.
Need to get 3,455kB of archives.
After this operation, 10.0MB of additional disk space will be used.
Do you want to continue [Y/n]?y

After than installed the mp4 plugin from hardy launchpad..
screen 1
Now if i was going to keep I'd create a desktop launcher and trackdown a xmms icon for it.

Instead opened from terminal ( the warning message in karmic is of no consequence that I can see

> doug@doug-laptop:~$ xmms

Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

Before playback went in and in options -> preferences and changed audio output to alsa ( the oss won't work here in karmic with xmms

Then loaded up an aac file (clipped warning
> doug@doug-laptop:~$ xmms
...........
Message: device: default
total-tracks: 1
testing-track: 0
total-tracks: 1
testing-track: 0
total-tracks: 1
testing-track: 0
MP4 - 2 channels @ 44100 Hz


If you mean xmms2 then the plugin is in synaptic

---

### Post by The Soul Man on 2009-11-14
Thanks !
Works fine now !

(Yes, i meant xmms)

---

