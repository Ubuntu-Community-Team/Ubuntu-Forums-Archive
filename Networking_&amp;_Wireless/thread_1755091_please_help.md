---
title: "please help"
date: 2011-05-10
forum: Networking &amp; Wireless
---

### Post by marwa7a on 2011-05-10
I'm still a beginner in Ubuntu and I recently used my home Internet connection to download and install it with no problems there.. the problem was with my work network which has this tunnel thing that requires every user to enter an IPv4 address, mask, gateway and DNS server.. then a connection proxy.. then after all this when I try to open Firefox it demands a User name and Password Authentication which every employee is given.. now Firefox works fine cuz it shows the username/pass window but all the other programs doesn't.. like Software Center and Update Manager and all the other programs.. I tried adding a username/pass in network connection by adding 802.1x Security and using the MD5 authentication and adding the username/pass there but the connection cuts off and it doesn't work again until I remove the Security option in the "editing connection" window.. and frankly I have no Idea how to configure TLS, Tunneled TLS or PEAP security options since all the company gave us to connect was the network's IPv4 settings, proxy and username/password.. I'm currently using Firefox to post this message and it's working fine.. I'm sure there must be a way to make the connection work.. help is so.. sooo. soooooooo appreciated :(

---

### Post by marwa7a on 2011-05-11
```
Ign http://archive.getdeb.net natty-getdeb InRelease
Ign http://ftp.linux.org.tr natty InRelease                         
Ign http://ftp.linux.org.tr natty-updates InRelease                  
Ign http://ftp.linux.org.tr natty-security InRelease                 
Ign http://archive.getdeb.net natty-getdeb Release.gpg               
Ign http://ftp.linux.org.tr natty Release.gpg                        
Ign http://ftp.linux.org.tr natty-updates Release.gpg                
Ign http://ftp.linux.org.tr natty-security Release.gpg               
Ign http://archive.getdeb.net natty-getdeb Release                   
Ign http://ftp.linux.org.tr natty Release                            
Ign http://ftp.linux.org.tr natty-updates Release                    
Ign http://ftp.linux.org.tr natty-security Release                   
Ign http://archive.getdeb.net natty-getdeb/apps TranslationIndex     
Ign http://ftp.linux.org.tr natty/main Sources/DiffIndex             
Ign http://ftp.linux.org.tr natty/restricted Sources/DiffIndex       
Ign http://ftp.linux.org.tr natty/universe Sources/DiffIndex         
Ign http://ftp.linux.org.tr natty/multiverse Sources/DiffIndex       
Ign http://ftp.linux.org.tr natty/main amd64 Packages/DiffIndex      
Ign http://ftp.linux.org.tr natty/restricted amd64 Packages/DiffIndex
Ign http://ftp.linux.org.tr natty/universe amd64 Packages/DiffIndex  
Ign http://ftp.linux.org.tr natty/multiverse amd64 Packages/DiffIndex
Ign http://ftp.linux.org.tr natty/main TranslationIndex              
Ign http://ftp.linux.org.tr natty/multiverse TranslationIndex        
Ign http://ftp.linux.org.tr natty/restricted TranslationIndex        
Ign http://ftp.linux.org.tr natty/universe TranslationIndex          
Ign http://ftp.linux.org.tr natty-updates/main Sources/DiffIndex     
Ign http://ftp.linux.org.tr natty-updates/restricted Sources/DiffIndex
Ign http://ftp.linux.org.tr natty-updates/universe Sources/DiffIndex 
Ign http://ftp.linux.org.tr natty-updates/multiverse Sources/DiffIndex
Err http://archive.getdeb.net natty-getdeb/apps amd64 Packages       
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign http://ftp.linux.org.tr natty-updates/main amd64 Packages/DiffIndex
Ign http://ftp.linux.org.tr natty-updates/restricted amd64 Packages/DiffIndex
Ign http://ftp.linux.org.tr natty-updates/universe amd64 Packages/DiffIndex
Ign http://archive.getdeb.net natty-getdeb/apps Translation-en_US              
Ign http://archive.getdeb.net natty-getdeb/apps Translation-en                 
Ign http://ftp.linux.org.tr natty-updates/multiverse amd64 Packages/DiffIndex
Ign http://ftp.linux.org.tr natty-updates/main TranslationIndex      
Ign http://ftp.linux.org.tr natty-updates/multiverse TranslationIndex
Ign http://ftp.linux.org.tr natty-updates/restricted TranslationIndex
Ign http://ftp.linux.org.tr natty-updates/universe TranslationIndex
Ign http://ftp.linux.org.tr natty-security/main Sources/DiffIndex
Ign http://ftp.linux.org.tr natty-security/restricted Sources/DiffIndex
Ign http://ftp.linux.org.tr natty-security/universe Sources/DiffIndex
Ign http://ftp.linux.org.tr natty-security/multiverse Sources/DiffIndex
Ign http://ftp.linux.org.tr natty-security/main amd64 Packages/DiffIndex
Ign http://ftp.linux.org.tr natty-security/restricted amd64 Packages/DiffIndex
Ign http://ftp.linux.org.tr natty-security/universe amd64 Packages/DiffIndex
Ign http://ftp.linux.org.tr natty-security/multiverse amd64 Packages/DiffIndex
Ign http://ftp.linux.org.tr natty-security/main TranslationIndex
Ign http://ftp.linux.org.tr natty-security/multiverse TranslationIndex
Ign http://ftp.linux.org.tr natty-security/restricted TranslationIndex
Ign http://ftp.linux.org.tr natty-security/universe TranslationIndex
Err http://ftp.linux.org.tr natty/main Sources 
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://ftp.linux.org.tr natty/restricted Sources
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://ftp.linux.org.tr natty/universe Sources
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://ftp.linux.org.tr natty/multiverse Sources
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://ftp.linux.org.tr natty/main amd64 Packages
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://ftp.linux.org.tr natty/restricted amd64 Packages
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://ftp.linux.org.tr natty/universe amd64 Packages
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://ftp.linux.org.tr natty/multiverse amd64 Packages
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign http://ftp.linux.org.tr natty/main Translation-en_US
Ign http://ftp.linux.org.tr natty/main Translation-en
Ign http://ftp.linux.org.tr natty/multiverse Translation-en_US
Ign http://ftp.linux.org.tr natty/multiverse Translation-en
Ign http://ftp.linux.org.tr natty/restricted Translation-en_US
Ign http://ftp.linux.org.tr natty/restricted Translation-en
Ign http://ftp.linux.org.tr natty/universe Translation-en_US
Ign http://ftp.linux.org.tr natty/universe Translation-en
Err http://ftp.linux.org.tr natty-updates/main Sources
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://ftp.linux.org.tr natty-updates/restricted Sources
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://ftp.linux.org.tr natty-updates/universe Sources
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://ftp.linux.org.tr natty-updates/multiverse Sources
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://ftp.linux.org.tr natty-updates/main amd64 Packages        
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://ftp.linux.org.tr natty-updates/restricted amd64 Packages  
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://ftp.linux.org.tr natty-updates/universe amd64 Packages
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://ftp.linux.org.tr natty-updates/multiverse amd64 Packages
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign http://ftp.linux.org.tr natty-updates/main Translation-en_US
Ign http://ftp.linux.org.tr natty-updates/main Translation-en
Ign http://ftp.linux.org.tr natty-updates/multiverse Translation-en_US
Ign http://ftp.linux.org.tr natty-updates/multiverse Translation-en
Ign http://ftp.linux.org.tr natty-updates/restricted Translation-en_US
Ign http://ftp.linux.org.tr natty-updates/restricted Translation-en
Ign http://ftp.linux.org.tr natty-updates/universe Translation-en_US
Ign http://ftp.linux.org.tr natty-updates/universe Translation-en
Err http://ftp.linux.org.tr natty-security/main Sources
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://ftp.linux.org.tr natty-security/restricted Sources
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://ftp.linux.org.tr natty-security/universe Sources
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://ftp.linux.org.tr natty-security/multiverse Sources        
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://ftp.linux.org.tr natty-security/main amd64 Packages       
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://ftp.linux.org.tr natty-security/restricted amd64 Packages 
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://ftp.linux.org.tr natty-security/universe amd64 Packages   
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://ftp.linux.org.tr natty-security/multiverse amd64 Packages
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign http://ftp.linux.org.tr natty-security/main Translation-en_US
Ign http://ftp.linux.org.tr natty-security/main Translation-en
Ign http://ftp.linux.org.tr natty-security/multiverse Translation-en_US
Ign http://ftp.linux.org.tr natty-security/multiverse Translation-en
Ign http://ftp.linux.org.tr natty-security/restricted Translation-en_US
Ign http://ftp.linux.org.tr natty-security/restricted Translation-en
Ign http://ftp.linux.org.tr natty-security/universe Translation-en_US
Ign http://ftp.linux.org.tr natty-security/universe Translation-en
Ign http://archive.canonical.com natty InRelease
Ign http://archive.canonical.com natty Release.gpg
Ign http://archive.canonical.com natty Release
Ign http://archive.canonical.com natty/partner Sources/DiffIndex
Ign http://archive.canonical.com natty/partner amd64 Packages/DiffIndex
Ign http://archive.canonical.com natty/partner TranslationIndex
Err http://archive.canonical.com natty/partner Sources
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://archive.canonical.com natty/partner amd64 Packages
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign http://archive.canonical.com natty/partner Translation-en_US
Ign http://archive.canonical.com natty/partner Translation-en
Ign http://extras.ubuntu.com natty InRelease
Ign http://extras.ubuntu.com natty Release.gpg
Ign http://extras.ubuntu.com natty Release
Ign http://extras.ubuntu.com natty/main Sources/DiffIndex
Ign http://extras.ubuntu.com natty/main amd64 Packages/DiffIndex
Ign http://extras.ubuntu.com natty/main TranslationIndex
Err http://extras.ubuntu.com natty/main Sources
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://extras.ubuntu.com natty/main amd64 Packages
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign http://extras.ubuntu.com natty/main Translation-en_US
Ign http://extras.ubuntu.com natty/main Translation-en
W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/natty-getdeb/apps/binary-amd64/Packages  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://ftp.linux.org.tr/ubuntu/dists/natty/main/source/Sources  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://ftp.linux.org.tr/ubuntu/dists/natty/restricted/source/Sources  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://ftp.linux.org.tr/ubuntu/dists/natty/universe/source/Sources  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://ftp.linux.org.tr/ubuntu/dists/natty/multiverse/source/Sources  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://ftp.linux.org.tr/ubuntu/dists/natty/main/binary-amd64/Packages  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://ftp.linux.org.tr/ubuntu/dists/natty/restricted/binary-amd64/Packages  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://ftp.linux.org.tr/ubuntu/dists/natty/universe/binary-amd64/Packages  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://ftp.linux.org.tr/ubuntu/dists/natty/multiverse/binary-amd64/Packages  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://ftp.linux.org.tr/ubuntu/dists/natty-updates/main/source/Sources  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://ftp.linux.org.tr/ubuntu/dists/natty-updates/restricted/source/Sources  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://ftp.linux.org.tr/ubuntu/dists/natty-updates/universe/source/Sources  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://ftp.linux.org.tr/ubuntu/dists/natty-updates/multiverse/source/Sources  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://ftp.linux.org.tr/ubuntu/dists/natty-updates/main/binary-amd64/Packages  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://ftp.linux.org.tr/ubuntu/dists/natty-updates/restricted/binary-amd64/Packages  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://ftp.linux.org.tr/ubuntu/dists/natty-updates/universe/binary-amd64/Packages  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://ftp.linux.org.tr/ubuntu/dists/natty-updates/multiverse/binary-amd64/Packages  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://ftp.linux.org.tr/ubuntu/dists/natty-security/main/source/Sources  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://ftp.linux.org.tr/ubuntu/dists/natty-security/restricted/source/Sources  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://ftp.linux.org.tr/ubuntu/dists/natty-security/universe/source/Sources  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://ftp.linux.org.tr/ubuntu/dists/natty-security/multiverse/source/Sources  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://ftp.linux.org.tr/ubuntu/dists/natty-security/main/binary-amd64/Packages  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://ftp.linux.org.tr/ubuntu/dists/natty-security/restricted/binary-amd64/Packages  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://ftp.linux.org.tr/ubuntu/dists/natty-security/universe/binary-amd64/Packages  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://ftp.linux.org.tr/ubuntu/dists/natty-security/multiverse/binary-amd64/Packages  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/partner/source/Sources  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/partner/binary-amd64/Packages  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

E: Some index files failed to download. They have been ignored, or old ones used instead.


```
when I*** sudo apt-get update*** I get that massage.

---

