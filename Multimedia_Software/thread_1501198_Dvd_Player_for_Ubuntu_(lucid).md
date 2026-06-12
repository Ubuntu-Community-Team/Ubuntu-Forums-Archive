---
title: "Dvd Player for Ubuntu (lucid)"
date: 2010-06-04
forum: Multimedia Software
---

### Post by pr0t3g3 on 2010-06-04
I'm running ubuntu 10.04 lucid on a 32-bit dell Inspiron 8600, and am looking for suitable DVD Player software.  I've searched quite a bit and in passing found these articles:

[http://ubuntuforums.org/showthread.php?t=1500172&highlight=ubuntu+DVD+player](http://ubuntuforums.org/showthread.php?t=1500172&highlight=ubuntu+DVD+player)

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

They didn't help me.

The reason why I started this thread, was to see if anyone knew of a dvd player suitable for my specs... I tried using the default player but it gave me an error saying:
[COLOR=Red]
**No packages with the requested plugins found**[/COLOR][B]
[COLOR=Red]
The requested plugins are:

DVD source[/COLOR][/B]

and when I cancel that message this one follows:
[B][COLOR=Red]
An error occurred

The playback of this movie requires a DVD source plugin which is not installed.[/COLOR][/B][COLOR=Red][COLOR=Black]

[/COLOR][/COLOR]So if anyone has suggestions/ alternatives, I'm all ears.

---

### Post by lisati on 2010-06-04
I can't remember exactly what I did to get DVDs working on my 10.04 installation. I think it was this one: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Ubuntu%209.04,%209.10%20and%2010.04%20%28i386,%20amd64%29](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Ubuntu%209.04,%209.10%20and%2010.04%20%28i386,%20amd64%29)



(BTW: my user handle "lisati" is (almost) a transliteration of my real name, "Richard", into the Samoan language. My Samoan-speaking in-laws are likely to tell me that it should be "Risati", but in everyday speech their "r" sometimes sounds a bit like "l". The usual shortened form is "Sati", which sometimes sounds a bit like "Saki")

---

### Post by pr0t3g3 on 2010-06-04
> **lisati said:**
> I can't remember exactly what I did to get DVDs working on my 10.04 installation. I think it was this one: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Ubuntu%209.04,%209.10%20and%2010.04%20%28i386,%20amd64%29](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Ubuntu%209.04,%209.10%20and%2010.04%20%28i386,%20amd64%29)



(BTW: my user handle "lisati" is (almost) a transliteration of my real name, "Richard", into the Samoan language. My Samoan-speaking in-laws are likely to tell me that it should be "Risati", but in everyday speech their "r" sometimes sounds a bit like "l". The usual shortened form is "Sati", which sometimes sounds a bit like "Saki")

thanks I'll check out the link ^_^!

---

### Post by pr0t3g3 on 2010-06-04
It didn't help...

---

### Post by wilee-nilee on 2010-06-04
I have a external DVD player for my net-book and just have libdvdread and lidvdcss2 and the ubuntu restricted extras installed all from synaptic. The link by lisati is to the source for the libs.

I assume you have tried different DVD's.

I also have VLC installed.

---

### Post by WinterRain on 2010-06-04
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then
```
sudo apt-get install libdvdcss2
```
This has worked on many installs for me.

---

### Post by pr0t3g3 on 2010-06-04
> **wilee-nilee said:**
> I have a external DVD player for mt net-book and just have libdvdread and lidvdcss2 and the ubuntu restricted extras installed all from synaptic. The link by lisati is to the source for the libs.

I assume you have tried different DVD's.

I also have VLC installed.

Yes, I did all the things in the link and tried multiple DVD's .. none work.

---

### Post by pr0t3g3 on 2010-06-04
anthony@anthony-laptop:~$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
[sudo] password for anthony: 
--2010-06-04 02:42:54--  [http://www.medibuntu.org/sources.list.d/lucid.list](http://www.medibuntu.org/sources.list.d/lucid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 268 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 268         --.-K/s   in 0s      

2010-06-04 02:42:55 (12.2 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [268/268]

Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
Ign [http://ubuntu.global-web.us](http://ubuntu.global-web.us) binary/ Release.gpg
Ign [http://ubuntu.global-web.us/karmic/](http://ubuntu.global-web.us/karmic/) binary/ Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Ign [http://ubuntu.global-web.us](http://ubuntu.global-web.us) binary/ Release
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [189B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://ubuntu.global-web.us](http://ubuntu.global-web.us) binary/ Packages
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US
Ign [http://ubuntu.global-web.us](http://ubuntu.global-web.us) binary/ Packages
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release
Hit [http://ubuntu.global-web.us](http://ubuntu.global-web.us) binary/ Packages
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [38.5kB]
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Get:5 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages [3,253B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Get:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages [8,873B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [23.6kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [14B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [14B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [8,520B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [14B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [1,297B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [5,236B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [14B]
Fetched 96.6kB in 2s (34.9kB/s)
Reading package lists...
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
Reading package lists...
Building dependency tree...
Reading state information...
The following NEW packages will be installed:
  medibuntu-keyring
0 upgraded, 1 newly installed, 0 to remove and 28 not upgraded.
Need to get 3,448B of archives.
After this operation, 49.2kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Authentication warning overridden.
Get:1 [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free medibuntu-keyring 2008.04.20 [3,448B]
Fetched 3,448B in 3s (1,006B/s)
Selecting previously deselected package medibuntu-keyring.
(Reading database ... 176267 files and directories currently installed.)
Unpacking medibuntu-keyring (from .../medibuntu-keyring_2008.04.20_all.deb) ...
Setting up medibuntu-keyring (2008.04.20) ...
OK

Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
Ign [http://ubuntu.global-web.us](http://ubuntu.global-web.us) binary/ Release.gpg
Ign [http://ubuntu.global-web.us/karmic/](http://ubuntu.global-web.us/karmic/) binary/ Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US
Ign [http://ubuntu.global-web.us](http://ubuntu.global-web.us) binary/ Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Ign [http://ubuntu.global-web.us](http://ubuntu.global-web.us) binary/ Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]
Ign [http://ubuntu.global-web.us](http://ubuntu.global-web.us) binary/ Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Hit [http://ubuntu.global-web.us](http://ubuntu.global-web.us) binary/ Packages
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Fetched 198B in 1s (155B/s)
Reading package lists...
anthony@anthony-laptop:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.

---

### Post by pr0t3g3 on 2010-06-04
Still no...

---

### Post by wilee-nilee on 2010-06-04
Try installing vlc and right click on the dvd and start with vlc. If you have the right stuff installed sometimes totem still wont work when vlc or smplayer does.

---

### Post by pr0t3g3 on 2010-06-04
> **wilee-nilee said:**
> Try installing vlc and right click on the dvd and start with vlc. If you have the right stuff installed sometimes totem still wont work when vlc or smplayer does.
totem?

---

### Post by sites on 2010-06-04
[ubuntuguide.org]("http://ubuntuguide.org/wiki/Ubuntu:Lucid")

Look for "DVD playback capability" and you will find.....

*wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb)*

*sudo dpkg -i libdvdcss2_1.2.10-0.3medibuntu1_i386.deb*

copy/paste the above commands into terminal

---

### Post by wilee-nilee on 2010-06-04
> **pr0t3g3 said:**
> totem?

totem=Movie Player is the stock install media player and has some limitations,It may not be called totem anymore I don't know I don't use it much I like smplayer and vlc for regular use.

I'm curious about this at the end of the readout.
> 0 upgraded, 0 newly installed, 0 to remove and **28 not upgraded**.

---

### Post by pr0t3g3 on 2010-06-04
> **wilee-nilee said:**
> totem=Movie Player is the stock install media player and has some limitations,It may not be called totem anymore I don't know I don't use it much I like smplayer and vlc for regular use.

I'm curious about this at the end of the readout.
Me too but I don't have the slightest Idea why it says that or what to do about it... =_=

---

### Post by pr0t3g3 on 2010-06-04
> **sites said:**
> [ubuntuguide.org]("http://ubuntuguide.org/wiki/Ubuntu:Lucid")

Look for "DVD playback capability" and you will find.....

*wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb)*

*sudo dpkg -i libdvdcss2_1.2.10-0.3medibuntu1_i386.deb*

copy/paste the above commands into terminal
anthony@anthony-laptop:~$ wget -c [http://packages.medibuntu.org/pool/f...untu1_i386.deb](http://packages.medibuntu.org/pool/f...untu1_i386.deb)
--2010-06-04 03:16:32--  [http://packages.medibuntu.org/pool/f...untu1_i386.deb](http://packages.medibuntu.org/pool/f...untu1_i386.deb)
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-06-04 03:16:33 ERROR 404: Not Found.

anthony@anthony-laptop:~$ 
anthony@anthony-laptop:~$ sudo dpkg -i libdvdcss2_1.2.10-0.3medibuntu1_i386.deb
dpkg: error processing libdvdcss2_1.2.10-0.3medibuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libdvdcss2_1.2.10-0.3medibuntu1_i386.deb

---

### Post by cariboo on 2010-06-04
Make sure you have the ubuntu-restricted-extras meta package installed then got to /usr/share/doc/libdvdread4 and type:

```
sudo ./install-css.sh
```

This will automagically install libdvdcss2, which is all you should need to play dvds.

---

### Post by sites on 2010-06-04
Try [this]("http://ubuntuforums.org/showpost.php?p=9351355&postcount=3").

---

### Post by pr0t3g3 on 2010-06-04
> **cariboo907 said:**
> Make sure you have the ubuntu-restricted-extras meta package installed then got to /usr/share/doc/libdvdread4 and type:

```
sudo ./install-css.sh
```This will automagically install libdvdcss2, which is all you should need to play dvds.Where is that?

---

### Post by wilee-nilee on 2010-06-04
> **pr0t3g3 said:**
> Me too but I don't have the slightest Idea why it says that or what to do about it... =_=

cariboo907 seems to have additional information that seems relevant. I would look in synaptic for the packages marked but not installing and see if there are missing dependencies, by right clicking on the marked packages.

I just run ```
sudo apt-get dist-upgrade
``` generally, but I have nothing to lose so it is not the way for everybody.

---

### Post by sites on 2010-06-04
> **pr0t3g3 said:**
> Where is that?

sudo gedit /etc/apt/sources.list

cd /usr/share/doc/libdvdread4

---

### Post by pr0t3g3 on 2010-06-04
> **sites said:**
> sudo gedit /etc/apt/sources.list

cd /usr/share/doc/libdvdread4
I'd already found it before you guy's posted that stuff... I'm trying the ferret/squirrel's idea out.. maybe I need to upgrade...

Edit: Vlc appears to be working.. I forgot to try that out... but I'm going to continue with the update

---

### Post by pr0t3g3 on 2010-06-04
upgrade did nothing... I guess I'm going to have to go with VLC

---

### Post by luceerose on 2010-06-04
I just install;

libdvdcss2
ubuntu-restricted-extras
w64codecs [or w32codecs for 32-bit]
vlc
mozilla-plugin-vlc
libxine1-ffmpeg

That's gotten everything working for me in Intrepid, Jaunty, Karmic, Lucid & so far Maverick.

---

### Post by bodhi.zazen on 2010-06-04
See also :

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by MechanteAnemone on 2010-06-12
I'm in the same case as pr0t3g3.  I'm new to Ubuntu, got a box with Karmic Koala, couldn't get Movie Player to read DVDs or any Flash replacement plug-in to install.  

On a friend's advice, I installed 10.04, met no problem I could not figure out so far, but never got Totem to read encrypted DVDs, even after going through all the same steps as larsenguitars.  VLC works, though.

---

