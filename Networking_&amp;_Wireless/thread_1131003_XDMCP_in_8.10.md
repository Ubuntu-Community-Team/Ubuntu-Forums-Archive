---
title: "XDMCP in 8.10"
date: 2009-04-20
forum: Networking &amp; Wireless
---

### Post by xynamax on 2009-04-20
I can't get XDMCP to work.   I have the host running 32-bit Ubuntu 8.10, with a wired connection to the network getting its IP from DHCP. I have the Client running the same (32-bit Ubuntu 8.10), also with a wired connection getting its IP via DHCP. All software updates are current on both systems.

To configure the Host I went to Administration->Login Window.  On the 'Remote' tab I set 'Style' to 'Same as Local'.  I clicked the 'Configure XDMCP...' button and just left all the default values as they were. (Listening on UDP 177). Clicked 'Ok' out of everything.  Then created a new user to login remotely as 'foo'  and restarted the system.  

On the Client Side I just clicked 'Options' at the GDM Login Screen, and selected "Login via XDMCP...".  The host will show up as a Computer screen displaying the Gnome logo with the IP address and 'Linux 2.6.27-11-generic'.  When I click on it and click 'Connect' I get a blank black screen with an 'X' for the mouse cursor.  Nothing else happens on the client unless I give it a ctrl+alt+Backspace.


I've also tried Installing Firestarter and setting an Incoming connection rule to allow Port 177, but that didn't help anything.

Help please


**edit**
Here's the output from netstat -an
```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:6000            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp6       0      0 :::6000                 :::*                    LISTEN     
udp        0      0 192.168.2.77:46891      167.206.112.138:53      ESTABLISHED
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp        0      0 0.0.0.0:47359           0.0.0.0:*                          
udp6    1848      0 :::177                  :::*                              
```

---

