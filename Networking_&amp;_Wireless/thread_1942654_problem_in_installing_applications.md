---
title: "problem in installing applications"
date: 2012-03-18
forum: Networking &amp; Wireless
---

### Post by vicky9555 on 2012-03-18
when ever i am installing apps in software center the following messages are displayed 

 
Check your Internet connection.

The action would require the installation of packages from not authenticated sources.

pls tell me a solution 

but my internet is working properly and all the downloads and sites are opening i am using tikona net

---

### Post by 2F4U on 2012-03-18
Are you attempting to install from third party repositories which do not provide a GPG key? What repositories are you using?

---

### Post by 3v3rgr33n on 2012-03-18
> **2F4U said:**
> third party repositories which do not provide a GPG key? 

I know this has nuthin to do wit this thread but what is a "GPG" key.

Ive been trying to add repositories, i wanted to download this cool theme i saw. It kept telling me about a "GPG" key error or smthn

---

### Post by jerrrys on 2012-03-18
vicky:  open a terminal and enter

sudo apt-get update

any errors?

3v3r:
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=gpg+key&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=gpg+key&sa=Search&cof=FORID:9)

---

### Post by vicky9555 on 2012-03-20
i am trying to install GMIC application

---

### Post by 3v3rgr33n on 2012-03-20
Vicky, Im not an expert but have you checked your server connections?

Last time I couldnt download stuff from the download centre, I was connected at a server in the Ivory coast, and I'm in S.A.

---

### Post by vicky9555 on 2012-03-26
ok where to check the server location ????

---

### Post by matt_symes on 2012-03-26
Hi

@vicky9555.

Might i suggest you follow jerrrys' advice as well and run the command

```
sudo apt-get update
```

from the terminal ? To get a terminal press ctrl + alt + t at the same time.

After entering the command, enter your password. It will not be echoed to the screen.

Copy and paste the results from the terminal by "highlighting the text ->right click -> copy" and paste it into your next post between code tags 

[noparse]```
like this
```[/noparse]

to get output like this

```
like this
```

Kind regards

---

### Post by raja.genupula on 2012-03-26
hi please post that error messgaes here . so you're saying that some GPG errors right . 
open your terminal and do this 
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

and again try to install from terminal and if any error again . post that output here .

---

### Post by vicky9555 on 2012-03-30
This is what i get in the terminal pls help me 

```
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric Release.gpg
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric Release
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main TranslationIndex
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted TranslationIndex
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-en
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-en
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://security.ubuntu.com oneiric-security InRelease                      
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://in.archive.ubuntu.com oneiric InRelease                             
Ign http://in.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://in.archive.ubuntu.com oneiric-backports InRelease                   
Ign http://archive.ubuntu.com oneiric InRelease                                
Ign http://archive.ubuntu.com oneiric-updates InRelease                        
Ign http://archive.ubuntu.com oneiric-proposed InRelease                       
Get:1 http://security.ubuntu.com oneiric-security Release.gpg [198 B]          
Get:2 http://ppa.launchpad.net oneiric Release.gpg [316 B]                     
Get:3 http://extras.ubuntu.com oneiric Release.gpg [72 B]                      
Get:4 http://in.archive.ubuntu.com oneiric Release.gpg [198 B]                 
Get:5 http://archive.canonical.com oneiric Release.gpg [198 B]                 
Get:6 http://archive.ubuntu.com oneiric Release.gpg [198 B]                    
Get:7 http://security.ubuntu.com oneiric-security Release [40.8 kB]            
Get:8 http://ppa.launchpad.net oneiric Release.gpg [316 B]                     
Hit http://extras.ubuntu.com oneiric Release                                   
Get:9 http://in.archive.ubuntu.com oneiric-updates Release.gpg [198 B]         
Err http://extras.ubuntu.com oneiric Release                                   
  
Get:10 http://archive.ubuntu.com oneiric-updates Release.gpg [198 B]           
Hit http://archive.canonical.com oneiric Release                               
Ign http://archive.canonical.com oneiric Release                               
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://ppa.launchpad.net oneiric Release                                   
Get:11 http://in.archive.ubuntu.com oneiric-backports Release.gpg [198 B]      
Get:12 http://archive.ubuntu.com oneiric-proposed Release.gpg [198 B]          
Ign http://archive.canonical.com oneiric/partner Sources/DiffIndex             
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://in.archive.ubuntu.com oneiric Release                               
Hit http://archive.ubuntu.com oneiric Release                                  
Err http://ppa.launchpad.net oneiric Release                                   
  
Ign http://in.archive.ubuntu.com oneiric Release                               
Ign http://archive.canonical.com oneiric/partner i386 Packages/DiffIndex       
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Ign http://archive.ubuntu.com oneiric Release                                  
Ign http://ppa.launchpad.net oneiric/main Sources/DiffIndex                    
Ign http://ppa.launchpad.net oneiric/main i386 Packages/DiffIndex              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Get:13 http://in.archive.ubuntu.com oneiric-updates Release [40.8 kB]          
Get:14 http://archive.ubuntu.com oneiric-updates Release [40.8 kB]             
Get:15 http://archive.canonical.com oneiric/partner Sources [2,575 B]          
Get:16 http://ppa.launchpad.net oneiric/main Sources [506 B]                   
Get:17 http://security.ubuntu.com oneiric-security/main Sources [34.8 kB]      
Get:18 http://archive.canonical.com oneiric/partner i386 Packages [4,329 B]    
Hit http://in.archive.ubuntu.com oneiric-backports Release                     
Err http://in.archive.ubuntu.com oneiric-backports Release                     
  
Get:19 http://archive.ubuntu.com oneiric-proposed Release [40.8 kB]            
Get:20 http://ppa.launchpad.net oneiric/main i386 Packages [572 B]             
Ign http://in.archive.ubuntu.com oneiric/main Sources/DiffIndex                
Ign http://archive.ubuntu.com oneiric/main i386 Packages/DiffIndex             
Ign http://in.archive.ubuntu.com oneiric/restricted Sources/DiffIndex          
Get:21 http://security.ubuntu.com oneiric-security/restricted Sources [14 B]   
Ign http://in.archive.ubuntu.com oneiric/universe Sources/DiffIndex            
Get:22 http://security.ubuntu.com oneiric-security/universe Sources [13.3 kB]  
Ign http://in.archive.ubuntu.com oneiric/multiverse Sources/DiffIndex          
Ign http://archive.ubuntu.com oneiric/restricted i386 Packages/DiffIndex       
Ign http://in.archive.ubuntu.com oneiric/main i386 Packages/DiffIndex          
Get:23 http://security.ubuntu.com oneiric-security/multiverse Sources [1,638 B]
Get:24 http://archive.ubuntu.com oneiric/main TranslationIndex [3,289 B]       
Get:25 http://security.ubuntu.com oneiric-security/main i386 Packages [93.0 kB]
Get:26 http://archive.ubuntu.com oneiric/restricted TranslationIndex [2,263 B] 
Ign http://in.archive.ubuntu.com oneiric/restricted i386 Packages/DiffIndex    
Get:27 http://archive.ubuntu.com oneiric-updates/main i386 Packages [308 kB]   
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Ign http://in.archive.ubuntu.com oneiric/universe i386 Packages/DiffIndex      
Ign http://archive.canonical.com oneiric/partner Translation-en                
Ign http://in.archive.ubuntu.com oneiric/multiverse i386 Packages/DiffIndex    
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Get:28 http://in.archive.ubuntu.com oneiric/main TranslationIndex [3,289 B]    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Get:29 http://in.archive.ubuntu.com oneiric/multiverse TranslationIndex [2,265 B]
Get:30 http://in.archive.ubuntu.com oneiric/restricted TranslationIndex [2,263 B]
Get:31 http://security.ubuntu.com oneiric-security/restricted i386 Packages [14 B]
Get:32 http://in.archive.ubuntu.com oneiric/universe TranslationIndex [2,640 B]
Get:33 http://security.ubuntu.com oneiric-security/universe i386 Packages [31.1 kB]
Get:34 http://in.archive.ubuntu.com oneiric-updates/main Sources [133 kB]      
Get:35 http://archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,968 B]
Get:36 http://archive.ubuntu.com oneiric-updates/main TranslationIndex [74 B]  
Get:37 http://security.ubuntu.com oneiric-security/multiverse i386 Packages [3,372 B]
Get:38 http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B]
Get:39 http://security.ubuntu.com oneiric-security/main TranslationIndex [73 B]
Get:40 http://archive.ubuntu.com oneiric-proposed/restricted i386 Packages [2,394 B]
Get:41 http://security.ubuntu.com oneiric-security/multiverse TranslationIndex [72 B]
Get:42 http://archive.ubuntu.com oneiric-proposed/main i386 Packages [163 kB]  
Get:43 http://security.ubuntu.com oneiric-security/restricted TranslationIndex [70 B]
Get:44 http://security.ubuntu.com oneiric-security/universe TranslationIndex [73 B]
Get:45 http://in.archive.ubuntu.com oneiric-updates/restricted Sources [1,337 B]
Get:46 http://security.ubuntu.com oneiric-security/main Translation-en [51.5 kB]
Get:47 http://in.archive.ubuntu.com oneiric-updates/universe Sources [48.8 kB] 
Get:48 http://archive.ubuntu.com oneiric-proposed/multiverse i386 Packages [1,044 B]
Get:49 http://in.archive.ubuntu.com oneiric-updates/multiverse Sources [3,661 B]
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Get:50 http://archive.ubuntu.com oneiric-proposed/universe i386 Packages [23.7 kB]
Get:51 http://in.archive.ubuntu.com oneiric-updates/main i386 Packages [308 kB]
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Hit http://security.ubuntu.com oneiric-security/universe Translation-en                                                                      
Get:52 http://archive.ubuntu.com oneiric-proposed/main TranslationIndex [73 B]                                                               
Get:53 http://archive.ubuntu.com oneiric-proposed/multiverse TranslationIndex [71 B]                                                         
Get:54 http://archive.ubuntu.com oneiric-proposed/restricted TranslationIndex [71 B]                                                         
Get:55 http://archive.ubuntu.com oneiric-proposed/universe TranslationIndex [73 B]                                                           
Get:56 http://archive.ubuntu.com oneiric/main i386 Packages [1,226 kB]                                                                       
Get:57 http://archive.ubuntu.com oneiric/restricted i386 Packages [8,216 B]                                                                  
Hit http://archive.ubuntu.com oneiric/main Translation-en                                                                                    
Hit http://archive.ubuntu.com oneiric/restricted Translation-en                                                                              
Get:58 http://archive.ubuntu.com oneiric-updates/main Translation-en [143 kB]                                                                
Get:59 http://in.archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,968 B]                                                       
Get:60 http://in.archive.ubuntu.com oneiric-updates/universe i386 Packages [105 kB]                                                          
Hit http://archive.ubuntu.com oneiric-updates/restricted Translation-en                                                                      
Get:61 http://archive.ubuntu.com oneiric-proposed/main Translation-en [53.9 kB]                                                              
Get:62 http://in.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [6,356 B]                                                       
Hit http://archive.ubuntu.com oneiric-proposed/multiverse Translation-en                                                                     
Get:63 http://in.archive.ubuntu.com oneiric-updates/main TranslationIndex [74 B]
Hit http://archive.ubuntu.com oneiric-proposed/restricted Translation-en                                                                     
Get:64 http://in.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]                                                       
Get:65 http://archive.ubuntu.com oneiric-proposed/universe Translation-en [14.6 kB]                                                          
Get:66 http://in.archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B]                                                       
Get:67 http://in.archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]                                                         
Get:68 http://in.archive.ubuntu.com oneiric/main Sources [877 kB]                                                                            
Get:69 http://in.archive.ubuntu.com oneiric/restricted Sources [5,351 B]                                                                     
Get:70 http://in.archive.ubuntu.com oneiric/universe Sources [4,677 kB]                                                                      
Get:71 http://in.archive.ubuntu.com oneiric/multiverse Sources [149 kB]                                                                      
Get:72 http://in.archive.ubuntu.com oneiric/main i386 Packages [1,226 kB]                                                                    
Get:73 http://in.archive.ubuntu.com oneiric/restricted i386 Packages [8,216 B]                                                               
Get:74 http://in.archive.ubuntu.com oneiric/universe i386 Packages [4,468 kB]                                                                
Get:75 http://in.archive.ubuntu.com oneiric/multiverse i386 Packages [119 kB]                                                                
Hit http://in.archive.ubuntu.com oneiric/main Translation-en                                                                                 
Hit http://in.archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://in.archive.ubuntu.com oneiric/restricted Translation-en
Hit http://in.archive.ubuntu.com oneiric/universe Translation-en
Get:76 http://in.archive.ubuntu.com oneiric-updates/main Translation-en [143 kB]
Hit http://in.archive.ubuntu.com oneiric-updates/multiverse Translation-en                                                                   
Hit http://in.archive.ubuntu.com oneiric-updates/restricted Translation-en
Get:77 http://in.archive.ubuntu.com oneiric-updates/universe Translation-en [63.0 kB]
Fetched 14.7 MB in 26min 53s (9,119 B/s)                                                                                                     
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://archive.canonical.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://ppa.launchpad.net oneiric Release: The following signatures were invalid: BADSIG 928C86FE5879C434 Launchpad PPA for Claudio Novais
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://ppa.launchpad.net oneiric Release: The following signatures were invalid: BADSIG 6AF0E1940624A220 Launchpad PPA for TualatriX

W: GPG error: http://in.archive.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://archive.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://in.archive.ubuntu.com oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/dists/oneiric/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release  

W: Failed to fetch http://ppa.launchpad.net/tualatrix/next/ubuntu/dists/oneiric/Release  

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ oneiric-security/main i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_oneiric-security_main_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ oneiric-security/restricted i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_oneiric-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ oneiric/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages)

```

---

### Post by matt_symes on 2012-03-30
Hi

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://archive.canonical.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://ppa.launchpad.net oneiric Release: The following signatures were invalid: BADSIG 928C86FE5879C434 Launchpad PPA for Claudio Novais
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://ppa.launchpad.net oneiric Release: The following signatures were invalid: BADSIG 6AF0E1940624A220 Launchpad PPA for TualatriX

W: GPG error: http://in.archive.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://archive.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://in.archive.ubuntu.com oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/dists/oneiric/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release  

W: Failed to fetch http://ppa.launchpad.net/tualatrix/next/ubuntu/dists/oneiric/Release  

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ oneiric-security/main i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_oneiric-security_main_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ oneiric-security/restricted i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_oneiric-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ oneiric/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages)
```

There are multiple errors here. Can you start off by opening a terminal and typing

```
grep -n ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
```

Post the results back here. We'll remove the duplicate entries

Your main problem is the BADSIG errors though. They might be fixed by changing to a new mirror.

Kind regards

---

