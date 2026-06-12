---
title: "cant install tv-maxe"
date: 2012-06-10
forum: Multimedia Software
---

### Post by gabrielaca on 2012-06-10
im on ubuntu 12.01LTS 64b and trying to install tv-maxe, i get a warning on terminal "needs dependncy sp-auth, wont install"    in synaptic i get a lot dependencies (all 32b) and wont install also cites the sp-auth, what can i do?

---

### Post by nickrout on 2012-06-11
> **gabrielaca said:**
> im on ubuntu 12.01LTS 64b and trying to install tv-maxe, i get a warning on terminal "needs dependncy sp-auth, wont install"    in synaptic i get a lot dependencies (all 32b) and wont install also cites the sp-auth, what can i do?

What are you doing to try and install it? According to [http://packages.ubuntu.com/search?keywords=tv-maxe&searchon=names&suite=precise&section=all](http://packages.ubuntu.com/search?keywords=tv-maxe&searchon=names&suite=precise&section=all) it is not packaged for ubuntu. Nor is sp-auth for that matter, what is it?

By the way there is no 12.01, I assume you mean 12.04?

---

### Post by gabrielaca on 2012-06-11
yeah finger fail, its 12.04, i found this [http://www.webupd8.org/2012/04/tv-maxe-07-released-ubuntu-ppa.html]("http://www.webupd8.org/2012/04/tv-maxe-07-released-ubuntu-ppa.html") and tried to install from PPA but got me all this missing dependencies, i guess if its not that clear to install and run im not going to need it, so if you can help i appreciate it

---

### Post by nickrout on 2012-06-11
> **gabrielaca said:**
> yeah finger fail, its 12.04, i found this [http://www.webupd8.org/2012/04/tv-maxe-07-released-ubuntu-ppa.html]("http://www.webupd8.org/2012/04/tv-maxe-07-released-ubuntu-ppa.html") and tried to install from PPA but got me all this missing dependencies, i guess if its not that clear to install and run im not going to need it, so if you can help i appreciate it

sp-auth is in the same ppa.

Please post the output of ```
sudo apt-get install tv-maxe
```

---

### Post by gabrielaca on 2012-06-11
i alreasy downloaded the sp-auth in tar.gz also the tar.gz for tv-maxe.


from the terminal ```
gabriel@gabriel-G41MT-S2:~$ sudo apt-get install tv-maxe
[sudo] password for gabriel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 tv-maxe : Depends: sp-auth but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
gabriel@gabriel-G41MT-S2:~$ 

```




and the attached pics are from synaptic

---

### Post by nickrout on 2012-06-11
works here on 12.04 (in that it installs, I haven't tried the program yet)

Did you add the repository then update then install?

Try it again step by step and post any errors:

```
sudo add-apt-repository ppa:venerix/blug
sudo apt-get update
sudo apt-get install tv-maxe
```

---

### Post by gabrielaca on 2012-06-12
this is what i get in the terminal:
```

gabriel@gabriel-G41MT-S2:~$ sudo add-apt-repository ppa:venerix/blug
[sudo] password for gabriel: 
You are about to add the following PPA to your system:
 Work in progress ...
 More info: https://launchpad.net/~venerix/+archive/blug
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.KwXG4XX6j8 --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv FED7BB22D83790748FDCE04625EEBC6F080059AF
gpg: requesting key 080059AF from hkp server keyserver.ubuntu.com
gpg: key 080059AF: "Launchpad venerix" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
gabriel@gabriel-G41MT-S2:~$ sudo apt-get update
Ign http://linux.dropbox.com precise InRelease
Get:1 http://linux.dropbox.com precise Release.gpg [489 B]                     
Get:2 http://linux.dropbox.com precise Release [2,603 B]                       
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://mx.archive.ubuntu.com precise InRelease                             
Ign http://mx.archive.ubuntu.com precise-updates InRelease                     
Ign http://mx.archive.ubuntu.com precise-backports InRelease                   
Ign http://security.ubuntu.com precise-security InRelease                      
Get:3 http://linux.dropbox.com precise/main amd64 Packages [1,029 B]           
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://archive.canonical.com precise InRelease                             
Get:4 http://linux.dropbox.com precise/main i386 Packages [1,029 B]            
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Get:5 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Get:6 http://mx.archive.ubuntu.com precise Release.gpg [198 B]                 
Get:7 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://extras.ubuntu.com precise Release                                   
Get:8 http://mx.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Get:9 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Get:10 http://security.ubuntu.com
```

and a lot more, at the end i get  warnings about jdownloader being duplicated.

```
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Fetched 20.0 MB in 46s (435 kB/s)                                              
Reading package lists... Done
W: Duplicate sources.list entry http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_jd-team_jdownloader_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/ precise/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_jd-team_jdownloader_ubuntu_dists_precise_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
gabriel@gabriel-G41MT-S2:~$ sudo apt-get install tv-maxe
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 tv-maxe : Depends: sp-auth but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
gabriel@gabriel-G41MT-S2:~$ ^C

```

---

### Post by gabrielaca on 2012-06-12
all the code

```
gabriel@gabriel-G41MT-S2:~$ sudo add-apt-repository ppa:venerix/blug
[sudo] password for gabriel: 
You are about to add the following PPA to your system:
 Work in progress ...
 More info: https://launchpad.net/~venerix/+archive/blug
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.KwXG4XX6j8 --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv FED7BB22D83790748FDCE04625EEBC6F080059AF
gpg: requesting key 080059AF from hkp server keyserver.ubuntu.com
gpg: key 080059AF: "Launchpad venerix" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
gabriel@gabriel-G41MT-S2:~$ sudo apt-get update
Ign http://linux.dropbox.com precise InRelease
Get:1 http://linux.dropbox.com precise Release.gpg [489 B]                     
Get:2 http://linux.dropbox.com precise Release [2,603 B]                       
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://mx.archive.ubuntu.com precise InRelease                             
Ign http://mx.archive.ubuntu.com precise-updates InRelease                     
Ign http://mx.archive.ubuntu.com precise-backports InRelease                   
Ign http://security.ubuntu.com precise-security InRelease                      
Get:3 http://linux.dropbox.com precise/main amd64 Packages [1,029 B]           
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://archive.canonical.com precise InRelease                             
Get:4 http://linux.dropbox.com precise/main i386 Packages [1,029 B]            
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Get:5 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Get:6 http://mx.archive.ubuntu.com precise Release.gpg [198 B]                 
Get:7 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://extras.ubuntu.com precise Release                                   
Get:8 http://mx.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Get:9 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Get:10 http://security.ubuntu.com precise-security Release [49.6 kB]           
Get:11 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Hit http://archive.canonical.com precise Release                               
Get:12 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Hit http://extras.ubuntu.com precise/main Sources                              
Get:13 http://mx.archive.ubuntu.com precise-backports Release.gpg [198 B]      
Get:14 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:15 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://archive.canonical.com precise/partner amd64 Packages                
Get:16 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Ign http://linux.dropbox.com precise/main Translation-en_US                    
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Get:17 http://mx.archive.ubuntu.com precise Release [49.6 kB]                  
Ign http://linux.dropbox.com precise/main Translation-en                       
Get:18 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:19 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Get:20 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:21 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:22 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:23 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:24 http://mx.archive.ubuntu.com precise-updates Release [49.6 kB]          
Get:25 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:26 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:27 http://mx.archive.ubuntu.com precise-backports Release [49.6 kB]        
Get:28 http://security.ubuntu.com precise-security/main Sources [16.3 kB]      
Get:29 http://ppa.launchpad.net precise Release [11.9 kB]                      
Hit http://ppa.launchpad.net precise Release                                   
Get:30 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:31 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:32 http://mx.archive.ubuntu.com precise/main Sources [934 kB]              
Get:33 http://security.ubuntu.com precise-security/restricted Sources [14 B]   
Get:34 http://security.ubuntu.com precise-security/universe Sources [4,935 B]  
Get:35 http://security.ubuntu.com precise-security/multiverse Sources [713 B]  
Get:36 http://security.ubuntu.com precise-security/main amd64 Packages [51.3 kB]
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Get:37 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:38 http://ppa.launchpad.net precise Release [11.8 kB]                      
Get:39 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:40 http://security.ubuntu.com precise-security/restricted amd64 Packages [14 B]
Get:41 http://security.ubuntu.com precise-security/universe amd64 Packages [12.0 kB]
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Get:42 http://security.ubuntu.com precise-security/multiverse amd64 Packages [1,155 B]
Get:43 http://security.ubuntu.com precise-security/main i386 Packages [52.6 kB]
Get:44 http://ppa.launchpad.net precise/main Sources [2,268 B]                 
Get:45 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:46 http://security.ubuntu.com precise-security/universe i386 Packages [12.1 kB]
Get:47 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,394 B]
Get:48 http://security.ubuntu.com precise-security/main TranslationIndex [73 B]
Get:49 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:50 http://security.ubuntu.com precise-security/restricted TranslationIndex [70 B]
Get:51 http://security.ubuntu.com precise-security/universe TranslationIndex [72 B]
Get:52 http://ppa.launchpad.net precise/main amd64 Packages [1,724 B]          
Get:53 http://security.ubuntu.com precise-security/main Translation-en [26.2 kB]
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Get:54 http://ppa.launchpad.net precise/main i386 Packages [1,724 B]           
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Get:55 http://security.ubuntu.com precise-security/universe Translation-en [8,835 B]
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://extras.ubuntu.com precise/main Translation-en                      
Ign http://archive.canonical.com precise/partner Translation-en               
Get:56 http://ppa.launchpad.net precise/main Sources [853 B]                  
Get:57 http://ppa.launchpad.net precise/main amd64 Packages [1,339 B]          
Get:58 http://ppa.launchpad.net precise/main i386 Packages [1,351 B]           
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:59 http://ppa.launchpad.net precise/main Sources [2,455 B]
Get:60 http://mx.archive.ubuntu.com precise/restricted Sources [5,470 B]       
Get:61 http://mx.archive.ubuntu.com precise/universe Sources [5,019 kB]        
Get:62 http://ppa.launchpad.net precise/main amd64 Packages [1,822 B]        
Get:63 http://ppa.launchpad.net precise/main i386 Packages [1,819 B]           
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:64 http://ppa.launchpad.net precise/main Sources [1,004 B]                 
Get:65 http://ppa.launchpad.net precise/main amd64 Packages [1,617 B]          
Get:66 http://ppa.launchpad.net precise/main i386 Packages [1,624 B]           
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:67 http://ppa.launchpad.net precise/main Sources [973 B]
Get:68 http://ppa.launchpad.net precise/main amd64 Packages [1,421 B]          
Get:69 http://ppa.launchpad.net precise/main i386 Packages [1,421 B]           
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:70 http://ppa.launchpad.net precise/main Sources [1,674 B]                 
Get:71 http://ppa.launchpad.net precise/main amd64 Packages [2,390 B]          
Get:72 http://ppa.launchpad.net precise/main i386 Packages [2,382 B]           
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:73 http://ppa.launchpad.net precise/main Sources [4,138 B]                 
Get:74 http://ppa.launchpad.net precise/main amd64 Packages [15.2 kB]          
Get:75 http://ppa.launchpad.net precise/main i386 Packages [15.2 kB]           
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:76 http://ppa.launchpad.net precise/main Sources [1,611 B]                 
Get:77 http://ppa.launchpad.net precise/main amd64 Packages [2,058 B]          
Get:78 http://ppa.launchpad.net precise/main i386 Packages [2,058 B]           
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:79 http://ppa.launchpad.net precise/main Sources [323 B]                   
Get:80 http://ppa.launchpad.net precise/main amd64 Packages [398 B]            
Get:81 http://ppa.launchpad.net precise/main i386 Packages [398 B]             
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:82 http://ppa.launchpad.net precise/main Sources [546 B]                   
Get:83 http://ppa.launchpad.net precise/main amd64 Packages [649 B]            
Get:84 http://ppa.launchpad.net precise/main i386 Packages [649 B]             
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:85 http://mx.archive.ubuntu.com precise/multiverse Sources [155 kB]        
Get:86 http://mx.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]     
Get:87 http://mx.archive.ubuntu.com precise/restricted amd64 Packages [8,452 B]
Get:88 http://mx.archive.ubuntu.com precise/universe amd64 Packages [4,786 kB] 
Get:89 http://mx.archive.ubuntu.com precise/multiverse amd64 Packages [119 kB] 
Get:90 http://mx.archive.ubuntu.com precise/main i386 Packages [1,274 kB]      
Get:91 http://mx.archive.ubuntu.com precise/restricted i386 Packages [8,431 B] 
Get:92 http://mx.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]  
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Get:93 http://mx.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]  
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Hit http://mx.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://mx.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://mx.archive.ubuntu.com precise/restricted TranslationIndex    
Hit http://mx.archive.ubuntu.com precise/universe TranslationIndex      
Get:94 http://mx.archive.ubuntu.com precise-updates/main Sources [104 kB]
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:95 http://mx.archive.ubuntu.com precise-updates/restricted Sources [1,379 B]
Get:96 http://mx.archive.ubuntu.com precise-updates/universe Sources [22.8 kB] 
Get:97 http://mx.archive.ubuntu.com precise-updates/multiverse Sources [1,058 B]
Get:98 http://mx.archive.ubuntu.com precise-updates/main amd64 Packages [246 kB]
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Get:99 http://mx.archive.ubuntu.com precise-updates/restricted amd64 Packages [2,417 B]
Get:100 http://mx.archive.ubuntu.com precise-updates/universe amd64 Packages [66.4 kB]
Get:101 http://mx.archive.ubuntu.com precise-updates/multiverse amd64 Packages [1,825 B]
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:102 http://mx.archive.ubuntu.com precise-updates/main i386 Packages [248 kB]
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:103 http://mx.archive.ubuntu.com precise-updates/restricted i386 Packages [2,439 B]
Get:104 http://mx.archive.ubuntu.com precise-updates/universe i386 Packages [66.8 kB]
Get:105 http://mx.archive.ubuntu.com precise-updates/multiverse i386 Packages [2,049 B]
Get:106 http://mx.archive.ubuntu.com precise-updates/main TranslationIndex [74 B]
Get:107 http://mx.archive.ubuntu.com precise-updates/multiverse TranslationIndex [71 B]
Get:108 http://mx.archive.ubuntu.com precise-updates/restricted TranslationIndex [71 B]
Get:109 http://mx.archive.ubuntu.com precise-updates/universe TranslationIndex [73 B]
Get:110 http://mx.archive.ubuntu.com precise-backports/main Sources [700 B]
Get:111 http://mx.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Ign http://ppa.launchpad.net precise/main Translation-en_US             
Get:112 http://mx.archive.ubuntu.com precise-backports/universe Sources [6,109 B]
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:113 http://mx.archive.ubuntu.com precise-backports/multiverse Sources [1,383 B]
Get:114 http://mx.archive.ubuntu.com precise-backports/main amd64 Packages [559 B]
Get:115 http://mx.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Get:116 http://mx.archive.ubuntu.com precise-backports/universe amd64 Packages [5,200 B]
Get:117 http://mx.archive.ubuntu.com precise-backports/multiverse amd64 Packages [996 B]
Get:118 http://mx.archive.ubuntu.com precise-backports/main i386 Packages [559 B]
Get:119 http://mx.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:120 http://mx.archive.ubuntu.com precise-backports/universe i386 Packages [5,227 B]
Get:121 http://mx.archive.ubuntu.com precise-backports/multiverse i386 Packages [999 B]
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Hit http://mx.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://mx.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://mx.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://mx.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://mx.archive.ubuntu.com precise/main Translation-en                   
Hit http://mx.archive.ubuntu.com precise/multiverse Translation-en             
Ign http://ppa.launchpad.net precise/main Translation-en                       
Hit http://mx.archive.ubuntu.com precise/restricted Translation-en             
Hit http://mx.archive.ubuntu.com precise/universe Translation-en               
Get:122 http://mx.archive.ubuntu.com precise-updates/main Translation-en [115 kB]
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Hit http://mx.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://mx.archive.ubuntu.com precise-updates/restricted Translation-en     
Get:123 http://mx.archive.ubuntu.com precise-updates/universe Translation-en [39.9 kB]
Hit http://mx.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://mx.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://mx.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://mx.archive.ubuntu.com precise-backports/universe Translation-en     
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Fetched 20.0 MB in 46s (435 kB/s)                                              
Reading package lists... Done
W: Duplicate sources.list entry http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_jd-team_jdownloader_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/ precise/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_jd-team_jdownloader_ubuntu_dists_precise_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
gabriel@gabriel-G41MT-S2:~$ sudo apt-get install tv-maxe
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 tv-maxe : Depends: sp-auth but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
gabriel@gabriel-G41MT-S2:~$ ^C
gabriel@gabriel-G41MT-S2:~$ ^C
gabriel@gabriel-G41MT-S2:~$ 

```

greetings

---

### Post by JoZ3 on 2012-06-12
I have the same issue, 

tv-maxe depends on sp-auth.
sp-auth depends on ia32libs.
ia32libs depends on ia32-libs-multiarch ... etc.

My system is Ubuntu 12.04 64bits

---

### Post by nickrout on 2012-06-12
ahh mine is 32 bit, so that's the difference.

This is a packaging issue form the ppa. Go to the ppa web page and email the maintainer, there is a link there.

Of course it might also be that sp-auth will only run in 32 bit, in which case it becomes more difficult.

---

### Post by gabrielaca on 2012-06-13
thats what i thought, anyway thanks nickrout, ill email the maintener.):P

---

