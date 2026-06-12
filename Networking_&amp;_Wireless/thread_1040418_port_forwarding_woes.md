---
title: "port forwarding woes"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by unused_bagels on 2009-01-15
I just installed Kubuntu 8 on my windows machine.  I'm using Ktorrent.  
I'm no stranger to port forwarding, and I've forwarded my ktorrent ports to my router AND my modem.  I tried using a portforwarding website (two actually) and they both said that the ports weren't forwarded.  I spent all morning relearning Konsole (yeah, I'm a return customer) to set up my static IP with the router, and the ports still aren't forwarded, and I'm downloading at a whopping 3Kb/s !! ](*,) I'll give you whatever Konsole outputs you want.  I can't figure out what I'm doing wrong.

---

### Post by unused_bagels on 2009-01-15
This is my netstat -a output.  At the top is KTorrent.  I'm using a range of 6881-6889 on my ports forwarding.
```
derek@Mr:~$ netstat -a
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:6881                  *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 Mr.local:57286          oam-d03c.blue.aol.c:aol ESTABLISHED
tcp        0      0 Mr.local:53628          64.12.104.180:aol       ESTABLISHED
tcp        0      0 Mr.local:39732          206-169.amazon.com:www  ESTABLISHED
tcp        0      0 Mr.local:39730          206-169.amazon.com:www  ESTABLISHED
tcp        0      0 Mr.local:55810          caim-d04b.blue.aol.:aol ESTABLISHED
tcp        0      0 Mr.local:51261          203.212.220.142:50233   ESTABLISHED
tcp        0      0 Mr.local:47362          64.12.28.52:aol         ESTABLISHED
tcp        0      0 Mr.local:39731          206-169.amazon.com:www  ESTABLISHED
tcp        0      0 Mr.local:39733          206-169.amazon.com:www  ESTABLISHED
tcp        0      0 Mr.local:48076          205.188.8.129:aol       ESTABLISHED
tcp        1      0 Mr.local:38832          198.78.220.125:www      CLOSE_WAIT 
tcp        0      0 Mr.local:47717          166-176.amazon.com:www  ESTABLISHED
tcp        0  44350 Mr.local:40862          fibhost-195-151.f:37899 ESTABLISHED
tcp        0  12510 Mr.local:60453          host-92-2-223-207:65090 ESTABLISHED
tcp6       0      0 [::]:netbios-ssn        [::]:*                  LISTEN     
tcp6       0      0 [::]:microsoft-ds       [::]:*                  LISTEN     
udp        0      0 Mr.local:netbios-ns     *:*                                
udp        0      0 *:netbios-ns            *:*                                
udp        0      0 Mr.local:netbios-dgm    *:*                                
udp        0      0 *:netbios-dgm           *:*                                
udp        0      0 *:bootpc                *:*                                
udp        0      0 *:43853                 *:*                                
udp        0      0 *:mdns                  *:*                                
udp6       0      0 [::]:6883               [::]:*                             
Active UNIX domain sockets (servers and established)                           
Proto RefCnt Flags       Type       State         I-Node   Path                
unix  2      [ ACC ]     STREAM     LISTENING     15083    /tmp/.winbindd/pipe 
unix  2      [ ACC ]     STREAM     LISTENING     16097    /tmp/.X11-unix/X0   
unix  2      [ ACC ]     STREAM     LISTENING     15878    /var/run/sdp        
unix  2      [ ACC ]     STREAM     LISTENING     16677    /tmp/ssh-Lkpqzn5442/agent.5442
unix  2      [ ACC ]     STREAM     LISTENING     17162    /tmp/ksocket-derek/kdeinit4__0
unix  2      [ ACC ]     STREAM     LISTENING     17174    /tmp/ksocket-derek/klauncherMT5578.slave-socket
unix  2      [ ACC ]     STREAM     LISTENING     17236    /tmp/.ICE-unix/5586                            
unix  2      [ ACC ]     STREAM     LISTENING     15071    @/var/run/hald/dbus-1dgAlKKhXg                 
unix  2      [ ACC ]     STREAM     LISTENING     19080    /tmp/orbit-derek/linc-16d2-0-17a53192d47ac     
unix  2      [ ACC ]     STREAM     LISTENING     66624    /tmp/orbit-derek/linc-31d2-0-301e7da299ea0     
unix  2      [ ACC ]     STREAM     LISTENING     18717    /tmp/ksocket-derek/Mr.Hooper-Desky-1690-496e83a8
unix  2      [ ACC ]     STREAM     LISTENING     18291    /tmp/ksocket-derek/kdeinit__0                   
unix  2      [ ACC ]     STREAM     LISTENING     18293    /tmp/ksocket-derek/kdeinit-:0                   
unix  2      [ ACC ]     STREAM     LISTENING     18312    /tmp/.ICE-unix/dcop5751-1231979413              
unix  2      [ ACC ]     STREAM     LISTENING     19092    /tmp/orbit-derek/linc-163e-0-169e199d7ca5       
unix  2      [ ACC ]     STREAM     LISTENING     18332    /tmp/ksocket-derek/klauncherWI6Mrc.slave-socket 
unix  2      [ ACC ]     STREAM     LISTENING     21711    /tmp/ksocket-root/kdeinit4__0                   
unix  2      [ ACC ]     STREAM     LISTENING     21729    /tmp/ksocket-root/klauncherMT8926.slave-socket  
unix  2      [ ACC ]     STREAM     LISTENING     15093    @/var/run/hald/dbus-yEWAJ6Z9uO                  
unix  2      [ ]         DGRAM                    5585     @/com/ubuntu/upstart                            
unix  2      [ ACC ]     STREAM     LISTENING     21686    @/tmp/dbus-WFq2PqKs1a                           
unix  2      [ ACC ]     STREAM     LISTENING     14414    /var/run/acpid.socket                           
unix  2      [ ACC ]     STREAM     LISTENING     15900    @/org/bluez/audio                               
unix  2      [ ACC ]     STREAM     LISTENING     16096    @/tmp/.X11-unix/X0                              
unix  2      [ ]         DGRAM                    5821     @/org/kernel/udev/udevd                         
unix  2      [ ACC ]     STREAM     LISTENING     14725    /var/run/dbus/system_bus_socket                 
unix  2      [ ]         DGRAM                    15120    @/org/freedesktop/hal/udev_event                
unix  2      [ ACC ]     STREAM     LISTENING     17646    /home/derek/.kde/share/apps/nepomuk/socket      
unix  2      [ ACC ]     STREAM     LISTENING     14774    /var/run/avahi-daemon/socket                    
unix  2      [ ACC ]     STREAM     LISTENING     16064    /var/run/xdmctl/dmctl/socket                    
unix  2      [ ACC ]     STREAM     LISTENING     16450    @/tmp/dbus-gwQCFWstpl                           
unix  2      [ ACC ]     STREAM     LISTENING     16806    @/tmp/dbus-0HH1HglOEV                           
unix  2      [ ACC ]     STREAM     LISTENING     16364    /var/run/xdmctl/dmctl-:0/socket                 
unix  2      [ ACC ]     STREAM     LISTENING     15085    /var/run/samba/winbindd_privileged/pipe         
unix  2      [ ACC ]     STREAM     LISTENING     33789    /var/run/cups/cups.sock                         
unix  10     [ ]         DGRAM                    14590    /dev/log                                        
unix  3      [ ]         STREAM     CONNECTED     86126    /tmp/.ICE-unix/5586                             
unix  3      [ ]         STREAM     CONNECTED     86125                                                    
unix  3      [ ]         STREAM     CONNECTED     86120    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     86119                                                    
unix  3      [ ]         STREAM     CONNECTED     86110    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     86109                                                    
unix  3      [ ]         STREAM     CONNECTED     86103    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     86102                                                    
unix  7      [ ]         STREAM     CONNECTED     86041    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     86040                                                    
unix  3      [ ]         STREAM     CONNECTED     86039    /tmp/ksocket-derek/ktorrentt12911.slave-socket  
unix  3      [ ]         STREAM     CONNECTED     86038                                                    
unix  3      [ ]         STREAM     CONNECTED     85707    /tmp/ksocket-root/klauncherMT8926.slave-socket  
unix  3      [ ]         STREAM     CONNECTED     85706                                                    
unix  3      [ ]         STREAM     CONNECTED     85705    /tmp/ksocket-derek/klauncherMT5578.slave-socket 
unix  3      [ ]         STREAM     CONNECTED     85704                                                    
unix  3      [ ]         STREAM     CONNECTED     85703    /tmp/ksocket-derek/klauncherWI6Mrc.slave-socket 
unix  3      [ ]         STREAM     CONNECTED     85702                                                    
unix  2      [ ]         STREAM     CONNECTED     84758                                                    
unix  2      [ ]         STREAM     CONNECTED     84743                                                    
unix  2      [ ]         STREAM     CONNECTED     81544                                                    
unix  2      [ ]         STREAM     CONNECTED     75964                                                    
unix  2      [ ]         STREAM     CONNECTED     75391                                                    
unix  2      [ ]         STREAM     CONNECTED     75174                                                    
unix  2      [ ]         STREAM     CONNECTED     74936                                                    
unix  2      [ ]         STREAM     CONNECTED     74689                                                    
unix  2      [ ]         STREAM     CONNECTED     74307                                                    
unix  2      [ ]         STREAM     CONNECTED     74301                                                    
unix  2      [ ]         STREAM     CONNECTED     73076                                                    
unix  232    [ ]         STREAM     CONNECTED     73039    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     73038                                                    
unix  2      [ ]         STREAM     CONNECTED     72878                                                    
unix  2      [ ]         STREAM     CONNECTED     71267                                                    
unix  2      [ ]         STREAM     CONNECTED     71249                                                    
unix  2      [ ]         STREAM     CONNECTED     70959                                                    
unix  3      [ ]         STREAM     CONNECTED     69531    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     69530                                                    
unix  2      [ ]         STREAM     CONNECTED     69492                                                    
unix  2      [ ]         STREAM     CONNECTED     69096                                                    
unix  3      [ ]         STREAM     CONNECTED     68830    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     68829                                                    
unix  3      [ ]         STREAM     CONNECTED     68828    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     68827                                                    
unix  3      [ ]         STREAM     CONNECTED     68379    /tmp/.ICE-unix/5586                             
unix  3      [ ]         STREAM     CONNECTED     68378                                                    
unix  3      [ ]         STREAM     CONNECTED     68377    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     68376                                                    
unix  3      [ ]         STREAM     CONNECTED     68366    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     68365                                                    
unix  3      [ ]         STREAM     CONNECTED     66645    /tmp/.ICE-unix/5586                             
unix  3      [ ]         STREAM     CONNECTED     66644                                                    
unix  259    [ ]         STREAM     CONNECTED     66643    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     66642                                                    
unix  3      [ ]         STREAM     CONNECTED     66635    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     66634                                                    
unix  3      [ ]         STREAM     CONNECTED     66627    /tmp/orbit-derek/linc-31d2-0-301e7da299ea0      
unix  3      [ ]         STREAM     CONNECTED     66626                                                    
unix  3      [ ]         STREAM     CONNECTED     66623    /tmp/orbit-derek/linc-16d2-0-17a53192d47ac      
unix  3      [ ]         STREAM     CONNECTED     66622                                                    
unix  3      [ ]         STREAM     CONNECTED     66621    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     66620                                                    
unix  3      [ ]         STREAM     CONNECTED     66619    /tmp/.ICE-unix/5586                             
unix  3      [ ]         STREAM     CONNECTED     66618                                                    
unix  3      [ ]         STREAM     CONNECTED     66612    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     66611                                                    
unix  3      [ ]         STREAM     CONNECTED     63815    /tmp/.ICE-unix/5586                             
unix  3      [ ]         STREAM     CONNECTED     63814                                                    
unix  3      [ ]         STREAM     CONNECTED     63813    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     63810                                                    
unix  3      [ ]         STREAM     CONNECTED     63807    /tmp/.ICE-unix/dcop5751-1231979413              
unix  3      [ ]         STREAM     CONNECTED     63806                                                    
unix  3      [ ]         STREAM     CONNECTED     63566                                                    
unix  3      [ ]         STREAM     CONNECTED     63565                                                    
unix  3      [ ]         STREAM     CONNECTED     63564                                                    
unix  3      [ ]         STREAM     CONNECTED     63563                                                    
unix  3      [ ]         STREAM     CONNECTED     63562                                                    
unix  3      [ ]         STREAM     CONNECTED     63561                                                    
unix  3      [ ]         STREAM     CONNECTED     63517    /tmp/.ICE-unix/dcop5751-1231979413              
unix  3      [ ]         STREAM     CONNECTED     63516                                                    
unix  3      [ ]         STREAM     CONNECTED     63508    /tmp/.ICE-unix/5586                             
unix  3      [ ]         STREAM     CONNECTED     63507                                                    
unix  3      [ ]         STREAM     CONNECTED     63506    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     63505                                                    
unix  2      [ ]         STREAM     CONNECTED     63503                                                    
unix  3      [ ]         STREAM     CONNECTED     62528    /tmp/.ICE-unix/dcop5751-1231979413              
unix  3      [ ]         STREAM     CONNECTED     62527                                                    
unix  3      [ ]         STREAM     CONNECTED     62517    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     62516                                                    
unix  3      [ ]         STREAM     CONNECTED     58993    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     58992                                                    
unix  3      [ ]         STREAM     CONNECTED     49135    /tmp/.ICE-unix/5586                             
unix  3      [ ]         STREAM     CONNECTED     49134                                                    
unix  3      [ ]         STREAM     CONNECTED     49133    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     49132                                                    
unix  3      [ ]         STREAM     CONNECTED     49123    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     49122                                                    
unix  2      [ ]         STREAM     CONNECTED     23243                                                    
unix  2      [ ]         STREAM     CONNECTED     21955                                                    
unix  3      [ ]         STREAM     CONNECTED     21759    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     21758                                                    
unix  3      [ ]         STREAM     CONNECTED     21745    @/tmp/dbus-WFq2PqKs1a                           
unix  3      [ ]         STREAM     CONNECTED     21744                                                    
unix  3      [ ]         STREAM     CONNECTED     21732    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     21731                                                    
unix  3      [ ]         STREAM     CONNECTED     21727    @/tmp/dbus-WFq2PqKs1a                           
unix  3      [ ]         STREAM     CONNECTED     21726                                                    
unix  3      [ ]         STREAM     CONNECTED     21714                                                    
unix  3      [ ]         STREAM     CONNECTED     21713                                                    
unix  3      [ ]         STREAM     CONNECTED     21690    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     21689                                                    
unix  3      [ ]         STREAM     CONNECTED     21688                                                    
unix  3      [ ]         STREAM     CONNECTED     21687                                                    
unix  3      [ ]         STREAM     CONNECTED     21674    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     21673                                                    
unix  3      [ ]         STREAM     CONNECTED     20812    /home/derek/.kde/share/apps/nepomuk/socket      
unix  3      [ ]         STREAM     CONNECTED     20811                                                    
unix  3      [ ]         STREAM     CONNECTED     20567    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     20566                                                    
unix  3      [ ]         STREAM     CONNECTED     19095    /tmp/orbit-derek/linc-163e-0-169e199d7ca5       
unix  3      [ ]         STREAM     CONNECTED     19094                                                    
unix  3      [ ]         STREAM     CONNECTED     19091    /tmp/orbit-derek/linc-16d2-0-17a53192d47ac      
unix  3      [ ]         STREAM     CONNECTED     19090                                                    
unix  3      [ ]         STREAM     CONNECTED     19087    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     19086                                                    
unix  3      [ ]         STREAM     CONNECTED     19083    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     19082                                                    
unix  3      [ ]         STREAM     CONNECTED     19022    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     19021                                                    
unix  3      [ ]         STREAM     CONNECTED     19020    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     19019                                                    
unix  3      [ ]         STREAM     CONNECTED     19011    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     19010                                                    
unix  3      [ ]         STREAM     CONNECTED     19007    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     19006                                                    
unix  3      [ ]         STREAM     CONNECTED     19005    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     19004                                                    
unix  3      [ ]         STREAM     CONNECTED     18738    /tmp/ksocket-derek/Mr.Hooper-Desky-1690-496e83a8
unix  3      [ ]         STREAM     CONNECTED     18737                                                    
unix  2      [ ]         STREAM     CONNECTED     18712    /tmp/ksocket-derek/kdeinit__0                   
unix  3      [ ]         STREAM     CONNECTED     18687    /tmp/.ICE-unix/5586                             
unix  3      [ ]         STREAM     CONNECTED     18686                                                    
unix  3      [ ]         STREAM     CONNECTED     18684    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     18682                                                    
unix  3      [ ]         STREAM     CONNECTED     18679    /tmp/.ICE-unix/dcop5751-1231979413              
unix  3      [ ]         STREAM     CONNECTED     18678                                                    
unix  3      [ ]         STREAM     CONNECTED     18348    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     18347                                                    
unix  3      [ ]         STREAM     CONNECTED     18344    /tmp/.ICE-unix/dcop5751-1231979413              
unix  3      [ ]         STREAM     CONNECTED     18343                                                    
unix  3      [ ]         STREAM     CONNECTED     18335    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     18334                                                    
unix  3      [ ]         STREAM     CONNECTED     18326    /tmp/.ICE-unix/dcop5751-1231979413              
unix  3      [ ]         STREAM     CONNECTED     18325                                                    
unix  3      [ ]         STREAM     CONNECTED     18323                                                    
unix  3      [ ]         STREAM     CONNECTED     18322                                                    
unix  3      [ ]         STREAM     CONNECTED     18278    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     18277                                                    
unix  3      [ ]         STREAM     CONNECTED     18208    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     18207                                                    
unix  3      [ ]         STREAM     CONNECTED     18205    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     18204                                                    
unix  3      [ ]         STREAM     CONNECTED     18191    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     18190                                                    
unix  3      [ ]         STREAM     CONNECTED     18189    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     18188                                                    
unix  3      [ ]         STREAM     CONNECTED     18163    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     18162                                                    
unix  3      [ ]         STREAM     CONNECTED     18180    /tmp/.ICE-unix/5586                             
unix  3      [ ]         STREAM     CONNECTED     18161                                                    
unix  3      [ ]         STREAM     CONNECTED     18160    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     18159                                                    
unix  3      [ ]         STREAM     CONNECTED     18158    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     18157                                                    
unix  3      [ ]         STREAM     CONNECTED     18179    /tmp/.ICE-unix/5586                             
unix  3      [ ]         STREAM     CONNECTED     18152                                                    
unix  3      [ ]         STREAM     CONNECTED     18151    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     18150                                                    
unix  3      [ ]         STREAM     CONNECTED     18149    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     18148                                                    
unix  3      [ ]         STREAM     CONNECTED     18178    /tmp/.ICE-unix/5586                             
unix  3      [ ]         STREAM     CONNECTED     18137                                                    
unix  3      [ ]         STREAM     CONNECTED     18136    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     18135                                                    
unix  3      [ ]         STREAM     CONNECTED     18177    /tmp/.ICE-unix/5586                             
unix  3      [ ]         STREAM     CONNECTED     18134                                                    
unix  3      [ ]         STREAM     CONNECTED     18133    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     18132                                                    
unix  3      [ ]         STREAM     CONNECTED     18127    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     18126                                                    
unix  3      [ ]         STREAM     CONNECTED     18119    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     18118                                                    
unix  2      [ ]         STREAM     CONNECTED     18102                                                    
unix  3      [ ]         STREAM     CONNECTED     18008    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     18007                                                    
unix  3      [ ]         STREAM     CONNECTED     18000    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     17999                                                    
unix  3      [ ]         STREAM     CONNECTED     17998    /tmp/.ICE-unix/5586                             
unix  3      [ ]         STREAM     CONNECTED     17997                                                    
unix  3      [ ]         STREAM     CONNECTED     17960    /tmp/.ICE-unix/5586                             
unix  3      [ ]         STREAM     CONNECTED     17959                                                    
unix  259    [ ]         STREAM     CONNECTED     17956    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     17955                                                    
unix  3      [ ]         STREAM     CONNECTED     17950    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     17949                                                    
unix  3      [ ]         STREAM     CONNECTED     17947    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     17946                                                    
unix  3      [ ]         STREAM     CONNECTED     17944    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     17943                                                    
unix  3      [ ]         STREAM     CONNECTED     17760    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     17759                                                    
unix  3      [ ]         STREAM     CONNECTED     17693    /tmp/.ICE-unix/5586                             
unix  3      [ ]         STREAM     CONNECTED     17692                                                    
unix  3      [ ]         STREAM     CONNECTED     17691    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     17688                                                    
unix  3      [ ]         STREAM     CONNECTED     17683    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     17682                                                    
unix  3      [ ]         STREAM     CONNECTED     17673    /home/derek/.kde/share/apps/nepomuk/socket      
unix  3      [ ]         STREAM     CONNECTED     17672                                                    
unix  3      [ ]         STREAM     CONNECTED     17671    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     17670                                                    
unix  3      [ ]         STREAM     CONNECTED     17666    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     17665                                                    
unix  3      [ ]         STREAM     CONNECTED     17586    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     17585                                                    
unix  3      [ ]         STREAM     CONNECTED     17566    /tmp/.ICE-unix/5586                             
unix  3      [ ]         STREAM     CONNECTED     17565                                                    
unix  3      [ ]         STREAM     CONNECTED     17556    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     17555                                                    
unix  3      [ ]         STREAM     CONNECTED     17535    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     17533                                                    
unix  3      [ ]         STREAM     CONNECTED     17510    /tmp/.ICE-unix/5586                             
unix  3      [ ]         STREAM     CONNECTED     17479                                                    
unix  3      [ ]         STREAM     CONNECTED     17478    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     17477                                                    
unix  3      [ ]         STREAM     CONNECTED     17470    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     17469                                                    
unix  3      [ ]         STREAM     CONNECTED     17387    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     17386                                                    
unix  3      [ ]         STREAM     CONNECTED     17380    /tmp/.ICE-unix/5586                             
unix  3      [ ]         STREAM     CONNECTED     17379                                                    
unix  3      [ ]         STREAM     CONNECTED     17372    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     17371                                                    
unix  3      [ ]         STREAM     CONNECTED     17367    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     17366                                                    
unix  3      [ ]         STREAM     CONNECTED     17362    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     17361                                                    
unix  3      [ ]         STREAM     CONNECTED     17356    /tmp/.ICE-unix/5586                             
unix  3      [ ]         STREAM     CONNECTED     17355                                                    
unix  3      [ ]         STREAM     CONNECTED     17354    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     17353                                                    
unix  3      [ ]         STREAM     CONNECTED     17346    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     17345                                                    
unix  3      [ ]         STREAM     CONNECTED     17344    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     17343                                                    
unix  3      [ ]         STREAM     CONNECTED     17333    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     17332                                                    
unix  3      [ ]         STREAM     CONNECTED     17321    /tmp/.ICE-unix/5586                             
unix  3      [ ]         STREAM     CONNECTED     17320                                                    
unix  3      [ ]         STREAM     CONNECTED     17255    /tmp/.ICE-unix/5586                             
unix  3      [ ]         STREAM     CONNECTED     17254                                                    
unix  3      [ ]         STREAM     CONNECTED     17253    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     17252                                                    
unix  3      [ ]         STREAM     CONNECTED     17251    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     17250                                                    
unix  3      [ ]         STREAM     CONNECTED     17235    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     17234                                                    
unix  3      [ ]         STREAM     CONNECTED     17229    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     17228                                                    
unix  3      [ ]         STREAM     CONNECTED     17221    /tmp/ksocket-derek/kdeinit4__0                  
unix  3      [ ]         STREAM     CONNECTED     17220                                                    
unix  3      [ ]         STREAM     CONNECTED     17196    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     17195                                                    
unix  3      [ ]         STREAM     CONNECTED     17184    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     17183                                                    
unix  3      [ ]         STREAM     CONNECTED     17177    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     17176                                                    
unix  3      [ ]         STREAM     CONNECTED     17172    @/tmp/dbus-0HH1HglOEV                           
unix  3      [ ]         STREAM     CONNECTED     17171                                                    
unix  3      [ ]         STREAM     CONNECTED     17165                                                    
unix  3      [ ]         STREAM     CONNECTED     17164                                                    
unix  3      [ ]         STREAM     CONNECTED     16810    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     16809                                                    
unix  3      [ ]         STREAM     CONNECTED     16808                                                    
unix  3      [ ]         STREAM     CONNECTED     16807                                                    
unix  4      [ ]         STREAM     CONNECTED     16792    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     16791                                                    
unix  3      [ ]         STREAM     CONNECTED     16680    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     16679                                                    
unix  2      [ ]         DGRAM                    16643                                                    
unix  3      [ ]         STREAM     CONNECTED     16459    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     16458                                                    
unix  3      [ ]         STREAM     CONNECTED     16452                                                    
unix  3      [ ]         STREAM     CONNECTED     16451                                                    
unix  2      [ ]         STREAM     CONNECTED     16437                                                    
unix  2      [ ]         DGRAM                    16411                                                    
unix  5      [ ]         STREAM     CONNECTED     16375    /tmp/.X11-unix/X0                               
unix  3      [ ]         STREAM     CONNECTED     16372                                                    
unix  3      [ ]         STREAM     CONNECTED     16371    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     16370                                                    
unix  3      [ ]         STREAM     CONNECTED     16369                                                    
unix  3      [ ]         STREAM     CONNECTED     16368                                                    
unix  3      [ ]         STREAM     CONNECTED     16367                                                    
unix  3      [ ]         STREAM     CONNECTED     16366                                                    
unix  3      [ ]         STREAM     CONNECTED     16135    /var/run/acpid.socket                           
unix  3      [ ]         STREAM     CONNECTED     16134                                                    
unix  3      [ ]         STREAM     CONNECTED     16069    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     16068                                                    
unix  2      [ ]         DGRAM                    16059                                                    
unix  3      [ ]         STREAM     CONNECTED     16058    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     16057                                                    
unix  3      [ ]         STREAM     CONNECTED     15958    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     15957                                                    
unix  2      [ ]         DGRAM                    15954                                                    
unix  3      [ ]         STREAM     CONNECTED     15870    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     15869                                                    
unix  2      [ ]         DGRAM                    15861                                                    
unix  3      [ ]         STREAM     CONNECTED     15676    @/var/run/hald/dbus-1dgAlKKhXg                  
unix  3      [ ]         STREAM     CONNECTED     15675                                                    
unix  3      [ ]         STREAM     CONNECTED     15672    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     15671                                                    
unix  3      [ ]         STREAM     CONNECTED     15547    @/var/run/hald/dbus-1dgAlKKhXg                  
unix  3      [ ]         STREAM     CONNECTED     15546                                                    
unix  3      [ ]         STREAM     CONNECTED     15545    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     15544                                                    
unix  3      [ ]         STREAM     CONNECTED     15509    @/var/run/hald/dbus-1dgAlKKhXg                  
unix  3      [ ]         STREAM     CONNECTED     15508                                                    
unix  3      [ ]         STREAM     CONNECTED     15507    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     15506                                                    
unix  3      [ ]         STREAM     CONNECTED     15471    @/var/run/hald/dbus-1dgAlKKhXg                  
unix  3      [ ]         STREAM     CONNECTED     15470                                                    
unix  3      [ ]         STREAM     CONNECTED     15469    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     15468                                                    
unix  3      [ ]         STREAM     CONNECTED     15446    @/var/run/hald/dbus-1dgAlKKhXg                  
unix  3      [ ]         STREAM     CONNECTED     15445                                                    
unix  3      [ ]         STREAM     CONNECTED     15444    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     15443                                                    
unix  3      [ ]         STREAM     CONNECTED     15386    /var/run/dbus/system_bus_socket                 
unix  3      [ ]         STREAM     CONNECTED     15385                                                    
unix  2      [ ]         DGRAM                    15384                                                    
unix  3      [ ]         STREAM     CONNECTED     15383    /var/run/acpid.socket                           
unix  3      [ ]         STREAM     CONNECTED     15382
unix  3      [ ]         STREAM     CONNECTED     15377    @/var/run/hald/dbus-1dgAlKKhXg
unix  3      [ ]         STREAM     CONNECTED     15374
unix  3      [ ]         STREAM     CONNECTED     15376    @/var/run/hald/dbus-1dgAlKKhXg
unix  3      [ ]         STREAM     CONNECTED     15364
unix  3      [ ]         STREAM     CONNECTED     15305    @/var/run/hald/dbus-1dgAlKKhXg
unix  3      [ ]         STREAM     CONNECTED     15304
unix  3      [ ]         STREAM     CONNECTED     15113    @/var/run/hald/dbus-yEWAJ6Z9uO
unix  3      [ ]         STREAM     CONNECTED     15112
unix  3      [ ]         STREAM     CONNECTED     15110    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15109
unix  3      [ ]         STREAM     CONNECTED     15088
unix  3      [ ]         STREAM     CONNECTED     15087
unix  3      [ ]         STREAM     CONNECTED     15073    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15072
unix  3      [ ]         STREAM     CONNECTED     14777    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14776
unix  3      [ ]         STREAM     CONNECTED     14771
unix  3      [ ]         STREAM     CONNECTED     14770
unix  2      [ ]         DGRAM                    14768
unix  3      [ ]         STREAM     CONNECTED     14729
unix  3      [ ]         STREAM     CONNECTED     14728
unix  2      [ ]         DGRAM                    14684

```

---

### Post by unused_bagels on 2009-01-16
Ok, so I switched to Ubuntu HH, and I still have the same problem, although all the ports are forwarded from my modem and my router to my static IP.
Is there a firewall I'm not aware of?  If so, do I have to punch a hole in it?

---

