---
title: "having some issues"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by saab on 2007-11-06
i recently installed gutsy on my gateway.  

i am trying to install audacious, but am unable to.    The first thing I did was uninstall rhythmbox.  I then tried to install audacious but it still told me there were conflicting programs.

I also tried to install the w32codecs, but keep getting the same error:
> Depends: libstdc++5 (>=1:3.3.4-1) but it is not installable 

what should I try?  I have been searching for the past couple of days when I get a chance, but nothing I have found has helped.

Thanks
-John

---

### Post by deadgobby on 2007-11-06
Try this.
 Sudo aptitude install (program name here)
 Aptitude installs depends and see if that works.
Gobby

---

### Post by saab on 2007-11-06
This is what I got:
> john@john-laptop:~$ sudo aptitude install audacious
[sudo] password for john:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  audacious-plugins audacious-plugins-extra qjackctl 
The following NEW packages will be automatically installed:
  jackd ladcca2 libaudacious5 libbinio1c2 libfluidsynth1 libfreebob0 
  libjack0 libjack0.100.0-0 libmcs1 libmms0 libresid-builder0c2a 
  libsidplay2 
The following NEW packages will be installed:
  audacious jackd ladcca2 libaudacious5 libbinio1c2 libfluidsynth1 
  libfreebob0 libjack0 libjack0.100.0-0 libmcs1 libmms0 
  libresid-builder0c2a libsidplay2 
0 packages upgraded, 16 newly installed, 0 to remove and 0 not upgraded.
Need to get 4188kB of archives. After unpacking 11.5MB will be used.
The following packages have unmet dependencies:
  qjackctl: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) which is a virtual package.
  audacious-plugins: Depends: libmad0 (>= 0.15.1b) which is a virtual package.
  audacious-plugins-extra: Depends: libartsc0 (>= 1.5.0-1) which is a virtual package.
                           Depends: libmpcdec3 which is a virtual package.
                           Depends: libpulse0 which is a virtual package.
                           Depends: libsamplerate0 which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
audacious [Not Installed]
audacious-plugins [Not Installed]
audacious-plugins-extra [Not Installed]
jackd [Not Installed]
libfluidsynth1 [Not Installed]
libjack0 [Not Installed]
libjack0.100.0-0 [Not Installed]
qjackctl [Not Installed]

Score is -9818

Accept this solution? [Y/n/q/?] 


I don't think accepting this solution would help as none of the programs would be installed.

Any ideas?

Thanks again
-John

---

### Post by saab on 2007-11-06
any suggestions?  the main purpose of this laptop is media.  As it stands, I can't watch any videos or play any music.

is there any where else I could look?

thanks again
-John

---

### Post by erginemr on 2007-11-06
Hi saab, welcome to Ubuntu forums.

I do not use Audacious, but its screenshots on the web hint at the fact that it follows the footsteps of winamp and xmms. Probably good for playing music, but can it also handle videos?

My recommendations to you would be to use Listen music player:
sudo aptitude install listen

for playing music and totem-xine & gxine:
sudo aptitude install totem-xine
sudo aptitude install gxine

for playing movies.

Listen music player follows the footsteps of amarok, the famous kde music player.
(You can also install that with: sudo aptitude install amarok,
but is loads lots of kde and sql libraries, which is a drawback for a Gnome system, IMHO.)

Listen is very functional and versatile as a all-in-one music player. I bet you will like it. 

You may also try Exaile music player (which has a similar look) with:
sudo aptitude install exaile.

---

### Post by erginemr on 2007-11-06
...
Totem-xine and gxine uses the libraries of the legendary movie player xine, which dates back to the time of xmms. You can play many video types (including divx) with it, but not the encrypted DVD's. To play DVD's, you will need to install a few more modules:
sudo aptitude install libdvdnav4 libdvdread3

from the Ubuntu repositories, and
sudo aptitude install libdvdcss2

But the package libdvdcss2 is in the Medibuntu repositories. You need to add it to your list of repositories by reading the following guide:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

If you do not find totem of gxine to your taste, you may also consider installing another great video player: vlc
sudo aptitude install vlc

---

### Post by saab on 2007-11-06
i do not plan on audacious for videos.  in my original post, I mentioned that I can not get the w32codecs to install either.

I took your advice and tried the listen install.  This is what I got:
> john@john-laptop:~$ sudo aptitude install listen
[sudo] password for john:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  listen python-ctypes python-pymad python-tunepimp 
The following NEW packages will be automatically installed:
  libdiscid0 python-musicbrainz2 
The following NEW packages will be installed:
  libdiscid0 python-musicbrainz2 
0 packages upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 704kB of archives. After unpacking 3391kB will be used.
The following packages have unmet dependencies:
  python-pymad: Depends: libmad0 (>= 0.15.1b) which is a virtual package.
  python-ctypes: Depends: libffi4 (>= 4.2-20070208) which is a virtual package.
  python-tunepimp: Depends: libtunepimp5 (>= 0.5.3-4ubuntu2) which is a virtual package.
  listen: Depends: python-pyogg (>= 1.3-1.1) which is a virtual package.
          Depends: python-pysqlite2 which is a virtual package.
          Depends: python-pyvorbis (>= 1.3) which is a virtual package.
          Depends: python-mutagen (>= 1.8) which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
listen [Not Installed]
python-ctypes [Not Installed]
python-musicbrainz2 [Not Installed]
python-pymad [Not Installed]
python-tunepimp [Not Installed]

Score is -9845

Accept this solution? [Y/n/q/?] 


do I have a bad install of Gutsy?  is there something I messed up on?

Thanks again for your help.  I am still looking for a solution.
-John

---

### Post by saab on 2007-11-06
i thought I did install the medi repositories.  I will have to go through that again.  I will let you know what I find.

Thanks

---

### Post by erginemr on 2007-11-06
> **saab said:**
> i recently installed gutsy on my gateway.  

i am trying to install audacious, but am unable to.    The first thing I did was uninstall rhythmbox.  I then tried to install audacious but it still told me there were conflicting programs.

I also tried to install the w32codecs, but keep getting the same error:

Depends: libstdc++5 (>=1:3.3.4-1) but it is not installable 

what should I try?  I have been searching for the past couple of days when I get a chance, but nothing I have found has helped.

Thanks
-John

Regarding the w32codecs, the default c++ library installed in Gutsy is libstdc++ ver.6, but you may also install version 5 to co-exist with ver.6 with:
sudo aptitude install libstdc++5

Although the warning "is not installable" is quite fishy, you may at least give a try to the above and then try installing w32codecs, again.

---

### Post by erginemr on 2007-11-06
> **saab said:**
> i do not plan on audacious for videos.  in my original post, I mentioned that I can not get the w32codecs to install either.

I took your advice and tried the listen install.  This is what I got:


do I have a bad install of Gutsy?  is there something I messed up on?

Thanks again for your help.  I am still looking for a solution.
-John

Very strange results. There is definitely something wrong in your system. I started suspecting your sources.list (repositories). Can you please post its contents with:

cat /etc/apt/sources.list

---

### Post by saab on 2007-11-06
i still get quite a few unmet dependancies with just about everything I try.  I have the medibuntu installed, but maybe I messed something up?

---

### Post by saab on 2007-11-06
> **erginemr said:**
> Very strange results. There is definitely something wrong in your system. I started suspecting your sources.list (repositories). Can you please post its contents with:

cat /etc/apt/sources.list

This is what I got:
> john@john-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe multiverse


thanks again for taking the time to help me out!

---

### Post by erginemr on 2007-11-06
> **saab said:**
> This is what I got:


thanks again for taking the time to help me out!

You are most welcome friend. I wish I (or any other Ubuntu user) can help so that your problem will be resolved with minor headaches.

In my sources.list, the following items are active:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted

but the cdrom repository has been disabled with:
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

Inyours, there is a line:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe multiverse

but there is no "main" there!! I think the problem lies under this "main". More later...

---

### Post by erginemr on 2007-11-06
Can you please open your synaptic, from its menu
Settings -> Repositories 

And make sure that in the first tab, main, universe, restricted, multiverse and source code has been enabled, and down below, the gutsy cdrom has been disabled. Also, there should be a drop-down menu to locate the download server, you should select "main server".

In the third tab, also enable gutsy-security and gutsy-updates.

Finally, press the update button. And lets hope that it will work...

---

### Post by saab on 2007-11-06
you sir are a genius.  so far that seems to have been the trick.

I will let you know how things turn out.

Thanks again.  What a great community!

---

### Post by saab on 2007-11-06
everything works like a charm now.  Thank you so much for your help!!

---

### Post by erginemr on 2007-11-06
You are most welcome bro, but dit it really work? 

In your initial posts for installing audacious and listen, there were lots of different error messages. Can you install audacious now for instance?

---

### Post by erginemr on 2007-11-06
> **saab said:**
> everything works like a charm now.  Thank you so much for your help!!

I am very glad to hear that, friend. I am sure you will also help other people soon, when you learn more of your beloved Linux system.

Could you please mark this thread as solved (by using the thread tools drop-down menu above) to let the others know?

Take Care Yourself...

---

