---
title: "Ubuntu 9.1 Server and Netatalk Issue"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by endlessracingz on 2010-02-26
So I have found plenty of how to's on installing netatalk onto ubuntu 9.1 however NONE of them have worked for me. There are several how to's in this forum which I couldn't not get to work for me and no one else seemed to have a similar problem. I replied to those threads with no answer. I also found how to's on the web such as [http://notepad.bobkmertz.com/2010/01/apple-time-machine-backups-to-ubuntu.html](http://notepad.bobkmertz.com/2010/01/apple-time-machine-backups-to-ubuntu.html)

However no matter how I try I always seem to run into an issue of dependencies and not being able to install any of them. 

For the above link after adding the repository to the source.list file I attempt to get netatalk via the command given
```
*sudo apt-get install netatalk*
```
however what I get afterwards is ```
$ sudo apt-get install netatalk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  fuppes: Depends: libavcodec1d (>= 0.cvs20070307) but it is not installable
          Depends: libavformat1d (>= 0.cvs20070307) but it is not installable
          Depends: libavutil1d (>= 0.cvs20070307) but it is not installable
          Depends: libgif4 (>= 4.1.6) but it is not going to be installed
          Depends: libjpeg62 but it is not going to be installed
          Depends: libmad0 (>= 0.15.1b) but it is not going to be installed
          Depends: libmagick++10 but it is not installable
          Depends: libmagick10 but it is not installable
          Depends: libogg0 but it is not going to be installed
          Depends: libpng12-0 (>= 1.2.13-4) but it is not going to be installed
          Depends: libraw1394-8 but it is not installable
          Depends: libsimage20 but it is not going to be installed
          Depends: libswscale1d (>= 0.cvs20070307) but it is not installable
          Depends: libtag1c2a (>= 1.4) but it is not going to be installed
          Depends: libtheora0 but it is not going to be installed
          Depends: libtiff4 but it is not going to be installed
          Depends: libvorbis0a (>= 1.2.0) but it is not going to be installed
          Depends: libvorbisenc2 (>= 1.1.2) but it is not going to be installed
          Depends: libvorbisfile3 (>= 1.2.0) but it is not going to be installed
  netatalk: Depends: libcrack2 (>= 2.8.12) but it is not going to be installed
            Depends: libdb4.8 but it is not going to be installed
            Recommends: rc but it is not going to be installed
            Recommends: db4.8-util but it is not going to be installed
            Recommends: cracklib-runtime but it is not going to be installed
            Recommends: libpam-cracklib but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
I have tried installing the dependencies it lists but get an error such as the following
```
$ sudo apt-get install libavcodec1d
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libavcodec1d is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libavcodec1d has no installation candidate

```

I am at a loss... can someone please shed some light on to what is going on?

---

### Post by dmovad on 2010-02-27
I have used the following on 8.10 with excellent results:

[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

Good luck...

---

### Post by endlessracingz on 2010-02-27
> **dmovad said:**
> I have used the following on 8.10 with excellent results:

[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

Good luck...

I have also tried following those instructions before but I run into the following

```
$ sudo apt-get build-dep netatalk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libcupsys2-dev is a virtual package provided by:
  libcups2-dev 1.4.2-9+b1
You should explicitly select one to install.
E: Package libcupsys2-dev has no installation candidate
E: Failed to satisfy Build-Depends dependency for netatalk: libcupsys2-dev

```
Because of this I try to install libcupsys2-dev
```

$ sudo apt-get install libcupsys2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libcupsys2-dev is a virtual package provided by:
  libcups2-dev 1.4.2-9+b1
You should explicitly select one to install.
E: Package libcupsys2-dev has no installation candidate

```
and I fail with no luck. In the comments it says to> For those that are getting the “libcups2-dev” error. (“E: Package libcupsys2-dev has no installation candidate
E: Failed to satisfy Build-Depends dependency for netatalk: libcupsys2-dev”)
 Solution: Open up Preferences > Admin > Synaptic Package Manager. Search for “libcups2-dev” and install it. Retry the steps above. 
 Worked for me, hope it works for you!


However, I am using ubuntu server and have no GUI and therefore cannot follow those instructions. From my understanding the above code that I used to try and find libcupsys2-dev is the correct way.

---

### Post by endlessracingz on 2010-02-27
using the ```
sudo aptitude install netatalk
``` command found several issues in my server that it suggest corrections too. Going through the list i chose to correct them all and everything work after that...

Why do people use ```
apt-get
``` if ```
aptitude
``` is so much more powerful? or am I missing something?

---

### Post by capscrew on 2010-02-27
> **endlessracingz said:**
> using the ```
sudo aptitude install netatalk
``` command found several issues in my server that it suggest corrections too. Going through the list i chose to correct them all and everything work after that...

Why do people use ```
apt-get
``` if ```
aptitude
``` is so much more powerful? or am I missing something?

They achieve the same thing.  Both are front ends (along with the GUI synaptics) the the primative ***apt ***.  See [**[COLOR="Navy"]_here _[/COLOR]**]("http://www.linuxquestions.org/questions/debian-26/apt-get-vs.-aptitude-363365/").

---

