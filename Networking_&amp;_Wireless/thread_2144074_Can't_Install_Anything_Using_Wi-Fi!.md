---
title: "Can't Install Anything Using Wi-Fi!"
date: 2013-05-11
forum: Networking &amp; Wireless
---

### Post by Ashfaqur Rahman on 2013-05-11
I cant install/download anything using apt-get or ubuntu software center via wifi.
If I run:
```
sudo apt-get update
```

It gives following:
```

Ign http://us.archive.ubuntu.com quantal Release.gpg
Ign http://security.ubuntu.com quantal-security Release.gpg         
Ign http://ppa.launchpad.net quantal Release.gpg                               
Ign http://extras.ubuntu.com quantal Release.gpg                               
Ign http://us.archive.ubuntu.com quantal-updates Release.gpg                   
Ign http://security.ubuntu.com quantal-security Release                  
Ign http://extras.ubuntu.com quantal Release                             
Ign http://us.archive.ubuntu.com quantal-backports Release.gpg                 
Ign http://security.ubuntu.com quantal-security/main Sources/DiffIndex         
Ign http://extras.ubuntu.com quantal/main Sources/DiffIndex
Ign http://security.ubuntu.com quantal-security/restricted Sources/DiffIndex
Ign http://extras.ubuntu.com quantal/main i386 Packages/DiffIndex        
Ign http://security.ubuntu.com quantal-security/universe Sources/DiffIndex
Ign http://security.ubuntu.com quantal-security/multiverse Sources/DiffIndex
Ign http://us.archive.ubuntu.com quantal Release
Ign http://ppa.launchpad.net quantal Release                             
Ign http://us.archive.ubuntu.com quantal-updates Release                       
Ign http://security.ubuntu.com quantal-security/main i386 Packages/DiffIndex   
Ign http://ppa.launchpad.net quantal/main Sources/DiffIndex                    
Ign http://us.archive.ubuntu.com quantal-backports Release                     
Ign http://security.ubuntu.com quantal-security/restricted i386 Packages/DiffIndex
Ign http://ppa.launchpad.net quantal/main i386 Packages/DiffIndex              
Ign http://us.archive.ubuntu.com quantal/main Sources/DiffIndex                
Ign http://security.ubuntu.com quantal-security/universe i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com quantal/restricted Sources/DiffIndex          
Ign http://security.ubuntu.com quantal-security/multiverse i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com quantal/universe Sources/DiffIndex            
Ign http://us.archive.ubuntu.com quantal/multiverse Sources/DiffIndex          
Ign http://us.archive.ubuntu.com quantal/main i386 Packages/DiffIndex          
Ign http://us.archive.ubuntu.com quantal/restricted i386 Packages/DiffIndex    
Ign http://us.archive.ubuntu.com quantal/universe i386 Packages/DiffIndex      
Ign http://us.archive.ubuntu.com quantal/multiverse i386 Packages/DiffIndex    
Ign http://extras.ubuntu.com quantal/main Translation-en_US                    
Ign http://extras.ubuntu.com quantal/main Translation-en                       
Err http://extras.ubuntu.com quantal/main Sources                    
  407  Proxy Authentication Required
Err http://extras.ubuntu.com quantal/main i386 Packages                        
  407  Proxy Authentication Required
Ign http://us.archive.ubuntu.com quantal-updates/main Sources/DiffIndex        
Ign http://ppa.launchpad.net quantal/main Translation-en_US                    
Ign http://us.archive.ubuntu.com quantal-updates/restricted Sources/DiffIndex  
Ign http://ppa.launchpad.net quantal/main Translation-en                       
Ign http://us.archive.ubuntu.com quantal-updates/universe Sources/DiffIndex
Err http://ppa.launchpad.net quantal/main Sources                        
  407  Proxy Authentication Required
Ign http://us.archive.ubuntu.com quantal-updates/multiverse Sources/DiffIndex
Err http://ppa.launchpad.net quantal/main i386 Packages                  
  407  Proxy Authentication Required
Ign http://us.archive.ubuntu.com quantal-updates/main i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com quantal-updates/restricted i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com quantal-updates/universe i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com quantal-updates/multiverse i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com quantal-backports/main Sources/DiffIndex
Ign http://us.archive.ubuntu.com quantal-backports/restricted Sources/DiffIndex
Ign http://us.archive.ubuntu.com quantal-backports/universe Sources/DiffIndex
Ign http://us.archive.ubuntu.com quantal-backports/multiverse Sources/DiffIndex
Ign http://us.archive.ubuntu.com quantal-backports/main i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com quantal-backports/restricted i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com quantal-backports/universe i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com quantal-backports/multiverse i386 Packages/DiffIndex
Ign http://security.ubuntu.com quantal-security/main Translation-en_US         
Ign http://security.ubuntu.com quantal-security/main Translation-en
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en_US
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en
Ign http://security.ubuntu.com quantal-security/restricted Translation-en_US
Ign http://security.ubuntu.com quantal-security/restricted Translation-en
Ign http://security.ubuntu.com quantal-security/universe Translation-en_US
Ign http://security.ubuntu.com quantal-security/universe Translation-en
Err http://security.ubuntu.com quantal-security/main Sources
  407  Proxy Authentication Required
Err http://security.ubuntu.com quantal-security/restricted Sources
  407  Proxy Authentication Required
Err http://security.ubuntu.com quantal-security/universe Sources
  407  Proxy Authentication Required
Err http://security.ubuntu.com quantal-security/multiverse Sources
  407  Proxy Authentication Required
Err http://security.ubuntu.com quantal-security/main i386 Packages
  407  Proxy Authentication Required
Err http://security.ubuntu.com quantal-security/restricted i386 Packages
  407  Proxy Authentication Required
Err http://security.ubuntu.com quantal-security/universe i386 Packages
  407  Proxy Authentication Required
Err http://security.ubuntu.com quantal-security/multiverse i386 Packages
  407  Proxy Authentication Required
Ign http://us.archive.ubuntu.com quantal/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal/main Translation-en
Ign http://us.archive.ubuntu.com quantal/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal/multiverse Translation-en
Ign http://us.archive.ubuntu.com quantal/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal/restricted Translation-en
Ign http://us.archive.ubuntu.com quantal/universe Translation-en_US
Ign http://us.archive.ubuntu.com quantal/universe Translation-en
Ign http://us.archive.ubuntu.com quantal-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/main Translation-en
Ign http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com quantal-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com quantal-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/universe Translation-en
Ign http://us.archive.ubuntu.com quantal-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/main Translation-en
Ign http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en
Ign http://us.archive.ubuntu.com quantal-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/restricted Translation-en
Ign http://us.archive.ubuntu.com quantal-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/universe Translation-en
Err http://us.archive.ubuntu.com quantal/main Sources
  407  Proxy Authentication Required
Err http://us.archive.ubuntu.com quantal/restricted Sources
  407  Proxy Authentication Required
Err http://us.archive.ubuntu.com quantal/universe Sources
  407  Proxy Authentication Required
Err http://us.archive.ubuntu.com quantal/multiverse Sources
  407  Proxy Authentication Required
Err http://us.archive.ubuntu.com quantal/main i386 Packages
  407  Proxy Authentication Required
Err http://us.archive.ubuntu.com quantal/restricted i386 Packages
  407  Proxy Authentication Required
Err http://us.archive.ubuntu.com quantal/universe i386 Packages
  407  Proxy Authentication Required
Err http://us.archive.ubuntu.com quantal/multiverse i386 Packages
  407  Proxy Authentication Required
Err http://us.archive.ubuntu.com quantal-updates/main Sources
  407  Proxy Authentication Required
Err http://us.archive.ubuntu.com quantal-updates/restricted Sources
  407  Proxy Authentication Required
Err http://us.archive.ubuntu.com quantal-updates/universe Sources
  407  Proxy Authentication Required
Err http://us.archive.ubuntu.com quantal-updates/multiverse Sources
  407  Proxy Authentication Required
Err http://us.archive.ubuntu.com quantal-updates/main i386 Packages
  407  Proxy Authentication Required
Err http://us.archive.ubuntu.com quantal-updates/restricted i386 Packages
  407  Proxy Authentication Required
Err http://us.archive.ubuntu.com quantal-updates/universe i386 Packages
  407  Proxy Authentication Required
Err http://us.archive.ubuntu.com quantal-updates/multiverse i386 Packages
  407  Proxy Authentication Required
Err http://us.archive.ubuntu.com quantal-backports/main Sources
  407  Proxy Authentication Required
Err http://us.archive.ubuntu.com quantal-backports/restricted Sources
  407  Proxy Authentication Required
Err http://us.archive.ubuntu.com quantal-backports/universe Sources
  407  Proxy Authentication Required
Err http://us.archive.ubuntu.com quantal-backports/multiverse Sources
  407  Proxy Authentication Required
Err http://us.archive.ubuntu.com quantal-backports/main i386 Packages
  407  Proxy Authentication Required
Err http://us.archive.ubuntu.com quantal-backports/restricted i386 Packages
  407  Proxy Authentication Required
Err http://us.archive.ubuntu.com quantal-backports/universe i386 Packages
  407  Proxy Authentication Required
Err http://us.archive.ubuntu.com quantal-backports/multiverse i386 Packages
  407  Proxy Authentication Required
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources  407  Proxy Authentication Required

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/quantal/main/source/Sources  407  Proxy Authentication Required

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources  407  Proxy Authentication Required

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages  407  Proxy Authentication Required

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources  407  Proxy Authentication Required

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources  407  Proxy Authentication Required

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages  407  Proxy Authentication Required

W: Failed to fetch http://ppa.launchpad.net/linuxonly/modem+manager+gui/ubuntu/dists/quantal/main/source/Sources  407  Proxy Authentication Required

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages  407  Proxy Authentication Required

W: Failed to fetch http://ppa.launchpad.net/linuxonly/modem+manager+gui/ubuntu/dists/quantal/main/binary-i386/Packages  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources  407  Proxy Authentication Required

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources  407  Proxy Authentication Required

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages  407  Proxy Authentication Required

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages  407  Proxy Authentication Required

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

If I try to install via software center it gives this  [http://s22.postimg.org/nrc8l11mp/Screenshot_from_2013_05_11_11_08_04.png](http://s22.postimg.org/nrc8l11mp/Screenshot_from_2013_05_11_11_08_04.png)

---

### Post by 2F4U on 2013-05-11
Looks to me as if you are accessing the internet through a proxy. Is that correct? It seems as if apt-get is not configured to use a proxy.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

---

### Post by Ashfaqur Rahman on 2013-05-19
I have tried BASH rc method (as I want other application to work too) but it didn't work for me!!
```

http_proxy=http://username:password@yourproxyaddress:proxyport
```

Its giving following errors:
```

Ign http://us.archive.ubuntu.com quantal-backports/universe i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com quantal-backports/multiverse i386 Packages/DiffIndex
Err http://security.ubuntu.com quantal-security/main Translation-en_US       
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com quantal-security/main Translation-en          
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com quantal-security/multiverse Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com quantal-security/multiverse Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com quantal-security/restricted Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com quantal-security/restricted Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com quantal-security/universe Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com quantal-security/universe Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com quantal-security/main Sources                 
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com quantal-security/restricted Sources           
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com quantal-security/universe Sources             
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com quantal-security/multiverse Sources           
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com quantal-security/main i386 Packages           
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com quantal-security/restricted i386 Packages     
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com quantal-security/universe i386 Packages       
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com quantal-security/multiverse i386 Packages     
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal/main Translation-en_US              
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal/main Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal/multiverse Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal/multiverse Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal/restricted Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal/restricted Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal/universe Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal/universe Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-updates/main Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-updates/main Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-updates/restricted Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-updates/restricted Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-updates/universe Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-updates/universe Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-backports/main Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-backports/main Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-backports/restricted Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-backports/restricted Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-backports/universe Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-backports/universe Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal/main Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal/restricted Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal/universe Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal/multiverse Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal/main i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal/restricted i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal/universe i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal/multiverse i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-updates/main Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-updates/restricted Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-updates/universe Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-updates/multiverse Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-updates/main i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-updates/restricted i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-updates/universe i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-updates/multiverse i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-backports/main Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-backports/restricted Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-backports/universe Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-backports/multiverse Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-backports/main i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-backports/restricted i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-backports/universe i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com quantal-backports/multiverse i386 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/Release.gpg  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/quantal/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/linuxonly/modem+manager+gui/ubuntu/dists/quantal/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/main/i18n/Translation-en_US  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/main/i18n/Translation-en  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/i18n/Translation-en  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/i18n/Translation-en_US  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/i18n/Translation-en  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/i18n/Translation-en_US  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/i18n/Translation-en  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/linuxonly/modem+manager+gui/ubuntu/dists/quantal/main/i18n/Translation-en_US  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/linuxonly/modem+manager+gui/ubuntu/dists/quantal/main/i18n/Translation-en  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/quantal/main/i18n/Translation-en_US  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/quantal/main/i18n/Translation-en  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/quantal/main/source/Sources  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/linuxonly/modem+manager+gui/ubuntu/dists/quantal/main/source/Sources  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/linuxonly/modem+manager+gui/ubuntu/dists/quantal/main/binary-i386/Packages  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

