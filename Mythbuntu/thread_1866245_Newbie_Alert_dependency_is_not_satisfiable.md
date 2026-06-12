---
title: "Newbie Alert: dependency is not satisfiable"
date: 2011-10-21
forum: Mythbuntu
---

### Post by MarsdeNation on 2011-10-21
Hi Everyone,

I am working on a new Installation of MythBuntu 11.10 32bit.

I am trying to follow the instructions to Install Shepherd for the TV Guide: [http://svn.whuffy.com/](http://svn.whuffy.com/)

I am up to the part where I am trying to install the Pearl Dependencies.

The "libmozjs0d_1.8.1.16+nobinonly-0ubuntu1_i386.deb" file installed fine, but when I try to install the "libjavascript-perl_1.12-1_i386.deb" file, the Ubuntu Software center tells me "dependency is not satisfiable: perlapi-5.10.1" and will not install.  I have done this successfully with a 64bit version of MythBuntu (Which I ditched because of tuner card issues).

I am a complete newbie to Ubuntu and I don't know what this means and / or what to do about it.

Please Help
Thanks in advance.

---

### Post by klc5555 on 2011-10-22
> **MarsdeNation said:**
> Hi Everyone,

I am working on a new Installation of MythBuntu 11.10 32bit.

I am trying to follow the instructions to Install Shepherd for the TV Guide: [http://svn.whuffy.com/](http://svn.whuffy.com/)

I am up to the part where I am trying to install the Pearl Dependencies.

The "libmozjs0d_1.8.1.16+nobinonly-0ubuntu1_i386.deb" file installed fine, but when I try to install the "libjavascript-perl_1.12-1_i386.deb" file, the Ubuntu Software center tells me "dependency is not satisfiable: perlapi-5.10.1" and will not install.  I have done this successfully with a 64bit version of MythBuntu (Which I ditched because of tuner card issues).

I am a complete newbie to Ubuntu and I don't know what this means and / or what to do about it.

Please Help
Thanks in advance.

By way of full disclosure, I have never seen or used the utility "Shepherd". However ...

perlapi is provided in the package "perl-base", which in turn is a dependency of the package "perl". I think the current version of perlapi in Ubuntu 11.10 is 5.12.4

On the other hand, libmozjs0d_1.8.1.16 seems to be fairly ancient, since the package appears to have been discontinued after Ubuntu 8.04, at which point it was already at version 1.8.1.18

Accordingly, you would appear to have one of two problems. Either you do not have the package "perl-base" installed in your new Mythbuntu installation --Mythbuntu has historically been a bit iffy about installing all needed perl modules and such in the default install, so this is a possibility ; or, more likely, you do have the package "perl-base" installed, but the package libjavascript-perl_1.12-1_i386.deb may be fussy in that it may really require exactly perlapi 5.10.1 (or so) and may in fact be incompatible with perlapi version 5.12.4 as contained in Ubuntu 11.10.

You can check in any of your package managers (like synaptic) to see whether perl-base is installed. If it isn't, install it. 

If perl-base with perlapi 5.12.4 is already installed, but turns out to be incompatible with your older package libjavascript-perl, then you may need to decide how to proceed. perlapi version 5.10.1 is included in all versions of Mythbuntu from pre-8.04 to 11.04 --you may need to back down a Mythbuntu version, to say 11.04. At least until Shepherd coding catches up with Ubuntu. Or try backleveling the Perl installation to the 11.04 level within the 11.10 install, but that wouldn't necessarily be something for a "complete newbie to Ubuntu" to try: cascading "Dependency Hell" in Ubuntu is a significant annoyance when it happens, and support people get cranky if an installation has been hybridized. 

Beyond this, you may need to contact the Shepherd folk, since they seem to be all set up for proper support.

---

### Post by Onthax on 2011-11-01
I'm also having this issue


OP, did you have any luck resolving this?

---

### Post by klc5555 on 2011-11-02
> **Onthax said:**
> I'm also having this issue


OP, did you have any luck resolving this?

There's now (since 10/22) an open bug trac ticket on this problem with the Shepherd folks: [http://svn.whuffy.com/ticket/361](http://svn.whuffy.com/ticket/361)

Backleveling the Perl installation in Ubuntu 11.10 was tried by the person writing up the bug, but resulted in too much breakage from the usual .debfile "dependency hell".

So until the Shepherd folks code their way around this, your only Mythbuntu solution appears to be holding your installation at the Mythbuntu 11.04 level, which is the last that includes the older version of perlapi.

---

### Post by Kaibosh on 2011-11-06
In the same boat myself - and unfortunately know just enough linux to get myself in trouble :)

After some searching, and coming up with [http://groups.google.com/group/shepherd-list/browse_thread/thread/d02423673428f7e3?hl=en](http://groups.google.com/group/shepherd-list/browse_thread/thread/d02423673428f7e3?hl=en) (and then trying to make sense of it - failing quite miserably) I've spent the last few hours (I don't even want to know how many!) tapping away on virtual machines and then blowing them away when it invariably stuffs up..

I've ended up (borrowing VERY heavily from the link above - so thanks to the guys who posted their notes there) with a process that's both (relatively) easy and seems to have worked. Posting here in case it helps anyone else..

First up, see first line about the extent of my linux knowledge. This worked for me - for all I know it started some countdown inside my media centre pc that will start a fire and burn down my apartment..

I'm running 11.10 on i386, so these are the instructions for that.  If you're running on something else, peruse the above link and you should be able to work out what needs to be different.

* Install all other Shepherd/Perl pre-reqs, aside from libjavascript-perl 

* Download libmozjs2d_1.9.1.16-10_i386 and the associated dev package:
wget [http://ftp.us.debian.org/debian/pool/main/i/iceweasel/libmozjs2d_1.9.1.16-10_i386.deb](http://ftp.us.debian.org/debian/pool/main/i/iceweasel/libmozjs2d_1.9.1.16-10_i386.deb)
wget [http://ftp.us.debian.org/debian/pool/main/i/iceweasel/libmozjs-dev_1.9.1.16-10_i386.deb](http://ftp.us.debian.org/debian/pool/main/i/iceweasel/libmozjs-dev_1.9.1.16-10_i386.deb)

* Install each:
sudo dpkg -i libmozjs2d_1.9.1.16-10_i386.deb
sudo dpkg -i libmozjs-dev_1.9.1.16-10_i386.deb

* I got an error on the dev package that I needed libnspr4-dev. The first time I tried to install it I got another dependency error saying that I needed perlapi-5.10.1 (which is why we need to do this hoop jumping to get things installed) - A fresh install and several hours later there was no error when trying to install:
sudo apt-get install libnspr4-dev

* Download the source for libjavascript-perl:
wget [http://ftp.de.debian.org/debian/pool/main/libj/libjavascript-perl/libjavascript-perl_1.16-3.dsc](http://ftp.de.debian.org/debian/pool/main/libj/libjavascript-perl/libjavascript-perl_1.16-3.dsc)
wget [http://ftp.de.debian.org/debian/pool/main/libj/libjavascript-perl/libjavascript-perl_1.16.orig.tar.gz](http://ftp.de.debian.org/debian/pool/main/libj/libjavascript-perl/libjavascript-perl_1.16.orig.tar.gz)
wget [http://ftp.de.debian.org/debian/pool/main/libj/libjavascript-perl/libjavascript-perl_1.16-3.debian.tar.gz](http://ftp.de.debian.org/debian/pool/main/libj/libjavascript-perl/libjavascript-perl_1.16-3.debian.tar.gz)

* Create a folder and extract files into folder (debian file inside orig):
mkdir libjavascript-perl
cd libjavascript-perl
tar zxvf ../libjavascript-perl_1.16.orig.tar.gz
cd JavaScript-1.16
tar zxvf ../../libjavascript-perl_1.16-3.debian.tar.gz

* At some point around here, I previously got dependency errors on my tests, but not on my actual system so I can't document them exactly.  The package build-essentials is always one of the first things I install on a new system, so perhaps that's why.  If you get dependency errors at any point, install what you need via apt-get install.

* While in the same folder (libjavascript-perl/JavaScript-1.16), run Makefile script (I answered default to all questions):
perl Makefile.PL

* Compile:
make

* Install:
sudo make install


.. and that's it.  My subsequent installation of shepherd (via the downloaded shepherd perl script) went smoothly, and the "news" grabber downloaded and tested without incident - when previously it would error due to lack of JavaScript support.

Everything *seems* ok - time will tell..

---

