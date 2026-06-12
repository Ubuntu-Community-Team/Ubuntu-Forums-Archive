---
title: "Amarok will not play mp3 files"
date: 2009-05-15
forum: Multimedia Software
---

### Post by lsutiger on 2009-05-15
I installed 9.04 today. I installed amarok 2.0.2 from the package manager.

Wow, what a jump from 1.x of amarok! It's to minimalistic.
Anyhow, to my problem.

I can not get amarok to play any mp3 files. I can play mp3 files in totem. The configuration does not have a lot of the configuration items that 1.x did.

So...what should I do?

Thanx in advance!

---

### Post by mc4man on 2009-05-15
All amarok should need for mp3's is libxine1-ffmpeg installed.

If *it was already* then look in home folder (show hidden files) for .xine.
Open it, inside should be a file "catalog.cache", delete and then *restart* amarok and ck.

---

### Post by lsutiger on 2009-05-15
Thanx for the reply!

I really do not like the 2.0 version. 
I found [this post]("http://www.akemapa.com/2009/05/06/install-amarok-14-in-ubuntu-jaunty/comment-page-1/#comment-3282") on how to d/l 1.4 from the package manager.

I think that 1.4 is much better, but that is just one man's opinion.

Thanx again for your help!

---

### Post by mc4man on 2009-05-15
> I really do not like the 2.0 version.

While I only tried it on a live jaunty cd (use hardy) I 100% agree, if I used jaunty the first thing I'd do is install the amarok 14 package .

I'd use this ppa directly
[https://edge.launchpad.net/~bogdanb/+archive/ppa](https://edge.launchpad.net/~bogdanb/+archive/ppa)

---

### Post by mntokman on 2009-05-16
I am a newbie when it comes to coding and Kubuntu and I could not install the package needed for mp3 and mpeg files yet... I keep getting the following error. I installed 8.10 and then included some jaunty repisoteries and not sure what I should have in my source list to get the necessary packages without any problem for my system. 

```
mntokman@greenworld:~$ sudo apt-get install amarok                
Reading package lists... Done                                     
Building dependency tree                                          
Reading state information... Done                                 
The following extra packages will be installed:                   
  amarok-common libc6 libc6-dev libc6-i686 libexiv2-5 libgpod4-nogtk libloudmouth1-0 libqt4-assistant
  libqt4-core libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support 
  libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-test libqt4-webkit libqt4-xml          
  libqt4-xmlpatterns libqtcore4 libqtgui4 libsearchclient0 libsqlite3-0 libstreamanalyzer0 libstreams0
  libstrigihtmlgui0 libstrigiqtdbusclient0 qt4-qtconfig strigi-client strigi-daemon                   
Suggested packages:                                                                                   
  libqt4-sql-sqlite libqt4-sql-psql glibc-doc manpages-dev libqt4-dev strigi-plugins                  
The following NEW packages will be installed:                                                         
  amarok libexiv2-5 libgpod4-nogtk libloudmouth1-0                                                    
The following packages will be upgraded:                                                              
  amarok-common libc6 libc6-dev libc6-i686 libqt4-assistant libqt4-core libqt4-dbus libqt4-designer   
  libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql
  libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4             
  libsearchclient0 libsqlite3-0 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libstrigiqtdbusclient0
  qt4-qtconfig strigi-client strigi-daemon                                                             
31 upgraded, 4 newly installed, 0 to remove and 779 not upgraded.                                      
Need to get 11.2MB/36.1MB of archives.                                                                 
After this operation, 26.9MB of additional disk space will be used.                                    
Do you want to continue [Y/n]? y
Err http://ubuntu.cbn.net.id jaunty/main libsqlite3-0 3.6.10-1
  404 Not Found
Err http://ubuntu.cbn.net.id jaunty/main strigi-daemon 0.6.4-0ubuntu2
  404 Not Found
Err http://ubuntu.cbn.net.id jaunty/main strigi-client 0.6.4-0ubuntu2
  404 Not Found
Err http://ubuntu.cbn.net.id jaunty/main libstreamanalyzer0 0.6.4-0ubuntu2
  404 Not Found
Err http://ubuntu.cbn.net.id jaunty/main libstreams0 0.6.4-0ubuntu2
  404 Not Found
Err http://ubuntu.cbn.net.id jaunty/main libstrigiqtdbusclient0 0.6.4-0ubuntu2
  404 Not Found
Err http://ubuntu.cbn.net.id jaunty/main libexiv2-5 0.18-1
  404 Not Found
Get:1 http://ubuntu.cbn.net.id jaunty/main amarok 2:2.0.2mysql5.1.30-0ubuntu3 [9675kB]
Fetched 9675kB in 1min54s (84.8kB/s)
Failed to fetch http://ubuntu.cbn.net.id/Ubuntu/pool/main/s/sqlite3/libsqlite3-0_3.6.10-1_i386.deb  404 Not Found
Failed to fetch http://ubuntu.cbn.net.id/Ubuntu/pool/main/s/strigi/strigi-daemon_0.6.4-0ubuntu2_i386.deb  404 Not Found
Failed to fetch http://ubuntu.cbn.net.id/Ubuntu/pool/main/s/strigi/strigi-client_0.6.4-0ubuntu2_i386.deb  404 Not Found
Failed to fetch http://ubuntu.cbn.net.id/Ubuntu/pool/main/s/strigi/libstreamanalyzer0_0.6.4-0ubuntu2_i386.deb  404 Not Found
Failed to fetch http://ubuntu.cbn.net.id/Ubuntu/pool/main/s/strigi/libstreams0_0.6.4-0ubuntu2_i386.deb  404 Not Found
Failed to fetch http://ubuntu.cbn.net.id/Ubuntu/pool/main/s/strigi/libstrigiqtdbusclient0_0.6.4-0ubuntu2_i386.deb  404 Not Found
Failed to fetch http://ubuntu.cbn.net.id/Ubuntu/pool/main/e/exiv2/libexiv2-5_0.18-1_i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

---

### Post by mntokman on 2009-05-16
I just did full upgrade to 9.04 and my music plays just fine but I still want to know where I can find the list of main repositories for a new release.

---

### Post by bobe84 on 2009-05-28
@mc4man
Thank you, it helped i was puzzled for 2 days! :)

---

### Post by joserpena on 2009-06-05
Tnx, mc4man. The only thing I had to do was installing libxine1-ffmpeg. BTW, I did that using Synaptic Manager and chose libxine1-all-plugins.

---

