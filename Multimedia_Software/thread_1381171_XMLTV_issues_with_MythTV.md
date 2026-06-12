---
title: "XMLTV issues with MythTV"
date: 2010-01-14
forum: Multimedia Software
---

### Post by CMos_UK on 2010-01-14
Hi there,

Currently I have a Ubuntu 9.10 machine running various things including MythTV backend.    Recently I have noticed that my listings (grabbed using tv_grab_uk_rt) have been failing.

running:
```
mythfilldatabase -v all
```returns:
```
...
2010-01-14 18:40:33.418 ----------------- Start of XMLTV output -----------------
XMLTV requires a Date::Manip timezone of +0000 to work properly.
Current Date::Manip timezone is 1.
2010-01-14 18:40:35.995 ------------------ End of XMLTV output ------------------
...
```On doing some googling I discovered that this was a problem in the tv_grab_uk_rt and that there is a time zone check that can be commented out on line 100 as per this post: [http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/054ab4c27528bad2/c45cc8af1c329228?lnk=raot](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/054ab4c27528bad2/c45cc8af1c329228?lnk=raot)

I have commented out this line and now get a new error:

```
...
2010-01-14 18:24:57.710 ----------------- Start of XMLTV output -----------------
XMLTV library version: 0.5.56
tv_grab_uk_rt version: 1.220, 2009/08/09 04:00:57 

Retrieving channels



The Radio Times has usable data available for 297 channels which we
can use to generate TV listings for regular and some timeshifted
channels. The tv_grab_uk_rt software also has support for an additional
52 timeshifted, 5 part-time, and 2 part-time timeshifted channels
based on the Radio Times data.

In total, tv_grab_uk_rt currently supports 356 channels.


     +------------------------------------------------+     
     |  All data is the copyright of the Radio Times  |     
     |    and the use of this data is restricted to   |     
     | personal use only. <http://www.radiotimes.com> |     
     +------------------------------------------------+     


Will download listings for 44 configured channels

Retrieving listings




Processing listings for '4Music' (4music.channel4.com)
http://xmltv.radiotimes.com/xmltv/1544.dat: bad delta +0:0:+0:0:0:0:0 at /usr/share/perl5/XMLTV/TZ.pm line 101.
2010-01-14 18:25:00.823 ------------------ End of XMLTV output ------------------
...
```"TZ.pm" is attached.

The libdate-manip-perl version installed is 5.54-1 if this is important.

Is anyone else having this problem?  I have tried various things to get this to work and had no luck.  I have even used CPAN to make sure Date::Manip is up to date, which it is.

All my channels have been changed to use the off air guide but the Radio Times guide is far superior.  Any assistance would be greatly appreciated.

Many thanks,

CMos

---

### Post by CMos_UK on 2010-01-19
Looks like Date::Manip has changed the way it handles time zones.

There seems to be a solution to this here: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=560300](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=560300)

Might get a chance to test this out later on, if I do I will post results here.

Look forward to the packages being updated.

CMos

---

### Post by Jose Catre-Vandis on 2010-05-02
I don't use MythTV but I do use xmltv. Got the same problem when upgrading to Xubuntu 10.04.

To fix I downloaded the latest source for XMLTV from sourceforge, compiled it and installed it. This goes into /usr/local/bin so you may need to change some settings to point Myth at the right "tv_grab_uk_rt" script.

---

### Post by singedwings on 2010-05-25
You do not need to install to a custom directory. Once installed MythTV can see the grabber without any other changes. I did uninstall the previous version before compiling.

---

### Post by Paresh on 2010-05-30
> **Jose Catre-Vandis said:**
> I don't use MythTV but I do use xmltv. Got the same problem when upgrading to Xubuntu 10.04.

To fix I downloaded the latest source for XMLTV from sourceforge, compiled it and installed it. This goes into /usr/local/bin so you may need to change some settings to point Myth at the right "tv_grab_uk_rt" script.

Hi

I'm trying to get xmltv to work.  I have downloaded the latest source, but can you explain how to compile it?

---

