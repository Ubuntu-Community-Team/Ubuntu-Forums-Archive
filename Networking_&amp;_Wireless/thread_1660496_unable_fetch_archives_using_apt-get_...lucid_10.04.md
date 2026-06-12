---
title: "unable fetch archives using apt-get ...lucid 10.04.1(LTS)"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by noobad@linux on 2011-01-05
used command **sudo apt-get update**
and got this :

**root@ravi-laptop:/home/ravi# apt-get update**

Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release.gpg                             
  Could not connect to in.archive.ubuntu.com:80 (111.91.91.37). - connect (110: Connection timed out)
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN          
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_IN    
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IN      
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_IN    
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release.gpg                     
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN  
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release                                 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Packages  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Sources   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Sources              
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Packages               
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Sources                
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Packages             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Sources              
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Packages                           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Sources    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Sources
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Packages                           
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Packages                     
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Sources                            
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Sources
  Unable to connect to in.archive.ubuntu.com:http:
26% [Connecting to security.ubuntu.com (91.189.88.37)]^C

then used **export http_proxy=http://10.1.8.30:8080**
10.1.8.30 is my localhost.

  still the same error...Please help..need it as soon as possible

---

### Post by PatchesTheCaveman on 2011-01-05
If you need to connect through a proxy, follow these instructions to configure the APT proxy settings.  AFAICT *apt-get* ignores the HTTP_PROXY environment variable.

To configure APT to use a proxy server, follow the instructions here:
[http://www.debian-administration.org/articles/177](http://www.debian-administration.org/articles/177)

---

### Post by noobad@linux on 2011-01-05
thanxs a lot man...it worked !

---

