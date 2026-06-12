---
title: "Too many open ports for ISP"
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by bogulo on 2010-04-06
Hello!
I really hope you can help me here, and thank you for your time. I am a total Ubuntu novice so bear with me :-)

A few months ago I installed Ubuntu 9.10 on my girlfriends laptop, on her request, as she didn´t like Windows any more. 
Since then the internet connection periodically slows down due to too many open ports/connections. Always when this happens I call our ISP and usually there are around 80-200(!) active connections to various IP´s.

She is not downloading torrents or anything.
She only uses Firefox and a few open tabs as people do.
Skype is open.
Wireless internet connection.

I´m thinking either Ubuntu is updating more or less constantly or the ports/connections aren´t closed "after use".

Thank you for your help!


bogulo

---

### Post by mbehamin on 2010-04-06
Hi
please insert "netstat -n" and "netstat -npl" in your ubuntu terminal and send it again in this thread ! 
and if you are connected to internet please install the "nmap" package and after installing try to insert "nmap localhost" and let us know what the problems. 
after that you can find the processes which sends the packet and we will find a way to kill them :) 
for checking you network traffic you can using bwm-ng package in the command line 

sorry i  have not ever worked with Graphic edition of linux . it may has an alternative graphical approach ! 

regards/

---

### Post by bogulo on 2010-04-06
Thank you very much for your time! This is what I get:

netstat -n
Verbunden means connected.

```
Aktive Internetverbindungen (ohne Server)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 192.168.1.112:44704     193.4.144.81:80         VERBUNDEN  
tcp        0      0 192.168.1.112:44705     193.4.144.81:80         VERBUNDEN  
tcp        0      0 192.168.1.112:34778     69.63.190.22:80         VERBUNDEN  
tcp        0      0 192.168.1.112:44706     193.4.144.81:80         VERBUNDEN  
tcp        0      0 192.168.1.112:51146     79.171.98.194:110       TIME_WAIT  
tcp        0      0 192.168.1.112:44707     193.4.144.81:80         VERBUNDEN  
tcp        1      0 192.168.1.112:48097     74.125.79.104:80        CLOSE_WAIT 
tcp        0      0 192.168.1.112:44703     193.4.144.81:80         VERBUNDEN  
tcp        0      0 192.168.1.112:60267     74.125.77.102:80        VERBUNDEN  
tcp        0      0 192.168.1.112:40269     69.63.176.165:80        VERBUNDEN  
Aktive Sockets in der UNIX-Domäne (ohne Server)
Proto RefCnt Flags       Type       State         I-Node   Pfad
unix  2      [ ]         DGRAM                    2931     @/org/kernel/udev/udevd
unix  2      [ ]         DGRAM                    4398     @/org/freedesktop/hal/udev_event
unix  15     [ ]         DGRAM                    4253     /dev/log
unix  3      [ ]         STREAM     VERBUNDEN     113370   @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     113369   
unix  3      [ ]         STREAM     VERBUNDEN     112902   
unix  3      [ ]         STREAM     VERBUNDEN     112901   
unix  3      [ ]         STREAM     VERBUNDEN     112899   @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     112898   
unix  3      [ ]         STREAM     VERBUNDEN     112891   /tmp/orbit-kristina/linc-16dc-0-14a55203dae24
unix  3      [ ]         STREAM     VERBUNDEN     112890   
unix  3      [ ]         STREAM     VERBUNDEN     112887   /tmp/orbit-kristina/linc-506-0-2946d54ca043
unix  3      [ ]         STREAM     VERBUNDEN     112886   
unix  3      [ ]         STREAM     VERBUNDEN     112882   @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     112881   
unix  3      [ ]         STREAM     VERBUNDEN     112880   @/tmp/.ICE-unix/1227
unix  3      [ ]         STREAM     VERBUNDEN     112879   
unix  3      [ ]         STREAM     VERBUNDEN     112877   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     112876   
unix  3      [ ]         STREAM     VERBUNDEN     112317   /tmp/orbit-kristina/linc-16bf-0-59388771975df
unix  3      [ ]         STREAM     VERBUNDEN     112316   
unix  3      [ ]         STREAM     VERBUNDEN     112313   /tmp/orbit-kristina/linc-506-0-2946d54ca043
unix  3      [ ]         STREAM     VERBUNDEN     112312   
unix  3      [ ]         STREAM     VERBUNDEN     112305   @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     112304   
unix  3      [ ]         STREAM     VERBUNDEN     112285   @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     112284   
unix  3      [ ]         STREAM     VERBUNDEN     11484    @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     11483    
unix  3      [ ]         STREAM     VERBUNDEN     11439    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     11438    
unix  3      [ ]         STREAM     VERBUNDEN     11433    /tmp/orbit-kristina/linc-7d7-0-2ac575f9d55b5
unix  3      [ ]         STREAM     VERBUNDEN     11432    
unix  3      [ ]         STREAM     VERBUNDEN     11429    /tmp/orbit-kristina/linc-506-0-2946d54ca043
unix  3      [ ]         STREAM     VERBUNDEN     11428    
unix  3      [ ]         STREAM     VERBUNDEN     11426    @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     11425    
unix  3      [ ]         STREAM     VERBUNDEN     11424    @/tmp/.ICE-unix/1227
unix  3      [ ]         STREAM     VERBUNDEN     11423    
unix  3      [ ]         STREAM     VERBUNDEN     11417    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     11416    
unix  3      [ ]         STREAM     VERBUNDEN     11275    /tmp/orbit-kristina/linc-7aa-0-77af360cc522d
unix  3      [ ]         STREAM     VERBUNDEN     11272    
unix  3      [ ]         STREAM     VERBUNDEN     11145    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     11144    
unix  3      [ ]         STREAM     VERBUNDEN     11143    @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     11142    
unix  3      [ ]         STREAM     VERBUNDEN     11120    /tmp/orbit-kristina/linc-644-0-6e1d30e18f16
unix  3      [ ]         STREAM     VERBUNDEN     11119    
unix  3      [ ]         STREAM     VERBUNDEN     11102    /tmp/orbit-kristina/linc-7aa-0-77af360cc522d
unix  3      [ ]         STREAM     VERBUNDEN     11101    
unix  3      [ ]         STREAM     VERBUNDEN     11100    /tmp/orbit-kristina/linc-597-0-60810c2b8c5b7
unix  3      [ ]         STREAM     VERBUNDEN     11099    
unix  3      [ ]         STREAM     VERBUNDEN     11087    /tmp/orbit-kristina/linc-7aa-0-77af360cc522d
unix  3      [ ]         STREAM     VERBUNDEN     11086    
unix  3      [ ]         STREAM     VERBUNDEN     11083    /tmp/orbit-kristina/linc-506-0-2946d54ca043
unix  3      [ ]         STREAM     VERBUNDEN     11082    
unix  3      [ ]         STREAM     VERBUNDEN     11080    @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     11079    
unix  3      [ ]         STREAM     VERBUNDEN     11078    @/tmp/.ICE-unix/1227
unix  3      [ ]         STREAM     VERBUNDEN     11077    
unix  3      [ ]         STREAM     VERBUNDEN     11073    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     11072    
unix  2      [ ]         DGRAM                    10762    
unix  3      [ ]         STREAM     VERBUNDEN     10463    @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     10462    
unix  3      [ ]         STREAM     VERBUNDEN     10455    @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     10454    
unix  3      [ ]         STREAM     VERBUNDEN     10453    @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     10452    
unix  3      [ ]         STREAM     VERBUNDEN     9918     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     9917     
unix  3      [ ]         STREAM     VERBUNDEN     9079     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     9078     
unix  3      [ ]         STREAM     VERBUNDEN     9077     /tmp/orbit-kristina/linc-5a9-0-3d77dd6dacee9
unix  3      [ ]         STREAM     VERBUNDEN     9075     
unix  3      [ ]         STREAM     VERBUNDEN     9074     /tmp/orbit-kristina/linc-640-0-5db8fb41d3ce7
unix  3      [ ]         STREAM     VERBUNDEN     9073     
unix  3      [ ]         STREAM     VERBUNDEN     9070     /tmp/orbit-kristina/linc-644-0-6e1d30e18f16
unix  3      [ ]         STREAM     VERBUNDEN     9069     
unix  3      [ ]         STREAM     VERBUNDEN     9068     /tmp/orbit-kristina/linc-597-0-60810c2b8c5b7
unix  3      [ ]         STREAM     VERBUNDEN     9067     
unix  3      [ ]         STREAM     VERBUNDEN     9065     /tmp/orbit-kristina/linc-644-0-6e1d30e18f16
unix  3      [ ]         STREAM     VERBUNDEN     9064     
unix  3      [ ]         STREAM     VERBUNDEN     9061     /tmp/orbit-kristina/linc-506-0-2946d54ca043
unix  3      [ ]         STREAM     VERBUNDEN     9060     
unix  3      [ ]         STREAM     VERBUNDEN     9058     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     9057     
unix  3      [ ]         STREAM     VERBUNDEN     9056     @/tmp/.ICE-unix/1227
unix  3      [ ]         STREAM     VERBUNDEN     9055     
unix  3      [ ]         STREAM     VERBUNDEN     9047     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     9046     
unix  3      [ ]         STREAM     VERBUNDEN     9043     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     9042     
unix  3      [ ]         STREAM     VERBUNDEN     9041     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     9040     
unix  3      [ ]         STREAM     VERBUNDEN     9038     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     9037     
unix  3      [ ]         STREAM     VERBUNDEN     9036     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     9035     
unix  3      [ ]         STREAM     VERBUNDEN     9032     /tmp/orbit-kristina/linc-640-0-5db8fb41d3ce7
unix  3      [ ]         STREAM     VERBUNDEN     9031     
unix  3      [ ]         STREAM     VERBUNDEN     9030     /tmp/orbit-kristina/linc-506-0-2946d54ca043
unix  3      [ ]         STREAM     VERBUNDEN     9029     
unix  3      [ ]         STREAM     VERBUNDEN     8987     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     8986     
unix  3      [ ]         STREAM     VERBUNDEN     8985     /tmp/orbit-kristina/linc-640-0-5db8fb41d3ce7
unix  3      [ ]         STREAM     VERBUNDEN     8984     
unix  3      [ ]         STREAM     VERBUNDEN     8983     /tmp/orbit-kristina/linc-597-0-60810c2b8c5b7
unix  3      [ ]         STREAM     VERBUNDEN     8980     
unix  3      [ ]         STREAM     VERBUNDEN     8934     /tmp/orbit-kristina/linc-5a9-0-3d77dd6dacee9
unix  3      [ ]         STREAM     VERBUNDEN     8933     
unix  3      [ ]         STREAM     VERBUNDEN     8932     /tmp/orbit-kristina/linc-597-0-60810c2b8c5b7
unix  3      [ ]         STREAM     VERBUNDEN     8931     
unix  3      [ ]         STREAM     VERBUNDEN     8928     /tmp/orbit-kristina/linc-5a9-0-3d77dd6dacee9
unix  3      [ ]         STREAM     VERBUNDEN     8927     
unix  3      [ ]         STREAM     VERBUNDEN     8924     /tmp/orbit-kristina/linc-506-0-2946d54ca043
unix  3      [ ]         STREAM     VERBUNDEN     8923     
unix  3      [ ]         STREAM     VERBUNDEN     8921     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     8920     
unix  3      [ ]         STREAM     VERBUNDEN     8919     @/tmp/.ICE-unix/1227
unix  3      [ ]         STREAM     VERBUNDEN     8918     
unix  3      [ ]         STREAM     VERBUNDEN     8914     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     8913     
unix  3      [ ]         STREAM     VERBUNDEN     8409     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     8407     
unix  3      [ ]         STREAM     VERBUNDEN     8290     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     8289     
unix  3      [ ]         STREAM     VERBUNDEN     8232     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     8231     
unix  3      [ ]         STREAM     VERBUNDEN     8230     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     8229     
unix  3      [ ]         STREAM     VERBUNDEN     8228     /tmp/orbit-kristina/linc-60f-0-72181f0f85275
unix  3      [ ]         STREAM     VERBUNDEN     8227     
unix  3      [ ]         STREAM     VERBUNDEN     8224     /tmp/orbit-kristina/linc-506-0-2946d54ca043
unix  3      [ ]         STREAM     VERBUNDEN     8223     
unix  3      [ ]         STREAM     VERBUNDEN     8211     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     8205     
unix  3      [ ]         STREAM     VERBUNDEN     8210     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     8200     
unix  3      [ ]         STREAM     VERBUNDEN     8209     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     8194     
unix  3      [ ]         STREAM     VERBUNDEN     8188     @/tmp/.ICE-unix/1227
unix  3      [ ]         STREAM     VERBUNDEN     8187     
unix  3      [ ]         STREAM     VERBUNDEN     8189     /tmp/orbit-kristina/linc-592-0-223de2e34e9d7
unix  3      [ ]         STREAM     VERBUNDEN     8186     
unix  3      [ ]         STREAM     VERBUNDEN     8181     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     8180     
unix  2      [ ]         DGRAM                    8143     
unix  3      [ ]         STREAM     VERBUNDEN     8142     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     8141     
unix  3      [ ]         STREAM     VERBUNDEN     8131     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     8130     
unix  3      [ ]         STREAM     VERBUNDEN     8126     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     8125     
unix  3      [ ]         STREAM     VERBUNDEN     8118     @/tmp/.ICE-unix/1227
unix  3      [ ]         STREAM     VERBUNDEN     8117     
unix  3      [ ]         STREAM     VERBUNDEN     8120     /tmp/orbit-kristina/linc-592-0-223de2e34e9d7
unix  3      [ ]         STREAM     VERBUNDEN     8116     
unix  3      [ ]         STREAM     VERBUNDEN     8115     /tmp/orbit-kristina/linc-5fc-0-22948029dd48f
unix  3      [ ]         STREAM     VERBUNDEN     8114     
unix  3      [ ]         STREAM     VERBUNDEN     8119     /tmp/orbit-kristina/linc-5f8-0-57dd9c26dd054
unix  3      [ ]         STREAM     VERBUNDEN     8113     
unix  3      [ ]         STREAM     VERBUNDEN     8100     @/dbus-vfs-daemon/socket-Ci2YzE8v
unix  3      [ ]         STREAM     VERBUNDEN     8099     
unix  3      [ ]         STREAM     VERBUNDEN     8101     @/dbus-vfs-daemon/socket-TDxsLKHh
unix  3      [ ]         STREAM     VERBUNDEN     8098     
unix  3      [ ]         STREAM     VERBUNDEN     8090     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     8089     
unix  3      [ ]         STREAM     VERBUNDEN     8064     /tmp/orbit-kristina/linc-5fc-0-22948029dd48f
unix  3      [ ]         STREAM     VERBUNDEN     8063     
unix  3      [ ]         STREAM     VERBUNDEN     8062     /tmp/orbit-kristina/linc-506-0-2946d54ca043
unix  3      [ ]         STREAM     VERBUNDEN     8061     
unix  3      [ ]         STREAM     VERBUNDEN     8059     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     8058     
unix  3      [ ]         STREAM     VERBUNDEN     8057     /tmp/orbit-kristina/linc-5f8-0-57dd9c26dd054
unix  3      [ ]         STREAM     VERBUNDEN     8056     
unix  3      [ ]         STREAM     VERBUNDEN     8055     /tmp/orbit-kristina/linc-506-0-2946d54ca043
unix  3      [ ]         STREAM     VERBUNDEN     8054     
unix  3      [ ]         STREAM     VERBUNDEN     8051     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     8050     
unix  3      [ ]         STREAM     VERBUNDEN     8053     /tmp/orbit-kristina/linc-5fc-0-22948029dd48f
unix  3      [ ]         STREAM     VERBUNDEN     8049     
unix  3      [ ]         STREAM     VERBUNDEN     8048     /tmp/orbit-kristina/linc-597-0-60810c2b8c5b7
unix  3      [ ]         STREAM     VERBUNDEN     8045     
unix  3      [ ]         STREAM     VERBUNDEN     8044     /tmp/orbit-kristina/linc-5f8-0-57dd9c26dd054
unix  3      [ ]         STREAM     VERBUNDEN     8043     
unix  3      [ ]         STREAM     VERBUNDEN     8036     /tmp/orbit-kristina/linc-597-0-60810c2b8c5b7
unix  3      [ ]         STREAM     VERBUNDEN     8035     
unix  3      [ ]         STREAM     VERBUNDEN     8031     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     8030     
unix  3      [ ]         STREAM     VERBUNDEN     8026     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     8025     
unix  3      [ ]         STREAM     VERBUNDEN     7863     /tmp/orbit-kristina/linc-5d4-0-12e5af945d328
unix  3      [ ]         STREAM     VERBUNDEN     7862     
unix  3      [ ]         STREAM     VERBUNDEN     7859     /tmp/orbit-kristina/linc-506-0-2946d54ca043
unix  3      [ ]         STREAM     VERBUNDEN     7858     
unix  3      [ ]         STREAM     VERBUNDEN     7850     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7849     
unix  3      [ ]         STREAM     VERBUNDEN     7835     @/dbus-vfs-daemon/socket-0PBJGcxm
unix  3      [ ]         STREAM     VERBUNDEN     7832     
unix  3      [ ]         STREAM     VERBUNDEN     7836     @/dbus-vfs-daemon/socket-2yGylaRY
unix  3      [ ]         STREAM     VERBUNDEN     7831     
unix  3      [ ]         STREAM     VERBUNDEN     7830     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     7829     
unix  3      [ ]         STREAM     VERBUNDEN     7819     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7818     
unix  3      [ ]         STREAM     VERBUNDEN     7795     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7794     
unix  3      [ ]         STREAM     VERBUNDEN     7796     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     7790     
unix  3      [ ]         STREAM     VERBUNDEN     7745     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7744     
unix  3      [ ]         STREAM     VERBUNDEN     7739     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7738     
unix  3      [ ]         STREAM     VERBUNDEN     7710     /tmp/orbit-kristina/linc-591-0-6bf038251f456
unix  3      [ ]         STREAM     VERBUNDEN     7709     
unix  3      [ ]         STREAM     VERBUNDEN     7706     /tmp/orbit-kristina/linc-506-0-2946d54ca043
unix  3      [ ]         STREAM     VERBUNDEN     7705     
unix  3      [ ]         STREAM     VERBUNDEN     7691     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7690     
unix  3      [ ]         STREAM     VERBUNDEN     7682     /tmp/orbit-kristina/linc-592-0-223de2e34e9d7
unix  3      [ ]         STREAM     VERBUNDEN     7681     
unix  3      [ ]         STREAM     VERBUNDEN     7680     /tmp/orbit-kristina/linc-5bd-0-8c803bf62f13
unix  3      [ ]         STREAM     VERBUNDEN     7679     
unix  3      [ ]         STREAM     VERBUNDEN     7678     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7677     
unix  3      [ ]         STREAM     VERBUNDEN     7674     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7672     
unix  3      [ ]         STREAM     VERBUNDEN     7666     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7665     
unix  3      [ ]         STREAM     VERBUNDEN     7663     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7662     
unix  3      [ ]         STREAM     VERBUNDEN     7646     @/dbus-vfs-daemon/socket-926v3yku
unix  3      [ ]         STREAM     VERBUNDEN     7645     
unix  3      [ ]         STREAM     VERBUNDEN     7647     @/dbus-vfs-daemon/socket-TOxDOgWM
unix  3      [ ]         STREAM     VERBUNDEN     7644     
unix  3      [ ]         STREAM     VERBUNDEN     7636     @/dbus-vfs-daemon/socket-WWqXHyFb
unix  3      [ ]         STREAM     VERBUNDEN     7635     
unix  3      [ ]         STREAM     VERBUNDEN     7637     @/dbus-vfs-daemon/socket-njRIiJx3
unix  3      [ ]         STREAM     VERBUNDEN     7634     
unix  3      [ ]         STREAM     VERBUNDEN     7628     @/dbus-vfs-daemon/socket-r7dMecWP
unix  3      [ ]         STREAM     VERBUNDEN     7627     
unix  3      [ ]         STREAM     VERBUNDEN     7629     @/dbus-vfs-daemon/socket-QQuWK2p2
unix  3      [ ]         STREAM     VERBUNDEN     7626     
unix  3      [ ]         STREAM     VERBUNDEN     7620     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7619     
unix  3      [ ]         STREAM     VERBUNDEN     7617     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7616     
unix  3      [ ]         STREAM     VERBUNDEN     7615     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7614     
unix  3      [ ]         STREAM     VERBUNDEN     7612     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7611     
unix  3      [ ]         STREAM     VERBUNDEN     7592     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7591     
unix  3      [ ]         STREAM     VERBUNDEN     7590     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7589     
unix  3      [ ]         STREAM     VERBUNDEN     7588     /tmp/orbit-kristina/linc-5bd-0-8c803bf62f13
unix  3      [ ]         STREAM     VERBUNDEN     7587     
unix  3      [ ]         STREAM     VERBUNDEN     7585     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     7584     
unix  3      [ ]         STREAM     VERBUNDEN     7586     /tmp/orbit-kristina/linc-506-0-2946d54ca043
unix  3      [ ]         STREAM     VERBUNDEN     7583     
unix  3      [ ]         STREAM     VERBUNDEN     7581     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7580     
unix  3      [ ]         STREAM     VERBUNDEN     7579     /tmp/orbit-kristina/linc-5bd-0-8c803bf62f13
unix  3      [ ]         STREAM     VERBUNDEN     7576     
unix  3      [ ]         STREAM     VERBUNDEN     7575     /tmp/orbit-kristina/linc-597-0-60810c2b8c5b7
unix  3      [ ]         STREAM     VERBUNDEN     7572     
unix  3      [ ]         STREAM     VERBUNDEN     7568     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     7567     
unix  3      [ ]         STREAM     VERBUNDEN     7564     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     7563     
unix  3      [ ]         STREAM     VERBUNDEN     7558     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7554     
unix  3      [ ]         STREAM     VERBUNDEN     7557     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7553     
unix  3      [ ]         STREAM     VERBUNDEN     7507     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7506     
unix  3      [ ]         STREAM     VERBUNDEN     7502     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     7501     
unix  3      [ ]         STREAM     VERBUNDEN     7499     /tmp/orbit-kristina/linc-5ae-0-332fbfcde341
unix  3      [ ]         STREAM     VERBUNDEN     7498     
unix  3      [ ]         STREAM     VERBUNDEN     7495     /tmp/orbit-kristina/linc-506-0-2946d54ca043
unix  3      [ ]         STREAM     VERBUNDEN     7494     
unix  3      [ ]         STREAM     VERBUNDEN     7450     /tmp/orbit-kristina/linc-5a8-0-31678c91142b
unix  3      [ ]         STREAM     VERBUNDEN     7449     
unix  3      [ ]         STREAM     VERBUNDEN     7446     /tmp/orbit-kristina/linc-506-0-2946d54ca043
unix  3      [ ]         STREAM     VERBUNDEN     7445     
unix  3      [ ]         STREAM     VERBUNDEN     7439     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7438     
unix  3      [ ]         STREAM     VERBUNDEN     7441     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     7426     
unix  3      [ ]         STREAM     VERBUNDEN     7423     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     7421     
unix  3      [ ]         STREAM     VERBUNDEN     7419     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7418     
unix  3      [ ]         STREAM     VERBUNDEN     7416     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     7415     
unix  3      [ ]         STREAM     VERBUNDEN     7411     /tmp/orbit-kristina/linc-5a4-0-7381513fd78d1
unix  3      [ ]         STREAM     VERBUNDEN     7410     
unix  3      [ ]         STREAM     VERBUNDEN     7407     /tmp/orbit-kristina/linc-506-0-2946d54ca043
unix  3      [ ]         STREAM     VERBUNDEN     7406     
unix  3      [ ]         STREAM     VERBUNDEN     7401     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     7397     
unix  3      [ ]         STREAM     VERBUNDEN     7381     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7380     
unix  3      [ ]         STREAM     VERBUNDEN     7388     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     7379     
unix  3      [ ]         STREAM     VERBUNDEN     7378     /tmp/orbit-kristina/linc-5a0-0-54f09c12c845a
unix  3      [ ]         STREAM     VERBUNDEN     7377     
unix  3      [ ]         STREAM     VERBUNDEN     7373     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7372     
unix  3      [ ]         STREAM     VERBUNDEN     7366     /tmp/orbit-kristina/linc-506-0-2946d54ca043
unix  3      [ ]         STREAM     VERBUNDEN     7362     
unix  3      [ ]         STREAM     VERBUNDEN     7358     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7357     
unix  3      [ ]         STREAM     VERBUNDEN     7356     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     7355     
unix  3      [ ]         STREAM     VERBUNDEN     7350     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7349     
unix  3      [ ]         STREAM     VERBUNDEN     7344     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     7343     
unix  3      [ ]         STREAM     VERBUNDEN     7336     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7335     
unix  3      [ ]         STREAM     VERBUNDEN     7330     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     7329     
unix  3      [ ]         STREAM     VERBUNDEN     7326     /tmp/orbit-kristina/linc-592-0-223de2e34e9d7
unix  3      [ ]         STREAM     VERBUNDEN     7325     
unix  3      [ ]         STREAM     VERBUNDEN     7324     /tmp/orbit-kristina/linc-597-0-60810c2b8c5b7
unix  3      [ ]         STREAM     VERBUNDEN     7323     
unix  3      [ ]         STREAM     VERBUNDEN     7320     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7319     
unix  3      [ ]         STREAM     VERBUNDEN     7311     /tmp/orbit-kristina/linc-595-0-4df1e7aa99864
unix  3      [ ]         STREAM     VERBUNDEN     7310     
unix  3      [ ]         STREAM     VERBUNDEN     7307     /tmp/orbit-kristina/linc-506-0-2946d54ca043
unix  3      [ ]         STREAM     VERBUNDEN     7306     
unix  3      [ ]         STREAM     VERBUNDEN     7300     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     7299     
unix  3      [ ]         STREAM     VERBUNDEN     7296     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     7295     
unix  3      [ ]         STREAM     VERBUNDEN     7294     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     7290     
unix  3      [ ]         STREAM     VERBUNDEN     7293     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     7287     
unix  3      [ ]         STREAM     VERBUNDEN     7255     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     7254     
unix  3      [ ]         STREAM     VERBUNDEN     7249     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     7248     
unix  3      [ ]         STREAM     VERBUNDEN     7198     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     7197     
unix  3      [ ]         STREAM     VERBUNDEN     7108     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     7107     
unix  3      [ ]         STREAM     VERBUNDEN     6722     @/tmp/.ICE-unix/1227
unix  3      [ ]         STREAM     VERBUNDEN     6721     
unix  3      [ ]         STREAM     VERBUNDEN     6719     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     6718     
unix  3      [ ]         STREAM     VERBUNDEN     6645     @/tmp/.ICE-unix/1227
unix  3      [ ]         STREAM     VERBUNDEN     6644     
unix  3      [ ]         STREAM     VERBUNDEN     6621     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     6620     
unix  3      [ ]         STREAM     VERBUNDEN     6617     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     6616     
unix  3      [ ]         STREAM     VERBUNDEN     6615     /tmp/orbit-kristina/linc-592-0-223de2e34e9d7
unix  3      [ ]         STREAM     VERBUNDEN     6614     
unix  3      [ ]         STREAM     VERBUNDEN     6611     /tmp/orbit-kristina/linc-506-0-2946d54ca043
unix  3      [ ]         STREAM     VERBUNDEN     6610     
unix  3      [ ]         STREAM     VERBUNDEN     6608     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     6607     
unix  3      [ ]         STREAM     VERBUNDEN     6603     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     6602     
unix  3      [ ]         STREAM     VERBUNDEN     6599     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     6598     
unix  3      [ ]         STREAM     VERBUNDEN     6568     @/tmp/.ICE-unix/1227
unix  3      [ ]         STREAM     VERBUNDEN     6567     
unix  3      [ ]         STREAM     VERBUNDEN     6314     /tmp/orbit-kristina/linc-54c-0-7c6f7c8eb247c
unix  3      [ ]         STREAM     VERBUNDEN     6313     
unix  3      [ ]         STREAM     VERBUNDEN     6310     /tmp/orbit-kristina/linc-506-0-2946d54ca043
unix  3      [ ]         STREAM     VERBUNDEN     6309     
unix  3      [ ]         STREAM     VERBUNDEN     6304     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     6303     
unix  3      [ ]         STREAM     VERBUNDEN     6301     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     6300     
unix  3      [ ]         STREAM     VERBUNDEN     6293     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     6292     
unix  2      [ ]         DGRAM                    6189     
unix  3      [ ]         STREAM     VERBUNDEN     6188     /tmp/orbit-kristina/linc-52c-0-cc814aec60ec
unix  3      [ ]         STREAM     VERBUNDEN     6187     
unix  3      [ ]         STREAM     VERBUNDEN     6184     /tmp/orbit-kristina/linc-506-0-2946d54ca043
unix  3      [ ]         STREAM     VERBUNDEN     6183     
unix  3      [ ]         STREAM     VERBUNDEN     6180     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     6179     
unix  3      [ ]         STREAM     VERBUNDEN     6177     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     6176     
unix  3      [ ]         STREAM     VERBUNDEN     6167     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     6166     
unix  3      [ ]         STREAM     VERBUNDEN     6162     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     6161     
unix  3      [ ]         STREAM     VERBUNDEN     6123     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     6121     
unix  3      [ ]         STREAM     VERBUNDEN     6115     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     6114     
unix  3      [ ]         STREAM     VERBUNDEN     6112     /tmp/orbit-kristina/linc-52b-0-12d827de4cb52
unix  3      [ ]         STREAM     VERBUNDEN     6111     
unix  3      [ ]         STREAM     VERBUNDEN     6108     /tmp/orbit-kristina/linc-506-0-2946d54ca043
unix  3      [ ]         STREAM     VERBUNDEN     6107     
unix  3      [ ]         STREAM     VERBUNDEN     6100     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     6099     
unix  3      [ ]         STREAM     VERBUNDEN     6093     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     6092     
unix  3      [ ]         STREAM     VERBUNDEN     6086     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     6085     
unix  3      [ ]         STREAM     VERBUNDEN     5984     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     5983     
unix  3      [ ]         STREAM     VERBUNDEN     5934     /tmp/orbit-kristina/linc-4cb-0-3a7bce6c100e8
unix  3      [ ]         STREAM     VERBUNDEN     5933     
unix  3      [ ]         STREAM     VERBUNDEN     5930     /tmp/orbit-kristina/linc-506-0-2946d54ca043
unix  3      [ ]         STREAM     VERBUNDEN     5929     
unix  3      [ ]         STREAM     VERBUNDEN     5922     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     5921     
unix  3      [ ]         STREAM     VERBUNDEN     5669     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     5667     
unix  3      [ ]         STREAM     VERBUNDEN     5632     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     5631     
unix  3      [ ]         STREAM     VERBUNDEN     5628     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     5626     
unix  3      [ ]         STREAM     VERBUNDEN     5618     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     5617     
unix  3      [ ]         STREAM     VERBUNDEN     5589     @/tmp/dbus-vUsPIetHFg
unix  3      [ ]         STREAM     VERBUNDEN     5588     
unix  3      [ ]         STREAM     VERBUNDEN     5586     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     5585     
unix  3      [ ]         STREAM     VERBUNDEN     5576     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     5575     
unix  3      [ ]         STREAM     VERBUNDEN     5568     
unix  3      [ ]         STREAM     VERBUNDEN     5567     
unix  3      [ ]         STREAM     VERBUNDEN     5556     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     5555     
unix  2      [ ]         DGRAM                    5466     
unix  3      [ ]         STREAM     VERBUNDEN     5355     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     5354     
unix  2      [ ]         DGRAM                    5353     
unix  3      [ ]         STREAM     VERBUNDEN     5344     @/tmp/gdm-session-GTdapcyk
unix  3      [ ]         STREAM     VERBUNDEN     5342     
unix  3      [ ]         STREAM     VERBUNDEN     5306     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     VERBUNDEN     5305     
unix  3      [ ]         STREAM     VERBUNDEN     5303     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     5302     
unix  3      [ ]         STREAM     VERBUNDEN     5273     @/var/run/hald/dbus-U6RzUNBu5H
unix  3      [ ]         STREAM     VERBUNDEN     5272     
unix  3      [ ]         STREAM     VERBUNDEN     5270     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     5269     
unix  3      [ ]         STREAM     VERBUNDEN     5198     @/var/run/hald/dbus-U6RzUNBu5H
unix  3      [ ]         STREAM     VERBUNDEN     5195     
unix  3      [ ]         STREAM     VERBUNDEN     5179     /var/run/acpid.socket
unix  3      [ ]         STREAM     VERBUNDEN     5178     
unix  3      [ ]         STREAM     VERBUNDEN     5173     @/var/run/hald/dbus-U6RzUNBu5H
unix  3      [ ]         STREAM     VERBUNDEN     5172     
unix  2      [ ]         DGRAM                    5129     
unix  3      [ ]         STREAM     VERBUNDEN     5139     @/var/run/hald/dbus-U6RzUNBu5H
unix  3      [ ]         STREAM     VERBUNDEN     5063     
unix  3      [ ]         STREAM     VERBUNDEN     5136     @/var/run/hald/dbus-U6RzUNBu5H
unix  3      [ ]         STREAM     VERBUNDEN     5008     
unix  3      [ ]         STREAM     VERBUNDEN     5135     @/var/run/hald/dbus-U6RzUNBu5H
unix  3      [ ]         STREAM     VERBUNDEN     4985     
unix  3      [ ]         STREAM     VERBUNDEN     4898     
unix  3      [ ]         STREAM     VERBUNDEN     4897     
unix  3      [ ]         STREAM     VERBUNDEN     4862     /var/run/acpid.socket
unix  3      [ ]         STREAM     VERBUNDEN     4861     
unix  3      [ ]         STREAM     VERBUNDEN     4813     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     4796     
unix  2      [ ]         DGRAM                    4795     
unix  2      [ ]         DGRAM                    4682     
unix  2      [ ]         DGRAM                    4659     
unix  3      [ ]         STREAM     VERBUNDEN     4592     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     4591     
unix  2      [ ]         DGRAM                    4590     
unix  3      [ ]         STREAM     VERBUNDEN     4542     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     4541     
unix  3      [ ]         STREAM     VERBUNDEN     4393     @/var/run/hald/dbus-OlGPTAl75r
unix  3      [ ]         STREAM     VERBUNDEN     4392     
unix  2      [ ]         DGRAM                    4370     
unix  3      [ ]         STREAM     VERBUNDEN     4360     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     4357     
unix  3      [ ]         STREAM     VERBUNDEN     4359     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     4353     
unix  3      [ ]         STREAM     VERBUNDEN     4345     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     4344     
unix  3      [ ]         STREAM     VERBUNDEN     4341     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     4340     
unix  2      [ ]         DGRAM                    4337     
unix  3      [ ]         STREAM     VERBUNDEN     4334     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     4333     
unix  3      [ ]         STREAM     VERBUNDEN     4328     
unix  3      [ ]         STREAM     VERBUNDEN     4327     
unix  2      [ ]         DGRAM                    4325     
unix  3      [ ]         STREAM     VERBUNDEN     4306     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     4300     
unix  3      [ ]         STREAM     VERBUNDEN     4287     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     4286     
unix  3      [ ]         STREAM     VERBUNDEN     4269     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     VERBUNDEN     4268     
unix  3      [ ]         STREAM     VERBUNDEN     4267     
unix  3      [ ]         STREAM     VERBUNDEN     4266     
unix  3      [ ]         DGRAM                    2963     
unix  3      [ ]         DGRAM                    2962     
unix  3      [ ]         STREAM     VERBUNDEN     2929     @/com/ubuntu/upstart
unix  3      [ ]         STREAM     VERBUNDEN     2925     

```----
netstat -npl
It says I have to be in "root" to see all processes. How do I do that?

```
Aktive Internetverbindungen (Nur Server)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:587           0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:631             0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      -               
tcp6       0      0 :::139                  :::*                    LISTEN      -               
tcp6       0      0 :::631                  :::*                    LISTEN      -               
tcp6       0      0 :::445                  :::*                    LISTEN      -               
udp        0      0 0.0.0.0:49058           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -               
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -               
udp        0      0 0.0.0.0:631             0.0.0.0:*                           -               
udp        0      0 192.168.1.112:137       0.0.0.0:*                           -               
udp        0      0 0.0.0.0:137             0.0.0.0:*                           -               
udp        0      0 192.168.1.112:138       0.0.0.0:*                           -               
udp        0      0 0.0.0.0:138             0.0.0.0:*                           -               
Aktive Sockets in der UNIX-Domäne (Nur Server)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Pfad
unix  2      [ ACC ]     STREAM     HÖRT         4631     -                   /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     HÖRT         4893     -                   /tmp/.winbindd/pipe
unix  2      [ ACC ]     STREAM     HÖRT         5553     -                   /tmp/ssh-llBndJ1227/agent.1227
unix  2      [ ACC ]     STREAM     HÖRT         5607     1227/gnome-session  /tmp/.ICE-unix/1227
unix  2      [ ACC ]     STREAM     HÖRT         5665     1286/gconfd-2       /tmp/orbit-kristina/linc-506-0-2946d54ca043
unix  2      [ ACC ]     STREAM     HÖRT         5931     1227/gnome-session  /tmp/orbit-kristina/linc-4cb-0-3a7bce6c100e8
unix  2      [ ACC ]     STREAM     HÖRT         5980     1317/gnome-keyring- /tmp/keyring-xZSQ4o/socket
unix  2      [ ACC ]     STREAM     HÖRT         5990     1317/gnome-keyring- /tmp/orbit-kristina/linc-522-0-6e332f6637369
unix  2      [ ACC ]     STREAM     HÖRT         5994     1317/gnome-keyring- /tmp/keyring-xZSQ4o/socket.ssh
unix  2      [ ACC ]     STREAM     HÖRT         5996     1317/gnome-keyring- /tmp/keyring-xZSQ4o/socket.pkcs11
unix  2      [ ACC ]     STREAM     HÖRT         6109     1323/gnome-settings /tmp/orbit-kristina/linc-52b-0-12d827de4cb52
unix  2      [ ACC ]     STREAM     HÖRT         6185     1324/seahorse-daemo /tmp/orbit-kristina/linc-52c-0-cc814aec60ec
unix  2      [ ACC ]     STREAM     HÖRT         6311     1356/notify-osd     /tmp/orbit-kristina/linc-54c-0-7c6f7c8eb247c
unix  2      [ ACC ]     STREAM     HÖRT         6612     1426/gnome-panel    /tmp/orbit-kristina/linc-592-0-223de2e34e9d7
unix  2      [ ACC ]     STREAM     HÖRT         7291     1431/bonobo-activat /tmp/orbit-kristina/linc-597-0-60810c2b8c5b7
unix  2      [ ACC ]     STREAM     HÖRT         7308     1429/nautilus       /tmp/orbit-kristina/linc-595-0-4df1e7aa99864
unix  2      [ ACC ]     STREAM     HÖRT         7496     1454/bluetooth-appl /tmp/orbit-kristina/linc-5ae-0-332fbfcde341
unix  2      [ ACC ]     STREAM     HÖRT         7375     1464/gnome-screensa /tmp/orbit-kristina/linc-5a0-0-54f09c12c845a
unix  2      [ ACC ]     STREAM     HÖRT         7408     1444/update-notifie /tmp/orbit-kristina/linc-5a4-0-7381513fd78d1
unix  2      [ ACC ]     STREAM     HÖRT         7447     1448/nm-applet      /tmp/orbit-kristina/linc-5a8-0-31678c91142b
unix  2      [ ACC ]     STREAM     HÖRT         7573     1469/trashapplet    /tmp/orbit-kristina/linc-5bd-0-8c803bf62f13
unix  2      [ ACC ]     STREAM     HÖRT         7707     1425/compiz.real    /tmp/orbit-kristina/linc-591-0-6bf038251f456
unix  2      [ ACC ]     STREAM     HÖRT         7860     1492/gtk-window-dec /tmp/orbit-kristina/linc-5d4-0-12e5af945d328
unix  2      [ ACC ]     STREAM     HÖRT         4895     -                   /var/run/samba/winbindd_privileged/pipe
unix  2      [ ACC ]     STREAM     HÖRT         8041     1528/indicator-appl /tmp/orbit-kristina/linc-5f8-0-57dd9c26dd054
unix  2      [ ACC ]     STREAM     HÖRT         8046     1532/indicator-appl /tmp/orbit-kristina/linc-5fc-0-22948029dd48f
unix  2      [ ACC ]     STREAM     HÖRT         8225     1551/indicator-sess /tmp/orbit-kristina/linc-60f-0-72181f0f85275
unix  2      [ ACC ]     STREAM     HÖRT         8925     1449/evolution-alar /tmp/orbit-kristina/linc-5a9-0-3d77dd6dacee9
unix  2      [ ACC ]     STREAM     HÖRT         8981     1600/evolution-data /tmp/orbit-kristina/linc-640-0-5db8fb41d3ce7
unix  2      [ ACC ]     STREAM     HÖRT         5566     1270/dbus-daemon    @/tmp/dbus-vUsPIetHFg
unix  2      [ ACC ]     STREAM     HÖRT         9062     1604/evolution-exch /tmp/orbit-kristina/linc-644-0-6e1d30e18f16
unix  2      [ ACC ]     STREAM     HÖRT         11084    1962/evolution      /tmp/orbit-kristina/linc-7aa-0-77af360cc522d
unix  2      [ ACC ]     STREAM     HÖRT         11430    2007/firefox        /tmp/orbit-kristina/linc-7d7-0-2ac575f9d55b5
unix  2      [ ACC ]     STREAM     HÖRT         2861     -                   @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     HÖRT         4672     -                   /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     HÖRT         5328     -                   @/tmp/gdm-session-GTdapcyk
unix  2      [ ACC ]     STREAM     HÖRT         4630     -                   @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     HÖRT         5606     1227/gnome-session  @/tmp/.ICE-unix/1227
unix  2      [ ACC ]     STREAM     HÖRT         4285     -                   @/var/run/hald/dbus-U6RzUNBu5H
unix  2      [ ACC ]     STREAM     HÖRT         4258     -                   /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     HÖRT         9385     -                   /var/run/sendmail/mta/smcontrol
unix  2      [ ACC ]     STREAM     HÖRT         112314   5823/gvfsd-http     /tmp/orbit-kristina/linc-16bf-0-59388771975df
unix  2      [ ACC ]     STREAM     HÖRT         112888   5852/gnome-terminal /tmp/orbit-kristina/linc-16dc-0-14a55203dae24
unix  2      [ ACC ]     STREAM     HÖRT         9444     -                   /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     HÖRT         4331     -                   /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     HÖRT         4376     -                   @/var/run/hald/dbus-OlGPTAl75r

```----
netstat localhost

```
Starting Nmap 5.00 ( http://nmap.org ) at 2010-04-07 00:01 GMT
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 995 closed ports
PORT    STATE SERVICE
25/tcp  open  smtp
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
587/tcp open  submission
631/tcp open  ipp

Nmap done: 1 IP address (1 host up) scanned in 0.14 seconds

```---
bwm-ng
Nothing happening here...
```
  
  bwm-ng v0.6 (probing every 0.500s), press 'h' for help
  input: /proc/net/dev type: rate
  \         iface                   Rx                   Tx                Total
  ==============================================================================
               lo:           0.00 KB/s            0.00 KB/s            0.00 KB/s
             eth0:           0.00 KB/s            0.00 KB/s            0.00 KB/s
         wmaster0:           0.00 KB/s            0.00 KB/s            0.00 KB/s
            wlan0:           0.00 KB/s            0.00 KB/s            0.00 KB/s
  ------------------------------------------------------------------------------
            total:           0.00 KB/s            0.00 KB/s            0.00 KB/s

```

---

### Post by bogulo on 2010-04-08
Does anyone have an idea on this?

:popcorn:

---

### Post by wojox on 2010-04-08
So this is a wubi install I take it?

---

### Post by psusi on 2010-04-08
Prefix the command with sudo to run it as root.  Most likely it sounds like you have an open wireless router and one of your neighbors is downloading torrents using your connection.

---

### Post by puppywhacker on 2010-04-08
You may have a "leak" in your wireless network like psusi mentioned. Make sure you use WPA2 for link encryption.

You shouldn't run a mailserver towards the evil internet. Port 25 and 587 are used by an email server. You probably don't need it and it might be an open-relay. Serving as a jumpingboard for spam.

run the netstat -n when you have the problem, it will show you the port that is used during an attack, now you only have connections to vodafone and google. port 80 is for webtraffic. port 25 for email, and 139 and 445 for samba windows network sharing. 

You can also disconnect the network for 30 seconds to kill all connections.

And ultimately you can use tcpdump or wireshark to make a network trace of the traffic during an attack.

---

### Post by mbehamin on 2010-04-11
Hi again 

your computer is listening on port 25 and perhaps many spammers are uses your smtp to send mail. please check that with your mail server logs. 
note that your computer are connected to many webserver (whats the meaning of VERBUNDEN  !!?). did you connect to them yourself? 

but in your traffic view there is no traffic through your computer. do you have any computer connected to your network ?

---

