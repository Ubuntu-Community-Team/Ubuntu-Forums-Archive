---
title: "apt-get behind proxy server"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by shrik_kshir on 2009-04-23
Hi
I'm using ubuntu intrepid & I'm behind a university proxy server ("squid proxy-caching server" ) which requires authentication; so I tried each of the foll. ways (& all their permutations & combinations):

1. set the appropriate fields in synaptics packet manager (GUI) synaptic packet manager ->preferences->network
2. edit apt.conf file as : Acquire::http: proxy "http://user: psswd@proxy: port/";
3. append to bash.bashrc file: export http_proxy = [http://user: psswd@proxy: port/]("http://user:psswd@proxy/")
4. setting appropriate fields in system->preferences->network proxy and applying system-wide

However nothing seems to work; I keep getting the error :"407 proxy authentication required" whenever I try to do sudo apt-get update.

Please help soon

(P.S. Could the problem be because I have a "$" character in my psswd or "_" character in my username?)

---

### Post by lunamystry on 2009-04-23
I also have the same problem. I had apt working before and this morning it just stopped and started giving the error. Thing is someone set-up the proxy for me before and I don't know what they did. Synaptic also does not seem to be downloading anything when I reload but I can installed things I don't know. It says that hit but 0k downloaded. 

Oh I also tried all those things mentioned. I have a $ character in my password. I don't know what kind of proxy is used.

I am SUPER FRUSTRATED RIGHT NOW

---

### Post by Maleeq on 2009-05-07
Hi,

I am faced with the same issue too. Anyone with a solution please?

---

### Post by kamaji792 on 2009-06-05
Not much help, but here was my experience.

Had a proxy system added to a current network so I had to get **apt-get** to work.

I edited the **/etc/bash.bashrc** file (you have to be root or use sudo).  I added the following two lines to the end of the file:

```
export http_proxy=http://192.168.1.2:8080/
export ftp_proxy=http://192.168.1.2:8080/
```

I guess if my proxy needed authentication it would have been:

```
export http_proxy=http://user_name:password@192.168.1.2:8080/
export ftp_proxy=http://user_name:password@192.168.1.2:8080/
```

Looking at the first post the only difference I can see is there there are no spaces in mine apart from after the export.

Just in case it help :P

---

### Post by 1sk on 2009-07-02
Hi

Had the same problem myself with a ISA proxy for a 8.04 server. Below is my how to, just ignore the bits about connecting to the CD for a VM. Hope it helps.

[X]  3, Install NTLMAPS Application To Authenticate To the Proxy Server
=======================================================================

Download the ntlmaps_0.9.9.0.1-7_all.deb package and cut to a CD

Put CD with package file for NTLMAPS and openssh-server into client PC CDROM drive --> In the VI Client --> Connect CD/DVD 1 

    --> Mount the CDROM --> sudo mount /dev/scd0 /media/cdrom0 

    --> sudo dpkg /media/cdrom0/ntlmaps

    --> Listen Port: 5865 --> OK --> Parent Proxy: proxy.server.name.or.ip --> OK --> Parent Proxy Port: 8080???.or.your.port

    --> NT Windows Domain: your.domain --> OK --> NT Windows Username: login --> OK 

    --> NT Windows Password: (Leave Blank, ie no password) --> OK

    --> Note: Sometimes the config above doesn't always give all the screens, to be able to reconfigure NTLMAPS run --> sudo dpkg-reconfigure ntlmaps

    --> Create a file /etc/apt/apt.conf.d/proxy     --> and input the following line: 'Acquire::http::Proxy "http://127.0.0.1:5865/";'
                            --> and input the following line: 'Acquire::http::Proxy "ftp://127.0.0.1:5865/";'

    --> sudo cp /etc/ntlmaps/server.cfg /usr/share/ntlmaps/server.cfg

    --> sudo vi /usr/share/ntlmaps/server.cfg --> Add @ FRIENDLY_IPS: server.ip.address 127.0.0.1

    --> export http_proxy=http://127.0.0.1:5865 and export http_proxy=ftp://127.0.0.1:5865

    --> sudo vi /etc/apt/apt.conf     --> and input the following line: 'Acquire::http::Proxy "http://127.0.0.1:5865/";'
                    --> and input the following line: 'Acquire::http::Proxy "ftp://127.0.0.1:5865/";'

    --> sudo /etc/init.d/ntlmaps stop 

    --> Alt + F2 --> sudo /usr/share/ntlmaps/main.py --> Enter password 

    --> Alt + F1 --> sudo /etc/init.d/ntlmaps start


You should now be able to run apt-get or aptitude

---

### Post by shrik_kshir on 2009-09-15
As I said, the problem is specifying my username and password to the http proxy. Unlike the solution pointed out in the previous post, my proxy server requires a username and password authentication. How do I specify the same for getting apt-get to work?

---

### Post by shrik_kshir on 2009-09-15
As I said, the problem is specifying my username and password to the http proxy. Unlike the solution pointed out in the previous post, my proxy server requires a username and password authentication. How do I specify the same for getting apt-get to work?
Below is the list of errors I get.

```

sudo apt-get update
Hit ftp://ftp.iitb.ac.in jaunty-security Release.gpg
Get:1 ftp://ftp.iitb.ac.in jaunty-security/main Translation-en_IN              
Ign ftp://ftp.iitb.ac.in jaunty-security/main Translation-en_IN                
Get:2 ftp://ftp.iitb.ac.in jaunty-security/restricted Translation-en_IN        
Ign http://packages.medibuntu.org jaunty Release.gpg                           
Ign ftp://ftp.iitb.ac.in jaunty-security/restricted Translation-en_IN          
Get:3 ftp://ftp.iitb.ac.in jaunty-security/universe Translation-en_IN          
Ign ftp://ftp.iitb.ac.in jaunty-security/universe Translation-en_IN            
Ign http://packages.medibuntu.org jaunty/free Translation-en_IN                
Get:4 ftp://ftp.iitb.ac.in jaunty-security/multiverse Translation-en_IN        
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_IN            
Ign ftp://ftp.iitb.ac.in jaunty-security/multiverse Translation-en_IN          
Ign http://packages.medibuntu.org jaunty Release                               
Hit ftp://ftp.iitb.ac.in jaunty-updates Release.gpg                            
Get:5 ftp://ftp.iitb.ac.in jaunty-updates/multiverse Translation-en_IN
Ign ftp://ftp.iitb.ac.in jaunty-updates/multiverse Translation-en_IN           
Get:6 ftp://ftp.iitb.ac.in jaunty-updates/universe Translation-en_IN           
Ign ftp://ftp.iitb.ac.in jaunty-updates/universe Translation-en_IN             
Ign http://packages.medibuntu.org jaunty/free Packages                         
Get:7 ftp://ftp.iitb.ac.in jaunty-updates/main Translation-en_IN               
Ign ftp://ftp.iitb.ac.in jaunty-updates/main Translation-en_IN                 
Get:8 ftp://ftp.iitb.ac.in jaunty-updates/restricted Translation-en_IN         
Ign ftp://ftp.iitb.ac.in jaunty-updates/restricted Translation-en_IN           
Hit ftp://ftp.iitb.ac.in jaunty Release.gpg                                    
Get:9 ftp://ftp.iitb.ac.in jaunty/multiverse Translation-en_IN                 
Ign http://packages.medibuntu.org jaunty/non-free Packages                     
Ign ftp://ftp.iitb.ac.in jaunty/multiverse Translation-en_IN                   
Get:10 ftp://ftp.iitb.ac.in jaunty/universe Translation-en_IN                  
Ign ftp://ftp.iitb.ac.in jaunty/universe Translation-en_IN                     
Ign http://packages.medibuntu.org jaunty/free Sources                          
Get:11 ftp://ftp.iitb.ac.in jaunty/main Translation-en_IN                      
Ign ftp://ftp.iitb.ac.in jaunty/main Translation-en_IN                         
Get:12 ftp://ftp.iitb.ac.in jaunty/restricted Translation-en_IN                
Ign ftp://ftp.iitb.ac.in jaunty/restricted Translation-en_IN                   
Ign http://packages.medibuntu.org jaunty/non-free Sources                      
Hit ftp://ftp.iitb.ac.in jaunty-security Release                               
Ign http://packages.medibuntu.org jaunty/free Packages                         
Ign http://packages.medibuntu.org jaunty/non-free Packages                     
Ign http://packages.medibuntu.org jaunty/free Sources                          
Hit ftp://ftp.iitb.ac.in jaunty-updates Release                                
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_IN                      
Ign http://packages.medibuntu.org jaunty/non-free Sources                      
Hit ftp://ftp.iitb.ac.in jaunty Release                                        
Hit ftp://ftp.iitb.ac.in jaunty-security/main Packages                         
Ign http://ppa.launchpad.net jaunty Release.gpg                                
Hit ftp://ftp.iitb.ac.in jaunty-security/restricted Packages                   
Err http://packages.medibuntu.org jaunty/free Packages                         
  407 Proxy Authentication Required
Hit ftp://ftp.iitb.ac.in jaunty-security/main Sources                          
Hit ftp://ftp.iitb.ac.in jaunty-security/restricted Sources                    
Hit ftp://ftp.iitb.ac.in jaunty-security/universe Packages                     
Hit ftp://ftp.iitb.ac.in jaunty-security/universe Sources                      
Hit ftp://ftp.iitb.ac.in jaunty-security/multiverse Packages                   
Hit ftp://ftp.iitb.ac.in jaunty-security/multiverse Sources                    
Ign http://ppa.launchpad.net jaunty/main Translation-en_IN                     
Hit ftp://ftp.iitb.ac.in jaunty-updates/multiverse Packages                    
Hit ftp://ftp.iitb.ac.in jaunty-updates/multiverse Sources                     
Hit ftp://ftp.iitb.ac.in jaunty-updates/universe Packages                      
Hit ftp://ftp.iitb.ac.in jaunty-updates/universe Sources                       
Hit ftp://ftp.iitb.ac.in jaunty-updates/main Packages                          
Hit ftp://ftp.iitb.ac.in jaunty-updates/restricted Packages                    
Hit ftp://ftp.iitb.ac.in jaunty-updates/main Sources                           
Hit ftp://ftp.iitb.ac.in jaunty-updates/restricted Sources                     
Ign http://archive.canonical.com jaunty Release.gpg                            
Ign http://archive.ubuntu.com jaunty Release.gpg                               
Hit ftp://ftp.iitb.ac.in jaunty/multiverse Packages                            
Hit ftp://ftp.iitb.ac.in jaunty/multiverse Sources                             
Hit ftp://ftp.iitb.ac.in jaunty/universe Packages                              
Hit ftp://ftp.iitb.ac.in jaunty/universe Sources                               
Hit ftp://ftp.iitb.ac.in jaunty/main Packages                                  
Hit ftp://ftp.iitb.ac.in jaunty/restricted Packages                            
Hit ftp://ftp.iitb.ac.in jaunty/main Sources                                   
Hit ftp://ftp.iitb.ac.in jaunty/restricted Sources                             
Err http://packages.medibuntu.org jaunty/non-free Packages                     
  407 Proxy Authentication Required
Err http://packages.medibuntu.org jaunty/free Sources                          
  407 Proxy Authentication Required
Err http://packages.medibuntu.org jaunty/non-free Sources                      
  407 Proxy Authentication Required
Ign http://archive.canonical.com jaunty/partner Translation-en_IN              
Ign http://archive.canonical.com jaunty Release                                
Ign http://archive.canonical.com jaunty/partner Packages
Ign http://archive.canonical.com jaunty/partner Sources
Ign http://archive.canonical.com jaunty/partner Packages
Ign http://archive.canonical.com jaunty/partner Sources
Ign http://ppa.launchpad.net hardy Release     
Err http://archive.canonical.com jaunty/partner Packages                       
  407 Proxy Authentication Required
Ign http://ppa.launchpad.net jaunty Release                                    
Ign http://ppa.launchpad.net hardy/main Packages                          
Err http://archive.canonical.com jaunty/partner Sources                        
  407 Proxy Authentication Required
Ign http://ppa.launchpad.net hardy/main Sources                                
Ign http://ppa.launchpad.net jaunty/main Packages                         
Ign http://ppa.launchpad.net jaunty/main Sources                          
Ign http://ppa.launchpad.net hardy/main Packages                          
Ign http://archive.ubuntu.com jaunty/main Translation-en_IN               
Ign http://ppa.launchpad.net hardy/main Sources                                
Ign http://ppa.launchpad.net jaunty/main Packages                              
Ign http://ppa.launchpad.net jaunty/main Sources                               
Err http://ppa.launchpad.net hardy/main Packages                          
  407 Proxy Authentication Required
Ign http://archive.ubuntu.com jaunty/restricted Translation-en_IN         
Ign http://archive.ubuntu.com jaunty/universe Translation-en_IN           
Ign http://archive.ubuntu.com jaunty/multiverse Translation-en_IN         
Ign http://archive.ubuntu.com jaunty-updates Release.gpg                  
Ign http://archive.ubuntu.com jaunty-updates/main Translation-en_IN       
Ign http://archive.ubuntu.com jaunty-updates/restricted Translation-en_IN 
Ign http://archive.ubuntu.com jaunty-updates/universe Translation-en_IN   
Ign http://archive.ubuntu.com jaunty-updates/multiverse Translation-en_IN 
Ign http://archive.ubuntu.com jaunty-backports Release.gpg                
Ign http://archive.ubuntu.com jaunty-backports/main Translation-en_IN     
Ign http://archive.ubuntu.com jaunty-backports/restricted Translation-en_IN
Ign http://archive.ubuntu.com jaunty-backports/universe Translation-en_IN 
Ign http://archive.ubuntu.com jaunty-backports/multiverse Translation-en_IN
Ign http://archive.ubuntu.com jaunty-security Release.gpg                 
Err http://ppa.launchpad.net hardy/main Sources                           
  407 Proxy Authentication Required
Ign http://archive.ubuntu.com jaunty-security/main Translation-en_IN           
Ign http://archive.ubuntu.com jaunty-security/restricted Translation-en_IN     
Ign http://archive.ubuntu.com jaunty-security/universe Translation-en_IN       
Ign http://archive.ubuntu.com jaunty-security/multiverse Translation-en_IN     
Ign http://archive.ubuntu.com jaunty Release                                   
Ign http://archive.ubuntu.com jaunty-updates Release                           
Ign http://archive.ubuntu.com jaunty-backports Release                         
Err http://ppa.launchpad.net jaunty/main Packages                         
  407 Proxy Authentication Required
Ign http://archive.ubuntu.com jaunty-security Release                          
Err http://ppa.launchpad.net jaunty/main Sources                               
  407 Proxy Authentication Required
Ign http://archive.ubuntu.com jaunty/main Packages                             
Ign http://archive.ubuntu.com jaunty/restricted Packages
Ign http://archive.ubuntu.com jaunty/main Sources   
Ign http://archive.ubuntu.com jaunty/restricted Sources
Ign http://archive.ubuntu.com jaunty/universe Packages
Ign http://archive.ubuntu.com jaunty/universe Sources
Ign http://archive.ubuntu.com jaunty/multiverse Packages
Ign http://archive.ubuntu.com jaunty/multiverse Sources
Ign http://archive.ubuntu.com jaunty-updates/main Packages
Ign http://archive.ubuntu.com jaunty-updates/restricted Packages
Ign http://archive.ubuntu.com jaunty-updates/main Sources
Ign http://archive.ubuntu.com jaunty-updates/restricted Sources
Ign http://archive.ubuntu.com jaunty-updates/universe Packages
Ign http://archive.ubuntu.com jaunty-updates/universe Sources
Ign http://archive.ubuntu.com jaunty-updates/multiverse Packages
Ign http://archive.ubuntu.com jaunty-updates/multiverse Sources
Ign http://archive.ubuntu.com jaunty-backports/main Packages
Ign http://archive.ubuntu.com jaunty-backports/restricted Packages
Ign http://archive.ubuntu.com jaunty-backports/universe Packages
Ign http://archive.ubuntu.com jaunty-backports/multiverse Packages
Ign http://archive.ubuntu.com jaunty-backports/main Sources
Ign http://archive.ubuntu.com jaunty-backports/restricted Sources
Ign http://archive.ubuntu.com jaunty-backports/universe Sources
Ign http://archive.ubuntu.com jaunty-backports/multiverse Sources
Ign http://archive.ubuntu.com jaunty-security/main Packages
Ign http://archive.ubuntu.com jaunty-security/restricted Packages
Ign http://archive.ubuntu.com jaunty-security/main Sources
Ign http://archive.ubuntu.com jaunty-security/restricted Sources
Ign http://archive.ubuntu.com jaunty-security/universe Packages
Ign http://archive.ubuntu.com jaunty-security/universe Sources
Ign http://archive.ubuntu.com jaunty-security/multiverse Packages
Ign http://archive.ubuntu.com jaunty-security/multiverse Sources
Ign http://archive.ubuntu.com jaunty/main Packages  
Ign http://archive.ubuntu.com jaunty/restricted Packages
Ign http://archive.ubuntu.com jaunty/main Sources   
Ign http://archive.ubuntu.com jaunty/restricted Sources
Ign http://archive.ubuntu.com jaunty/universe Packages
Ign http://archive.ubuntu.com jaunty/universe Sources
Ign http://archive.ubuntu.com jaunty/multiverse Packages
Ign http://archive.ubuntu.com jaunty/multiverse Sources
Ign http://archive.ubuntu.com jaunty-updates/main Packages
Ign http://archive.ubuntu.com jaunty-updates/restricted Packages
Ign http://archive.ubuntu.com jaunty-updates/main Sources
Ign http://archive.ubuntu.com jaunty-updates/restricted Sources
Ign http://archive.ubuntu.com jaunty-updates/universe Packages
Ign http://archive.ubuntu.com jaunty-updates/universe Sources
Ign http://archive.ubuntu.com jaunty-updates/multiverse Packages
Ign http://archive.ubuntu.com jaunty-updates/multiverse Sources
Ign http://archive.ubuntu.com jaunty-backports/main Packages
Ign http://archive.ubuntu.com jaunty-backports/restricted Packages
Ign http://archive.ubuntu.com jaunty-backports/universe Packages
Ign http://archive.ubuntu.com jaunty-backports/multiverse Packages
Ign http://archive.ubuntu.com jaunty-backports/main Sources
Ign http://archive.ubuntu.com jaunty-backports/restricted Sources
Ign http://archive.ubuntu.com jaunty-backports/universe Sources
Ign http://archive.ubuntu.com jaunty-backports/multiverse Sources
Ign http://archive.ubuntu.com jaunty-security/main Packages
Ign http://archive.ubuntu.com jaunty-security/restricted Packages
Ign http://archive.ubuntu.com jaunty-security/main Sources
Ign http://archive.ubuntu.com jaunty-security/restricted Sources
Ign http://archive.ubuntu.com jaunty-security/universe Packages
Ign http://archive.ubuntu.com jaunty-security/universe Sources
Ign http://archive.ubuntu.com jaunty-security/multiverse Packages
Ign http://archive.ubuntu.com jaunty-security/multiverse Sources
Err http://archive.ubuntu.com jaunty/main Packages  
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty/restricted Packages
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty/main Sources   
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty/restricted Sources
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty/universe Packages
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty/universe Sources
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty/multiverse Packages
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty/multiverse Sources
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty-updates/main Packages
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty-updates/restricted Packages
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty-updates/main Sources
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty-updates/restricted Sources
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty-updates/universe Packages
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty-updates/universe Sources
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty-updates/multiverse Packages
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty-updates/multiverse Sources
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty-backports/main Packages
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty-backports/restricted Packages
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty-backports/universe Packages
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty-backports/multiverse Packages
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty-backports/main Sources
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty-backports/restricted Sources
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty-backports/universe Sources
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty-backports/multiverse Sources
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty-security/main Packages
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty-security/restricted Packages
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty-security/main Sources
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty-security/restricted Sources
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty-security/universe Packages
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty-security/universe Sources
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty-security/multiverse Packages
  407 Proxy Authentication Required
Err http://archive.ubuntu.com jaunty-security/multiverse Sources
  407 Proxy Authentication Required
W: Failed to fetch http://packages.medibuntu.org/dists/jaunty/free/binary-i386/Packages  407 Proxy Authentication Required

W: Failed to fetch http://packages.medibuntu.org/dists/jaunty/non-free/binary-i386/Packages  407 Proxy Authentication Required

W: Failed to fetch http://packages.medibuntu.org/dists/jaunty/free/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://packages.medibuntu.org/dists/jaunty/non-free/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/jaunty/partner/binary-i386/Packages  407 Proxy Authentication Required

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/jaunty/partner/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://ppa.launchpad.net/zman0900/ubuntu/dists/hardy/main/binary-i386/Packages  407 Proxy Authentication Required

W: Failed to fetch http://ppa.launchpad.net/zman0900/ubuntu/dists/hardy/main/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/jaunty/main/binary-i386/Packages  407 Proxy Authentication Required

W: Failed to fetch http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/jaunty/main/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages  407 Proxy Authentication Required

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources  407 Proxy Authentication Required

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Any help would be highly appreciated!

---

### Post by aliulu on 2009-09-15
hi
i had same problem and cant run apt-get behind proxy. i solved my problem like this. under system/network proxy menu click manual proxy configuration and write ip adress and port number. after this apt-get run without a problem.

---

### Post by MalphasWats on 2009-09-15
I have a similar issue - I can't seem to specify my login information for the proxy and I think it's because my username for my system at work is an email address, so it ends up looking like this:

```
export http_proxy="http://username@domain.com:password@poxyipaddress:proxyport"
```

and it just doesn't like it. Works fine in Firefox but won't work anywhere else - terminal etc.

I'll add also that if I try an apt-get update from a fresh terminal, it can't find anything, if I run the above, it gives the error that it can't resolve password@proxyipaddress, which suggests it is picking up the proxy setting, but doesn't like the format of my username.

Any ideas?
-M

---

### Post by lunamystry on 2009-09-15
I had a similar problem. I am using a university proxy server and how I solved the problem was editing the apt.conf file in the directory /etc/apt/

Mine looks kinda different from the MalphasWats's one ( I think, maybe the symbols mean the same thing)

```
Acquire::http::Proxy "http://<domain>\<username>:<password>@<proxyserver>:80/";
```

and someone told me I need to have that semicolon (";") and "/" at the end there. I am not sure if the capitalization matters. That worked from me. Hope It helps.

edit: my user name doesn't have an email address.

---

### Post by MalphasWats on 2009-09-15
> **lunamystry said:**
> I had a similar problem. I am using a university proxy server and how I solved the problem was editing the apt.conf file in the directory /etc/apt/

Mine looks kinda different from the MalphasWats's one ( I think, maybe the symbols mean the same thing)

```
Acquire::http::Proxy "http://<domain>\<username>:<password>@<proxyserver>:80/";
```

and someone told me I need to have that semicolon (";") and "/" at the end there. I am not sure if the capitalization matters. That worked from me. Hope It helps.

edit: my user name doesn't have an email address.

Thanks for the help, I don't seem to have a apt.conf, so I created one, put in what you suggested and still get an error about the proxy needing authentication :(

Would I need to restart after I edit the file?

My username is only an email address because it needs to include the domain, the auth machine is an NT server of some flavour.

---

### Post by p1t0u on 2009-09-15
```
export http_proxy="http://username@domain.com:password@poxyipaddress:proxyport"
```Since you have an @ in your user name you propably have to escape it;
that character is used to separate the userid password and the proxy address
so try:
```
export http_proxy="http://username\@domain.com:password@poxyipaddress:proxyport"
```

---

### Post by MalphasWats on 2009-09-15
> **p1t0u said:**
> Since you have an @ in your user name you propably have to escape it;
that character is used to separate the userid password and the proxy address
so try:


Thanks for the reply - that doesn't work either, I think the issue is that I need to auth against a microsoft ISA server, I've done a little bit more research and I've come across [cntlm]("http://manpages.ubuntu.com/manpages/hardy/man1/cntlm.1.html#toptoc4") which I think is what I'm going to need.

I was hoping for an easier solution, configured a few ubuntu systems but I'm still very much a noob and proxies always seem to make things complicated.

---

### Post by mshtawythug on 2009-09-29
MalphasWats you are the best really thank you for the solution look guys all you need to do is 
go to 
[https://launchpad.net/ubuntu/karmic/i386/cntlm/0.35.1-4](https://launchpad.net/ubuntu/karmic/i386/cntlm/0.35.1-4)
and download the cntlm .deb
install the package then 

```
#nano /etc/cntlm.conf

```
then edit
Proxy           proxyserver:port   
Proxy           proxyserver:port


#
# This is the port number where Cntlm will listen
#
Listen          1000 (or any open port in your computer)

after that 

```
#/etc/init.d/cntlm start
```

and now its time to authenticate

```
#cntlm  -u <user> -p <pass> <proxy_host> <proxy_port>
```

$$$$ leave this terminal open $$$$

now if you want to apt-get from the Terminal run this

```
#export http_proxy=127.0.0.1:1000
``` (note that 1000 is the port we added in the configuration file)
```
#export ftp_proxy=127.0.0.1:1000
```

now if you want to use Synaptic Package manager
in the window of Synaptic Package manager go to 

Settings ---> Preferences ---> Network 

click on  Manual proxy configuration 

and insert for both http and ftp 

127.0.0.1  and 1000 for the port (note that 1000 is what we added in the configuration file)

$$$$$$$$$$ENJOY$$$$$$$$$$

#########################################################################
 NOTE: if you had a problem in                                          
```
# cntlm  -u <user> -p <pass> <proxy_host> <proxy_port>  
```                
                                                                       
 run                                                                   
```
# cntlm  -v -u <user> -p <pass> <proxy_host> <proxy_port>                     
```                                                             
 one of the problems you are going to see is port #### is already used  
 this means you need to change the port number in our case the 1000 in  the configuration file 

 this was the only problem i had
#########################################################################

---

### Post by mshtawythug on 2009-09-29
by the way i had a ? in my password some guys have @ some others have $ so i think this may be the problem

---

### Post by AlexanderDGreat on 2009-12-26
Hi I'm behind a firewall, I can't apt-get update. I've already tried ALL suggestions here: [https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGet#Setting%20up%20apt-get%20to%20use%20a%20http-proxy]("https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGet#Setting%20up%20apt-get%20to%20use%20a%20http-proxy")

But they're NOT working for me! I'm using Karmic Koala on server and client. Pls. Help!

@mshtawythug - will your method work even if my proxy is not AUTHENTICATING users? Also, why does it have to be complicated?

---

