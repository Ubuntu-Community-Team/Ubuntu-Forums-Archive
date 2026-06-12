---
title: "Installing XBMC fails in 9.10 Karmic"
date: 2010-08-14
forum: Multimedia Software
---

### Post by kevinhorsey on 2010-08-14
Hi,

I'm fairly new to Ubuntu, but worked with Oracle/Unix in support/development for many years so I'm not a complete novice!

I'm trying to install XBMC in a new installation of Ubuntu 9.10 on my ASRock ION330HT

I've followed the XBMC install instructions in: 
[http://wiki.xbmc.org/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step](http://wiki.xbmc.org/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step)
[FONT=monospace]
[/FONT]sudo apt-get install python-software-properties pkg-config[FONT=monospace]
[/FONT]sudo add-apt-repository ppa:team-xbmc[FONT=monospace]
[/FONT]sudo apt-get update[FONT=monospace]
[/FONT]sudo apt-get install xbmc xbmc-standalone[FONT=monospace]
[/FONT]sudo apt-get update

I get the following after sudo apt-get update

ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Translation-en_US
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) kermic Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) kermic Release    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_US 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) kermic/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) kermic/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Sources
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) kermic/main Sources
  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/kermic/main/source/Sources.gz](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/kermic/main/source/Sources.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
ubuntu@ubuntu:~$sudo apt-get install xbmc xbmc-standalone
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xbmc
ubuntu@ubuntu:~$ 

The same thing happened when I tried to install XBMC on 10.04. I've searched the forum and tried all the suggested solutions, but I still get the same errors which is why I've reverted to a clean 9.10 installation which gives the errors above.

Does anyone know how to fix this, or a workaround?

Thanks,
Kevin

---

### Post by ssplayer on 2010-08-14
I had the same problem. Turns out their repository is down. Thinking about trying Boxee instead, but you have to register with them to use it.

---

### Post by bprins on 2010-08-15
open the link address:
[http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/kermic/main/source/Sources.gz](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/kermic/main/source/Sources.gz)

it states "k**e**rmic"

dunno how you managed to do that, but rename it to karmic and you're the man.

in lucid:
sudo nano /etc/apt/sources.list.d/team-xbmc-ppa-lucid.list

---

