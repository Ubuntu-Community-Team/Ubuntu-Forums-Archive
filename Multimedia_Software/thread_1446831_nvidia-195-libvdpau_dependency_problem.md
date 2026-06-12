---
title: "nvidia-195-libvdpau dependency problem"
date: 2010-04-04
forum: Multimedia Software
---

### Post by ejp on 2010-04-04
Hi,

I want to install mplayer-nogui as advised in the Medibuntu page
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)), 
but some stange dependency problem prohibits this.
The error does not make sense to me, so I would highly appreciate some help.

For completeness sake, I'm running: 

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

mplayer-nogui apparently depends on nvidia-195-libvdpau.
When I try to install nvidia-195-libvdpau, I get the following error message:

E: /var/cache/apt/archives/nvidia-195-libvdpau_195.30-0ubuntu0~ppa1_i386.deb: 
trying to overwrite '/usr/lib/libvdpau.so.1', which is also in package libvdpau1 0

When I search for all packages that have "libvdpau" in the name,
the only package installed on my system is libvdpau1.
Uninstalling this package would also remove a ton of other packages, 
including some very basic ones, so I'm very hesitant to go that route.
I have no broken packages according to Synaptic Package Manager.

I have not seen this error message before, nor can I find it on the web.
Any advice on how to proceed would be very welcome!

Thanks in advance,

EJ

---

### Post by cchhrriiss121212 on 2010-04-05
I have mplayer-nogui + nvidia 195 and it does not require that nvidia package, so I'd recommend installing from here to get vdpau playback:
[http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)

---

### Post by ejp on 2010-04-11
Hi Chris,

Thanks for the reply! I had already added the **ppa:nvidia-vdpau/ppa** 
repository to my system, and followed instructions in the post you refer to
([http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)).
I have indeed a xorg.conf file as described there, and then the instructions
ask to install mplayer-nogui. That's precisely the step that I can't get through
because of the described dependency problem.

It is remarkable that apparently you have different dependencies...
How can that happen? I use Synaptic Package Manager, 
and when I mark mplayer-nogui for installation, it tells me that also
nvidia-195-libvdpau needs to be installed. 
Do I understand correctly that that may not be the case usually?

Cheers,

Evert-Jan

---

### Post by cchhrriiss121212 on 2010-04-11
> It is remarkable that apparently you have different dependencies...
How can that happen? I use Synaptic Package Manager, 
and when I mark mplayer-nogui for installation, it tells me that also
nvidia-195-libvdpau needs to be installed. 
Do I understand correctly that that may not be the case usually?
I don't know how that happens and I don't know what happens usually, but my system does not have the nvidia libvdpau package as a dependency or even as an available package for download. I had the opposite problem when trying to get vdpau, mplayer needed libvpau1 and I had the nvidia version of it.

I'd reccomend that you re-install your nvidia driver by this method:
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

### Post by ejp on 2010-04-17
Hello Chris,

It's very strange... I have uninstalled the nvidia drivers,
and still the package manager insists that mplayer-nogui needs
nvidia-195-libvdpau. This is starting to sound like a true dependency problem.
What would you recommend? Perhaps I could try to rebuild my dependency db? 

Thanks,

EJ

---

### Post by cchhrriiss121212 on 2010-04-17
How did you re-install the driver? Did you remove everything to do with nvidia from synaptic?
When you go to install mplayer-nogui from synaptic, what source is displayed under "latest available version"?

Mine is this: 2:1.0~rc3+svn20091207-0ubuntu1~karmic~nvidiavdpauppa11

---

### Post by ejp on 2010-04-17
Now this really has me stumped:

In order to check the dependency trail from mplayer-nogui to nvidia-195-libvdpau,
I installed apt-rdepends
(see [http://www.howtoforge.com/checking-package-dependencies-with-apt-rdepends-on-debian-ubuntu](http://www.howtoforge.com/checking-package-dependencies-with-apt-rdepends-on-debian-ubuntu))

Then I executed the commands:

>apt-rdepends mplayer-nogui > dep.txt
>grep nvidia dep.txt
>grep libvdpau dep.txt

The output of both greps was empty. I checked the dep.txt file with Kate,
searching for nvidia and libvdpau. Nada. I could not beleive it.
Then I started the Synaptic Package Manager, marked mplayer-nogui for installation,
and it immediately informed me that also nvidia-195-libvdpau is needed....

Final check: attempt to install mplayer-nogui from the command line with apt-get:

====================
>sudo apt-get install mplayer-nogui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgdata5 libgdata-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  nvidia-195-libvdpau
Suggested packages:
  mplayer-doc ladspa-sdk
The following NEW packages will be installed:
  mplayer-nogui nvidia-195-libvdpau
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 873kB/5,518kB of archives.
After this operation, 13.0MB of additional disk space will be used.
Do you want to continue [Y/n]? ^C
=======================
 
Are there any other ways to check how dependencies are processed?
Any pointers as to what may be going on are very much appreciated!!

Thanks in advance,

EJ

---

### Post by ejp on 2010-04-17
Hi Chris,

I have not reinstalled the nvidia driver (yet). After uninstalling the nvidia driver
I tried to install mplayer-nogui (that should be possible too, right?), 
and the mysterious dependency to nvidia-195-libvdpau still surfaced.

At the moment, I have no packages installed with "nvidia" in the name.

Synaptic displays in tab "common" as version: 3:1.0~svn30146-0ubuntu0~ppa0
and in tab "Dependencies" it does list nvidia-195-libvdpau

Cheers,

EJ

---

### Post by ejp on 2010-04-17
As mentioned in an erlier post however, I do have libvdpau1 installed, which in the "description" does mentions nvidia.
Installed version: 0.4.2~karmic~nvidiavdpauppa4
And under "dependencies" is does mention conflicts with nvidia-libvdpau and other similar packages.

Is this the source of the problem?

As mentioned above, when I try to mark it for removal,
many, many other packages are also marked for removal, including KDE.
It seems that if I remove libvdpau1, I will not have a desktop anymore.

EJ

---

### Post by cchhrriiss121212 on 2010-04-17
> Synaptic displays in tab "common" as version: 3:1.0~svn30146-0ubuntu0~ppa0
I think this is the problem, EJ. The version in this ppa must have the nvidia-vdpau as a dependency. You can do 2 things: either disable this ppa so that the packages are not seen as available. Or highlight the mplayer-nogui in synaptic and go to Package>Force verison and select the one from the nvidia ppa which has the correct dependency.

I would go for the first one, as it will just cause you more problems with dependencies.

---

### Post by ejp on 2010-04-18
Hi Chris,

Yep, you were right! I can now install mplayer without problems.
Next step is to reinstall the nvidia drivers. 

Cheers,

EJ

---

