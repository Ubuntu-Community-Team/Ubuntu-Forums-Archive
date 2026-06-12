---
title: "Is the package avidemux in multiverse repos? Not in mine's"
date: 2006-07-29
forum: Multimedia &amp; Video
---

### Post by dangerous666 on 2006-07-29
I tried to install avidemux throught apt, but there's not such package in my repos. I have searched about and everybody says that avidemux is in multiverse repository... But it's not. I have tried to install avidemux by downloading 3rd party packges (like the one in avidemux site, marillat, berlios, etc) without success because of lots of dependency problems... 

Can anybody helpme to install this video editor?

Thanks a lot.

My sources.list is as follows
```

# deb cdrom:[Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted 

# Line commented out by installer because it failed to verify:
deb http://br.archive.ubuntu.com/ubuntu/ dapper main restricted 
deb-src http://br.archive.ubuntu.com/ubuntu/ dapper main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb http://br.archive.ubuntu.com/ubuntu/ dapper-updates main restricted 
deb-src http://br.archive.ubuntu.com/ubuntu/ dapper-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://br.archive.ubuntu.com/ubuntu/ dapper universe 
deb-src http://br.archive.ubuntu.com/ubuntu/ dapper universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://br.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse  
deb-src http://br.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse  

deb http://security.ubuntu.com/ubuntu/ dapper-security main restricted  
deb-src http://security.ubuntu.com/ubuntu/ dapper-security main restricted  
deb http://security.ubuntu.com/ubuntu/ dapper-security universe  
deb-src http://security.ubuntu.com/ubuntu/ dapper-security universe  

#KDE 3.5.3
# deb http://kubuntu.org/packages/kde-353/ dapper main  

#amarok 1.4.1
# deb http://kubuntu.org/packages/amarok-141/ dapper main   

# Seveas' packages (packages, GPG key: 1135D466)
# deb http://mirror.ubuntulinux.nl/ dapper-seveas all  

# Seveas' packages (sources, GPG key: 1135D466)
# deb-src http://mirror.ubuntulinux.nl/ dapper-seveas all  

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
# deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main  

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
# deb-src ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main  

#Automatix
# deb http://www.beerorkid.com/automatix/apt/ dapper main 




```

---

