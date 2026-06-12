---
title: "apt-get update fails"
date: 2011-04-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by 65 mustang on 2011-04-14
```
:~$ sudo apt-get update
Ign http://security.ubuntu.com natty-security InRelease
Ign http://us.archive.ubuntu.com natty InRelease                    
Ign http://us.archive.ubuntu.com natty-updates InRelease             
Ign http://extras.ubuntu.com natty InRelease                         
Ign http://archive.ubuntu.com natty InRelease                        
Hit http://security.ubuntu.com natty-security Release.gpg            
Hit http://us.archive.ubuntu.com natty Release.gpg                   
Hit http://extras.ubuntu.com natty Release.gpg                       
Hit http://archive.ubuntu.com natty Release.gpg                      
Hit http://security.ubuntu.com natty-security Release                
Hit http://us.archive.ubuntu.com natty-updates Release.gpg                     
Hit http://extras.ubuntu.com natty Release                                     
Hit http://archive.ubuntu.com natty Release                                    
Hit http://us.archive.ubuntu.com natty Release                                 
Hit http://security.ubuntu.com natty-security/restricted Sources               
Hit http://extras.ubuntu.com natty/main amd64 Packages                         
Hit http://archive.ubuntu.com natty/main Sources                     
Hit http://us.archive.ubuntu.com natty-updates Release               
Hit http://security.ubuntu.com natty-security/main Sources                     
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://security.ubuntu.com natty-security/multiverse Sources     
Hit http://security.ubuntu.com natty-security/universe Sources       
Hit http://security.ubuntu.com natty-security/main amd64 Packages    
Hit http://security.ubuntu.com natty-security/restricted amd64 Packages        
Hit http://archive.ubuntu.com natty/restricted Sources                         
Hit http://us.archive.ubuntu.com natty/restricted Sources                      
Hit http://us.archive.ubuntu.com natty/multiverse Sources            
Hit http://us.archive.ubuntu.com natty/main amd64 Packages
Hit http://security.ubuntu.com natty-security/universe amd64 Packages
Hit http://security.ubuntu.com natty-security/multiverse amd64 Packages
Ign http://security.ubuntu.com natty-security/main TranslationIndex
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex
Ign http://security.ubuntu.com natty-security/universe TranslationIndex
Hit http://us.archive.ubuntu.com natty/restricted amd64 Packages
Hit http://us.archive.ubuntu.com natty/universe amd64 Packages
Hit http://us.archive.ubuntu.com natty/multiverse amd64 Packages
Ign http://us.archive.ubuntu.com natty/main TranslationIndex         
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex   
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex   
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex     
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources    
Hit http://us.archive.ubuntu.com natty-updates/main Sources          
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources    
Hit http://us.archive.ubuntu.com natty-updates/universe Sources      
Hit http://us.archive.ubuntu.com natty-updates/main amd64 Packages   
Hit http://us.archive.ubuntu.com natty-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com natty-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com natty-updates/multiverse amd64 Packages
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex
Get:1 http://us.archive.ubuntu.com natty/main Sources [1,080 kB]     
Get:2 http://us.archive.ubuntu.com natty/universe Sources [5,431 kB]           
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://extras.ubuntu.com natty/main Translation-en               
Ign http://security.ubuntu.com natty-security/main Translation-en_US
Ign http://security.ubuntu.com natty-security/main Translation-en
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en_US
Ign http://security.ubuntu.com natty-security/universe Translation-en
Ign http://us.archive.ubuntu.com natty/main Translation-en_US
Ign http://us.archive.ubuntu.com natty/main Translation-en
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty/restricted Translation-en
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty/universe Translation-en
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en
Fetched 2 B in 3s (1 B/s)
W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty_main_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Note:
```
W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty_main_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Then:
```
~$ sudo apt-get upgrade
Reading package lists... Done
~$ ency tree... 50%
```
program exits.

I cant update my system.  Been running 11.04 for about a month with no problems.  Help!?

---

### Post by seeker5528 on 2011-04-15
> **65 mustang said:**
> ```
W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources  Hash Sum mismatch
```


I had that happening to me intermittently in Debian for a while. Usually opening a terminal window and typing
```
sudo rm -rf /var/lib/apt/lists/partial/*
```

would take care of it, some times I had to do it multiple times. Sometimes I would just have to wait a little while and try again.

Later, Seeker

---

