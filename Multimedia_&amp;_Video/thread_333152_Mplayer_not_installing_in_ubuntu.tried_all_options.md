---
title: "Mplayer not installing in ubuntu.tried all options"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by sankarnkp on 2007-01-07
Friends,
I installed ubuntu breezy from CD in my dell inspiron 1100. Immediately after installing, I upgraded the distro using apt-get dist-upgrade in following sequence:
Breezy-->Dapper-->edgy. Upgrade went fine and so I thought I will go ahead and install all packages. while installing mplayer using apt-get this is the error I get: I tried all different options and read through different forums but did not make any progress:

sankar@sankarlaptop:~$ sudo apt-get install mplayer
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
mplayer: Depends: libartsc0 (>= 1.5.0-1) but 1.4.3-0ubuntu1 is to be installed
Depends: libasound2 (> 1.0.11) but 1.0.9-2 is to be installed
Depends: libatk1.0-0 (>= 1.12.1) but 1.10.3-0ubuntu2 is to be install ed
Depends: libc6 (>= 2.4-1) but 2.3.5-1ubuntu12 is to be installed
Depends: libcairo2 (>= 1.2.4) but 1.0.2-0ubuntu1.1 is to be installed
Depends: libdvdread3 (>= 0.9.6) but 0.9.4-5 is to be installed
Depends: libfaac0 (>= 1.24clean) but it is not going to be installed
Depends: libfreetype6 (>= 2.2) but 2.1.10-1ubuntu2.2 is to be install ed
Depends: libfribidi0 (>= 0.10.7) but 0.10.5-2 is to be installed
Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.1-4ubuntu9 is to be instal led
Depends: libggi2 (>= 1:2.2.1) but it is not going to be installed
Depends: libglib2.0-0 (>= 2.12.0) but 2.8.3-0ubuntu1 is to be install ed 	
Depends: libgtk2.0-0 (>= 2.10.3) but 2.8.6-0ubuntu2.1 is to be instal led
Depends: libmp4v2-0 (>= 2.0.0+cvs20040908+mp4v2+bmp) but it is not go ing to be installed
Depends: libogg0 (>= 1.1.3) but 1.1.2-1 is to be installed
Depends: libpango1.0-0 (>= 1.14.5) but 1.10.1-0ubuntu1 is to be insta lled
Depends: libsdl1.2debian (>= 1.2.10-1) but 1.2.7+1.2.8cvs20041007-5.3 ubuntu2 is to be installed

Any help in how to solve the issue is appreciated.

Thanks guys
Sankar

---

### Post by pay on 2007-01-07
Using apt-get to upgrade versions can cause problems with dependencies. i would reccomend upgrading with aptitude or doing a clean installation. Try```
sudo aptitude dist-upgrade
```If that doesn't work try compilling mplayer from source.

---

### Post by Canis familiaris on 2007-01-07
Install Mplayer from Automatix. For info of installing Automatix2, [refer to this thread]("http://ubuntuforums.org/showpost.php?p=1953858&postcount=2").

---

### Post by Gremlinzzz on 2007-01-07
I don't have a clue about the package deal with brezzy,I would do a fresh install using edgy cd .     [http://distrowatch.com/?newsid=03804#0](http://distrowatch.com/?newsid=03804#0)

---

### Post by dmizer on 2007-01-07
yeah ... i'd say you have quite a few things working against you here.  first of all the dist-upgrade from dapper to edgy is less than workable for more than just a few people.  if you want to use edgy, your best bet is simply to do a fresh install of edgy.  breezy to dapper went okay for me, but it didn't for everyone.  but instantly going from breezy to dapper and to edgy is probably the root of your problem.

is there any particular reason why you didn't make your own edgy install cd?

ps.  don't use automatix.  i sincerely feel that there are far better ways of doing things.

---

### Post by arnieboy on 2007-01-07
> **dmizer said:**
> there are far better ways of doing things than relying on a closed source script.
Automatix is GPL-ed and open source. What are you talking about?

---

### Post by dmizer on 2007-01-07
my mistake.  humble apologies.

---

