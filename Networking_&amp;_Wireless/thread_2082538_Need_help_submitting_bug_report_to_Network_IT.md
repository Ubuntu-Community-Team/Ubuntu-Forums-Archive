---
title: "Need help submitting bug report to Network IT"
date: 2012-11-09
forum: Networking &amp; Wireless
---

### Post by ETecoli on 2012-11-09
Hi all. My university made some changes to the network firewall due to hurricane Sandy ruining some equipment. I want to submit a bug report because I can no longer access some services.

On Ubuntu 12.04LTS on the university's network

1) I can ping, but can't ssh to a university server (known problem with .edu addresses - I *can* ssh to a .com). 

2) apt-get fails. For example:
```
$ sudo apt-get update

Ign http://dl.google.com stable InRelease
Ign http://lib.stat.cmu.edu precise/ InRelease                                                                                                       
Err http://dl.google.com stable Release.gpg                                                                                                          
  Connection failed [IP: 74.125.228.38 80]
Err http://lib.stat.cmu.edu precise/ Release.gpg                                                                                                     
  Connection failed
Ign http://us.archive.ubuntu.com precise InRelease                                                                                                   
Ign http://dl.google.com stable Release                                                                                                              
Ign http://lib.stat.cmu.edu precise/ Release                                                                                                         
Ign http://ppa.launchpad.net precise InRelease                                                                                                       
Ign http://extras.ubuntu.com precise InRelease                                                                                                       
Ign http://security.ubuntu.com precise-security InRelease                                                                                            
Ign http://us.archive.ubuntu.com precise-updates InRelease                                                                                           
Ign http://dl.google.com stable/main i386 Packages/DiffIndex                                                                                         
Ign http://lib.stat.cmu.edu precise/ Packages/DiffIndex                                                                                              
Ign http://dl.google.com stable/main TranslationIndex                                                                                                
Ign http://archive.canonical.com precise InRelease                                                                                                   
Err http://us.archive.ubuntu.com precise Release.gpg                                                                                                 
  Connection failed [IP: 91.189.91.14 80]
Err http://extras.ubuntu.com precise Release.gpg                                                                                                     
  Connection failed

```
The above is just a snippet of the output.

I'm guessing there's a range of ports or specific kinds of processes that are getting blocked. Any suggestions on what to check to submit a great report? (The department is slammed thanks to the storm so I want to be as comprehensive as possible to avoid wasting network IT resources).

Thanks!

---

