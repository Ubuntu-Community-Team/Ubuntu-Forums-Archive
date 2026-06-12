---
title: "Skype Install"
date: 2013-02-19
forum: Multimedia Software
---

### Post by mblanco2000 on 2013-02-19
My mom just recently transfered to Dubai.  She wants to see her grand daughter on Skype.  So I am trying to get it installed on my ubuntu laptop.

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype) I followed the previous link, and added the repository, and then tried to do the following command on that page to install skype.  However, I am not seeing Skype under the applications menu.  I did also read the Skype troubleshooting page, trying to be diligent, before posting.

Here is the output from the commands:

[COLOR=Blue]mblanco@mblanco-lap:~$ sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner"
mblanco@mblanco-lap:~$ sudo apt-get update && sudo apt-get install skype
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg                     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper InRelease                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates InRelease               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports InRelease             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release               
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) precise InRelease [7,096 B]      
Get:2 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main TranslationIndex           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted TranslationIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise InRelease                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe TranslationIndex       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg                       
Get:3 [http://archive.canonical.com](http://archive.canonical.com) precise Release [7,078 B]                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages/DiffIndex         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free TranslationIndex                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release                         
Get:4 [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources [4,523 B]           
Get:5 [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages [6,030 B]     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main TranslationIndex                     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources                    
  404  Not Found [IP: 91.189.91.13 80]
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse TranslationIndex               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted TranslationIndex               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe TranslationIndex                 
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources              
  404  Not Found [IP: 91.189.91.13 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources                
  404  Not Found [IP: 91.189.91.13 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources              
  404  Not Found [IP: 91.189.91.13 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main i386 Packages              
  404  Not Found [IP: 91.189.91.13 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted i386 Packages        
  404  Not Found [IP: 91.189.91.13 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe i386 Packages          
  404  Not Found [IP: 91.189.91.13 80]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main TranslationIndex             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse TranslationIndex       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted TranslationIndex       
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse i386 Packages        
  404  Not Found [IP: 91.189.91.13 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe TranslationIndex         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Translation-en             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main TranslationIndex           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Translation-en       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Translation-en       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse TranslationIndex     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted TranslationIndex     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe TranslationIndex       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Translation-en         
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en_US               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main i386 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted i386 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe i386 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources                
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources                  
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources                
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main i386 Packages                
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted i386 Packages          
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe i386 Packages            
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse i386 Packages          
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources                    
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources              
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources                
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources              
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main i386 Packages              
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted i386 Packages        
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe i386 Packages          
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse i386 Packages        
  404  Not Found [IP: 91.189.92.200 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Translation-en_US                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Translation-en                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Translation-en                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Translation-en                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Translation-en                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Translation-en               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Translation-en         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Translation-en         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Translation-en           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Translation-en             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Translation-en       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Translation-en       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Translation-en         
Fetched 24.9 kB in 6s (3,573 B/s)                                              
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) precise InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/source/Sources)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.200 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.[/COLOR]

I hope someone can help me w/ this issue.  Thanks in advance..

---

### Post by fuorviatos on 2013-02-19
Please, next time you're pasting an output, use the WRAP function to put the text in quotes.
The most up-to-date Skype version can be downloaded and installed directly from the official website. (Ignore Ubuntu version, just install it) it should run smoothly.

---

### Post by mblanco2000 on 2013-02-19
Ok will do just do not know what WRAP is, sorry.  In the past I had modified my source file, and I think it was a pretty old tutorial that advised me to do the modifications to the source file.  I went back and researched it and well Dapper which kept popping up in the output, is apparently a release of Ubuntu back from 06.

Luckily I had saved my original source file and just re-enabled it, then did the commands to install Skype.  Everything is working fine now.

One other question.  When I installed Skype on my Macbook a few days ago I had the option to sign in w/ facebook.  Is this an option w/ the Linux version?  Thanks for the help.

---

### Post by Nobi on 2013-02-19
hey dear, its amazing cos i used the same command you used and it worked on my laptop but my other laptop i used commands from this link...


[http://www.noobslab.com/2012/11/install-latest-skype-41-in-ubuntu.html](http://www.noobslab.com/2012/11/install-latest-skype-41-in-ubuntu.html)

---

### Post by auxilium on 2013-02-19
Hi,

You may go to the Skype official Download page. Install directly the skype.

[http://www.skype.com/en/download-skype/skype-for-linux/](http://www.skype.com/en/download-skype/skype-for-linux/)

Instructions are straight forward.





Cheers,

---

### Post by ajgreeny on 2013-02-19
You do, however, have a major problem either with your OS version or your sources.list file!

According to the terminal output you showed us, you are still using **Dapper Drake.** I can't even remember which numbered version of Ubuntu that was, (6.04?), but it lost any support, or ability to download and install applications, many years ago.

I therefore recommend that you forget about trying to update or install skype on to that OS version, if it really is Dapper Drake (it probably will not be possible anyway) and get yourself a brand new clean install of 12.04, using whichever DE you prefer.

---

### Post by fuorviatos on 2013-02-19
> **ajgreeny said:**
> You do, however, have a major problem either with your OS version or your sources.list file!

According to the terminal output you showed us, you are still using **Dapper Drake.** I can't even remember which numbered version of Ubuntu that was, (6.04?), but it lost any support, or ability to download and install applications, many years ago.

I therefore recommend that you forget about trying to update or install skype on to that OS version, if it really is Dapper Drake (it probably will not be possible anyway) and get yourself a brand new clean install of 12.04, using whichever DE you prefer.

I agree with that :)

---

### Post by mblanco2000 on 2013-02-19
It was my source file.  I am running the latest version of Ubuntu.  I just had "updated" my source file with old dapper repository.  Got that resolved and skpe is now installed and running.  Thanks.

Anyone know if skype for linux has the ability to login using facebook credientails?

---

