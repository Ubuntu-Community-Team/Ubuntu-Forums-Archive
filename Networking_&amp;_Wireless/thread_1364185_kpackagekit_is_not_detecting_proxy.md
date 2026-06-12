---
title: "kpackagekit is not detecting proxy"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by rkakkar on 2009-12-25
although i'm able to surf, kpackagekit is not detecting my proxy and neither is apt-get. i have set manual proxy settings in 'system settings' any ideas?

---

### Post by tazz74 on 2010-01-06
Try this [thread ]("http://newyork.ubuntuforums.org/showthread.php?p=8320934")(post by _Ajat_), It helped me, I had the same issue. 

I had authentication issues that I could browse but kpackagekit did not work.

My proxy requires authentication so i just added by user-name in front of it like: on each of the values (ftpProxy,httpProxy,httpsProxy) ```
username:password@proxy:port
```

Thkx.

---

### Post by sar.vivek on 2010-01-10
I am using Ubuntu from last 2 years. This time I switched to KUbuntu 9.10 via fresh installation. 
My box is behind my campus proxy. So, I configured proxy via NetworkManager. I am able to browse internet. But when I do sudo apt-get update It gives error : 111: Connection Refused.

I tried export http_proxy=campusproxy:port.
But it didnt worked fine for me. Also I tried different server .Still apt-get giving the same error 

 sudo apt-get update
Err [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111: Connection refused)
Err [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_IN                                   
  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111: Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                                                    
  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_IN                                                           
  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_IN                                                     
  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_IN                                                       
  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_IN                                                     
  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg                                                              
  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_IN                                                   
  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_IN                                             
  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_IN                                               
  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_IN                                             
  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release.gpg                                                             
  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Translation-en_IN                                                  
  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Translation-en_IN                                            
  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Translation-en_IN                                              
  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Translation-en_IN                                            
  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]
Reading package lists... Done                                                                                         
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]                                                                                                                                                                                              

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]                                                                                                                                                                          

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]                                                                                                                                                                    

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]                                                                                                                                                                      

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]                                                                                                                                                                    

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg](http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111: Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_IN.bz2](http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_IN.bz2)  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111: Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]

Please help me..
Thanks.

---

### Post by ravi.xolve on 2010-12-22
From now on use

sudo -E apt-get <command>

with http_proxy variables.

---

