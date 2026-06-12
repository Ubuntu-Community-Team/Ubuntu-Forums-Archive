---
title: "unable to install VLC"
date: 2010-05-08
forum: Multimedia Software
---

### Post by yawnmoth on 2010-05-08
I type in vlc in the command prompt and get the following back:

> The program 'vlc' is currently not installed.  You can install it by typing:
sudo apt-get install vlc-nox
You will have to enable the component called 'universe'
vlc: command not found

I type in "sudo apt-get install vlc-nox" and get the following:

> Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package vlc-nox
Maybe I'm getting the "Couldn't find package vlc-nox" because I've not enabled the 'universe' component.  How do I do that via the command line?

VLC's website discusses an alternative way to install VLC:

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

% sudo apt-get update
% sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc

Unfortunately, that doesn't work for me either.  When I try I get the following error:

> Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package vlc
Any ideas?

---

### Post by proggy on 2010-05-08
From the Vlc site [QUOTE][     [B]Lucid Lynx 10.04 LTS, Ubunty Karmic Koala 9.10 
Ubuntu Jaunty Jackalope 9.04[/B]

  **Graphical way**

 Open Synaptic (System -> Administration -> Synaptic Package  Manager). In Settings -> Repositories, make sure you have a "multiverse"  repository activated.
 Search for vlc and install it. You should also install  vlc-plugin-pulse, mozilla-plugin-vlc (and libdvdcss2).
 If you are interrested in streaming or transcoding, you should also  install libavcodec-extra-52.
 **Command line way**

 You need to check that a "multiverse" mirror is listed in your /etc/apt/sources.list.[INDENT] % sudo apt-get update
% sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc[/INDENT]/QUOTE]

---

### Post by th0mas on 2010-05-09
same problem here, it's been the same since at least 1 year actually. I found the workaround of installing the right packages from packages.ubuntu.com website, but I guess there is a better way to fix that.

My sources.list is :

```
deb http://ftp.free.org/mirrors/archive.ubuntu.com/ubuntu/ lucid-security main universe

deb http://ftp.free.org/mirrors/archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb http://ftp.free.org/mirrors/archive.ubuntu.com/ubuntu/ lucid-updates main restricted

##Universe

deb http://ftp.free.org/mirrors/archive.ubuntu.com/ubuntu/ lucid universe
deb http://ftp.free.org/mirrors/archive.ubuntu.com/ubuntu/ lucid-updates universe

## Multiverse

deb http://ftp.free.org/mirrors/archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://ftp.free.org/mirrors/archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Backports

deb http://ftp.free.org/mirrors/archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Canonical Partner Repository 

deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu hardy partner
deb http://ftp.free.org/mirrors/archive.ubuntu.com/ubuntu/ lucid-security restricted
deb http://ftp.free.org/mirrors/archive.ubuntu.com/ubuntu/ lucid-security multiverse

```

and I get this 

```
$ sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vlc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libvlc0 vlc-nox vlc-data libvlc2
E: Package vlc has no installation candidate

```

---

### Post by WinterRain on 2010-05-09
Install the medibuntu repos and try again.
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

---

### Post by th0mas on 2010-05-09
mmm, I tried this but I still get the same error :

```
E: Package vlc has no installation candidate
```

I also get "Candidate: (none)" here :
```

~$ sudo apt-cache policy vlc
vlc:
  Installed: (none)
  Candidate: (none)
  Package pin: (not found)
  Version table:
     1.0.6-1ubuntu1 990
        500 http://ftp.free.org/mirrors/archive.ubuntu.com/ubuntu/ lucid/universe Packages
     0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.3 990
        100 /var/lib/dpkg/status

```

---

### Post by mc4man on 2010-05-09
edit: was looking at wrong package list for that mirror - vlc is there in universe

---

### Post by th0mas on 2010-05-09
well, even with main ubuntu server selected, I still had 'vlc' not available. But I could install the amazing 'vlc-nox' though.

But I fixed the problem by browsing again Synaptic, noticing that an old by-hand installation was preventing from installing any version of vlc... I think I solved the problem by hitting "force version", and selecting lucid version.

---

### Post by proggy on 2010-05-09
Congratulations!

---

