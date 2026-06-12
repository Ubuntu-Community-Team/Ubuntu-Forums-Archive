---
title: "Mythbuntu 9.04 can't update...."
date: 2009-09-07
forum: Mythbuntu
---

### Post by sawbuck on 2009-09-07
This has been happening for about a week.  Things have gotten progresssively worse so that I am now unable to open MythTV frontend any longer.  To make matters worse I have two major problems dealing with it.  First, I am quite linux illeterate.  I have had a Fedora/MythTV box about a year before hardware issues required forced a build so I opted for the Mythbunu 9.04 bundle supposedly to make life easier.  With the assistance of several folks on the the forums and past posts I got it up and riunning smoothly for about a month until this current upgrade problem.  Second, and this makes matters worse, I am only able to focus on the dealing with the problem an hour or a few times a week.  So lack of knowledge often means researching simple things like how to edit a system file.
 
When it first occurred, I was directed to a bug report dialog screen so I reported it and got several responses back but none solved the problem.  Mainly I get an error indicating "libmono0" needs to be reinstalled but an archive can not be found to do so.  Outside of the updater, I have tried "apt-get" and "yum" to no avail - they can't find a dependency or archive.
 
In the synaptic package manager I have found and fixed MANY times 5 files but always get the same "libmono0" error mentiuoned above when I go back to update the software.
 
Is there anyway of fixing the current installation or do I have to trash it and redo a fresh installation?  
 
BTW, I did reinstall Mythbuntu 9.04 again on the same box side-by-side with the original in an effort to preserve prior recordings.  (I have several weeks of recordings that I wanted to watch this past week - about 5 hour long programs.)  But neither seems to recognize the other installation.  Is there any way to recover the prior recordings?
 
Any suggestions?

---

### Post by oboedad55 on 2009-09-07
> **sawbuck said:**
> This has been happening for about a week.  Things have gotten progresssively worse so that I am now unable to open MythTV frontend any longer.  To make matters worse I have two major problems dealing with it.  First, I am quite linux illeterate.  I have had a Fedora/MythTV box about a year before hardware issues required forced a build so I opted for the Mythbunu 9.04 bundle supposedly to make life easier.  With the assistance of several folks on the the forums and past posts I got it up and riunning smoothly for about a month until this current upgrade problem.  Second, and this makes matters worse, I am only able to focus on the dealing with the problem an hour or a few times a week.  So lack of knowledge often means researching simple things like how to edit a system file.
 
When it first occurred, I was directed to a bug report dialog screen so I reported it and got several responses back but none solved the problem.  Mainly I get an error indicating "libmono0" needs to be reinstalled but an archive can not be found to do so.  Outside of the updater, I have tried "apt-get" and "yum" to no avail - they can't find a dependency or archive.
 
In the synaptic package manager I have found and fixed MANY times 5 files but always get the same "libmono0" error mentiuoned above when I go back to update the software.
 
Is there anyway of fixing the current installation or do I have to trash it and redo a fresh installation?  
 
BTW, I did reinstall Mythbuntu 9.04 again on the same box side-by-side with the original in an effort to preserve prior recordings.  (I have several weeks of recordings that I wanted to watch this past week - about 5 hour long programs.)  But neither seems to recognize the other installation.  Is there any way to recover the prior recordings?
 
Any suggestions?

Were these updates the normal updates to 9.04 or did you upgrade to 9.10? If you did a version upgrade that might be your problem. Karmic is still in alpha testing and, from the reports I've read, not quite ready for prime time.

---

### Post by sawbuck on 2009-09-07
> **oboedad55 said:**
> Were these updates the normal updates to 9.04 or did you upgrade to 9.10? If you did a version upgrade that might be your problem. Karmic is still in alpha testing and, from the reports I've read, not quite ready for prime time.
 
re:obodat55
 
Normal software updates to 9.04, I assume.  I did note a kernal update from .11 to .14 in the bootlist, that wiped out a 'vmalloc' change I had made to .11 when 9.04 initially installed.  I'm not on the system at the moment but will check tho from memory I recall the software updates had security, apache, and a bunch of lib**mumble**updates and not a version upgrade.
 
The side-by-side install of 9.04 was added to the bootloader as kernal .11 again.  Also, it doesn't matter if I try to load .11 (original) or .14 the updater has majorly  botched both and neither will open MythTV.  The new .11 install will open MythTV but I have yet to let it do a software update.

---

### Post by tgm4883 on 2009-09-08
Please attach this file:

```
/etc/apt/sources.list
```

---

### Post by sawbuck on 2009-09-08
> **tgm4883 said:**
> Please attach this file:

```
/etc/apt/sources.list
```


Here's the text of the Sours\ces \.list file:

# deb cdrom:[Mythbuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted universe
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

---

### Post by sawbuck on 2009-09-08
This is the error message I see at the moment:

E: The package libmono0 needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

---

### Post by laffinet on 2009-09-08
Is that you're whole sources.list ?

If it is then you don't have any repositories enabled.

Go to System -> Softwares sources

What software sources are enabled there (Ubuntu software and 3rd party)?

Enable the first 4 in "Ubuntu software", run

```
sudo apt-get update
``` 
and
```
sudo apt-get upgrade
```
again.
Any errors ?
Post your sources.list again after you enabled the repositories

---

### Post by sawbuck on 2009-09-08
Well I'm confused and weary of this mess: Here's a few responses to trying to follow instructions in the dialog boxes,  The result is it never gets fixed but goes in circles.  I think I must have keyed in some wrong repositories or added options from the Mythbuntu control center not knowing what the hell I was doing.

I guess I'm gonna scrap the installation and start fresh and REALLY screen the sugested updates carefully after studying the forums and keep it as a simple PVR.....

Here's the errors:

Error that popped up when synpatic manager opened:

The packages 'kdelibs5-data, libgl1-mesa-glx, linux-restricted-modules-common, 
libapache2-mod-php5, kate, apache2.2-common, libvorbisenc2, tzdata, libkdegames5, 
mono-common, mono-jit, libmono0, libvorbis0a, libplasma3, dragonplayer, mono-gac, 
libcurl3-gnutls, xfce4-terminal, bovo, php5-common, apache2-mpm-prefork, 
libgnutls26, kdelibs5, kdebase-runtime, libvorbisfile3' are in an inconsistent 
state and need to be reinstalled, but no archives can be found for them. 

Do you want to remove these packages now to continue?

*** I said yes, then got this:


Another error:

The packages 'kdelibs5-data, libgl1-mesa-glx, linux-restricted-modules-common, 
libapache2-mod-php5, kate, apache2.2-common, libvorbisenc2, tzdata, libkdegames5, 
mono-common, mono-jit, libmono0, libvorbis0a, libplasma3, dragonplayer, mono-gac, 
libcurl3-gnutls, xfce4-terminal, bovo, php5-common, apache2-mpm-prefork, 
libgnutls26, kdelibs5, kdebase-runtime, libvorbisfile3' are in an inconsistent 
state and need to be reinstalled, but no archive can be found for them. 
Please reinstall the packages manually or remove them from the system.

Another error after fixing broken packages and dependancyies in synaptic manager:

E: /var/cache/apt/archives/libgl1-mesa-glx_7.4-0ubuntu3.2_i386.deb: subprocess new post-removal script returned error exit status 2
E: /var/cache/apt/archives/libplasma3_4%3a4.2.2-0ubuntu5.1_i386.deb: subprocess new post-removal script returned error exit status 2
E: /var/cache/apt/archives/kdelibs5-data_4%3a4.2.2-0ubuntu5.1_all.deb: subprocess pre-installation script returned error exit status 2
E: /var/cache/apt/archives/kdelibs5_4%3a4.2.2-0ubuntu5.1_i386.deb: subprocess new post-removal script returned error exit status 2
E: /var/cache/apt/archives/linux-image-2.6.28-15-generic_2.6.28-15.49_i386.deb: subprocess pre-installation script returned error exit status 2
E: /var/cache/apt/archives/linux-restricted-modules-common_2.6.28-15.20_all.deb: subprocess pre-installation script returned error exit status 2
E: /var/cache/apt/archives/tzdata_2009l-0ubuntu0.9.04_all.deb: subprocess new post-removal script returned error exit status 2

---

### Post by tgm4883 on 2009-09-08
Hmm, yea thats odd that you don't have any active repos in your sources.list

I'm interested in what files are in /etc/apt/sources.list.d/ and what is contained in those files.

---

### Post by sawbuck on 2009-09-08
> **laffinet said:**
> Is that you're whole sources.list ?

If it is then you don't have any repositories enabled.

Go to System -> Softwares sources

What software sources are enabled there (Ubuntu software and 3rd party)?

Enable the first 4 in "Ubuntu software", run

```
sudo apt-get update
```and
```
sudo apt-get upgrade
```again.
Any errors ?
Post your sources.list again after you enabled the repositories


First error immediately after checking Software Sources list first  4 in 
Ubuntu software 



You have 5 broken packages on your system!

Use the "Broken" filter to locate them.

I fixed the brojken packaes aa\and still got the previous errors:

The Sources list shows:

# deb cdrom:[Mythbuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted universe
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe main restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security universe main restricted multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe main restricted multiverse

---

### Post by sawbuck on 2009-09-08
> **laffinet said:**
> Is that you're whole sources.list ?

If it is then you don't have any repositories enabled.

Go to System -> Softwares sources

What software sources are enabled there (Ubuntu software and 3rd party)?

Enable the first 4 in "Ubuntu software", run

```
sudo apt-get update
```and
```
sudo apt-get upgrade
```again.
Any errors ?
Post your sources.list again after you enabled the repositories

From  a terminal windoe using the code above update seems OK:

frank@frank4:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Reading package lists... Done

Upgrade is another story:

frank@frank4:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  kdebase-runtime: Depends: kdebase-runtime-bin-kde4 (= 4:4.2.2-0ubuntu1) but it is not installed
  kdelibs-bin: Depends: kdelibs5 (= 4:4.2.2-0ubuntu5.1) but 4:4.2.2-0ubuntu5 is installed
  libgl1-mesa-dri: Depends: libgl1-mesa-glx (= 7.4-0ubuntu3.2) but 7.4-0ubuntu3.1 is installed
  libmono-addins0.2-cil: Depends: mono-runtime (>= 1.1.8.1) but it is not installed
  mono-gac: Depends: mono-2.0-gac (= 2.0.1-4) but it is not installed
  php5: Depends: libapache2-mod-php5 (>= 5.2.6.dfsg.1-3ubuntu4.2) but 5.2.6.dfsg.1-3ubuntu4.1 is installed or
                 libapache2-mod-php5filter (>= 5.2.6.dfsg.1-3ubuntu4.2) but it is not installed or
                 php5-cgi (>= 5.2.6.dfsg.1-3ubuntu4.2) but it is not installed
        Depends: php5-common (>= 5.2.6.dfsg.1-3ubuntu4.2) but 5.2.6.dfsg.1-3ubuntu4.1 is installed
  php5-mysql: Depends: php5-common (= 5.2.6.dfsg.1-3ubuntu4.2) but 5.2.6.dfsg.1-3ubuntu4.1 is installed
  tomboy: Depends: mono-runtime (>= 1.1.8.1) but it is not installed
          Depends: libgconf2.24-cil (>= 2.24.0) but it is not installed
          Depends: libgnome2.24-cil (>= 2.24.0) but it is not installed
          Depends: libgnomepanel2.24-cil (>= 2.24.0) but it is not installed
E: Unmet dependencies. Try using -f.


I'll try suggested commands in the terminal display.

---

### Post by sawbuck on 2009-09-08
> **sawbuck said:**
> From  a terminal windoe using the code above update seems OK:

frank@frank4:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Reading package lists... Done

Upgrade is another story:

frank@frank4:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  kdebase-runtime: Depends: kdebase-runtime-bin-kde4 (= 4:4.2.2-0ubuntu1) but it is not installed
  kdelibs-bin: Depends: kdelibs5 (= 4:4.2.2-0ubuntu5.1) but 4:4.2.2-0ubuntu5 is installed
  libgl1-mesa-dri: Depends: libgl1-mesa-glx (= 7.4-0ubuntu3.2) but 7.4-0ubuntu3.1 is installed
  libmono-addins0.2-cil: Depends: mono-runtime (>= 1.1.8.1) but it is not installed
  mono-gac: Depends: mono-2.0-gac (= 2.0.1-4) but it is not installed
  php5: Depends: libapache2-mod-php5 (>= 5.2.6.dfsg.1-3ubuntu4.2) but 5.2.6.dfsg.1-3ubuntu4.1 is installed or
                 libapache2-mod-php5filter (>= 5.2.6.dfsg.1-3ubuntu4.2) but it is not installed or
                 php5-cgi (>= 5.2.6.dfsg.1-3ubuntu4.2) but it is not installed
        Depends: php5-common (>= 5.2.6.dfsg.1-3ubuntu4.2) but 5.2.6.dfsg.1-3ubuntu4.1 is installed
  php5-mysql: Depends: php5-common (= 5.2.6.dfsg.1-3ubuntu4.2) but 5.2.6.dfsg.1-3ubuntu4.1 is installed
  tomboy: Depends: mono-runtime (>= 1.1.8.1) but it is not installed
          Depends: libgconf2.24-cil (>= 2.24.0) but it is not installed
          Depends: libgnome2.24-cil (>= 2.24.0) but it is not installed
          Depends: libgnomepanel2.24-cil (>= 2.24.0) but it is not installed
E: Unmet dependencies. Try using -f.


I'll try suggested commands in the terminal display.

Here's the resi\ult ot the install -f command:
frank@frank4:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libscrollkeeper0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2-mpm-prefork apache2.2-common kdebase-runtime-bin-kde4 kdelibs5 kdelibs5-data libapache2-mod-php5
  libgconf2.24-cil libgl1-mesa-glx libgnome2.24-cil libgnomepanel2.24-cil libplasma3 linux-image-2.6.28-15-generic
  linux-restricted-modules-common mono-2.0-gac mono-2.0-runtime mono-common mono-gac mono-jit mono-runtime php5-common
  tzdata
Suggested packages:
  apache2-doc apache2-suexec apache2-suexec-custom php-pear monodoc-gtk2.0-manual fdutils linux-doc-2.6.28
  linux-source-2.6.28
The following NEW packages will be installed:
  kdebase-runtime-bin-kde4 libgconf2.24-cil libgnome2.24-cil libgnomepanel2.24-cil mono-2.0-gac mono-2.0-runtime
  mono-runtime
The following packages will be upgraded:
  apache2-mpm-prefork apache2.2-common kdelibs5 kdelibs5-data libapache2-mod-php5 libgl1-mesa-glx libplasma3
  linux-image-2.6.28-15-generic linux-restricted-modules-common mono-common mono-gac mono-jit php5-common tzdata
14 upgraded, 7 newly installed, 0 to remove and 19 not upgraded.
52 not fully installed or removed.
Need to get 0B/48.4MB of archives.
After this operation, 97.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 
dpkg: serious warning: files list file for package `linux-image-2.6.28-15-generic' missing, assuming package has no files currently installed.
140375 files and directories currently installed.)
Preparing to replace libgl1-mesa-glx 7.4-0ubuntu3.1 (using .../libgl1-mesa-glx_7.4-0ubuntu3.2_i386.deb) ...
Unpacking replacement libgl1-mesa-glx ...
dpkg (subprocess): unable to execute old post-removal script: Permission denied
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new post-removal script: Permission denied
dpkg: error processing /var/cache/apt/archives/libgl1-mesa-glx_7.4-0ubuntu3.2_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
dpkg (subprocess): unable to execute new post-removal script: Permission denied
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Preparing to replace libplasma3 4:4.2.2-0ubuntu5 (using .../libplasma3_4%3a4.2.2-0ubuntu5.1_i386.deb) ...
Unpacking replacement libplasma3 ...
dpkg (subprocess): unable to execute old post-removal script: Permission denied
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new post-removal script: Permission denied
dpkg: error processing /var/cache/apt/archives/libplasma3_4%3a4.2.2-0ubuntu5.1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
dpkg (subprocess): unable to execute new post-removal script: Permission denied
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Preparing to replace kdelibs5-data 4:4.2.2-0ubuntu5 (using .../kdelibs5-data_4%3a4.2.2-0ubuntu5.1_all.deb) ...
dpkg (subprocess): unable to execute new pre-installation script: Permission denied
dpkg: error processing /var/cache/apt/archives/kdelibs5-data_4%3a4.2.2-0ubuntu5.1_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
dpkg (subprocess): unable to execute new post-removal script: Permission denied
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Preparing to replace kdelibs5 4:4.2.2-0ubuntu5 (using .../kdelibs5_4%3a4.2.2-0ubuntu5.1_i386.deb) ...
Unpacking replacement kdelibs5 ...
dpkg (subprocess): unable to execute old post-removal script: Permission denied
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new post-removal script: Permission denied
dpkg: error processing /var/cache/apt/archives/kdelibs5_4%3a4.2.2-0ubuntu5.1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute new post-removal script: Permission denied
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Preparing to replace linux-image-2.6.28-15-generic 2.6.28-15.49 (using .../linux-image-2.6.28-15-generic_2.6.28-15.49_i386.deb) ...
dpkg (subprocess): unable to execute new pre-installation script: Permission denied
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.28-15-generic_2.6.28-15.49_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute new post-removal script: Permission denied
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Preparing to replace linux-restricted-modules-common 2.6.28-14.19 (using .../linux-restricted-modules-common_2.6.28-15.20_all.deb) ...
dpkg (subprocess): unable to execute new pre-installation script: Permission denied
dpkg: error processing /var/cache/apt/archives/linux-restricted-modules-common_2.6.28-15.20_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute new post-removal script: Permission denied
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Preparing to replace tzdata 2009j-0ubuntu0.9.04 (using .../tzdata_2009l-0ubuntu0.9.04_all.deb) ...
Unpacking replacement tzdata ...
dpkg (subprocess): unable to execute old post-removal script: Permission denied
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new post-removal script: Permission denied
dpkg: error processing /var/cache/apt/archives/tzdata_2009l-0ubuntu0.9.04_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute new post-removal script: Permission denied
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libgl1-mesa-glx_7.4-0ubuntu3.2_i386.deb
 /var/cache/apt/archives/libplasma3_4%3a4.2.2-0ubuntu5.1_i386.deb
 /var/cache/apt/archives/kdelibs5-data_4%3a4.2.2-0ubuntu5.1_all.deb
 /var/cache/apt/archives/kdelibs5_4%3a4.2.2-0ubuntu5.1_i386.deb
 /var/cache/apt/archives/linux-image-2.6.28-15-generic_2.6.28-15.49_i386.deb
 /var/cache/apt/archives/linux-restricted-modules-common_2.6.28-15.20_all.deb
 /var/cache/apt/archives/tzdata_2009l-0ubuntu0.9.04_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I'm gonna get off for now.  If it looks hopeless I guess my thought a few posts ago to scrap and restart might save some frustration.  However, with a clearer head walkind through these steps may provide a real learning experience in Linux.

Thanks for help folks....

---

### Post by sawbuck on 2009-09-11
Well, I finally got fed up with constant error messages using every tip the kind responders to this thread offered but in the end, after a little clear thinking, I realized I created the mess when I first added the Ubuntu desktop to my working  Mythbuntu installation.  I did it trying to get  the desktop to be a little more "Windows-like".  Then with all the stuff that got loaded with it, it became quite cluttered and I think I tried to remove some packages with the package manager - incorrectly, I guess.  Then it steadily got worse and I recall at some point turning off some repository sources.  I had assumed more was better earlier and turned on anything I could find.  Soooooo, the posts pointing out I had none was after I went to the other extreme trying to remove brokenb stuff.  Eventually, Mythtv took the hit.....

Recall I said I was a total linux greenie.  Still am but I hope to be more careful here on out.

I have started with a fresh installation of Ubunu, got the proper updates and learned the very basic rudiments of using gedit and vi editors.  Explored a bit, read a few more posts and then added Mythbuntu to this installation.  So far, I am back to a working system with both Ubuntu and Mythbuntu.  I have the system configured as a frontend/backend again.  

In addition, I have cobbled together another box with more cpu and display power that I hope tio succeed setting up as a frontend only system wired into the main TV, using this box as the only backend soruce on my home network.  So far I have it loaded with AMD64 Ubuntu, updated to current, and am about to add  Mythbuntu for Frontend only (it has no tuners),   I will add it to the Mythbuntu hardware thread when I have confidence I won't be changing much.  Of course, I'll be pleading for help still....

Once again, thinks to all who tried to bail me out on issues discussed in this thread......

---

### Post by madhusker on 2010-01-01
[URL="https://bugs.launchpad.net/ubuntu/+source/kdebase-runtime/+bug/345776"]https://bugs.launchpad.net/ubuntu/+source/kdebase-runtime/+bug/345776
[/URL]

More specifically the command:

dpkg-divert --package kdebase-runtime --divert /usr/lib/kde4/libexec/kdesu.not-kdebase-runtime --rename /usr/lib/kde4/libexec/kdesu

will fix it.  Then apt-get -f install to clean up.

---

