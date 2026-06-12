---
title: "Very strange! Audio control button on keyboard stopped working..."
date: 2011-12-18
forum: Multimedia Software
---

### Post by trekon86 on 2011-12-18
I think it must be a problem with my audio software in Ubuntu.

Maybe the sound applet? A few days ago I ran auto-update and when I rebooted my Panel was all fooked up.

Here's the output of that command that the Sound Troubleshooting page says to do:

```
pmz@pmz-laptop:~$ sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo add-apt-repository ppa:team-iquik/alsa; sudo apt-get update; sudo apt-get dist-upgrade; sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop linux-image-`uname -r` linux-alsa-driver-modules-$(uname -r) libasound2; sudo apt-get --reinstall install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop linux-image-`uname -r` linux-alsa-driver-modules-$(uname -r)  libasound2; killall pulseaudio; rm -r ~/.pulse*; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`
[sudo] password for pmz: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 4E9F485BF943EF0EABA10B5BD225991A72B194E5
gpg: requesting key 72B194E5 from hkp server keyserver.ubuntu.com
gpg: key 72B194E5: "Launchpad Ubuntu Audio Dev team PPA" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 1B05262E084BDE67358EF400210AE75EDC1FE094
gpg: requesting key DC1FE094 from hkp server keyserver.ubuntu.com
gpg: key DC1FE094: public key "Launchpad Addons PPA" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release.gpg
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) lucid/main Translation-en_US              
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]                           
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                       
Ign [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/) lucid/main Translation-en_US
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]                        
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release                           
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Ign [http://ppa.launchpad.net/team-iquik/alsa/ubuntu/](http://ppa.launchpad.net/team-iquik/alsa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages                               
Get:4 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,201B]                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release.gpg                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [13.9kB]                
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [4,796B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Packages
Fetched 21.8kB in 2s (10.0kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  alsa-base alsa-utils lib32asound2 libasound2 libasound2-plugins
  linux-sound-base
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,421kB of archives.
After this operation, 307kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ppa.launchpad.net/team-iquik/alsa/ubuntu/](http://ppa.launchpad.net/team-iquik/alsa/ubuntu/) lucid/main linux-sound-base 1.0.24+dfsg-0ubuntu2~lucid1 [36.3kB]
Get:2 [http://ppa.launchpad.net/team-iquik/alsa/ubuntu/](http://ppa.launchpad.net/team-iquik/alsa/ubuntu/) lucid/main alsa-base 1.0.24+dfsg-0ubuntu2~lucid1 [319kB]
Get:3 [http://ppa.launchpad.net/team-iquik/alsa/ubuntu/](http://ppa.launchpad.net/team-iquik/alsa/ubuntu/) lucid/main lib32asound2 1.0.24.1-0ubuntu6~lucid1 [346kB]
Get:4 [http://ppa.launchpad.net/team-iquik/alsa/ubuntu/](http://ppa.launchpad.net/team-iquik/alsa/ubuntu/) lucid/main libasound2 1.0.24.1-0ubuntu6~lucid1 [461kB]
Get:5 [http://ppa.launchpad.net/team-iquik/alsa/ubuntu/](http://ppa.launchpad.net/team-iquik/alsa/ubuntu/) lucid/main alsa-utils 1.0.24.2-0ubuntu6~lucid. [1,178kB]
Get:6 [http://ppa.launchpad.net/team-iquik/alsa/ubuntu/](http://ppa.launchpad.net/team-iquik/alsa/ubuntu/) lucid/main libasound2-plugins 1.0.24-0ubuntu1~lucid1 [80.5kB]
Fetched 2,421kB in 26s (90.0kB/s)                                              
Preconfiguring packages ...
(Reading database ... 250431 files and directories currently installed.)
Preparing to replace linux-sound-base 1.0.22.1+dfsg-0ubuntu3 (using .../linux-sound-base_1.0.24+dfsg-0ubuntu2~lucid1_all.deb) ...
Unpacking replacement linux-sound-base ...
Preparing to replace alsa-base 1.0.22.1+dfsg-0ubuntu3 (using .../alsa-base_1.0.24+dfsg-0ubuntu2~lucid1_all.deb) ...
Unpacking replacement alsa-base ...
Preparing to replace lib32asound2 1.0.22-0ubuntu7 (using .../lib32asound2_1.0.24.1-0ubuntu6~lucid1_amd64.deb) ...
Unpacking replacement lib32asound2 ...
Preparing to replace libasound2 1.0.22-0ubuntu7 (using .../libasound2_1.0.24.1-0ubuntu6~lucid1_amd64.deb) ...
Unpacking replacement libasound2 ...
Preparing to replace alsa-utils 1.0.22-0ubuntu5 (using .../alsa-utils_1.0.24.2-0ubuntu6~lucid._amd64.deb) ...
Unpacking replacement alsa-utils ...
Preparing to replace libasound2-plugins 1.0.22-0ubuntu6 (using .../libasound2-plugins_1.0.24-0ubuntu1~lucid1_amd64.deb) ...
Unpacking replacement libasound2-plugins ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up linux-sound-base (1.0.24+dfsg-0ubuntu2~lucid1) ...

Setting up alsa-base (1.0.24+dfsg-0ubuntu2~lucid1) ...
Installing new version of config file /etc/modprobe.d/alsa-base.conf ...

Setting up libasound2 (1.0.24.1-0ubuntu6~lucid1) ...

Setting up lib32asound2 (1.0.24.1-0ubuntu6~lucid1) ...

Setting up alsa-utils (1.0.24.2-0ubuntu6~lucid.) ...

Setting up libasound2-plugins (1.0.24-0ubuntu1~lucid1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-sound-base is already the newest version.
alsa-base is already the newest version.
alsa-utils is already the newest version.
gdm is already the newest version.
linux-image-2.6.32-36-generic is already the newest version.
linux-image-2.6.32-36-generic set to manually installed.
E: Couldn't find package linux-alsa-driver-modules-2.6.32-36-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-alsa-driver-modules-2.6.32-36-generic
pmz@pmz-laptop:~$ 
```

I am going to reboot and see if that does anything. Otherwise I'm going to assume it's a problem with one of the audio programs/drivers.

I can't imagine it would be that the sound button is worn out. I just got this HP laptop this summer.

Thanks for ahy help you all may have for me!
PMZ

---

### Post by CaptinGoogle on 2011-12-18
Have you tried going into Ubuntu 2D and seeing if everything looks normal and works normally?

---

