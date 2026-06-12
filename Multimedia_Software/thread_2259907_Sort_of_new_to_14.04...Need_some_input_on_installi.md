---
title: "Sort of new to 14.04...Need some input on installing packages."
date: 2015-01-07
forum: Multimedia Software
---

### Post by 77_GCSX on 2015-01-07
Been with Windows since 3.1 - Now I'm with Linux (Ubuntu 14.04). Excellent choice!!

Now, I have a fresh install and after doing some "Things to do after installing Ubuntu" I'm have some issues installing VLC and DVD Styler.

I receive the following when trying to install these from the Software Center:

VLC:

   vlc: Depends: vlc-nox (= 1:2.0.6-dmo2) but 1:2.0.6-dmo2 is to be installed  
      Depends: libavcodec54 (>= 8:1.0.0) but 8:1.0.10-dmo1 is to be installed  
      Depends: libavutil51 (>= 8:1.0.0) but 8:1.0.10-dmo1 is to be installed  
      Depends: libgcc1 (>= 1:4.1.1) but 1:4.9.1-0ubuntu1 is to be installed  
      Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is to be installed  
      Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is to be installed


DVD Styler:

 dvdstyler: Depends: dvdstyler-data (= 2.5.2-0ubuntu3) but 2.5.2-0ubuntu3 is to be installed  
             Depends: libavcodec-extra-54 (>= 6:9.10) but 7:1.2.6-1~trusty1 is to be installed  
             Depends: libavformat54 (>= 6:9.1-1) but 8:1.0.10-dmo1 is to be installed  
             Depends: libavutil52 (>= 6:9.1-1) but 7:1.2.6-1~trusty1 is to be installed  
             Depends: libc6 (>= 2.14) but 2.19-0ubuntu6.4 is to be installed  
             Depends: libfontconfig1 (>= 2.9.0) but 2.11.0-0ubuntu4.1 is to be installed  
             Depends: libgcc1 (>= 1:4.1.1) but 1:4.9.1-0ubuntu1 is to be installed  
             Depends: libjpeg8 (>= 8c) but 8c-2ubuntu8 is to be installed  
             Depends: libstdc++6 (>= 4.1.1) but 4.8.2-19ubuntu1 is to be installed  
             Depends: libswscale2 (>= 6:9.1-1) but 8:1.0.10-dmo1 is to be installed  
             Depends: libwxbase2.8-0 (>= 2.8.12.1) but 2.8.12.1+dfsg-2ubuntu2 is to be installed  
             Depends: libwxgtk-media2.8-0 (>= 2.8.12.1) but 2.8.12.1+dfsg-2ubuntu2 is to be installed  
             Depends: libwxgtk2.8-0 (>= 2.8.12.1) but 2.8.12.1+dfsg-2ubuntu2 is to be installed  


I've been at this - trying to fix it on my own for about a day and a half but with no luck. I'm still sort of new to Ubuntu but I am a computer person so I can understand some if not most commands.

Thanks in advance!
Paul

---

### Post by kerry_s on 2015-01-07
go into the terminal and type:

**sudo apt-get -f install**

it will try to resovle the dependency problem, if it can't it will remove so your systems not stuck.

---

### Post by 77_GCSX on 2015-01-07
> **kerry_s said:**
> go into the terminal and type:

**sudo apt-get -f install**

it will try to resovle the dependency problem, if it can't it will remove so your systems not stuck.

I just tried it with these results:

paul1@merklefamhomepc1:~$ sudo apt-get -f install
[sudo] password for paul1:
Reading package lists... Done
Building dependency tree      
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ciso faac libaacs0 libbluray1 libmp4v2-2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.

So, I tried the auto remove and came up with this:

paul1@merklefamhomepc1:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree      
Reading state information... Done
The following packages will be REMOVED:
  ciso faac libaacs0 libbluray1 libmp4v2-2
0 upgraded, 0 newly installed, 5 to remove and 6 not upgraded.
After this operation, 1,629 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 213813 files and directories currently installed.)
Removing ciso (1.0.0-0ubuntu2) ...
Removing faac (1:1.28-dmo3) ...
Removing libaacs0:amd64 (0.7.0-1) ...
Removing libbluray1:amd64 (1:0.5.0-1) ...
Removing libmp4v2-2:amd64 (2:2.0.0-dmo2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.4) ...
paul1@merklefamhomepc1:~$

I then exited Terminal and tried to install VLC first but received the same error msg which opens up a msg window titled:

"Package dependencies cannot be resolved"

(I have screen shots but I'm still trying to share them)

---

### Post by kerry_s on 2015-01-07
you should make sure all your sources are checked.
search dash for sources, it should show the program. i think you can also get to it from the update manager.
sorry i'm on a different system so i don't know the exact name.

if you go advanced you can attach screenshots.

---

### Post by 77_GCSX on 2015-01-07
> **kerry_s said:**
> you should make sure all your sources are checked.
search dash for sources, it should show the program. i think you can also get to it from the update manager.
sorry i'm on a different system so i don't know the exact name.

if you go advanced you can attach screenshots.

Thanks for the tip on the pics...Here are mine:


[ATTACH=CONFIG]259096[/ATTACH][ATTACH=CONFIG]259097[/ATTACH]

---

### Post by kerry_s on 2015-01-08
it looks like software-center is crashing to me.
try to install in terminal:

**sudo apt-get install vlc dvdstyler**

---

### Post by 77_GCSX on 2015-01-08
> **kerry_s said:**
> it looks like software-center is crashing to me.
try to install in terminal:

**sudo apt-get install vlc dvdstyler**

Tried with no luck. Here is the output:

paul1@merklefamhomepc1:~$ sudo apt-get install vlc dvdstyler
[sudo] password for paul1:
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
 
The following packages have unmet dependencies:
 vlc : Depends: vlc-nox (= 1:2.0.6-dmo2) but it is not going to be installed
       Recommends: vlc-plugin-notify (= 1:2.0.6-dmo2) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 1:2.0.6-dmo2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by kerry_s on 2015-01-08
do the :
**sudo apt-get -f install**

to fix the broken packages.
did you make sure all your sources are checked and you did :

**sudo apt-get update**

---

### Post by kerry_s on 2015-01-08
i'm going to be away a bit, hang in there i'll be right back. i'm booting into a os i want to try.

---

### Post by 77_GCSX on 2015-01-08
> **kerry_s said:**
> do the :
**sudo apt-get -f install**

to fix the broken packages.
did you make sure all your sources are checked and you did :

**sudo apt-get update**

I tried the -f install earlier on (up top of this post)..

Double checked the sources....

Just did the apt-get update....Would you like the output from that? There are several "not normal" msgs in it..mostly 404 not found types but a couple I am unsure of. Ah, what the heck, Here is the output from the latest apt-get update - WARNING - It's LONG!

```
paul1@merklefamhomepc1:~$ sudo apt*get update

[sudo] password for paul1:

Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty*security InRelease

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease

Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease

Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty*security Release.gpg [933 B]

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*updates InRelease

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease

Hit [http://shell.ninthgate.se](http://shell.ninthgate.se) wheezy InRelease

Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty*security Release [62.0 kB]

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*backports InRelease

Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease

Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease

Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*updates Release.gpg [933 B]

Hit [http://archive.getdeb.net](http://archive.getdeb.net) trusty*getdeb InRelease

Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg

Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release

Hit [http://www.deb*multimedia.org](http://www.deb*multimedia.org) wheezy InRelease

Hit [http://shell.ninthgate.se](http://shell.ninthgate.se) wheezy/main amd64 Packages

Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty*security/main Sources [59.3 kB]

Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*backports Release.gpg [933 B]

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release

Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty*security/restricted Sources [2,061 B]

Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release

Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources

Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*updates Release [62.0 kB]

Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty*security/universe Sources [17.4 kB]

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease

Hit [http://shell.ninthgate.se](http://shell.ninthgate.se) wheezy/main i386 Packages

Hit [http://archive.getdeb.net](http://archive.getdeb.net) trusty*getdeb/apps amd64 Packages

Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty*security/multiverse Sources [719 B]

Hit [http://www.deb*multimedia.org](http://www.deb*multimedia.org) wheezy/main amd64 Packages

Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages

Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources

Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty*security/main amd64 Packages [187 kB]

Hit [http://archive.getdeb.net](http://archive.getdeb.net) trusty*getdeb/games amd64 Packages

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease

Hit [http://www.deb*multimedia.org](http://www.deb*multimedia.org) wheezy/non*free amd64 Packages

Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages

Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*backports Release [62.0 kB]

Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages

Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty*security/restricted amd64 Packages [8,875 B]

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease

Hit [http://archive.getdeb.net](http://archive.getdeb.net) trusty*getdeb/apps i386 Packages

Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty*security/universe amd64 Packages [82.2 kB]

Hit [http://www.deb*multimedia.org](http://www.deb*multimedia.org) wheezy/main i386 Packages

Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages

Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty*security/multiverse amd64 Packages [1,157 B]

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease

Hit [http://archive.getdeb.net](http://archive.getdeb.net) trusty*getdeb/games i386 Packages

Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty*security/main i386 Packages [178 kB]

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources

Hit [http://www.deb*multimedia.org](http://www.deb*multimedia.org) wheezy/non*free i386 Packages

Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) trusty*security/restricted i386 Packages [8,846 B]

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease

Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) trusty*security/universe i386 Packages [82.2 kB]

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources

Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation*en

Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) trusty*security/multiverse i386 Packages [1,409 B]

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease

Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty*security/main Translation*en

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages

Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty*security/multiverse Translation*en

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg

Ign [http://download.videolan.org](http://download.videolan.org) InRelease

Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty*security/restricted Translation*en

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg

Hit [http://download.videolan.org](http://download.videolan.org) Release.gpg

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages

Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty*security/universe Translation*en

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg

Hit [http://download.videolan.org](http://download.videolan.org) Release

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg

Hit [http://download.videolan.org](http://download.videolan.org) Sources

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation*en

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg

Hit [http://download.videolan.org](http://download.videolan.org) Packages

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation*en

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation*en

Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation*en_US

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg

Ign [http://shell.ninthgate.se](http://shell.ninthgate.se) wheezy/main Translation*en_US

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation*en

Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation*en

Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*updates/main Sources [152 kB]

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg

Ign [http://shell.ninthgate.se](http://shell.ninthgate.se) wheezy/main Translation*en

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release

Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*updates/restricted Sources [2,061 B]

Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*updates/universe Sources [96.5 kB]

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release

Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*updates/multiverse Sources [3,543 B]

Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*updates/main amd64 Packages [392 kB]

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release

Ign [http://download.videolan.org](http://download.videolan.org) Translation*en_US

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release

Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*updates/restricted amd64 Packages [8,875 B]

Ign [http://download.videolan.org](http://download.videolan.org) Translation*en

Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*updates/universe amd64 Packages [236 kB]

Ign [http://www.deb*multimedia.org](http://www.deb*multimedia.org) wheezy/main Translation*en_US

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release

Ign [http://www.deb*multimedia.org](http://www.deb*multimedia.org) wheezy/main Translation*en

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release

Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*updates/multiverse amd64 Packages [9,370 B]

Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*updates/main i386 Packages [384 kB]

Ign [http://archive.getdeb.net](http://archive.getdeb.net) trusty*getdeb/apps Translation*en_US

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release

Ign [http://www.deb*multimedia.org](http://www.deb*multimedia.org) wheezy/non*free Translation*en_US

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release

Ign [http://archive.getdeb.net](http://archive.getdeb.net) trusty*getdeb/apps Translation*en

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages

Ign [http://www.deb*multimedia.org](http://www.deb*multimedia.org) wheezy/non*free Translation*en

Ign [http://archive.getdeb.net](http://archive.getdeb.net) trusty*getdeb/games Translation*en_US

Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*updates/restricted i386 Packages [8,846 B]

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages

Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*updates/universe i386 Packages [237 kB]

Ign [http://archive.getdeb.net](http://archive.getdeb.net) trusty*getdeb/games Translation*en

Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*updates/multiverse i386 Packages [9,553 B]

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*updates/main Translation*en

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*updates/multiverse Translation*en

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*updates/restricted Translation*en

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*updates/universe Translation*en

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages

Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*backports/main Sources [4,451 B]

Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*backports/restricted Sources [28 B]

Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*backports/universe Sources [19.6 kB]

Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*backports/multiverse Sources [1,898 B]

Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*backports/main amd64 Packages [5,165 B]

Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*backports/restricted amd64 Packages [28 B]

Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*backports/universe amd64 Packages [23.9 kB]

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages

Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*backports/multiverse amd64 Packages [1,245 B]

Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*backports/main i386 Packages [5,176 B]

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages

Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*backports/restricted i386 Packages [28 B]

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation*en

Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*backports/universe i386 Packages [24.0 kB]

Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*backports/multiverse i386 Packages [1,249 B]

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*backports/main Translation*en

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*backports/multiverse Translation*en

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*backports/restricted Translation*en

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty*backports/universe Translation*en

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation*en

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation*en_US

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation*en_US

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation*en_US

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation*en_US

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation*en

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation*en

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation*en

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation*en_US

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation*en

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation*en_US

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation*en

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages

404 Not Found

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages

404 Not Found

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation*en_US

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation*en

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation*en_US

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation*en

Fetched 2,443 kB in 12s (196 kB/s)

W: Failed to fetch [http://ppa.launchpad.net/stedy6/stedy*minidna/ubuntu/dists/trusty/main/binary-](http://ppa.launchpad.net/stedy6/stedy*minidna/ubuntu/dists/trusty/main/binary-)
amd64/Packages 404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/stedy6/stedy*minidna/ubuntu/dists/trusty/main/binary-](http://ppa.launchpad.net/stedy6/stedy*minidna/ubuntu/dists/trusty/main/binary-)
i386/Packages 404 Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

paul1@merklefamhomepc1:~$
```

---

### Post by 77_GCSX on 2015-01-08
Just an FYI - I'm at work remotely doing all of this....Hence the screen prints and the way they looked.

I appreciate the help too!

Question: I searched for this "type" of problem on Google. Could a remove and reinstall of the Software Center be helpful?

---

### Post by kerry_s on 2015-01-08
what hell,is this a distribution upgrade or a fresh install? cause your sources list is all mixed up, you have both wheezy & trusty repos.

i would try an complete it:

**sudo apt-get dist-upgrade**

---

### Post by kerry_s on 2015-01-08
> **77_GCXS said:**
> Just an FYI - I'm at work remotely doing all of this....Hence the screen prints and the way they looked.

I appreciate the help too!

Question: I searched for this "type" of problem on Google. Could a remove and reinstall of the Software Center be helpful?

no
your sources for software is messed up

---

### Post by 77_GCSX on 2015-01-08
> **kerry_s said:**
> what hell,is this a distribution upgrade or a fresh install? cause your sources list is all mixed up, you have both wheezy & trusty repos.

i would try an complete it:

**sudo apt-get dist-upgrade**

Fresh install...My bad on messing things up. It's a guy thing...It's like getting lost and waiting forever to ask for directions....Working on doing the dist-upgrade...posting soon!

---

### Post by 77_GCSX on 2015-01-08
Crap! Same thing....Package dependencies blah blah as before.

---

### Post by 77_GCSX on 2015-01-08
Right now I got VLC installed!!!!!!!!!!!

It's working on DVDStyler........Hang on!!!

---

### Post by 77_GCSX on 2015-01-08
When you mentioned that "Wheezy" name it got me thinking...So I went back to the sources and UNCHECKED the minidlna and wheezy lines, updated the list and TADA!!!! Everything works now.


So, who or WHAT is this "Wheezy" and why did it possibly mess things up for me?


And after the answer, a Kudo's to YOU for helping me!!:p

---

### Post by kerry_s on 2015-01-08
wheezy is before trusty, you can remove those lines/sources.

---

### Post by kerry_s on 2015-01-08
glad you got it working!

---

