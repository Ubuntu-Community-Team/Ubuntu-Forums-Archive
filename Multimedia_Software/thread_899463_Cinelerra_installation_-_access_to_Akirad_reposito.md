---
title: "Cinelerra installation - access to Akirad repository"
date: 2008-08-24
forum: Multimedia Software
---

### Post by Teddix2 on 2008-08-24
Hi,

having installed Cinelerra CV successfully on my desktop, I want it now on my laptop, using Ubuntu 8.04, 64 bit. All ways lead apparently to the Akirad repository, either direct or via get cinelerra on cinelerra.org. This is, however, what I get when reloading the synaptic package manager:

Failed to fetch [http://akirad.hfbk.net/dists/akirad-hardy/main/binary-amd64/Packages.gz](http://akirad.hfbk.net/dists/akirad-hardy/main/binary-amd64/Packages.gz)  504 Gateway Timeout
Failed to fetch [http://akirad.hfbk.net/dists/akirad-hardy/main/source/Sources.gz](http://akirad.hfbk.net/dists/akirad-hardy/main/source/Sources.gz) 504 Gateway Timeout
Some index files failed to download, they have been ignored, or old ones used instead.

The same happens when using the terminal. When downloading from [http://akirad.cinelerra.org/](http://akirad.cinelerra.org/)

the Package Installer replies:

Package: cinelerra-k8 (or whatever else)

Error: Dependency is not satisfiable: akiradnews


What's wrong? Any help will be greatly appreciated. Thank you all.

---

### Post by akir4d on 2008-08-25
Problem on install package that redirect to secondary mirror, re-download and install again.

Byez

Paolo Rampino aka Akirad

---

### Post by Teddix2 on 2008-08-26
Hello,

I'm sorry, but the problem persists. When trying to install addakirad.deb, the installation first goes well, but when reloading in synaptic package manager this happens:

Failed to fetch [http://akirad.cinelerra.org/dists/akirad-hardy/main/binary-amd64/Packages.bz2](http://akirad.cinelerra.org/dists/akirad-hardy/main/binary-amd64/Packages.bz2)  Hash Sum mismatch

When downloading fom
[http://akirad.cinelerra.org/pool/main-hardy/](http://akirad.cinelerra.org/pool/main-hardy/)
the installation file is downloaded, but the installer still displays:
Error: Dependency is not satisfiable: akiradnews

Trying the terminal with the commands given in the "black box" on the akirad repository site, this is the result:

me@my-laptop:~$ sudo wget [http://akirad.cinelerra.org/dists/hardy.list](http://akirad.cinelerra.org/dists/hardy.list) -O /etc/apt/sources.list.d/akirad.list
--15:36:03--  [http://akirad.cinelerra.org/dists/hardy.list](http://akirad.cinelerra.org/dists/hardy.list)
           => `/etc/apt/sources.list.d/akirad.list'
Resolving akirad.cinelerra.org... 78.47.64.243
Connecting to akirad.cinelerra.org|78.47.64.243|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 441 [text/plain]

100%[====================================>] 441           --.--K/s             

15:36:03 (84.81 MB/s) - `/etc/apt/sources.list.d/akirad.list' saved [441/441]

me@my-laptop:~$ wget -q [http://akirad.cinelerra.org/dists/akirad.key](http://akirad.cinelerra.org/dists/akirad.key) -O- | sudo apt-key add - && sudo apt-get update
OK
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy Release.gpg                  
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/main Translation-en_ZA        
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/restricted Translation-en_ZA  
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/universe Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/multiverse Translation-en_ZA
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/main Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/universe Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/multiverse Translation-en_ZA
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy Release                       
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates Release                         
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/main Packages                           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/restricted Packages           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/main Sources                  
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/restricted Sources            
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/universe Packages             
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/universe Sources              
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/multiverse Packages           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/multiverse Sources            
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/main Packages         
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/restricted Packages   
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/main Sources          
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/restricted Sources    
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/universe Packages     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/universe Sources      
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/multiverse Packages   
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/multiverse Sources    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_ZA 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_ZA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_ZA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_ZA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Ign [http://akirad.hfbk.net](http://akirad.hfbk.net) akirad-hardy Release.gpg
Ign [http://akirad.hfbk.net](http://akirad.hfbk.net) akirad-hardy/main Translation-en_ZA
Ign [http://akirad.hfbk.net](http://akirad.hfbk.net) akirad-hardy Release
Ign [http://akirad.hfbk.net](http://akirad.hfbk.net) akirad-hardy/main Packages
Err [http://akirad.hfbk.net](http://akirad.hfbk.net) akirad-hardy/main Packages
  504 Gateway Timeout
W: Failed to fetch [http://akirad.hfbk.net/dists/akirad-hardy/main/binary-amd64/Packages.gz](http://akirad.hfbk.net/dists/akirad-hardy/main/binary-amd64/Packages.gz)  504 Gateway Timeout

E: Some index files failed to download, they have been ignored, or old ones used instead.
me@my-laptop:~$ 

For information, I am using Ubuntu 8.04 (hardy), Gnome 2.22.3, Kernel 2.6.24-19-generic (#1 SMP Fri Jul 11 21:01:46 UTC 2008), Processor Intel(R) Core(TM)2 Duo CPU T8300  @ 2.40GHz.

Really would like to access the repository, install Cinelerra and get updates, when available.

A big cheers and thank you very much for every help.

---

### Post by akir4d on 2008-08-30
Try again with addakirad, I would thank you for bugs report... in this way I discovered that hardy.list and gutsy.list pointed to mirror 2 that in this moment is down due hardware failure.

byez

Paolo

---

### Post by Teddix2 on 2008-09-01
Dear Paolo, 
thank you very much for all your effort and support. At last I could install Cinelerra, although it came with some kind of twist in the tail. After first installing the akirad repository
(akirad-keyring and mirrors 2008.08.30 and akiradnews 20080818),
reloading in Synaptic Package Manager and finally installing using the manager, the result was always (and still is) the same; never mind using the GUI method or the terminal commandline method:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://akirad.cinelerra.org/dists/akirad-hardy/main/binary-amd64/Packages.bz2](http://akirad.cinelerra.org/dists/akirad-hardy/main/binary-amd64/Packages.bz2)  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.

The following finally led to success:

1. Downloaded cinelerra-generic_2.1.0-1svn20080826akirad1_amd64.deb
from mirror 1, opend with GDebi Package installer. Result:
Installer complaints: 
Dependency is not satisfiable: libmpeg3hv-generic.

2. Installed libmpeg3hv-generic from mirror 1 - success - repeat installation of
cinelerra-generic_2.1.0-1svn20080826akirad1_amd64.deb. Result:
Installer complaints: 
Dependency is not satisfiable: libquicktimehv-generic_2.1.0-1svn20080826akirad1_amd64db.
3. ...
4. ...
5. ... to cut a long story short, two more such incidents occurred, in the course of which
libguicast-k8_2.1.0-1svn20080826akirad1_amd64db and
libguicast-generic had to be installed from mirror 1 in the same manner.

After the last lib... was installed, installation of cinelerra-generic_2.1.0-1svn20080826akirad1_amd64.deb
was finalmente successful, again using GDebi Package installer.

So currently there seems to be no highway to cinelerra (at least to cinelerra CV), but there is always the old footpath over the mountain range. An attempt in-between to use cinelerra4-repack_20080819_amd64.deb, as well straight away from mirror 1 was not too successful. The package installed immediately, but the software was not readily usable; loaded videoclips behaved very stubbornly and were hardly to control, i.e. even the simplemost start/stop commands were outright ignored.

Cinelerra-generic now seems to work on my machine, but I have to figure out some preferences and set-ups yet. I am for instance not in a position to re-size the preferences window and can reach the "ok", "apply" etc buttons only after closing the upper and lower panels on my screen.

Keep it up ...
ciao,
Uwe

---

### Post by akir4d on 2008-09-02
I'm afraid for you, be sure that your /etc/resolv.conf use valid dns and/or your proxy ( if you have ) works right, after try:

sudo apt-get clean && sudo apt-get update

and fill free to send me to private email (akir4d on gmail) the output of:

sudo apt-conf dump

byez

Paolo

---

### Post by miraazja on 2010-04-02
Hi folks!

check for instructions [http://cvs.cinelerra.org/getting_cinelerra.php](http://cvs.cinelerra.org/getting_cinelerra.php)

Acually there I found solution.

---

