---
title: "MPD installation broke aptitude"
date: 2009-06-14
forum: Multimedia Software
---

### Post by k420 on 2009-06-14
Mpd works just fine but it is causing errors in my package manager as it keeps trying to configure it. I would like to kep mpd as i like it despite the skipping sometimes of songs for no reason   Here is the output 
```
nathan@nathan-gamer:~/Desktop$ sudo aptitude safe-upgrade 
Reading package lists... Done                             
Building dependency tree                                  
Reading state information... Done                         
Reading extended state information                        
Initializing package states... Done                       
The following partially installed packages will be configured:
  mpd                                                         
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.           
Setting up mpd (0.14.2-3ubuntu2) ...                                   
 * Starting Music Player Daemon mpd                                                                                                                  mkdir: cannot create directory `~/.mpd': No such file or directory                                                                                   
chown: cannot access `~/.mpd': No such file or directory                                                                                             
 * creating ~/.mpd/mpd.db/db...                                                                                                                      
unable to bind port 6600: Address already in use                                                                                                     
maybe MPD is still running?                                                                                                                          
Aborted                                                                                                                                              
                                                                                                                                              [fail] 
invoke-rc.d: initscript mpd, action "start" failed.                                                                                                  
dpkg: error processing mpd (--configure):                                                                                                            
 subprocess post-installation script returned error exit status 134                                                                                  
Errors were encountered while processing:                                                                                                            
 mpd                                                                                                                                                 
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mpd (0.14.2-3ubuntu2) ...
 * Starting Music Player Daemon mpdmkdir: cannot create directory `~/.mpd': No such file or directory
chown: cannot access `~/.mpd': No such file or directory
 * creating ~/.mpd/mpd.db/db...
unable to bind port 6600: Address already in use
maybe MPD is still running?
Aborted
                                                                                                                                              [fail]
invoke-rc.d: initscript mpd, action "start" failed.
dpkg: error processing mpd (--configure):
 subprocess post-installation script returned error exit status 134
Errors were encountered while processing:
 mpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done

nathan@nathan-gamer:~/Desktop$

```

---

