---
title: "Mythtv wont install due to broken packages."
date: 2009-06-19
forum: Multimedia Software
---

### Post by k420 on 2009-06-19
When i try to install mythtv i get this ```
nathan@nathan-gamer:~$ sudo aptitude install mythtv
                      
Reading package lists... Done                      
Building dependency tree                           
Reading state information... Done                  
Reading extended state information                 
Initializing package states... Done                
The following NEW packages will be installed:      
  libdbd-mysql-perl{a} libdbi-perl{a} libhtml-template-perl{a} libmyth-perl{a} libnet-daemon-perl{a} libplrpc-perl{a} mysql-client{a} 
  mysql-client-5.0{a} mysql-server{a} mysql-server-5.0{a} mythtv mythtv-backend{a} mythtv-common{a} mythtv-database{a} mythtv-frontend{a} 
  mythtv-theme-blootube mythtv-theme-blootube-osd mythtv-theme-blootube-wide mythtv-theme-blootubelite-wide mythtv-theme-glass-wide       
  mythtv-theme-gray-osd mythtv-theme-isthmus mythtv-theme-iulius mythtv-theme-iulius-osd mythtv-theme-minimalist-wide mythtv-theme-mythbuntu 
  mythtv-theme-mythcenter mythtv-theme-mythcenter-wide mythtv-theme-neon-wide mythtv-theme-projectgrayhem{a} mythtv-theme-projectgrayhem-osd 
  mythtv-theme-projectgrayhem-wide{a} mythtv-theme-retro mythtv-theme-retro-osd mythtv-theme-titivillus mythtv-theme-titivillus-osd          
  mythtv-themes{a} mythtv-transcode-utils{a}                                                                                                 
0 packages upgraded, 38 newly installed, 0 to remove and 13 not upgraded.                                                                    
Need to get 114MB/115MB of archives. After unpacking 208MB will be used.                                                                     
Do you want to continue? [Y/n/?] y                                                                                                           
Writing extended state information... Done                                                                                                   
Get:1 http://gb.archive.ubuntu.com karmic/main libdbd-mysql-perl 4.011-1 [135kB]                                                             
Get:2 http://gb.archive.ubuntu.com karmic/main mysql-client-5.0 5.1.30really5.0.75-0ubuntu10 [8291kB]                                        
Get:3 http://gb.archive.ubuntu.com karmic/main mysql-server-5.0 5.1.30really5.0.75-0ubuntu10 [24.0MB]                                                
Get:4 http://gb.archive.ubuntu.com karmic/main mysql-client 5.1.30really5.0.75-0ubuntu10 [54.8kB]                                                    
Get:5 http://gb.archive.ubuntu.com karmic/multiverse mythtv-common 0.21.0+fixes19961-0ubuntu8 [5693kB]                                               
Get:6 http://gb.archive.ubuntu.com karmic/multiverse mythtv-database 0.21.0+fixes19961-0ubuntu8 [56.4kB]                                             
Get:7 http://gb.archive.ubuntu.com karmic/multiverse mythtv-frontend 0.21.0+fixes19961-0ubuntu8 [2048kB]                                             
Get:8 http://gb.archive.ubuntu.com karmic/multiverse mythtv-transcode-utils 0.21.0+fixes19961-0ubuntu8 [177kB]                                       
Get:9 http://gb.archive.ubuntu.com karmic/multiverse mythtv-backend 0.21.0+fixes19961-0ubuntu8 [1137kB]                                              
Get:10 http://gb.archive.ubuntu.com karmic/multiverse mythtv 0.21.0+fixes19961-0ubuntu8 [32.5kB]                                                     
Get:11 http://gb.archive.ubuntu.com karmic/main mysql-server 5.1.30really5.0.75-0ubuntu10 [57.0kB]                                                   
Get:12 http://gb.archive.ubuntu.com karmic/multiverse mythtv-theme-blootube 1:0.21.0-0ubuntu1 [7358kB]                                               
Get:13 http://gb.archive.ubuntu.com karmic/multiverse mythtv-theme-blootube-osd 1:0.21.0-0ubuntu2 [325kB]                                            
Get:14 http://gb.archive.ubuntu.com karmic/multiverse mythtv-theme-blootube-wide 1:0.21.0-0ubuntu1 [18.1MB]                                          
Get:15 http://gb.archive.ubuntu.com karmic/multiverse mythtv-theme-blootubelite-wide 1:0.21.0-0ubuntu1 [5783kB]                                      
Get:16 http://gb.archive.ubuntu.com karmic/multiverse mythtv-theme-glass-wide 0.20080908-0ubuntu2 [7096kB]                                           
Get:17 http://gb.archive.ubuntu.com karmic/multiverse mythtv-theme-gray-osd 0.21.0-0ubuntu2 [315kB]                                                  
Get:18 http://gb.archive.ubuntu.com karmic/multiverse mythtv-theme-isthmus 0.21.0-0ubuntu2 [349kB]                                                   
Get:19 http://gb.archive.ubuntu.com karmic/multiverse mythtv-theme-iulius 0.21.0-0ubuntu2 [414kB]                                                    
Get:20 http://gb.archive.ubuntu.com karmic/multiverse mythtv-theme-iulius-osd 0.21.0-0ubuntu2 [330kB]                                                
Get:21 http://gb.archive.ubuntu.com karmic/multiverse mythtv-theme-minimalist-wide 0.21.0-0ubuntu2 [1895kB]                                          
Get:22 http://gb.archive.ubuntu.com karmic/multiverse mythtv-theme-projectgrayhem 1:0.21.0-0ubuntu1 [3131kB]                                         
Get:23 http://gb.archive.ubuntu.com karmic/multiverse mythtv-theme-projectgrayhem-wide 1:0.21.0-0ubuntu2 [3783kB]                                    
Get:24 http://gb.archive.ubuntu.com karmic/universe mythtv-theme-mythbuntu 0.20080421 [7893kB]                                                       
Get:25 http://gb.archive.ubuntu.com karmic/multiverse mythtv-theme-mythcenter 0.21.0-0ubuntu2 [872kB]                                                
Get:26 http://gb.archive.ubuntu.com karmic/multiverse mythtv-theme-mythcenter-wide 0.21.0-0ubuntu2 [1928kB]                                          
Get:27 http://gb.archive.ubuntu.com karmic/multiverse mythtv-theme-neon-wide 1:0.21.0-0ubuntu4 [3691kB]                                              
Get:28 http://gb.archive.ubuntu.com karmic/multiverse mythtv-theme-projectgrayhem-osd 1:0.21.0-0ubuntu2 [117kB]                                      
Get:29 http://gb.archive.ubuntu.com karmic/multiverse mythtv-theme-retro 0.21.0-0ubuntu2 [2097kB]                                                    
Get:30 http://gb.archive.ubuntu.com karmic/multiverse mythtv-theme-retro-osd 0.21.0-0ubuntu2 [442kB]                                                 
Get:31 http://gb.archive.ubuntu.com karmic/multiverse mythtv-theme-titivillus 0.21.0-0ubuntu2 [5830kB]                                               
Get:32 http://gb.archive.ubuntu.com karmic/multiverse mythtv-theme-titivillus-osd 0.21.0-0ubuntu2 [137kB]                                            
Get:33 http://gb.archive.ubuntu.com karmic/multiverse mythtv-themes 0.21.0-0ubuntu2 [132kB]                                                          
Fetched 114MB in 17min 14s (110kB/s)                                                                                                                 
E: Invalid archive signature                                                                                                                         
E: Prior errors apply to /var/cache/apt/archives/libnet-daemon-perl_0.43-1_all.deb                                                                   
E: Invalid archive signature                                                                                                                         
E: Prior errors apply to /var/cache/apt/archives/libplrpc-perl_0.2020-2_all.deb                                                                      
E: Invalid archive signature                                                                                                                         
E: Prior errors apply to /var/cache/apt/archives/libdbi-perl_1.608-1_amd64.deb                                                                       
E: Prior errors apply to /var/cache/apt/archives/libdbd-mysql-perl_4.011-1_amd64.deb                                                                 
E: Prior errors apply to /var/cache/apt/archives/mysql-client-5.0_5.1.30really5.0.75-0ubuntu10_amd64.deb                                             
E: Prior errors apply to /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10_amd64.deb                                             
E: Prior errors apply to /var/cache/apt/archives/mysql-client_5.1.30really5.0.75-0ubuntu10_all.deb                                                   
E: Prior errors apply to /var/cache/apt/archives/mythtv-common_0.21.0+fixes19961-0ubuntu8_all.deb                                                    
E: Prior errors apply to /var/cache/apt/archives/mythtv-database_0.21.0+fixes19961-0ubuntu8_all.deb                                                  
E: Prior errors apply to /var/cache/apt/archives/mythtv-frontend_0.21.0+fixes19961-0ubuntu8_amd64.deb                                                
E: Prior errors apply to /var/cache/apt/archives/mythtv-transcode-utils_0.21.0+fixes19961-0ubuntu8_amd64.deb                                         
E: Prior errors apply to /var/cache/apt/archives/libmyth-perl_0.21.0+fixes19961-0ubuntu8_all.deb                                                     
E: Prior errors apply to /var/cache/apt/archives/mythtv-backend_0.21.0+fixes19961-0ubuntu8_amd64.deb                                                 
E: Prior errors apply to /var/cache/apt/archives/mythtv_0.21.0+fixes19961-0ubuntu8_all.deb                                                           
E: Prior errors apply to /var/cache/apt/archives/libhtml-template-perl_2.9-1_all.deb                                                                 
E: Prior errors apply to /var/cache/apt/archives/mysql-server_5.1.30really5.0.75-0ubuntu10_all.deb                                                   
E: Prior errors apply to /var/cache/apt/archives/mythtv-theme-blootube_1%3a0.21.0-0ubuntu1_all.deb                                                   
E: Prior errors apply to /var/cache/apt/archives/mythtv-theme-blootube-osd_1%3a0.21.0-0ubuntu2_all.deb                                               
E: Prior errors apply to /var/cache/apt/archives/mythtv-theme-blootube-wide_1%3a0.21.0-0ubuntu1_all.deb                                              
E: Prior errors apply to /var/cache/apt/archives/mythtv-theme-blootubelite-wide_1%3a0.21.0-0ubuntu1_all.deb                                          
E: Prior errors apply to /var/cache/apt/archives/mythtv-theme-glass-wide_0.20080908-0ubuntu2_all.deb                                                 
E: Prior errors apply to /var/cache/apt/archives/mythtv-theme-gray-osd_0.21.0-0ubuntu2_all.deb                                                       
E: Prior errors apply to /var/cache/apt/archives/mythtv-theme-isthmus_0.21.0-0ubuntu2_all.deb                                                        
E: Prior errors apply to /var/cache/apt/archives/mythtv-theme-iulius_0.21.0-0ubuntu2_all.deb                                                         
E: Prior errors apply to /var/cache/apt/archives/mythtv-theme-iulius-osd_0.21.0-0ubuntu2_all.deb                                                     
E: Prior errors apply to /var/cache/apt/archives/mythtv-theme-minimalist-wide_0.21.0-0ubuntu2_all.deb                                                
E: Prior errors apply to /var/cache/apt/archives/mythtv-theme-projectgrayhem_1%3a0.21.0-0ubuntu1_all.deb                                             
E: Prior errors apply to /var/cache/apt/archives/mythtv-theme-projectgrayhem-wide_1%3a0.21.0-0ubuntu2_all.deb                                        
E: Prior errors apply to /var/cache/apt/archives/mythtv-theme-mythbuntu_0.20080421_all.deb                                                           
E: Prior errors apply to /var/cache/apt/archives/mythtv-theme-mythcenter_0.21.0-0ubuntu2_all.deb                                                     
debconf: apt-extracttemplates failed: Bad file descriptor                                                                                            
Extracting templates from packages: 100%                                                                                                             
dpkg-deb: `/var/cache/apt/archives/libnet-daemon-perl_0.43-1_all.deb' is not a debian format archive                                                 
dpkg: error processing /var/cache/apt/archives/libnet-daemon-perl_0.43-1_all.deb (--unpack):                                                         
 subprocess dpkg-deb --control returned error exit status 2                                                                                          
dpkg-deb: `/var/cache/apt/archives/libplrpc-perl_0.2020-2_all.deb' is not a debian format archive                                                    
dpkg: error processing /var/cache/apt/archives/libplrpc-perl_0.2020-2_all.deb (--unpack):                                                            
 subprocess dpkg-deb --control returned error exit status 2                                                                                          
dpkg-deb: `/var/cache/apt/archives/libdbi-perl_1.608-1_amd64.deb' is not a debian format archive                                                     
dpkg: error processing /var/cache/apt/archives/libdbi-perl_1.608-1_amd64.deb (--unpack):                                                             
 subprocess dpkg-deb --control returned error exit status 2                                                                                          
Selecting previously deselected package libdbd-mysql-perl.                                                                                           
(Reading database ...                                                                                                                                
dpkg: serious warning: files list file for package `libmysqlclient15off' missing, assuming package has no files currently installed.                 

dpkg: serious warning: files list file for package `libqt3-mt-mysql' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mysql-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libqt4-sql-mysql' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mysql-server-core-5.0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libaprutil1-dbd-mysql' missing, assuming package has no files currently installed.
271992 files and directories currently installed.)                                                                                    
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.011-1_amd64.deb) ...                                                        
Selecting previously deselected package mysql-client-5.0.                                                                             
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.1.30really5.0.75-0ubuntu10_amd64.deb) ...                                     
Selecting previously deselected package mysql-server-5.0.                                                                             
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.75-0ubuntu10_amd64.deb) ...                                     
Selecting previously deselected package mysql-client.                                                                                 
Unpacking mysql-client (from .../mysql-client_5.1.30really5.0.75-0ubuntu10_all.deb) ...                                               
Selecting previously deselected package mythtv-common.                                                                                
Unpacking mythtv-common (from .../mythtv-common_0.21.0+fixes19961-0ubuntu8_all.deb) ...                                               
Selecting previously deselected package mythtv-database.                                                                              
Unpacking mythtv-database (from .../mythtv-database_0.21.0+fixes19961-0ubuntu8_all.deb) ...                                           
Selecting previously deselected package mythtv-frontend.                                                                              
Unpacking mythtv-frontend (from .../mythtv-frontend_0.21.0+fixes19961-0ubuntu8_amd64.deb) ...                                         
Selecting previously deselected package mythtv-transcode-utils.                                                                       
Unpacking mythtv-transcode-utils (from .../mythtv-transcode-utils_0.21.0+fixes19961-0ubuntu8_amd64.deb) ...                           
Selecting previously deselected package libmyth-perl.                                                                                 
Unpacking libmyth-perl (from .../libmyth-perl_0.21.0+fixes19961-0ubuntu8_all.deb) ...                                                 
Selecting previously deselected package mythtv-backend.                                                                               
Unpacking mythtv-backend (from .../mythtv-backend_0.21.0+fixes19961-0ubuntu8_amd64.deb) ...                                           
Processing triggers for man-db ...                                                                                                    
Processing triggers for desktop-file-utils ...                                                                                        
Processing triggers for menu ...                                                                                                      
Errors were encountered while processing:                                                                                             
 /var/cache/apt/archives/libnet-daemon-perl_0.43-1_all.deb                                                                            
 /var/cache/apt/archives/libplrpc-perl_0.2020-2_all.deb                                                                               
 /var/cache/apt/archives/libdbi-perl_1.608-1_amd64.deb                                                                                
E: Sub-process /usr/bin/dpkg returned an error code (1)                                                                               
A package failed to install.  Trying to recover:                                                                                      
dpkg: dependency problems prevent configuration of libmyth-perl:                                                                      
 libmyth-perl depends on libdbi-perl; however:                                                                                        
  Package libdbi-perl is not installed.                                                                                               
dpkg: error processing libmyth-perl (--configure):                                                                                    
 dependency problems - leaving unconfigured                                                                                           
dpkg: dependency problems prevent configuration of libdbd-mysql-perl:                                                                 
 libdbd-mysql-perl depends on libdbi-perl (>= 1.607); however:                                                                        
  Package libdbi-perl is not installed.                                                                                               
dpkg: error processing libdbd-mysql-perl (--configure):                                                                               
 dependency problems - leaving unconfigured                                                                                           
dpkg: dependency problems prevent configuration of mysql-server-5.0:                                                                  
 mysql-server-5.0 depends on libdbi-perl; however:                                                                                    
  Package libdbi-perl is not installed.                                                                                               
dpkg: error processing mysql-server-5.0 (--configure):                                                                                
 dependency problems - leaving unconfigured                                                                                           
dpkg: dependency problems prevent configuration of mythtv-backend:                                                                    
 mythtv-backend depends on libmyth-perl; however:                                                                                     
  Package libmyth-perl is not configured yet.                                                                                         
dpkg: error processing mythtv-backend (--configure):                                                                                  
 dependency problems - leaving unconfigured                                                                                           
dpkg: dependency problems prevent configuration of mysql-client-5.0:                                                                  
 mysql-client-5.0 depends on libdbi-perl; however:                                                                                    
  Package libdbi-perl is not installed.                                                                                               
 mysql-client-5.0 depends on libdbd-mysql-perl (>= 1.2202); however:                                                                  
  Package libdbd-mysql-perl is not configured yet.                                                                                    
dpkg: error processing mysql-client-5.0 (--configure):                                                                                
 dependency problems - leaving unconfigured                                                                                           
dpkg: dependency problems prevent configuration of mythtv-database:                                                                   
 mythtv-database depends on libdbd-mysql-perl; however:                                                                               
  Package libdbd-mysql-perl is not configured yet.                                                                                    
dpkg: error processing mythtv-database (--configure):                                                                                 
 dependency problems - leaving unconfigured                                                                                           
dpkg: dependency problems prevent configuration of mysql-client:                                                                      
 mysql-client depends on mysql-client-5.0; however:                                                                                   
  Package mysql-client-5.0 is not configured yet.                                                                                     
dpkg: error processing mysql-client (--configure):                                                                                    
 dependency problems - leaving unconfigured                                                                                           
dpkg: dependency problems prevent configuration of mythtv-common:                                                                     
 mythtv-common depends on mysql-client; however:                                                                                      
  Package mysql-client is not configured yet.                                                                                         
  Package mysql-client-5.0 which provides mysql-client is not configured yet.                                                         
dpkg: error processing mythtv-common (--configure):                                                                                   
 dependency problems - leaving unconfigured                                                                                           
dpkg: dependency problems prevent configuration of mythtv-transcode-utils:                                                            
 mythtv-transcode-utils depends on mythtv-common (= 0.21.0+fixes19961-0ubuntu8); however:                                             
  Package mythtv-common is not configured yet.                                                                                        
dpkg: error processing mythtv-transcode-utils (--configure):                                                                          
 dependency problems - leaving unconfigured                                                                                           
dpkg: dependency problems prevent configuration of mythtv-frontend:                                                                   
 mythtv-frontend depends on mythtv-common (= 0.21.0+fixes19961-0ubuntu8); however:                                                    
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-frontend (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libmyth-perl
 libdbd-mysql-perl
 mysql-server-5.0
 mythtv-backend
 mysql-client-5.0
 mythtv-database
 mysql-client
 mythtv-common
 mythtv-transcode-utils
 mythtv-frontend
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done

Current status: 4 broken [+4].

```
Anyone know how to fix this

---

