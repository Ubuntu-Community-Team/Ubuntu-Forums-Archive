---
title: "no sound,"
date: 2010-05-13
forum: Multimedia Software
---

### Post by furoido on 2010-05-13
Got no sound since upgrading to 10.04. I tried following one suggestion from an earlier posting and got this...

Can anyone help me out with VERY CLEAR STEP-BY-STEP instructions on how to reolve this?! Thanks!

andrew@andrew-desktop:~$ sudo apt-get update
[sudo] password for andrew: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_GB   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
Get: 1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_GB [33.9kB]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages    
Get: 2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_GB [62.9kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources 
Get: 3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_GB [37.7kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Fetched 135kB in 3s (41.8kB/s)
Reading package lists... Done
andrew@andrew-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up nvidia-kernel-common (20051028+1ubuntu7) ...
update-rc.d: warning: /etc/init.d/nvidia-kernel missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
       update-rc.d [-n] <basename> disable|enable [S|2|3|4|5]
		-n: not really
		-f: force

The disable|enable API is not stable and might change in the future.
dpkg: error processing nvidia-kernel-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 nvidia-kernel-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
andrew@andrew-desktop:~$

---

