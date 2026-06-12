---
title: "ubuntu pudate manager is not working and netbook is not connecting to server"
date: 2013-01-07
forum: Networking &amp; Wireless
---

### Post by Vidyashree on 2013-01-07
I have the problem with my update manager. I am using ubuntu 12.04. I cannot install any package in terminal , my system is not exposed to any updates and I cannot install any package in ubuntu software center. 
Now i cannot connect to the sever computer using SSH login. I cannot add printer connected to the server in my netbook. Don't know what problem I am having in my netbook. Can anyone Please help me to come out of this...

---

### Post by ibjsb4 on 2013-01-07
Getting any error messages you can post?

---

### Post by Vidyashree on 2013-01-07
This is the output of sudo apt-get update

kalike@kalike-N102SP-N100SP-N101SP:~$ sudo apt-get update 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick InRelease                                                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security InRelease                                                      
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick InRelease                                                             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise InRelease                                                              
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise InRelease                                                                  
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                                                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates InRelease                                                        
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                                                              
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-security InRelease                                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                                                       
Err [http://linux.dropbox.com](http://linux.dropbox.com) precise Release.gpg                                                                
  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                                     
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports InRelease                                                      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates InRelease                                                      
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                                                    
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                                                           
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise Release                                                                    
Ign [http://dl.google.com](http://dl.google.com) stable Release                                                                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed InRelease                                                       
Err [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                                                            
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-proposed InRelease                                                     
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                                                     
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg                                                              
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                                                        
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick Release                                                               
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports InRelease                                                    
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                           
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main TranslationIndex                                                      
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg                                                      
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                                                         
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release.gpg                                                            
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://archive.canonical.com](http://archive.canonical.com) precise Release                                                                
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports Release.gpg                                                    
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-security Release.gpg                                                   
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed Release.gpg                                                     
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner TranslationIndex                                              
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release.gpg                                                    
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release                                                                  
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-proposed Release.gpg                                                   
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release                                                          
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex                                               
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release.gpg                                                  
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports Release                                                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main TranslationIndex                                          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release                                                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse TranslationIndex                                    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-security Release                                                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed Release                                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted TranslationIndex                                    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release                                                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe TranslationIndex                                      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-proposed Release                                                       
Err [http://linux.dropbox.com](http://linux.dropbox.com) precise/main i386 Packages                                                         
  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)
Err [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                              
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release                                                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main TranslationIndex                                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse TranslationIndex                                              
Err [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en_IN                                                     
  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)
Err [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN                                                          
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted TranslationIndex                                              
Err [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                             
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex                                           
Err [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en                                                        
  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe TranslationIndex                                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex                                       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main TranslationIndex                                                  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse TranslationIndex                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main TranslationIndex                                            
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted TranslationIndex                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse TranslationIndex                                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted TranslationIndex                                      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe TranslationIndex                                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe TranslationIndex                                        
Err [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                                                 
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                                                  
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/main TranslationIndex                                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/multiverse TranslationIndex                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/restricted TranslationIndex                                    
Err [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Translation-en_IN                                             
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/universe TranslationIndex                                      
Err [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Translation-en                                                
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
22% [Connecting to archive.ubuntu.com] [Connecting to security.ubuntu.com]

---

### Post by Vidyashree on 2013-01-07
I'm having precise running in my netbook but don't know why it is showing maverick in sudo apt-get update output.!

Pls help with this, i'm unable to install any software using apt-get and also in Ubuntu software center. :(


thanks in advance:)

---

### Post by ibjsb4 on 2013-01-07
First off, please use code tags.  

```
kalike@kalike-N102SP-N100SP-N101SP:~$ sudo apt-get update 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick InRelease                                                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security InRelease                                                      
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick InRelease                                                             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise InRelease                                                              
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise InRelease                                                                  
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                                                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates InRelease                                                        
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                                                              
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-security InRelease                                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                                                       
Err [http://linux.dropbox.com](http://linux.dropbox.com) precise Release.gpg                                                                
  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                                     
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports InRelease                                                      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates InRelease                                                      
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                                                    
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                                                           
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise Release                                                                    
Ign [http://dl.google.com](http://dl.google.com) stable Release                                                                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed InRelease                                                       
Err [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                                                            
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-proposed InRelease                                                     
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                                                     
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg                                                              
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                                                        
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick Release                                                               
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports InRelease                                                    
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                           
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main TranslationIndex                                                      
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg                                                      
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                                                         
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release.gpg                                                            
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://archive.canonical.com](http://archive.canonical.com) precise Release                                                                
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports Release.gpg                                                    
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-security Release.gpg                                                   
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed Release.gpg                                                     
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner TranslationIndex                                              
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release.gpg                                                    
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release                                                                  
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-proposed Release.gpg                                                   
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release                                                          
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex                                               
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release.gpg                                                  
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports Release                                                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main TranslationIndex                                          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release                                                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse TranslationIndex                                    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-security Release                                                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed Release                                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted TranslationIndex                                    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release                                                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe TranslationIndex                                      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-proposed Release                                                       
Err [http://linux.dropbox.com](http://linux.dropbox.com) precise/main i386 Packages                                                         
  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)
Err [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                              
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release                                                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main TranslationIndex                                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse TranslationIndex                                              
Err [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en_IN                                                     
  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)
Err [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN                                                          
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted TranslationIndex                                              
Err [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                             
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex                                           
Err [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en                                                        
  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe TranslationIndex                                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex                                       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main TranslationIndex                                                  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse TranslationIndex                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main TranslationIndex                                            
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted TranslationIndex                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse TranslationIndex                                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted TranslationIndex                                      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe TranslationIndex                                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe TranslationIndex                                        
Err [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                                                 
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                                                  
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/main TranslationIndex                                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/multiverse TranslationIndex                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/restricted TranslationIndex                                    
Err [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Translation-en_IN                                             
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/universe TranslationIndex                                      
Err [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Translation-en                                                
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
22% [Connecting to archive.ubuntu.com] [Connecting to security.ubuntu.com]
```

[ATTACH]229735[/ATTACH]

Are you sure your running 12o4?

```
cat /etc/issue
```

And please post the output of:

```
cat -n /etc/apt/sources.list
```

---

### Post by snowpine on 2013-01-07
Maverick has reached its "end of life" and is completely unsupported. I recommend a fresh reinstall of the current 12.04 or 12.10.

---

### Post by ibjsb4 on 2013-01-07
> **snowpine said:**
> Maverick has reached its "end of life" and is completely unsupported. I recommend a fresh reinstall of the current 12.04 or 12.10.

Yep, thats probably going to be the bottom line.  But thought I give it a try.

---

