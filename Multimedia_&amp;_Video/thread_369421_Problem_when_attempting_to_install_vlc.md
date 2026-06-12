---
title: "Problem when attempting to install vlc"
date: 2007-02-24
forum: Multimedia &amp; Video
---

### Post by fredxor on 2007-02-24
When I try to install VLC, I am unable to. I have tried aptitude, apt-get, the add/remove programs manager and the synaptic package manager.

When I attempt to use aptitude, it says that it's installing a package of 0 bytes and then finishes, without installing the package. It gives me the following output:

> $ sudo aptitude install vlc
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  vlc 
The following NEW packages will be automatically installed:
  libdvbpsi3 libtar ttf-thryomanes videolan-doc wxvlc 
The following NEW packages will be installed:
  libdvbpsi3 libtar ttf-thryomanes videolan-doc wxvlc 
0 packages upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.3MB of archives. After unpacking 22.5MB will be used.
The following packages have unmet dependencies:
  vlc: Depends: libdbus-1-1 (>= 0.36.2) which is a virtual package.
       Depends: libgnutls11 (>= 1.0.16) which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
vlc [Not Installed]
wxvlc [Not Installed]

Score is 8

Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done


When I use apt-get, it gives the following output:

> $ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: libdbus-1-1 (>= 0.36.2) but it is not installable
       Depends: libgnutls11 (>= 1.0.16) but it is not installable
E: Broken packages

The add/remove programs manager tells me this:
> Cannot install 'vlc'

This application conflicts with other installed software. To install 'vlc' the conflicting software must be removed before.

Switch to the advanced mode to resolve this conflict.

The spm tells me that there are unresolved dependancies:
> vlc:
 Depends: libdbus-1-1 (>=0.36.2) but it is not installable
 Depends: libgnutls11 (>=1.0.16) but it is not installable
 Depends: wxvlc but it is not going to be installed


Can anyone please help me install it?

Thankyou,
    Freddy

---

### Post by solar george on 2007-02-24
Make sure you have updated your package lists.

```
sudo apt-get update
```

---

### Post by fredxor on 2007-02-24
I just tried sudo apt-get update. Still doesn't work.

---

### Post by superm1 on 2007-02-24
> **fredxor said:**
> I just tried sudo apt-get update. Still doesn't work.
Sounds to me like you are either missing a universe/multiverse or have a third party repo messing you up.

---

### Post by fredxor on 2007-02-24
The only things I installed without the spm were downloaded from the ubuntu packages site. One of them was for using the divx codec in totem, and the other 15 (something around 15) were for mplayer and its dependencies (I didn't notice mplayer in the spm).

---

### Post by superm1 on 2007-02-24
> **fredxor said:**
> The only things I installed without the spm were downloaded from the ubuntu packages site. One of them was for using the divx codec in totem, and the other 15 (something around 15) were for mplayer and its dependencies (I didn't notice mplayer in the spm).
Just to make sure, can you post this:
```
apt-cache policy vlc
```

---

### Post by fredxor on 2007-02-24
Here's what I get:

> $ apt-cache policy vlc
vlc:
  Installed: (none)
  Candidate: 0.8.4-svn20050920-3+hal0ubuntu3
  Version table:
     0.8.4-svn20050920-3+hal0ubuntu3 0
        500 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/universe Packages


Thanks again for helping me!

---

### Post by solar george on 2007-02-25
Use synaptic to enable the universe repository.

---

### Post by fredxor on 2007-02-25
I enabled universe and multiverse in the spm. It works now. Thanks a lot for helping. I really appreciate it.

---

### Post by prothen on 2007-04-15
I have the same problems, and I do all steps, but I have problems.

prothen@prothen-desktop:~$ apt-cache policy vlc
vlc:
  Installed: (none)
  Candidate: 0.8.6-svn20061012.debian-1ubuntu1.1
  Version table:
     0.8.6-svn20061012.debian-1ubuntu1.1 0
        500 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
     0.8.6a-jb-videolan-1 0
        500 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) dapper/universe Packages
prothen@prothen-desktop:~$ 


When I try to install using terminal server the error is:
prothen@prothen-desktop:~$ sudo apt-get install vlc 
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 0.8.6-svn20061012.debian-1ubuntu1.1) but it is not going to be installed
       Depends: libiso9660-4 but it is not installable
       Depends: libtar but it is not installable
       Depends: libvcdinfo0 (> 0.7.23) but it is not installable
       Depends: libvlc0 (>= 0.8.6-svn20061012.debian) but it is not going to be installed
       Depends: libxosd2 (>= 2.2.13) but it is not installable
E: Broken packages
prothen@prothen-desktop:~$

---

### Post by superm1 on 2007-04-15
> **prothen said:**
> I have the same problems, and I do all steps, but I have problems.

prothen@prothen-desktop:~$ apt-cache policy vlc
vlc:
  Installed: (none)
  Candidate: 0.8.6-svn20061012.debian-1ubuntu1.1
  Version table:
     0.8.6-svn20061012.debian-1ubuntu1.1 0
        500 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
     0.8.6a-jb-videolan-1 0
        500 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) dapper/universe Packages
prothen@prothen-desktop:~$ 


When I try to install using terminal server the error is:
prothen@prothen-desktop:~$ sudo apt-get install vlc 
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 0.8.6-svn20061012.debian-1ubuntu1.1) but it is not going to be installed
       Depends: libiso9660-4 but it is not installable
       Depends: libtar but it is not installable
       Depends: libvcdinfo0 (> 0.7.23) but it is not installable
       Depends: libvlc0 (>= 0.8.6-svn20061012.debian) but it is not going to be installed
       Depends: libxosd2 (>= 2.2.13) but it is not installable
E: Broken packages
prothen@prothen-desktop:~$

Don't mix and match that third party repository.  Thats what is throwing you off.  remove it from /etc/apt/sources.list and you should be fine.

---

