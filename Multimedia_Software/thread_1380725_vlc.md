---
title: "vlc"
date: 2010-01-14
forum: Multimedia Software
---

### Post by porlaizquierda on 2010-01-14
I cannot install vlc on my laptop. i use a system 76 sterling netbook running 9.04. when i try to install vlc with synaptic i get this:

Could not mark all packages for installation or upgrade
The following pages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences. 

vlc:
 Depends: vlc-nox but it is not going to be installed
  Depends: libqtcore4 (>=4.5.1) but 4.5.0-0ubuntu4.3 is to be installed
  Depends: libqtgui4 (>=4.5.1) but 4.5.0-0ubuntu4.3 is to be installed
 Depends: libx264-67 (>=1:0.svn20090502) but it is not installable
 Recommends: vlc-plugin-pulse but it is not going to be installed

when i try to install vlc-nox i get this:

Could not mark all packages for installation or upgrade
The following pages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences. 

vlc-nox:
  Depends: libgcrypt11 (>=1.4.2) but 1.4.1-2ubuntu1 is to be installed
  Depends: libgnutls26 (>=2.7.14-0) but 2.4.2-6ubuntu0.1 is to be installed
  Depends: libgpg-error0 (>=1.6) but 1.4-2ubuntu7 is to be installed
  Depends: libschroedinger-1.0-0 (>=1.0.7) but 1.0.5-1 is to be installed
  Depends: libtag1c2a (>=1.6-2~) but 1.5-3 is to be installed
  Depends: libxml2 (>=2.7.4) but 2.6.32.dfsg-5ubuntu4.2 is to be installed

what's the deal? can anyone help?

---

### Post by Matt_Johnson on 2010-01-14
Not quiet sure of the error but just try this:
```
 sudo apt-get update
```
then type:
```
sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc
```
lemme know if it works. (basically were trying to reinstall)

---

### Post by porlaizquierda on 2010-01-14
when i type sudo apt-get update i get this:

Hit [http://planet76.com](http://planet76.com) ./ Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                                                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                                                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                                                              
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                                                                  
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release.gpg                                                                      
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Translation-en_US                                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg                                                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_US                                                                 
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                                                                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                                                                        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US                                                             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US                                                         
Ign [http://planet76.com](http://planet76.com) ./ Translation-en_US                                                                                
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                      
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release.gpg                                                                     
Ign [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/apps Translation-en_US                                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US                                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US                                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                                                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US                                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US                                                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg                                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US                                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US                                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release                                                                                
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.7kB]                                                                      
Hit [http://planet76.com](http://planet76.com) ./ Release                                                                                          
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release                                                                          
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [2540B]                                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                                           
Hit [http://archive.getdeb.net](http://archive.getdeb.net) jaunty-getdeb Release.gpg                                    
Ign [http://archive.getdeb.net](http://archive.getdeb.net) jaunty-getdeb/apps Translation-en_US
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release                                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                                                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                                                                
Ign [http://planet76.com](http://planet76.com) ./ Packages                                                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages                                                                          
Hit [http://archive.getdeb.net](http://archive.getdeb.net) jaunty-getdeb Release                                                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                                                                           
Get:5 [http://dl.google.com](http://dl.google.com) stable/main Packages [914B]                                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages                                                                   
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages                                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages                                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages                                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources                                                           
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                                                                    
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/apps Packages                                                                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                                                                      
Hit [http://planet76.com](http://planet76.com) ./ Packages                                                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources                                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://archive.getdeb.net](http://archive.getdeb.net) jaunty-getdeb/apps Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources
Fetched 3951B in 1s (3217B/s)                  
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7
W: You may want to run apt-get update to correct these problems


then when i type in sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc i get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mozilla-plugin-vlc: Depends: vlc-nox (= 1.0.4-1~getdeb1) but it is not going to be installed
  vlc: Depends: vlc-nox (= 1.0.4-1~getdeb1) but it is not going to be installed
       Depends: libqtcore4 (>= 4.5.1) but 4.5.0-0ubuntu4.3 is to be installed
       Depends: libqtgui4 (>= 4.5.1) but 4.5.0-0ubuntu4.3 is to be installed
       Depends: libx264-67 (>= 1:0.svn20090502) but it is not installable
  vlc-plugin-pulse: Depends: vlc-nox (= 1.0.4-1~getdeb1) but it is not going to be installed
E: Broken packages


what's the deal with that?

---

### Post by mc4man on 2010-01-14
You've added the getdeb source for karmic, but are using jaunty and won't be able to meet the install debs.
> Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release.gpg
Ign [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/apps Translation-en_US 

You'll need to remove that source, and find one for jaunty. ( whether from getdeb or a ppa that has a vlc for jaunty

Here's one for jaunty -[ vlc 1.0.2]("https://launchpad.net/~c-korn/+archive/vlc?field.series_filter=jaunty") ( there's not much love for vlc in ppa's jaunty wise, you may or may not like 1.0.2 better than 0.9.9a

( you need to click on the 'not using karmic' to expose jaunty ppa sources to add to software sources

---

### Post by porlaizquierda on 2010-01-14
worked like a charm my friend! thanks!

---

