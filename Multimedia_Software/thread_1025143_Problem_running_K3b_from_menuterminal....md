---
title: "Problem running K3b from menu/terminal..."
date: 2008-12-29
forum: Multimedia Software
---

### Post by KostadinDaveth on 2008-12-29
Okay, so I have a dvd that I need to burn.  When I tried to run k3b from the apps menu nothing happened.  I then tried running it from terminal using the sudo k3b command.  I got this output:

```
root@Josh Laptop:/home/josh# sudo k3b
sudo: unable to resolve host Josh Laptop
/usr/bin/iceauth:  creating new authority file /root/.ICEauthority
/usr/bin/iceauth: /tmp/dcopPfMg8b:1:  bad "add" command line
/usr/bin/iceauth: /tmp/dcopPfMg8b:2:  bad "add" command line
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
ICE Connection rejected!

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPServer self-test failed.
iceauth:  creating new authority file /root/.ICEauthority
ICE Connection rejected!

kdeinit: DCOPServer could not be started, aborting.

```

I have no idea what this means.  Do I need to reinstall k3b or something?

---

### Post by SuperSonic4 on 2008-12-29
k3b doesn't need root priveliges? What happens if you run it as user?
You might also need to do ```
kdesu k3b
``` as k3b is a GUI program.

I suppose it could be a sudo problem, have you done anything to sudo?

---

### Post by KostadinDaveth on 2008-12-29
That didn't seem to work.  I got another error...

```
josh@Josh Laptop:~$ kdesu k3b
bash: kdesu: command not found
josh@Josh Laptop:~$ sudo k3b
sudo: unable to resolve host Josh Laptop
[sudo] password for josh: 
Error: "/tmp/kde-josh" is owned by uid 1001 instead of uid 0.
Error: "/tmp/ksocket-josh" is owned by uid 1001 instead of uid 0.
/usr/bin/iceauth: /tmp/dcopPfMg8b:1:  bad "add" command line
/usr/bin/iceauth: /tmp/dcopPfMg8b:2:  bad "add" command line
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
ICE Connection rejected!

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPServer self-test failed.
ICE Connection rejected!

kdeinit: DCOPServer could not be started, aborting.

```

Wait, "sudo: unable to resolve host Josh Laptop"?  Would that have anything to do me changing my computer's name or id?  I changed it from "linuxlap1" to "Josh Laptop"

---

### Post by SuperSonic4 on 2008-12-29
What about running as normal user? 

I remember having a similar problem on mandriva where none of my kde3 apps would load up and so I changed to kubuntu. Does it work on any other kde3 apps assuming you have any. Hmm, it works for me with sudo

```
lee@lee-desktop:~$ sudo k3b
lee@lee-desktop:~$ (K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_model_DVD_RW_AD_7200S to device /dev/scd0
Mapping udi /org/freedesktop/Hal/devices/storage_model_DVD_Writer_1040d to device /dev/scd1
/dev/scd0 resolved to /dev/scd0                                                            
/dev/scd0 is block device (0)                                                              
/dev/scd0 seems to be cdrom                                                                
bus: 2, id: 0, lun: 0                                                                      
(K3bDevice::Device) /dev/scd0: init()                                                      
(K3bDevice::Device) /dev/scd0 feature: CD Mastering                                        
(K3bDevice::Device) /dev/scd0 feature: CD Track At Once                                    
(K3bDevice::Device) /dev/scd0 feature: CD-RW Media Write Support                           
(K3bDevice::Device) /dev/scd0 feature: DVD Read (MMC5)                                     
(K3bDevice::Device) /dev/scd0 feature: DVD+R                                               
(K3bDevice::Device) /dev/scd0 feature: DVD+RW                                              
(K3bDevice::Device) /dev/scd0 feature: DVD+R Double Layer                                  
(K3bDevice::Device) /dev/scd0 feature: DVD-R/-RW Write                                     
(K3bDevice::Device) /dev/scd0 feature: Rigid Restricted Overwrite                          
(K3bDevice::Device) /dev/scd0 feature: Layer Jump Recording                                
(K3bDevice::Device) /dev/scd0 unknown profile: 2                                           
(K3bDevice::Device) /dev/scd0: dataLen: 60                                                 
(K3bDevice::Device) /dev/scd0: checking for TAO                                            
(K3bDevice::Device) /dev/scd0: checking for SAO                                            
(K3bDevice::Device) /dev/scd0: checking for SAO_R96P                                       
(K3bDevice::ScsiCommand) failed:                                                           
                           command:    MODE SELECT (55)                                    
                           errorcode:  70                                                  
                           sense key:  ILLEGAL REQUEST (5)                                 
                           asc:        26                                                  
                           ascq:       0                                                   
(K3bDevice::Device) /dev/scd0: checking for SAO_R96R                                       
(K3bDevice::Device) /dev/scd0: checking for RAW_R16                                        
(K3bDevice::ScsiCommand) failed:                                                           
                           command:    MODE SELECT (55)                                    
                           errorcode:  70                                                  
                           sense key:  ILLEGAL REQUEST (5)                                 
                           asc:        26                                                  
                           ascq:       0                                                   
(K3bDevice::Device) /dev/scd0: checking for RAW_R96P                                       
(K3bDevice::ScsiCommand) failed:                                                           
                           command:    MODE SELECT (55)                                    
                           errorcode:  70                                                  
                           sense key:  ILLEGAL REQUEST (5)                                 
                           asc:        26                                                  
                           ascq:       0                                                   
(K3bDevice::Device) /dev/scd0: checking for RAW_R96R                                       
(K3bDevice::Device) /dev/scd0: GET PERFORMANCE dataLen = 104                               
(K3bDevice::Device) /dev/scd0: GET PERFORMANCE successful with reported length: 100        
(K3bDevice::Device) /dev/scd0:  Number of supported write speeds via GET PERFORMANCE: 6    
(K3bDevice::Device) /dev/scd0 : 8467 KB/s                                                  
(K3bDevice::Device) /dev/scd0 : 7056 KB/s                                                  
(K3bDevice::Device) /dev/scd0 : 5645 KB/s                                                  
(K3bDevice::Device) /dev/scd0 : 4234 KB/s                                                  
(K3bDevice::Device) /dev/scd0 : 2822 KB/s                                                  
(K3bDevice::Device) /dev/scd0 : 1411 KB/s                                                  
(K3bDevice::DeviceManager) setting current write speed of device /dev/scd0 to 3324         
/dev/scd1 resolved to /dev/scd1                                                            
/dev/scd1 is block device (1)                                                              
/dev/scd1 seems to be cdrom                                                                
bus: 9, id: 0, lun: 0                                                                      
(K3bDevice::Device) /dev/scd1: init()                                                      
(K3bDevice::Device) /dev/scd1 feature: CD Mastering                                        
(K3bDevice::Device) /dev/scd1 feature: CD Track At Once                                    
(K3bDevice::Device) /dev/scd1 feature: CD-RW Media Write Support                           
(K3bDevice::Device) /dev/scd1 feature: DVD Read (MMC5)                                     
(K3bDevice::Device) /dev/scd1 feature: DVD+R                                               
(K3bDevice::Device) /dev/scd1 feature: DVD+RW                                              
(K3bDevice::Device) /dev/scd1 feature: DVD+R Double Layer                                  
(K3bDevice::Device) /dev/scd1 feature: DVD-R/-RW Write                                     
(K3bDevice::Device) /dev/scd1 feature: Rigid Restricted Overwrite                          
(K3bDevice::Device) /dev/scd1 feature: Layer Jump Recording                                
(K3bDevice::Device) /dev/scd1 unknown profile: 2                                           
(K3bDevice::Device) /dev/scd1: dataLen: 60                                                 
(K3bDevice::Device) /dev/scd1: checking for TAO                                            
(K3bDevice::Device) /dev/scd1: checking for SAO                                            
(K3bDevice::Device) /dev/scd1: checking for SAO_R96P                                       
(K3bDevice::Device) /dev/scd1: checking for SAO_R96R                                       
(K3bDevice::Device) /dev/scd1: checking for RAW_R16                                        
(K3bDevice::Device) /dev/scd1: checking for RAW_R96P                                       
(K3bDevice::Device) /dev/scd1: checking for RAW_R96R                                       
(K3bDevice::DeviceManager) setting current write speed of device /dev/scd1 to 8467         
/dev/scd0 resolved to /dev/scd0                                                            
(K3bDevice::DeviceManager) dev /dev/scd0 already found                                     
/dev/scd1 resolved to /dev/scd1                                                            
(K3bDevice::DeviceManager) dev /dev/scd1 already found                                     
(K3bDevice::DeviceManager) found config entry for devicetype: Optiarc DVD RW AD-7200S      
(K3bDevice::DeviceManager) found config entry for devicetype: HP DVD Writer 1040d          
Devices:                                                                                   
------------------------------                                                             
Blockdevice:    /dev/scd0                                                                  
Generic device:                                                                            
Vendor:         Optiarc                                                                    
Description:    DVD RW AD-7200S                                                            
Version:        1.01                                                                       
Write speed:    3324                                                                       
Profiles:       DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW                                
Read Cap:       DVD-ROM, DVD-R, DVD-R Sequential, DVD-R Dual Layer, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+RW Dual Layer, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW                                                                                                           
Write Cap:      DVD-R, DVD-R Sequential, DVD-R Dual Layer, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-R, CD-RW                         
Writing modes:  SAO, TAO, RAW, SAO/R96R, RAW/R96R, Restricted Overwrite, Layer Jump                                   
Reader aliases: /dev/scd0                                                                                             
------------------------------                                                                                        
Blockdevice:    /dev/scd1                                                                                             
Generic device:                                                                                                       
Vendor:         HP                                                                                                    
Description:    DVD Writer 1040d                                                                                      
Version:        EH23                                                                                                  
Write speed:    0                                                                                                     
Profiles:       DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW                                
Read Cap:       DVD-ROM, DVD-R, DVD-R Sequential, DVD-R Dual Layer, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+RW Dual Layer, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW                                                                                                           
Write Cap:      DVD-R, DVD-R Sequential, DVD-R Dual Layer, DVD-R Dual Layer Jump, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-R, CD-RW                                                      
Writing modes:  SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump      
Reader aliases: /dev/scd1                                                                                             
------------------------------                                                                                        
   0 - 01001111 - 79                                                                                                  
   1 - 00111011 - 59                                                                                                  
   2 - 01001010 - 74                                                                                                  
/dev/scd1: ATIP capacity: 79:57:74                                                                                    
(K3bDevice::Device) READ CAPACITY: 79:33:64 other capacity: 79:57:74                                                  
DiskInfo:                                                                                                             
Mediatype:       CD-R                                                                                                 
Current Profile: CD-R                                                                                                 
Disk state:      complete                                                                                             
Empty:           0                                                                                                    
Rewritable:      0
Appendable:      0
Sessions:        1
Tracks:          1
Layers:          1
Capacity:        79:57:74 (LBA 359849) (736970752 Bytes)
Remaining size:  00:00:00 (LBA 0) (0 Bytes)
Used Size:       79:33:65 (LBA 358040) (733265920 Bytes)
Session |  ADR   | CONTROL|  TNO   | POINT  |  Min   |  Sec   | Frame  |  Zero  |  PMIN  |  PSEC  | PFRAME |
      1 |      1 |      4 |      0 |     a0 |      0 |      0 |      0 |      0 |      1 |      0 |      0 |
      1 |      1 |      4 |      0 |     a1 |      0 |      0 |      0 |      0 |      1 |      0 |      0 |
      1 |      1 |      4 |      0 |     a2 |      0 |      0 |      0 |      0 |     79 |     35 |     65 |
      1 |      1 |      4 |      0 |      1 |      0 |      0 |      0 |      0 |      0 |      2 |      0 |
(K3bDevice::Device) found invalid bcd values. No bcd toc.
Error: "/var/tmp/kdecache-lee" is owned by uid 500 instead of uid 0.
Error: "/tmp/kde-lee" is owned by uid 500 instead of uid 0.
Error: "/tmp/ksocket-lee" is owned by uid 500 instead of uid 0.
/dev/scd1: setting last sector of last track to 358039
(K3bDevice::Device) /dev/scd1:  Number of supported write speeds via 2A: 5
(K3bDevice::Device) /dev/scd1 : 8467 KB/s
(K3bDevice::Device) /dev/scd1 : 7056 KB/s
(K3bDevice::Device) /dev/scd1 : 5645 KB/s
(K3bDevice::Device) /dev/scd1 : 4234 KB/s
(K3bDevice::Device) /dev/scd1 : 2822 KB/s

```

---

### Post by KostadinDaveth on 2008-12-29
> **SuperSonic4 said:**
> What about running as normal user? 

I remember having a similar problem on mandriva where none of my kde3 apps would load up and so I changed to kubuntu. Does it work on any other kde3 apps assuming you have any. Hmm, it works for me with sudo

Well, I have Kbattleship and Klottski.  Do those count as KDE apps?

---

### Post by pansz on 2008-12-29
1. In ubuntu, gui-apps cannot run under sudo, so you should not use sudo for gui application.

2. some kde apps need kdeinit if you run it under gnome. so simply run kdeinit in your terminal and then run k3b, which might work.

3. if you need kdesu you should install kdesu first, I don't know if kdesu works in gnome, but I know gksu works in kubuntu.

4. k3b do not need root previledge at all and I don't know why you attempt to run it under root.

---

### Post by KostadinDaveth on 2008-12-29
When I try running kdeinit I still get the error I got previously.  I'm thinking that no one command will fix this?  Maybe it needs reinstalled or I need another app? Here's what I got:

```
kdeinit
/usr/bin/iceauth: /tmp/dcopPfMg8b:1:  bad "add" command line
/usr/bin/iceauth: /tmp/dcopPfMg8b:2:  bad "add" command line
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
ICE Connection rejected!

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPServer self-test failed.
ICE Connection rejected!

kdeinit: DCOPServer could not be started, aborting.

```

---

### Post by KostadinDaveth on 2008-12-30
Bump

---

### Post by KostadinDaveth on 2008-12-30
So I think the problem has something to do with my hostname...
```
josh@Josh Laptop:~$ hostname
Josh Laptop
josh@Josh Laptop:~$ hostname --fqd
hostname: Unknown host

```

And I get this when I try to run k3b...
```
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
ICE Connection rejected!

```

Okay.  I checked my /etc/hosts file and this is what it says:
```
127.0.0.1	Josh Laptop	localhost.localdomain	localhost
127.0.1.1 linuxlap1
```

It displays both hostnames (new and old).  Will fixing this somehow solve my hostname not found problem?

---

### Post by KostadinDaveth on 2008-12-30
Nevermind.  All I had to do was change my hostname back to linuxlap1.  Problem solved!

---

