---
title: "Trying to install samba"
date: 2013-04-27
forum: Networking &amp; Wireless
---

### Post by Gilgen on 2013-04-27
Hi
Am running 12.04 and am trying to install samba but it keeps coming up with this message

The following packages have unmet dependencies.
 samba : Depends: samba-common (= 2:3.6.3-2ubuntu2) but 2:3.6.3-2ubuntu2.3 is to be installed
         Depends: libwbclient0 (= 2:3.6.3-2ubuntu2) but 2:3.6.3-2ubuntu2.3 is to be installed
E: Unable to correct problems, you have held broken packages.

I have tried to install in term also.

I'm a bit of a newbie and don't know how to procede.

Gilgen

---

### Post by TheFu on 2013-04-27
Your package system appears to be in a non-good state. Please run:
```
$ sudo apt-get update
$ sudo apt-get dist-upgrade

```
and post the results.

I suspect some package is not fully installed AND configured for some reason.
Don't worry about "dist-upgrade" - it just installs new kernels for the current release you are running. If this isn't desirable for your specific situation, say that in a reply. It is very unusual for a new Linux user to care about the kernel version too much. I don't care on almost all my machines either.

---

### Post by Gilgen on 2013-04-27
Hi
Many thanks for your reply, here are the results


reg@Reg-Netbook:~$ sudo apt-get update
[sudo] password for reg: 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports Release.gpg                   
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:2 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports Release                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:3 [http://archive.canonical.com](http://archive.canonical.com) precise Release [7,078 B]                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/main Sources                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/restricted Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/universe Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/multiverse Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/main i386 Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/restricted i386 Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/universe i386 Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/multiverse i386 Packages      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/main TranslationIndex         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/multiverse TranslationIndex   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/restricted TranslationIndex   
Get:4 [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources [4,510 B]           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/universe TranslationIndex     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex            
Get:5 [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages [5,874 B]     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex                
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/main Translation-en_GB        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_GB                    
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en_GB [96.4 kB]       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/main Translation-en           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/multiverse Translation-en_GB  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/multiverse Translation-en     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/restricted Translation-en_GB  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/restricted Translation-en     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/universe Translation-en_GB    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/universe Translation-en       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_GB             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en_GB [79.8 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en             
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en_GB [5,492 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en                
Fetched 199 kB in 1s (116 kB/s)     
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
reg@Reg-Netbook:~$ sudo apt-get update
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports InRelease                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease                                
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports Release.gpg                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg                              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports Release                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/main Sources         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/restricted Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/universe Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/multiverse Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/main i386 Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/restricted i386 Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/universe i386 Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/multiverse i386 Packages      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/main TranslationIndex         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/multiverse TranslationIndex   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/restricted TranslationIndex   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/universe TranslationIndex     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en_GB                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en_GB             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en_GB               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/main Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/universe Translation-en
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
reg@Reg-Netbook:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


I ran apt-get update again but got the same result

Regards
Gilgen

---

### Post by TheFu on 2013-04-27
Ok, so it seems that your packages are not in a bad state.  Can you please try to install samba again - this time copy/paste the output from the command?
```

$ sudo apt-get install samba
```

BTW, running "update" and/or upgrade/dist-upgrade twice shouldn't harm anything, but if there isn't a connection issue, it won't help anything either.

---

### Post by Gilgen on 2013-04-27
Hi TheFu

Results-

reg@Reg-Netbook:~$ sudo apt-get install samba
[sudo] password for reg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 samba : Depends: samba-common (= 2:3.6.3-2ubuntu2) but 2:3.6.3-2ubuntu2.3 is to be installed
         Depends: libwbclient0 (= 2:3.6.3-2ubuntu2) but 2:3.6.3-2ubuntu2.3 is to be installed
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Unable to correct problems, you have held broken packages.
reg@Reg-Netbook:~$ 

Regards
Gilgen

---

### Post by Gilgen on 2013-04-27
Hi
Here's the results-
reg@Reg-Netbook:~$ sudo apt-get install samba
[sudo] password for reg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 samba : Depends: samba-common (= 2:3.6.3-2ubuntu2) but 2:3.6.3-2ubuntu2.3 is to be installed
         Depends: libwbclient0 (= 2:3.6.3-2ubuntu2) but 2:3.6.3-2ubuntu2.3 is to be installed
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Unable to correct problems, you have held broken packages.
reg@Reg-Netbook:~$ 

Regards

---

### Post by TheFu on 2013-04-28
Looks like you've added extra repositories that may not be compatible with Samba. Perhaps something in the "partner repositories?"

My currently patched 12.04 systems have these installed:```

samba                                         2:3.6.3-2ubuntu2.6
samba-common                          2:3.6.3-2ubuntu2.6
samba-common-bin                    2:3.6.3-2ubuntu2.6
libwbclient0                                 2:3.6.3-2ubuntu2.6
```

The only thing that I can think to try is a **sudo apt-get -f install** without any package to see if something is partially installed, not completely installed.  Sorry - not much help.

---

### Post by Gilgen on 2013-04-29
Thanks TF
This is what I got....

reg@Reg-Netbook:~$ sudo apt-get -f install
[sudo] password for reg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

I ran it again but the results were the same.
Many thanks for trying.
Regards
Gilgen

---

### Post by TheFu on 2013-05-01
What happens if you find all the  **[http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages** lines in your repository lists and remove them, then run
* update
* dist upgrade
* install samba?

I don't have those 3rd party repos in my install - why do you have them? Just curious.  could it be for ATI or nvidia GPU drivers is is there some other specific reason?

---

