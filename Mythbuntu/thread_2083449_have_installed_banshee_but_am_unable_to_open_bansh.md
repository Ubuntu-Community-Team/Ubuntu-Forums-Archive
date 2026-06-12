---
title: "have installed banshee but am unable to open banshee"
date: 2012-11-12
forum: Mythbuntu
---

### Post by noblegas on 2012-11-12
I've installed banshee using these commands:

> sudo add-apt-repository ppa:banshee-team/ppa
sudo apt-get update
sudo apt-get install banshee

And these are my results: 

> user@user-laptop:~$ sudo add-apt-repository ppa:banshee-team/banshee-daily
[sudo] password for user: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 9D2C2E0A3C88DD807EC787D74874D3686E80C6B7
gpg: requesting key 6E80C6B7 from hkp server keyserver.ubuntu.com
gpg: key 6E80C6B7: public key "Launchpad PPA for Banshee Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
user@user-laptop:~$ sudo apt-get update
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ natty/main Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ natty/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]            
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [58.3kB]              
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Translation-en_US              
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]                        
Ign [http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu/](http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu/) lucid/main Translation-en_US
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [14.0kB]                          
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [57.3kB]               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources                      
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [658kB]         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [13.7kB]                    
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [461kB]          
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [4,630B] 
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [231kB]         
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [2,196B]  
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [282kB]    
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [2,867B]  
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [132kB]          
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [104kB]     
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [11.5kB] 
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [5,827B]  
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [1,267B]   
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [138kB]     
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [42.5kB]     
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [5,353B]  
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [2,350B]   
Fetched 2,228kB in 20s (108kB/s)                                               
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_dists_lucid_partner_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_dists_lucid_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
user@user-laptop:~$ sudo apt-get install banshee
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgdata1.4-cil podsleuth libboo2.0.9-cil sdparm firefox-branding
  libwebkit1.1-cil
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  banshee-extension-ubuntuonemusicstore libgdata1.7-cil libgkeyfile1.0-cil
  libgpod4 libgudev1.0-cil libubuntuone1.0-cil
Suggested packages:
  banshee-dbg
The following NEW packages will be installed:
  banshee-extension-ubuntuonemusicstore libgdata1.7-cil libgkeyfile1.0-cil
  libgudev1.0-cil libubuntuone1.0-cil
The following packages will be upgraded:
  banshee libgpod4
2 upgraded, 5 newly installed, 0 to remove and 123 not upgraded.
Need to get 4,494kB of archives.
After this operation, 1,606kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libubuntuone1.0-cil 0.3.1-0ubuntu1 [7,466B]
Get:2 [http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu/](http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu/) lucid/main libgdata1.7-cil 1.7.0.1-1~lucid1 [298kB]
Get:3 [http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu/](http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu/) lucid/main libgkeyfile1.0-cil 0.1-1ubuntu1~hyper1+lucid [11.1kB]
Get:4 [http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu/](http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu/) lucid/main libgpod4 0.8.0-3~hyper1+lucid [263kB]
Get:5 [http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu/](http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu/) lucid/main libgudev1.0-cil 0.1-2~hyper1+lucid [8,346B]
Get:6 [http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu/](http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu/) lucid/main banshee 1.9.4+git20110228.r1.704ddb6-0ubuntu1+lucid [3,812kB]
Get:7 [http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu/](http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu/) lucid/main banshee-extension-ubuntuonemusicstore 1.9.4+git20110228.r1.704ddb6-0ubuntu1+lucid [93.8kB]
Fetched 4,494kB in 32s (139kB/s)                                               
Selecting previously deselected package libgdata1.7-cil.
(Reading database ... 148644 files and directories currently installed.)
Unpacking libgdata1.7-cil (from .../libgdata1.7-cil_1.7.0.1-1~lucid1_all.deb) ...
Selecting previously deselected package libgkeyfile1.0-cil.
Unpacking libgkeyfile1.0-cil (from .../libgkeyfile1.0-cil_0.1-1ubuntu1~hyper1+lucid_all.deb) ...
Preparing to replace libgpod4 0.7.93-0ubuntu1 (using .../libgpod4_0.8.0-3~hyper1+lucid_i386.deb) ...
Unpacking replacement libgpod4 ...
Selecting previously deselected package libgudev1.0-cil.
Unpacking libgudev1.0-cil (from .../libgudev1.0-cil_0.1-2~hyper1+lucid_all.deb) ...
Preparing to replace banshee 1.6.1-1~lucid1 (using .../banshee_1.9.4+git20110228.r1.704ddb6-0ubuntu1+lucid_i386.deb) ...
Unpacking replacement banshee ...
Selecting previously deselected package libubuntuone1.0-cil.
Unpacking libubuntuone1.0-cil (from .../libubuntuone1.0-cil_0.3.1-0ubuntu1_all.deb) ...
Selecting previously deselected package banshee-extension-ubuntuonemusicstore.
Unpacking banshee-extension-ubuntuonemusicstore (from .../banshee-extension-ubuntuonemusicstore_1.9.4+git20110228.r1.704ddb6-0ubuntu1+lucid_i386.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Setting up libgdata1.7-cil (1.7.0.1-1~lucid1) ...
* Installing 14 assemblies from libgdata1.7-cil into Mono

Setting up libgkeyfile1.0-cil (0.1-1ubuntu1~hyper1+lucid) ...
* Installing 1 assembly from libgkeyfile1.0-cil into Mono

Setting up libgpod4 (0.8.0-3~hyper1+lucid) ...

Setting up libgudev1.0-cil (0.1-2~hyper1+lucid) ...
* Installing 1 assembly from libgudev1.0-cil into Mono

Setting up banshee (1.9.4+git20110228.r1.704ddb6-0ubuntu1+lucid) ...

Setting up libubuntuone1.0-cil (0.3.1-0ubuntu1) ...
* Installing 1 assembly from libubuntuone1.0-cil into Mono

Setting up banshee-extension-ubuntuonemusicstore (1.9.4+git20110228.r1.704ddb6-0ubuntu1+lucid) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place


Apparently,the banshee file is a tar.gz type file and when I try to extract it in order to open it, it takes me to a menus with a list and I click on partial. When I click on the partial option and then I click on the extract button, this window will message appear:

> Extraction not performed

You don't have the right permissions to extract archives in the folder "file:///var/cache/apt/archives/partial"

What am I doing wrong?

---

### Post by ibjsb4 on 2012-11-12
Why have you decided to install the unstable banshee daily build vs the stable build located in your software center/package manager?

Also noticed that your sources list has a duplicate in it.  You should remove it.  If your not sure which one to remove please post the output (in terminal) of:

cat -n /etc/apt/sources.list

---

### Post by noblegas on 2012-11-12
> **ibjsb4 said:**
> Why have you decided to install the unstable banshee daily build vs the stable build located in your software center/package manager?

Also noticed that your sources list has a duplicate in it.  You should remove it.  If your not sure which one to remove please post the output (in terminal) of:

cat -n /etc/apt/sources.list

I did not know that their was a unstable banshee daily build? I have tried to delete all of my banshee programs that were installed but were unable to be opened. What version of banshee do you recommend me installl?

---

### Post by directhex on 2012-11-12
I don't see where you actually try to run Banshee. What happens if you type "banshee"?

And Ubuntu 10.04 is an OLD distro now, I don't think Loong Jin is really maintaining Banshee packages for it

---

### Post by ibjsb4 on 2012-11-12
First you need to remove banshee.  If you haven't already, remove the PPA in software sources.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab)

Then in terminal:

gksudo nautilus

And then go to your filesystem and do a search on banshee.  Remove all banshee files that you find.
Also be careful what you delete while in sudo, once deleted you cannot recover them, they are gone.

Then your ready to install and have two options.

#1  Simply install what is in the 10o4 repositories and that would be Banshee 1.6

sudo apt-get install banshee

#2  There is a Banshee 2.0 PPA (stable) offered for 10o4.

[https://launchpad.net/~banshee-team/+archive/ppa?field.series_filter=lucid](https://launchpad.net/~banshee-team/+archive/ppa?field.series_filter=lucid)

Good luck  :)

---

### Post by nickrout on 2012-11-13
Guys what does this have to do with mythbuntu?

---

