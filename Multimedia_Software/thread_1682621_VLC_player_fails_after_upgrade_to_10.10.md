---
title: "VLC player fails after upgrade to 10.10"
date: 2011-02-06
forum: Multimedia Software
---

### Post by whowinsdares on 2011-02-06
Hello,

Since I upgraded to 10.10 my VLC player wont work at all, I tried the advice in this thread:

[http://forum.videolan.org/viewtopic.php?f=13&t=86092](http://forum.videolan.org/viewtopic.php?f=13&t=86092)

which was to enter:

vlc --reset-config --reset-plugins-cache

in console but I got the following result:

*********@*********:~$ vlc --reset-config --reset-plugins-cache
VLC media player 1.1.4.1 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x98c58fc] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x9a2ec44] skins2 interface error: no suitable dialogs provider found (hint: compile the qt4 plugin, and make sure it is loaded properly)
[0x9a2ec44] skins2 interface error: cannot instanciate qt4 dialogs provider
[0x98c58fc] main libvlc error: interface "default" initialization failed

So its a total fail and I have no idea what to do, if someone could please help me it would be much appreciated.. 

thanks,

---

### Post by whowinsdares on 2011-02-06
I just purged VLC and can't reinstall it either, I think this may be a bug

---

### Post by CharlesA on 2011-02-06
What do you mean you can't reinstall it? Any error messages?

Being vague doesn't help anyone help you.

---

### Post by whowinsdares on 2011-02-06
[FONT=Arial Black][SIZE=2]I purged VLC through the command line, then in the Synaptic Package manager when I have attempted to reinstall I get this:
[/SIZE][/FONT]
The following packages have unresolvable dependencies. Make sure that all required repositiries are added and enabled in the preferences:

vlc:
  Depends: vlc-nox (=1.1.4-1ubuntu1.3) but 1.1.4.1-1~lffl~lucid~ppa1 is to be installed
 Recommends: vlc-plugin-notify but it is not going to be installed
  Recommends: vlc-plugin-pulse (=1.1.4-1ubuntu1.3) but 1.1.4.1-1~lffl~lucid~ppa1 is to be installed

[B]I used to use VLC all the time to watch videos and I need it specifically at the moment to rotate a video 90 degrees so I can upload something to youtube someone is waiting on.

Ever since I upgraded to 10.10 it wont start at all, I have no idea why[/B] [B]

Thanks for your inquiry[/B]

---

### Post by CharlesA on 2011-02-06
Can you post the contents of /etc/apt/sources.list in code tags please.

---

### Post by Paqman on 2011-02-06
Ah, you should have mentioned you're getting VLC from a PPA. When you upgrade, the system disables all PPAs, so that they don't cause conflicts during the upgrade. You have to enable the new PPA for your new version after the upgrade. 

Simply remove the PPA from your software sources list, reload Synaptic and try again.

---

### Post by whowinsdares on 2011-02-06
*******@***********:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
*******@***********:~$ sudo /etc/apt/sources.list
[sudo] password for *********: 
sudo: /etc/apt/sources.list: command not found

sorry don't understand my error...?

---

### Post by whowinsdares on 2011-02-06
> **Paqman said:**
> Ah, you should have mentioned you're getting VLC from a PPA. When you upgrade, the system disables all PPAs, so that they don't cause conflicts during the upgrade. You have to enable the new PPA for your new version after the upgrade. 

Simply remove the PPA from your software sources list, reload Synaptic and try again.

Hello,

Sorry i don't really understand what you mean, or how to fix the problem. I would like to repair the issue but I would also like to understand what you mean as a matter of interest too please,

thanks

---

### Post by Paqman on 2011-02-06
You can edit your sources list from Synaptic: Settings > Repositories > Other software. Just uncheck the offending PPA, or better yet delete it.

---

### Post by Paqman on 2011-02-06
> **whowinsdares said:**
> Hello,

Sorry i don't really understand what you mean, or how to fix the problem. I would like to repair the issue but I would also like to understand what you mean as a matter of interest too please,

thanks

Because PPAs can provide packages that replace the normal ones from the official repos, they can break the upgrade process. The upgrade system is designed with the assumption that it gets its packages from the official Ubuntu repos (and quite rightly). So to make sure the upgrade goes smoothly, all extra sources you've added (including PPAs) get disabled before the upgrade starts. This means they don't get upgraded to the right PPA for the next version.

That's not a huge problem, you just delete the old PPA and add the correct one for your version. 

Is there some reason why you were using a PPA for VLC anyway?

---

### Post by whowinsdares on 2011-02-06
There is no reason why I was or am using a PPA for VLC, I really don't understand what a PPA is or does, so I don't know how it happened that my software is configured that way, perhaps I installed it from the command line but I really have no idea, it wasn't a decision I made at all, I cant remember when I installed VLC so I don't remember the process I went through to install it.

When you say 'deselect the offending PPA through the synaptic repository manager', how do I tell which one it is, and what do I do once I un-install it, will VLC work then or will I have to do something else?

Thanks..

---

### Post by whowinsdares on 2011-02-06
Bump

someone please help me fix this i want to smash this computer

****!

---

### Post by whowinsdares on 2011-02-06
Everything you guys have told me is completely useless

---

### Post by CharlesA on 2011-02-06
What PPAs do you have listed in software sources?

---

### Post by Paqman on 2011-02-06
> **whowinsdares said:**
> There is no reason why I was or am using a PPA for VLC, I really don't understand what a PPA is or does, so I don't know how it happened that my software is configured that way, perhaps I installed it from the command line but I really have no idea, it wasn't a decision I made at all, I cant remember when I installed VLC so I don't remember the process I went through to install it.


Fair enough. You must have entered a command from somewhere without knowing what it was.

A PPA is a Private Package Archive. It's basically a very small repository that developers use to push the packages they're working on out to users and testers. The packages within them are often quite unstable, because they're under active development.

> 
When you say 'deselect the offending PPA through the synaptic repository manager', how do I tell which one it is, and what do I do once I un-install it, will VLC work then or will I have to do something else?

Thanks..

The error messages before referred to the packages being marked with "lffl", so i'm assuming it's [this PPA.]("https://launchpad.net/~ferramroberto/+archive/vlc") If that's the case it'll be quite obvious in the list. It'll be the one with VLC in the address (eg: [http://ppa.launchpad.net/ferramroberto/vlc/ubuntu](http://ppa.launchpad.net/ferramroberto/vlc/ubuntu)).

After getting rid of the PPA, it'll ask to update its index, which you should let it do. After that you should be able to reinstall VLC to make sure you've got the normal version. If you want to be really sure, purge the old version completely and install it fresh.

> **whowinsdares said:**
> Everything you guys have told me is completely useless

No it isn't, you're very close to the solution, if you just calm down and listen you'll be fine.

I know computer problems can be extremely frustrating, but your attitude to the help you're being given is not good, btw. Nobody *has* to help you, they're doing it out of the goodness of their hearts.

---

### Post by khelben1979 on 2011-02-06
In my opinion, you can learn to compile VLC from source code. Go to [the VLC homepage]("http://www.videolan.org/vlc/") and go through these 3 steps:

```
1. configure
```
(this starts to search for library files on your Ubuntu system to see if you need to install anything which is missing.)

```
2. make
```
(this compiles the source code)

```
3. make install
```
(Places the binary files in the Ubuntu system)

---

### Post by whowinsdares on 2011-02-06
> **Paqman said:**
> 

The error messages before referred to the packages being marked with "lffl", so i'm assuming it's [this PPA.]("https://launchpad.net/%7Eferramroberto/+archive/vlc") If that's the case it'll be quite obvious in the list. It'll be the one with VLC in the address (eg: [http://ppa.launchpad.net/ferramroberto/vlc/ubuntu](http://ppa.launchpad.net/ferramroberto/vlc/ubuntu)).



ok there were several marked with VLC, on trying to install the main VLC one I got the error I gave you. 

I did then go and delete all the ones beginning with VLC because there were about 6

> **Paqman said:**
> 

After getting rid of the PPA, it'll ask to update its index, which you should let it do. 



It never asked me to update its index, I just applied the changes I had selected and closed the Synaptic thing

> **Paqman said:**
> 
After that you should be able to reinstall VLC to make sure you've got the normal version.



When I go to the VLC download page I get directed to the Linux section automatically, this is the official VLC site so I don't know why I would need to look anywhere else. 

GUI installation instructions don't apply to me because I have deleted everything from the synaptic thing, and there is nothing referring to VLC in the synaptic thing at all now.

So when I apply the command line installation instructions nothing happens.

> **Paqman said:**
> 

If you want to be really sure, purge the old version completely and install it fresh.



I had already done this, previous to deleting the PPA's as you suggested through the synaptic manager as I had indicated.

Thank you very much for your assistance, I really hope we can complete this issue, and I honestly do appreciate your help. But if I knew everything you were referring to in trying to help me I most probably wouldn't be in a bad situation. When you say to use gedit to run that line of code, are you saying to create like an exe file with it in there and run it like that? I don't understand..

Thank you very much again

---

### Post by whowinsdares on 2011-02-06
> **khelben1979 said:**
> In my opinion, you can learn to compile VLC from source code. Go to [the VLC homepage]("http://www.videolan.org/vlc/") and go through these 3 steps:

```
1. configure
```(this starts to search for library files on your Ubuntu system to see if you need to install anything which is missing.)

```
2. make
```(this compiles the source code)

```
3. make install
```(Places the binary files in the Ubuntu system)

> *******@************:~$ configure
configure: command not found
*******@************:~$ 

:confused:

sorry..

I had some experience in C programming from University, and some Java but I don't know ANYTHING about ubuntu

---

### Post by Paqman on 2011-02-06
> **whowinsdares said:**
> ok there were several marked with VLC, on trying to install the main VLC one I got the error I gave you. 

I did then go and delete all the ones beginning with VLC because there were about 6


I think you might be looking in the wrong place. The main window of Synaptic shows the actual packages that are available and/or installed. You want to go to the menu Settings > Repositories. This shows which sources your machine is using to get software. Go to the Other tab and remove the PPA for VLC.

> It never asked me to update its index, I just applied the changes I had selected and closed the Synaptic thing

If you do what I detailed above, it will ask to update. Or you can hit "reload" yourself.

> When I go to the VLC download page I get directed to the Linux section automatically, this is the official VLC site so I don't know why I would need to look anywhere else. 


Good news! You don't need to rummage around the internet visiting sites to get your software any more. On Ubuntu you have a package manager that brings it all to you. You can use Synaptic or Ubuntu Software Centre to get any software you might need.


> GUI installation instructions don't apply to me because I have deleted everything from the synaptic thing, and there is nothing referring to VLC in the synaptic thing at all now.

So when I apply the command line installation instructions nothing happens.

Forget the command line, you don't need it for simple stuff like installing software. If you have the Universe repo enabled in your software sources, you'll be able to get VLC through Synaptic or Ubuntu Software Centre.

> 
When you say to use gedit to run that line of code, are you saying to create like an exe file with it in there and run it like that? I don't understand..


Gedit is a text editor, like Notepad on Windows (but much better). You don't need it for this.

---

### Post by whowinsdares on 2011-02-06
> # deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick-proposed restricted main multiverse universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) maverick-proposed restricted main multiverse universe #Added by software-properties
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main #Third party developers repository

:lolflag:

---

### Post by whowinsdares on 2011-02-06
I went back into the synaptic package manager to take a screenshot of what I was doing, and all the VLC stuff was there, so I am installing it now,  one of the things you told me to do worked but I am not sure which one!

.......

I always had universal repositories active so I don't quite know what let me do this..

.........

VLC media player is bsck on the menu but, as before when I attempted to open a file with VLC, or open it from the menu it wont work.

I have a new installation, and it wont work, but it used to before i upgraded to 10.10 

I just want a program that can rotate video files, VLC can do it, and I need it for some of the video files I have anyway..

:(

---

### Post by whowinsdares on 2011-02-06
BUMPY BUMP BUMP:guitar:

---

### Post by CharlesA on 2011-02-06
Please don't bump threads repeatedly before 24 hours has passed.

We'd really need more information to help you.

---

### Post by whowinsdares on 2011-02-06
> **CharlesA said:**
> Please don't bump threads repeatedly before 24 hours has passed.

We'd really need more information to help you.

OK Charles, 

Thanks again for your assistance. Just to be sure you have a full knowledge of my system and the reason why since the upgrade this issue has occurred, is there any code you would like me to run to give you all the information you require in order to solve this?

I don't know why the original VLC installation relied on PPA's but I will run any code, or perform any task on here to give you any information you request so I can fix this.

Its very frustrating but I don't know what to do.

Perhaps there is a way to force VLC to be dependant on other repositories or PPA's that will work with 10.10 on my machine?

What could possible have been disrupted during the upgrade? Should I go through the whole process of purging and reinstalling again? If so what do I need to do to make sure that everything is fresh and nothing is reused?

Ben

---

### Post by khelben1979 on 2011-02-06
> **whowinsdares said:**
> :confused:

sorry..

I had some experience in C programming from University, and some Java but I don't know ANYTHING about ubuntu

No problem! Okay, you need to be in the same file directory once you have downloaded the source archive from the VLC homepage. Unpack it is the first step.

Then use the CD command to enter that directory and use ./configure. You also need to have [the Gnu C++ compiler]("http://en.wikipedia.org/wiki/GNU_Compiler_Collection") (GCC) to be able compile source code, so make sure that it's installed, you will find it in [the Ubuntu Software Center]("http://en.wikipedia.org/wiki/Ubuntu_Software_Center").

---

### Post by CharlesA on 2011-02-06
> **whowinsdares said:**
> 
Its very frustrating but I don't know what to do.

Perhaps there is a way to force VLC to be dependant on other repositories or PPA's that will work with 10.10 on my machine?

What could possible have been disrupted during the upgrade? Should I go through the whole process of purging and reinstalling again? If so what do I need to do to make sure that everything is fresh and nothing is reused?

Ben

You can try purging it again, and then reinstalling. It should pull it from the main repos.

---

### Post by whowinsdares on 2011-02-06
I did this and reinstalled VLC and it still didn't fix it:

```
*********@s*******************:~$ sudo apt-get remove vlc --purge
[sudo] password for ************: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vlc is not installed, so not removed
The following packages were automatically installed and are no longer required:
  liblash3 libxcb-keysyms1 remuco-base libzvbi0 libcddb2 libdvbpsi5 libdvbpsi6
  libggi-target-x kdesudo libavutil-extra-49 libggi2 libdirac-decoder0 libgii1
  libupnp3 libzvbi-common xul-ext-adblock-plus libxcb-randr0 libgii1-target-x
  libfluidsynth1 update-manager-kde apport-hooks-medibuntu libmodplug0c2
  libtar libebml0 libebml2 libmpcdec3 libmatroska0 libmatroska2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 56 not upgraded.


*********@*************:~$ sudo apt-get autoremove vlc --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vlc is not installed, so not removed
The following packages will be REMOVED:
  apport-hooks-medibuntu* kdesudo* libavutil-extra-49* libcddb2*
  libdirac-decoder0* libdvbpsi5* libdvbpsi6* libebml0* libebml2*
  libfluidsynth1* libggi-target-x* libggi2* libgii1* libgii1-target-x*
  liblash3* libmatroska0* libmatroska2* libmodplug0c2* libmpcdec3* libtar*
  libupnp3* libxcb-keysyms1* libxcb-randr0* libzvbi-common* libzvbi0*
  remuco-base* update-manager-kde* xul-ext-adblock-plus*
0 upgraded, 0 newly installed, 28 to remove and 56 not upgraded.
After this operation, 10.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 190288 files and directories currently installed.)
Removing apport-hooks-medibuntu ...
Purging configuration files for apport-hooks-medibuntu ...
Removing update-manager-kde ...
Removing kdesudo ...
update-alternatives: using /usr/lib/kde4/libexec/kdesu-distrib/kdesu to provide /usr/lib/kde4/libexec/kdesu (kdesu) in auto mode.
Removing libavutil-extra-49 ...
Purging configuration files for libavutil-extra-49 ...
Removing libcddb2 ...
Purging configuration files for libcddb2 ...
Removing libdirac-decoder0 ...
Purging configuration files for libdirac-decoder0 ...
Removing libdvbpsi5 ...
Purging configuration files for libdvbpsi5 ...
Removing libdvbpsi6 ...
Purging configuration files for libdvbpsi6 ...
Removing libmatroska0 ...
Purging configuration files for libmatroska0 ...
Removing libebml0 ...
Purging configuration files for libebml0 ...
Removing libmatroska2 ...
Purging configuration files for libmatroska2 ...
Removing libebml2 ...
Purging configuration files for libebml2 ...
Removing libfluidsynth1 ...
Purging configuration files for libfluidsynth1 ...
Removing libggi-target-x ...
Removing libggi2 ...
Purging configuration files for libggi2 ...
Removing libgii1-target-x ...
Removing libgii1 ...
Purging configuration files for libgii1 ...
Removing liblash3 ...
Purging configuration files for liblash3 ...
Removing libmodplug0c2 ...
Purging configuration files for libmodplug0c2 ...
Removing libmpcdec3 ...
Purging configuration files for libmpcdec3 ...
Removing libtar ...
Purging configuration files for libtar ...
Removing libupnp3 ...
Purging configuration files for libupnp3 ...
Removing libxcb-keysyms1 ...
Purging configuration files for libxcb-keysyms1 ...
Removing libxcb-randr0 ...
Purging configuration files for libxcb-randr0 ...
Removing libzvbi0 ...
Purging configuration files for libzvbi0 ...
Removing libzvbi-common ...
Removing remuco-base ...
Removing xul-ext-adblock-plus ...
Purging configuration files for xul-ext-adblock-plus ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
*******@*****************:~$ 
```


:confused:

---

### Post by whowinsdares on 2011-02-06
> **khelben1979 said:**
> No problem! Okay, you need to be in the same file directory once you have downloaded the source archive from the VLC homepage. Unpack it is the first step.

Then use the CD command to enter that directory and use ./configure. You also need to have [the Gnu C++ compiler]("http://en.wikipedia.org/wiki/GNU_Compiler_Collection") (GCC) to be able compile source code, so make sure that it's installed, you will find it in [the Ubuntu Software Center]("http://en.wikipedia.org/wiki/Ubuntu_Software_Center").


Sorry I don't understand what you are suggesting I do. I am able to install VLC, I have used it on this machine for 4 months, and it stopped working the moment I upgraded to 10.10

[SIZE=4]WHAT ELSE CAN DO PLEASE?:confused::confused::confused:[/SIZE]

---

### Post by mc4man on 2011-02-06
Possibly try this - (even if you've done before.
First open Software sources by going -  Synaptic ->Settings -> Repositories. Click on Other and make sure _all_ entries are disabled. (if you still have any.

After that then click on the Reload button in synaptic.

After the sources reload search vlc in synaptic and right click on vlc-data > 'Mark for Complete Removal'

That should also then mark ALL vlc packages for removal, d. check that they are and then click Apply and close synaptic

When done open up your home folder and look for a hidden  file named .config 
Inside will be a vlc folder, delete it.

(if you don't see it then Ctrl+h will show hidden files (files and folders that begin with a .

After  deleting that folder in a terminal (one command, when it's complete then try opening vlc from the Applications menu, leave this terminal open for the moment
```
sudo apt-get update && sudo apt-get install vlc
```

If vlc still fails to open then post the _complete_ terminal output from the above command.

---

### Post by whowinsdares on 2011-02-06
> **mc4man said:**
> Possibly try this - (even if you've done before.
First open Software sources by going -  Synaptic ->Settings -> Repositories. Click on Other and make sure _all_ entries are disabled. (if you still have any.

After that then click on the Reload button in synaptic.

After the sources reload search vlc in synaptic and right click on vlc-data > 'Mark for Complete Removal'

That should also then mark ALL vlc packages for removal, d. check that they are and then click Apply and close synaptic

When done open up your home folder and look for a hidden  file named .config 
Inside will be a vlc folder, delete it.

(if you don't see it then Ctrl+h will show hidden files (files and folders that begin with a .

After  deleting that folder in a terminal (one command, when it's complete then try opening vlc from the Applications menu, leave this terminal open for the moment
```
sudo apt-get update && sudo apt-get install vlc
```If vlc still fails to open then post the _complete_ terminal output from the above command.

Wow I was so sure that would work, unfortunately it didn't I am sorry to say.

```
********@***********:~$ sudo apt-get update && sudo apt-get install vlc
[sudo] password for ********: 
Hit http://archive.ubuntu.com maverick Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Hit http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_AU
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Hit http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_AU
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Hit http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_AU
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_AU
Hit http://archive.ubuntu.com maverick Release
Hit http://archive.ubuntu.com maverick/main i386 Packages
Hit http://archive.ubuntu.com maverick/universe i386 Packages
Hit http://archive.ubuntu.com maverick/restricted i386 Packages
Hit http://archive.ubuntu.com maverick/multiverse i386 Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libvlc5 libvlccore4 vlc-data vlc-nox vlc-plugin-notify vlc-plugin-pulse
Suggested packages:
  mozilla-plugin-vlc videolan-doc
The following NEW packages will be installed:
  libvlc5 libvlccore4 vlc vlc-data vlc-nox vlc-plugin-notify vlc-plugin-pulse
0 upgraded, 7 newly installed, 0 to remove and 36 not upgraded.
Need to get 13.5MB of archives.
After this operation, 37.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ maverick/universe vlc-data all 1.1.4-1ubuntu1 [7,780kB]
Get:2 http://archive.ubuntu.com/ubuntu/ maverick/universe libvlccore4 i386 1.1.4-1ubuntu1 [446kB]
Get:3 http://archive.ubuntu.com/ubuntu/ maverick/universe libvlc5 i386 1.1.4-1ubuntu1 [43.7kB]
Get:4 http://archive.ubuntu.com/ubuntu/ maverick/universe vlc-nox i386 1.1.4-1ubuntu1 [3,190kB]
Get:5 http://archive.ubuntu.com/ubuntu/ maverick/universe vlc i386 1.1.4-1ubuntu1 [2,047kB]
Get:6 http://archive.ubuntu.com/ubuntu/ maverick/universe vlc-plugin-notify i386 1.1.4-1ubuntu1 [6,222B]
Get:7 http://archive.ubuntu.com/ubuntu/ maverick/universe vlc-plugin-pulse i386 1.1.4-1ubuntu1 [7,174B]
Fetched 13.5MB in 40s (331kB/s)                                                
Selecting previously deselected package vlc-data.
(Reading database ... 189823 files and directories currently installed.)
Unpacking vlc-data (from .../vlc-data_1.1.4-1ubuntu1_all.deb) ...
Selecting previously deselected package libvlccore4.
Unpacking libvlccore4 (from .../libvlccore4_1.1.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package libvlc5.
Unpacking libvlc5 (from .../libvlc5_1.1.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package vlc-nox.
Unpacking vlc-nox (from .../vlc-nox_1.1.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package vlc.
Unpacking vlc (from .../vlc_1.1.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package vlc-plugin-notify.
Unpacking vlc-plugin-notify (from .../vlc-plugin-notify_1.1.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package vlc-plugin-pulse.
Unpacking vlc-plugin-pulse (from .../vlc-plugin-pulse_1.1.4-1ubuntu1_i386.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_AU.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Processing triggers for python-support ...
Setting up vlc-data (1.1.4-1ubuntu1) ...
Setting up libvlccore4 (1.1.4-1ubuntu1) ...
Setting up libvlc5 (1.1.4-1ubuntu1) ...
Setting up vlc-nox (1.1.4-1ubuntu1) ...
Setting up vlc (1.1.4-1ubuntu1) ...
Setting up vlc-plugin-notify (1.1.4-1ubuntu1) ...
Setting up vlc-plugin-pulse (1.1.4-1ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
*********@***********:~$ 
```

Sorry about this, the trouble you guys are going to to try and help me is very much appreciated, there is some kind of joke I would like to make about getting attention because I have a broken arm or something, like its excellent getting this help but its because I have a serious defect here.

Please keep trying I am interested to get this resolved.

I did everything exactly as you said, in "other software" under repositories nothing is or was selected. Should I have re-selected some things as a step in there that you possibly missed as a step; I should have taken, and when should I re-select items in that section, and what should I re-select please?

Ben

---

### Post by whowinsdares on 2011-02-06
not sure if this is significant ???

```
********@************:~$ vlc
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x90938fc] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x9138454] skins2 interface error: no suitable dialogs provider found (hint: compile the qt4 plugin, and make sure it is loaded properly)
[0x9138454] skins2 interface error: cannot instanciate qt4 dialogs provider
[0x90938fc] main libvlc error: interface "default" initialization failed
*******@**********:~$ 
```

---

### Post by mc4man on 2011-02-06
Looks like you're having an issue with your qt4 lib's

You could confirm by starting vlc like this, 
```
vlc -Iqt4
```
if it returns error then try
```
sudo apt-get dist-upgrade
```

If still no go could you search in synaptic and post the version of the installed package 'libqtcore4'
Or 
```
apt-cache show libqtcore4
```

---

### Post by whowinsdares on 2011-02-06
> **mc4man said:**
> Looks like you're having an issue with your qt4 lib's

You could confirm by starting vlc like this, 
```
vlc -Iqt4
```if it returns error then try
```
sudo apt-get dist-upgrade
```If still no go could you search in synaptic and post the version of the installed package 'libqtcore4'
Or 
```
apt-cache show libqtcore4
```

thanks,
I ran everything you said and all the details are below..
I hope this gives you some insight..

  	 	 	 	p { margin-bottom: 0.21cm; }  

```
*******@**********:~$ vlc -Iqt4 
 VLC media player 1.1.4 The Luggage (revision exported) 
 Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS") 
 Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE") 
 [0x8944f94] main interface error: no suitable interface module 
 [0x88ad8fc] main libvlc error: interface "default" initialization failed 
 

 ********@**********:~$ sudo apt-get dist-upgrade 
 [sudo] password for *******:  
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 Calculating upgrade... Done 
 The following packages will be REMOVED: 
   xserver-xorg-video-geode 
 The following NEW packages will be installed: 
   libmtdev1 libutouch-grail1 libxcb-dri2-0 
 The following packages will be upgraded: 
   xserver-xorg xserver-xorg-core xserver-xorg-input-evdev 
   xserver-xorg-input-mouse xserver-xorg-input-synaptics 
   xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-apm 
   xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips 
   xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-i128 
   xserver-xorg-video-i740 xserver-xorg-video-intel xserver-xorg-video-mach64 
   xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nv 
   xserver-xorg-video-openchrome xserver-xorg-video-r128 
   xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3 
   xserver-xorg-video-s3virge xserver-xorg-video-savage 
   xserver-xorg-video-siliconmotion xserver-xorg-video-sis 
   xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident 
   xserver-xorg-video-v4l xserver-xorg-video-vesa xserver-xorg-video-vmware 
   xserver-xorg-video-voodoo 
 36 upgraded, 3 newly installed, 1 to remove and 0 not upgraded. 
 Need to get 4,713kB of archives. 
 After this operation, 1,929kB disk space will be freed. 
 Do you want to continue [Y/n]? y 
 Get:1 http://archive.ubuntu.com/ubuntu/ maverick/main libmtdev1 i386 1.0.10-0ubuntu1 [12.5kB] 
 Get:2 http://archive.ubuntu.com/ubuntu/ maverick/main libutouch-grail1 i386 1.0.14-0ubuntu1 [16.5kB] 
 Get:3 http://archive.ubuntu.com/ubuntu/ maverick/main libxcb-dri2-0 i386 1.6-1 [9,828B] 
 Get:4 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-input-mouse i386 1:1.5.0-2build1 [55.2kB] 
 Get:5 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-input-synaptics i386 1.2.2-2ubuntu5 [156kB] 
 Get:6 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-input-evdev i386 1:2.3.2-6ubuntu3 [76.7kB] 
 Get:7 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-input-wacom i386 1:0.10.8-0ubuntu1 [79.7kB] 
 Get:8 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg i386 1:7.5+6ubuntu3 [20.2kB] 
 Get:9 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-input-vmmouse i386 1:12.6.9-2build1 [30.8kB] 
 Get:10 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-siliconmotion i386 1:1.7.4-0ubuntu2 [85.3kB] 
 Get:11 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-r128 i386 6.8.1-3build1 [176kB] 
 Get:12 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-mach64 i386 6.8.2-3build2 [210kB] 
 Get:13 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-radeon i386 1:6.13.1-1ubuntu5 [416kB] 
 Get:14 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-ati i386 1:6.13.1-1ubuntu5 [21.2kB] 
 Get:15 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-i740 i386 1:1.3.2-2build1 [31.5kB] 
 Get:16 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-nv i386 1:2.1.17-3ubuntu3 [110kB] 
 Get:17 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-intel i386 2:2.12.0-1ubuntu5 [250kB] 
 Get:18 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-chips i386 1:1.2.3-1 [81.5kB] 
 Get:19 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-trident i386 1:1.3.4-0ubuntu1 [78.5kB] 
 Get:20 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-s3 i386 1:0.6.3-2build2 [41.2kB] 
 Get:21 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-i128 i386 1:1.3.3-2build2 [35.0kB] 
 Get:22 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-mga i386 1:1.4.11.dfsg-4build1 [112kB] 
 Get:23 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-neomagic i386 1:1.2.4-3build2 [44.1kB] 
 Get:24 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-cirrus i386 1:1.3.2-2ubuntu3 [45.1kB] 
 Get:25 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-ark i386 1:0.7.2-2build2 [17.5kB] 
 Get:26 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-tdfx i386 1:1.4.3-2build2 [43.8kB] 
 Get:27 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-sisusb i386 1:0.9.4-0ubuntu1 [48.0kB] 
 Get:28 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-rendition i386 1:4.2.4-0ubuntu1 [30.5kB] 
 Get:29 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-vesa i386 1:2.3.0-3build1 [26.7kB] 
 Get:30 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-fbdev i386 1:0.4.2-2ubuntu2 [22.2kB] 
 Get:31 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-savage i386 1:2.3.1-2ubuntu2 [90.2kB] 
 Get:32 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-vmware i386 1:11.0.1-2build1 [44.8kB] 
 Get:33 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-openchrome i386 1:0.2.904+svn842-0ubuntu1 [187kB] 
 Get:34 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-s3virge i386 1:1.10.4-2build2 [46.8kB] 
 Get:35 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-voodoo i386 1:1.2.4-0ubuntu1 [24.1kB] 
 Get:36 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-apm i386 1:1.2.3-0ubuntu1 [70.2kB] 
 Get:37 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-video-sis i386 1:0.10.3-1build1 [293kB] 
 Get:38 http://archive.ubuntu.com/ubuntu/ maverick/universe xserver-xorg-video-v4l i386 1:0.2.0-4ubuntu1 [25.9kB] 
 Get:39 http://archive.ubuntu.com/ubuntu/ maverick/main xserver-xorg-core i386 2:1.9.0-0ubuntu7 [1,547kB] 
 Fetched 4,713kB in 10s (450kB/s)                                                
 Extracting templates from packages: 100% 
 (Reading database ... 190547 files and directories currently installed.) 
 Removing xserver-xorg-video-geode ... 
 Selecting previously deselected package libmtdev1. 
 (Reading database ... 190537 files and directories currently installed.) 
 Unpacking libmtdev1 (from .../libmtdev1_1.0.10-0ubuntu1_i386.deb) ... 
 Selecting previously deselected package libutouch-grail1. 
 Unpacking libutouch-grail1 (from .../libutouch-grail1_1.0.14-0ubuntu1_i386.deb) ... 
 Selecting previously deselected package libxcb-dri2-0. 
 Unpacking libxcb-dri2-0 (from .../libxcb-dri2-0_1.6-1_i386.deb) ... 
 Preparing to replace xserver-xorg-input-mouse 1:1.5.0-1 (using .../xserver-xorg-input-mouse_1%3a1.5.0-2build1_i386.deb) ... 
 Unpacking replacement xserver-xorg-input-mouse ... 
 Preparing to replace xserver-xorg-input-synaptics 1.2.2-1ubuntu4 (using .../xserver-xorg-input-synaptics_1.2.2-2ubuntu5_i386.deb) ... 
 Unpacking replacement xserver-xorg-input-synaptics ... 
 Preparing to replace xserver-xorg-input-evdev 1:2.3.2-5ubuntu1 (using .../xserver-xorg-input-evdev_1%3a2.3.2-6ubuntu3_i386.deb) ... 
 Unpacking replacement xserver-xorg-input-evdev ... 
 Preparing to replace xserver-xorg-input-wacom 1:0.10.5-0ubuntu4.1 (using .../xserver-xorg-input-wacom_1%3a0.10.8-0ubuntu1_i386.deb) ... 
 Unpacking replacement xserver-xorg-input-wacom ... 
 Preparing to replace xserver-xorg 1:7.5+5ubuntu1 (using .../xserver-xorg_1%3a7.5+6ubuntu3_i386.deb) ... 
 Unpacking replacement xserver-xorg ... 
 Preparing to replace xserver-xorg-input-vmmouse 1:12.6.5-4ubuntu2 (using .../xserver-xorg-input-vmmouse_1%3a12.6.9-2build1_i386.deb) ... 
 Unpacking replacement xserver-xorg-input-vmmouse ... 
 Preparing to replace xserver-xorg-video-siliconmotion 1:1.7.3-1 (using .../xserver-xorg-video-siliconmotion_1%3a1.7.4-0ubuntu2_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-siliconmotion ... 
 Preparing to replace xserver-xorg-video-r128 6.8.1-2ubuntu1 (using .../xserver-xorg-video-r128_6.8.1-3build1_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-r128 ... 
 Preparing to replace xserver-xorg-video-mach64 6.8.2-2 (using .../xserver-xorg-video-mach64_6.8.2-3build2_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-mach64 ... 
 Preparing to replace xserver-xorg-video-radeon 1:6.13.0-1ubuntu5 (using .../xserver-xorg-video-radeon_1%3a6.13.1-1ubuntu5_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-radeon ... 
 Preparing to replace xserver-xorg-video-ati 1:6.13.0-1ubuntu5 (using .../xserver-xorg-video-ati_1%3a6.13.1-1ubuntu5_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-ati ... 
 Preparing to replace xserver-xorg-video-i740 1:1.3.2-1 (using .../xserver-xorg-video-i740_1%3a1.3.2-2build1_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-i740 ... 
 Preparing to replace xserver-xorg-video-nv 1:2.1.15-1ubuntu3 (using .../xserver-xorg-video-nv_1%3a2.1.17-3ubuntu3_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-nv ... 
 Preparing to replace xserver-xorg-video-intel 2:2.9.1-3ubuntu5 (using .../xserver-xorg-video-intel_2%3a2.12.0-1ubuntu5_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-intel ... 
 Preparing to replace xserver-xorg-video-chips 1:1.2.2-1 (using .../xserver-xorg-video-chips_1%3a1.2.3-1_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-chips ... 
 Preparing to replace xserver-xorg-video-trident 1:1.3.3-1 (using .../xserver-xorg-video-trident_1%3a1.3.4-0ubuntu1_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-trident ... 
 Preparing to replace xserver-xorg-video-s3 1:0.6.3-1 (using .../xserver-xorg-video-s3_1%3a0.6.3-2build2_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-s3 ... 
 Preparing to replace xserver-xorg-video-i128 1:1.3.3-1 (using .../xserver-xorg-video-i128_1%3a1.3.3-2build2_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-i128 ... 
 Preparing to replace xserver-xorg-video-mga 1:1.4.11.dfsg-2ubuntu1 (using .../xserver-xorg-video-mga_1%3a1.4.11.dfsg-4build1_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-mga ... 
 Preparing to replace xserver-xorg-video-neomagic 1:1.2.4-2 (using .../xserver-xorg-video-neomagic_1%3a1.2.4-3build2_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-neomagic ... 
 Preparing to replace xserver-xorg-video-cirrus 1:1.3.2-1ubuntu1 (using .../xserver-xorg-video-cirrus_1%3a1.3.2-2ubuntu3_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-cirrus ... 
 Preparing to replace xserver-xorg-video-ark 1:0.7.2-1 (using .../xserver-xorg-video-ark_1%3a0.7.2-2build2_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-ark ... 
 Preparing to replace xserver-xorg-video-tdfx 1:1.4.3-1 (using .../xserver-xorg-video-tdfx_1%3a1.4.3-2build2_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-tdfx ... 
 Preparing to replace xserver-xorg-video-sisusb 1:0.9.3-1 (using .../xserver-xorg-video-sisusb_1%3a0.9.4-0ubuntu1_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-sisusb ... 
 Preparing to replace xserver-xorg-video-rendition 1:4.2.3-1 (using .../xserver-xorg-video-rendition_1%3a4.2.4-0ubuntu1_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-rendition ... 
 Preparing to replace xserver-xorg-video-vesa 1:2.3.0-1ubuntu1 (using .../xserver-xorg-video-vesa_1%3a2.3.0-3build1_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-vesa ... 
 Preparing to replace xserver-xorg-video-fbdev 1:0.4.1-1ubuntu1 (using .../xserver-xorg-video-fbdev_1%3a0.4.2-2ubuntu2_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-fbdev ... 
 Preparing to replace xserver-xorg-video-savage 1:2.3.1-1ubuntu1 (using .../xserver-xorg-video-savage_1%3a2.3.1-2ubuntu2_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-savage ... 
 Preparing to replace xserver-xorg-video-vmware 1:10.16.9-1 (using .../xserver-xorg-video-vmware_1%3a11.0.1-2build1_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-vmware ... 
 Preparing to replace xserver-xorg-video-openchrome 1:0.2.904+svn827-1 (using .../xserver-xorg-video-openchrome_1%3a0.2.904+svn842-0ubuntu1_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-openchrome ... 
 Preparing to replace xserver-xorg-video-s3virge 1:1.10.4-1 (using .../xserver-xorg-video-s3virge_1%3a1.10.4-2build2_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-s3virge ... 
 Preparing to replace xserver-xorg-video-voodoo 1:1.2.3-1 (using .../xserver-xorg-video-voodoo_1%3a1.2.4-0ubuntu1_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-voodoo ... 
 Preparing to replace xserver-xorg-video-apm 1:1.2.2-1 (using .../xserver-xorg-video-apm_1%3a1.2.3-0ubuntu1_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-apm ... 
 Preparing to replace xserver-xorg-video-sis 1:0.10.2-2 (using .../xserver-xorg-video-sis_1%3a0.10.3-1build1_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-sis ... 
 Preparing to replace xserver-xorg-video-v4l 1:0.2.0-4 (using .../xserver-xorg-video-v4l_1%3a0.2.0-4ubuntu1_i386.deb) ... 
 Unpacking replacement xserver-xorg-video-v4l ... 
 Preparing to replace xserver-xorg-core 2:1.7.6-2ubuntu7.5 (using .../xserver-xorg-core_2%3a1.9.0-0ubuntu7_i386.deb) ... 
 Unpacking replacement xserver-xorg-core ... 
 Processing triggers for man-db ... 
 Setting up libmtdev1 (1.0.10-0ubuntu1) ... 
 Setting up libutouch-grail1 (1.0.14-0ubuntu1) ... 
 Setting up libxcb-dri2-0 (1.6-1) ... 
 Setting up xserver-xorg-core (2:1.9.0-0ubuntu7) ... 
 Setting up xserver-xorg-input-mouse (1:1.5.0-2build1) ... 
 Setting up xserver-xorg-video-v4l (1:0.2.0-4ubuntu1) ... 
 Setting up xserver-xorg-video-voodoo (1:1.2.4-0ubuntu1) ... 
 Setting up xserver-xorg-video-vmware (1:11.0.1-2build1) ... 
 Setting up xserver-xorg-video-vesa (1:2.3.0-3build1) ... 
 Setting up xserver-xorg-video-trident (1:1.3.4-0ubuntu1) ... 
 Setting up xserver-xorg-video-tdfx (1:1.4.3-2build2) ... 
 Setting up xserver-xorg-video-sisusb (1:0.9.4-0ubuntu1) ... 
 Setting up xserver-xorg-video-sis (1:0.10.3-1build1) ... 
 Setting up xserver-xorg-video-siliconmotion (1:1.7.4-0ubuntu2) ... 
 Setting up xserver-xorg-video-savage (1:2.3.1-2ubuntu2) ... 
 Setting up xserver-xorg-video-s3virge (1:1.10.4-2build2) ... 
 Setting up xserver-xorg-video-s3 (1:0.6.3-2build2) ... 
 Setting up xserver-xorg-video-rendition (1:4.2.4-0ubuntu1) ... 
 Setting up xserver-xorg-video-radeon (1:6.13.1-1ubuntu5) ... 
 Setting up xserver-xorg-video-r128 (6.8.1-3build1) ... 
 Setting up xserver-xorg-video-openchrome (1:0.2.904+svn842-0ubuntu1) ... 
 Setting up xserver-xorg-video-nv (1:2.1.17-3ubuntu3) ... 
 Setting up xserver-xorg-video-neomagic (1:1.2.4-3build2) ... 
 Setting up xserver-xorg-video-mga (1:1.4.11.dfsg-4build1) ... 
 Setting up xserver-xorg-video-mach64 (6.8.2-3build2) ... 
 Setting up xserver-xorg-video-intel (2:2.12.0-1ubuntu5) ... 
 Setting up xserver-xorg-video-i740 (1:1.3.2-2build1) ... 
 Setting up xserver-xorg-video-i128 (1:1.3.3-2build2) ... 
 Setting up xserver-xorg-video-fbdev (1:0.4.2-2ubuntu2) ... 
 Setting up xserver-xorg-video-cirrus (1:1.3.2-2ubuntu3) ... 
 Setting up xserver-xorg-video-chips (1:1.2.3-1) ... 
 Setting up xserver-xorg-video-ati (1:6.13.1-1ubuntu5) ... 
 Setting up xserver-xorg-video-ark (1:0.7.2-2build2) ... 
 Setting up xserver-xorg-video-apm (1:1.2.3-0ubuntu1) ... 
 Setting up xserver-xorg-input-wacom (1:0.10.8-0ubuntu1) ... 
 Setting up xserver-xorg-input-vmmouse (1:12.6.9-2build1) ... 
 Setting up xserver-xorg-input-synaptics (1.2.2-2ubuntu5) ... 
 Setting up xserver-xorg-input-evdev (1:2.3.2-6ubuntu3) ... 
 Setting up xserver-xorg (1:7.5+6ubuntu3) ... 
 Processing triggers for libc-bin ... 
 ldconfig deferred processing now taking place 
 **********@***********:~$
 

 ********@**********:~$ apt-cache show libqtcore4 
 Package: libqtcore4 
 Priority: optional 
 Section: libs 
 Installed-Size: 7412 
 Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com> 
 Original-Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org> 
 Architecture: i386 
 Source: qt4-x11 
 Version: 4:4.7.0-0ubuntu4 
 Replaces: libqt4-core (<< 4.4.0~beta1-1), libqt4-gui (<< 4.4.0~beta1-1) 
 Depends: libc6 (>= 2.9), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.12.0), libstdc++6 (>= 4.1.1), zlib1g (>= 1:1.1.4) 
 Breaks: libqt4-core (<< 4.4.0~beta1-1), libqt4-gui (<< 4.4.0~beta1-1) 
 Filename: pool/main/q/qt4-x11/libqtcore4_4.7.0-0ubuntu4_i386.deb 
 Size: 1848266 
 MD5sum: 6c4c2fac43078ace7d0326d26fa27e94 
 SHA1: 509852aa43bb8f387b33fa4f4442576cc929a897 
 SHA256: 0dca2df24c3361c2791807a6ba54dd3834b37cdd499d95524a192d6d7679803d 
 Description: Qt 4 core module 
  Qt is a cross-platform C++ application framework. Qt's primary feature 
  is its rich set of widgets that provide standard GUI functionality. 
  . 
  The QtCore module contains core non-GUI functionality. 
 Homepage: http://www.qtsoftware.com 
 Bugs: https://bugs.launchpad.net/ubuntu/+filebug 
 Origin: Ubuntu 
 Supported: 18m 
 Task: kubuntu-desktop, kubuntu-mobile, kubuntu-netbook, edubuntu-desktop-gnome, edubuntu-desktop-kde, mythbuntu-backend-master, mythbuntu-backend-master, mythbuntu-backend-slave, mythbuntu-backend-slave, mythbuntu-desktop, mythbuntu-frontend, mythbuntu-frontend 
  
 Package: libqtcore4 
 Status: install ok installed 
 Priority: optional 
 Section: libs 
 Installed-Size: 7412 
 Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com> 
 Architecture: i386 
 Source: qt4-x11 
 Version: 4:4.7.0-0ubuntu4.2 
 Replaces: libqt4-core (<< 4.4.0~beta1-1), libqt4-gui (<< 4.4.0~beta1-1) 
 Depends: libc6 (>= 2.9), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.12.0), libstdc++6 (>= 4.1.1), zlib1g (>= 1:1.1.4) 
 Breaks: libqt4-core (<< 4.4.0~beta1-1), libqt4-gui (<< 4.4.0~beta1-1) 
 Conffiles: 
  /etc/xdg/Trolltech.conf 0fd6f087c3c44994cae7891adffafece 
 Description: Qt 4 core module 
  Qt is a cross-platform C++ application framework. Qt's primary feature 
  is its rich set of widgets that provide standard GUI functionality. 
  . 
  The QtCore module contains core non-GUI functionality. 
 Homepage: http://www.qtsoftware.com 
 Original-Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org> 
  
 **********@*******:~$  
 

```

---

### Post by mc4man on 2011-02-06
Everything unfortunately looks fine, ck. on libqtgui4, it should be the same version as libqtcore4

(also search libqt4 in synaptic and make sure libqt4-core and libqt4-gui are not installed.

Maybe try a restart if not already

What does this show
```
ls /usr/local/lib
```

---

### Post by whowinsdares on 2011-02-06
> **mc4man said:**
> Everything unfortunately looks fine, ck. on libqtgui4, it should be the same version as libqtcore4

(also search libqt4 in synaptic and make sure libqt4-core and libqt4-gui are not installed.

Maybe try a restart if not already

What does this show
```
ls /usr/local/lib
```

```

****@**********:~$ ls /usr/local/lib
python2.6  site_ruby
```

I just realised Skype isn't working either, neither is Aurora, so there are probably other programs that don't work I haven't discovered yet.

Previous to the upgrade, on logging in after entering my password, I got a funny message along the lines of, "couldn't authenticate" or "couldn't authenticate session" or something but then my desktop would load anyway after a short delay. It started doing this after I tried deleting several programs using a specific un-installer program. This was about 3 months ago.

About 3 weeks ago I ran BleachBit I don't know if that destroyed something.

I hate considering reinstalling as I am very paranoid I will delete some essential document or file I haven't backed up by accident, but I think that might be the only way to fix this unfortunately :-({|=

---

### Post by CharlesA on 2011-02-06
It would probably be less frustrating to just do a clean install of 10.10, upgrades can be messy sometimes. :(

Unless you store yer documents elsewhere, you can just backup yer home directory and then reinstall.

---

### Post by whowinsdares on 2011-02-06
yes I think it might be a case of, see you on the other side... lol

thanks for your efforts!

---

### Post by whowinsdares on 2011-02-08
Hi,

Could someone please recommend any free online back up solution for Ubuntu? I have signed up for 2 which I got from searching for Ubuntu online backup and they both work only with Windows or Mac, and this seems like a recurring issue..

Does anyone know of one that works with Ubuntu please, so I can back my files up and reinstall?

Thank you

---

### Post by CharlesA on 2011-02-08
UbuntuOne works, as does DropBox.

You get an extra 250MB if you [join]("https://www.dropbox.com/referrals/NTE2MTMyNDU0OQ?src=global0").

They support Windows, Mac and Linux.

---

### Post by whowinsdares on 2011-02-08
CharlesA,

I am using Amazon and soon I will be able to reinstall. Something wrong with my CD drive and I couldnt burn even a CD.

So I will have to reinstall using Jaunty, on an old cd and upgrade.

---

### Post by mc4man on 2011-02-08
> So I will have to reinstall using [COLOR="Red"]Jaunty[/COLOR], on an old cd and upgrade.
You are looking for trouble trying to get from a fresh jaunty(EOL) to 10.10, better to get a 10.04 or 10.10 cd somehow or a new cd drive or if your pc can do, install from a usb flash drive

If inclined to try then ask how to switch to the old-release repo

---

### Post by CharlesA on 2011-02-08
> **mc4man said:**
> You are looking for trouble trying to get from a fresh jaunty(EOL) to 10.10, better to get a 10.04 or 10.10 cd somehow or a new cd drive or if your pc can do, install from a usb flash drive

If inclined to try then ask how to switch to the old-release repo

+1. It'll be messy to upgrade from such an old distro.

---

### Post by mc4man on 2011-02-08
If you still have this install one last thing you could ck. (seeing as I never asked what you upgraded from.
At some point there was a name change for many qt4 libs, so - 
search in synaptic using libqt4
If you see any of these 3 packages then mark for complete removal, apply and restart.
libqt4-core
libqt4-gui
libqt4-assistant (this one isn't too important but if there remove

---

### Post by whowinsdares on 2011-02-08
The strangest thing has happened on this acer desktop PC, its not seeming to recognise ANY CD's now,  but I downloaded a 10.10 ISO..

needless to say I couldn't burn it to a CDR-80 but I created a boot disk with a USB

I have played around with BIOS settings, trying all the possible alternatives trying to get the PC to boot from USB..

The last setting I left the BIOS with was all boot - up priorities set to USB and the thing still boots up of the hard-drive to my 'old' desk-top.

If I cant create a boot disk on CD, and the thing wont boot off a USB, and I seriously cant afford a new computer anyhow, what does anyone suggest ?

I might have to just make do - it can still do everything I want, but it just seems so LAME / limited..

Can you believe the BIOS thing, still boots up off hard-drive when all 3 priorities are set to USB ??

There are several different distinctions of USB boot device defined on the BIOS, but I tried them all. One is termed USB zip ??



](*,)

---

### Post by beew on 2011-02-08
> **whowinsdares said:**
> 


The last setting I left the BIOS with was all boot - up priorities set to USB and the thing still boots up of the hard-drive to my 'old' desk-top.
...
Can you believe the BIOS thing, still boots up off hard-drive when all 3 priorities are set to USB ??



My SamSung laptop is like that. Setting BIOS priority makes no difference. However, I can bring up a one time boot menu if I press ESC when it boots and change the boot option to "usb device". On other computers the key may be F10, F12 or something like that. Usually that would fix the problem.

But my laptop is especially stubborn, even changing the boot priority in the one time boot menu it still insists on booting into the hard disk, I have to do it a second time in order to boot into the usb (have to catch it trying to boot into the hard disk and press ESC to bring up the one time boot menu again) With most computers I think bringing up the one time boot menu once is enough. 

I don't know if you have tried this already, if not you may as well try it.

---

### Post by whowinsdares on 2011-02-09
> **beew said:**
> My SamSung laptop is like that. Setting BIOS priority makes no difference. However, I can bring up a one time boot menu if I press ESC when it boots and change the boot option to "usb device". On other computers the key may be F10, F12 or something like that. Usually that would fix the problem.

But my laptop is especially stubborn, even changing the boot priority in the one time boot menu it still insists on booting into the hard disk, I have to do it a second time in order to boot into the usb (have to catch it trying to boot into the hard disk and press ESC to bring up the one time boot menu again) With most computers I think bringing up the one time boot menu once is enough. 

I don't know if you have tried this already, if not you may as well try it.

Thanks ! That worked. I now have a fresh 10.10 installation

---

### Post by whowinsdares on 2011-02-09
Just a final question now, the online back-up I made I can't seem to get my files back from.

When I go online to the Amazon S3 server I can see my files are there, but because I reinstalled the folders I backed up on this computer no longer exist, so I can't sync them back again..

How do I work around this?

---

### Post by CharlesA on 2011-02-09
I don't use amazon s3, but a quick google showed a lot of stuff to access that data. I'm not sure of a linux specific solution tho.

---

### Post by whowinsdares on 2011-02-15
Hi,

I am wondering if I should post a new thread on this but it is related. Firstly, upgrading to 10.10 has fixed my DVD player, I can now read data DVD's.

I downloaded the backed up files, but they are not accepting my encryption password. I have been speaking to 2 or 3 of the support people from Amazon S3 and they have suggested taking my PC to a data recovery expert to see if they can recover files from my hard drive, or compile a pass cracker to try and get past the encryption.

I have downloaded and compiled Hydra to try and do this. But I need some help as I don't know what I am doing..

Also now I can't download ANYTHING using the software center, and I keep getting this error:

```
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 769, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 948, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.
```

I get the message to report it as a bug but I don't know how to do this..

Thanks

---

