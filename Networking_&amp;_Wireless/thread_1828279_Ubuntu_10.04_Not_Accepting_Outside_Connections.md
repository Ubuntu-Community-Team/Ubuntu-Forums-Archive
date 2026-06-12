---
title: "Ubuntu 10.04 Not Accepting Outside Connections"
date: 2011-08-18
forum: Networking &amp; Wireless
---

### Post by Devilman13 on 2011-08-18
I'm not sure what update it was... but something updated around a week ago that has totally borked my outside connections.

For a couple of years now I've had SSH, Apache2, and 2 servers for a couple of oldschool games running 24/7 with no problems. Now, for some reason I can't connect from the outside to SSH via gFTP, to my game servers, or to the Apache2 server. This leads me to believe some sort of config was over-written which is of higher priority than any of those. Does anyone have any idea what it could be?

I have checked to make sure my router settings are the same they have been for a very long time, local connections work fine, and my network settings are still the same.

---

### Post by CharlesA on 2011-08-18
Post the output of these please:

```
sudo iptables -L
```

```
netstat -nl
```

---

### Post by Devilman13 on 2011-08-18
OK

```
devilman13@UbuntuServ:~$ sudo iptables -L
[sudo] password for devilman13: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
devilman13@UbuntuServ:~$ netstat -nl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:34437         0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:6000            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp6       0      0 :::139                  :::*                    LISTEN     
tcp6       0      0 :::6000                 :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
tcp6       0      0 :::445                  :::*                    LISTEN     
udp        0      0 192.168.1.60:137        0.0.0.0:*                          
udp        0      0 0.0.0.0:137             0.0.0.0:*                          
udp        0      0 192.168.1.60:138        0.0.0.0:*                          
udp        0      0 0.0.0.0:138             0.0.0.0:*                          
udp        0      0 0.0.0.0:10000           0.0.0.0:*                          
udp        0      0 0.0.0.0:59822           0.0.0.0:*                          
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     3839     /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     7290     /tmp/ssh-HcCojR1349/agent.1349
unix  2      [ ACC ]     STREAM     LISTENING     7332     /tmp/.ICE-unix/1349
unix  2      [ ACC ]     STREAM     LISTENING     4640     /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     6613     @/var/run/hald/dbus-6kXZ5Fmbpm
unix  2      [ ACC ]     STREAM     LISTENING     2452     @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     5899     @/tmp/gdm-session-nnPDHStM
unix  2      [ ACC ]     STREAM     LISTENING     4525     /tmp/.winbindd/pipe
unix  2      [ ACC ]     STREAM     LISTENING     5479     /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     5691     @/tmp/.X11-unix/X1
unix  2      [ ACC ]     STREAM     LISTENING     5478     @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     4194     /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     7303     @/tmp/dbus-u2iGWZGYiy
unix  2      [ ACC ]     STREAM     LISTENING     3705     /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     7501     /tmp/orbit-devilman13/linc-545-0-69a25099a7cd4
unix  2      [ ACC ]     STREAM     LISTENING     5756     @/tmp/gdm-greeter-cgbyxrUe
unix  2      [ ACC ]     STREAM     LISTENING     8638     /tmp/orbit-devilman13/linc-5bc-0-4bf36ca160b00
unix  2      [ ACC ]     STREAM     LISTENING     8659     /tmp/orbit-devilman13/linc-5c3-0-60bb0fa197e11
unix  2      [ ACC ]     STREAM     LISTENING     8679     /tmp/orbit-devilman13/linc-5c2-0-72a2f87fa32ee
unix  2      [ ACC ]     STREAM     LISTENING     8715     /tmp/orbit-devilman13/linc-5c1-0-44349a1cba13f
unix  2      [ ACC ]     STREAM     LISTENING     9054     /tmp/orbit-devilman13/linc-5dc-0-5ab7e329d83ee
unix  2      [ ACC ]     STREAM     LISTENING     5692     /tmp/.X11-unix/X1
unix  2      [ ACC ]     STREAM     LISTENING     7625     /tmp/keyring-dOc4s4/ssh
unix  2      [ ACC ]     STREAM     LISTENING     9876     /tmp/orbit-devilman13/linc-67d-0-4d8d496ca99f
unix  2      [ ACC ]     STREAM     LISTENING     4527     /var/run/samba/winbindd_privileged/pipe
unix  2      [ ACC ]     STREAM     LISTENING     7352     /tmp/orbit-devilman13/linc-56e-0-4e8a16f0a18e1
unix  2      [ ACC ]     STREAM     LISTENING     7046     /tmp/keyring-dOc4s4/control
unix  2      [ ACC ]     STREAM     LISTENING     7643     /tmp/orbit-devilman13/linc-575-0-4d6ad295ea71
unix  2      [ ACC ]     STREAM     LISTENING     7654     /tmp/keyring-dOc4s4/pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     8230     /tmp/orbit-devilman13/linc-58f-0-82b6c3723654
unix  2      [ ACC ]     STREAM     LISTENING     8132     /tmp/orbit-devilman13/linc-591-0-6f8f0ce851975
unix  2      [ ACC ]     STREAM     LISTENING     8070     /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     8073     /home/devilman13/.pulse/db10dca2e1de2c9737658e454b1a6f3e-runtime/native
unix  2      [ ACC ]     STREAM     LISTENING     8147     /tmp/orbit-devilman13/linc-58d-0-d4daf865dd39
unix  2      [ ACC ]     STREAM     LISTENING     6618     @/var/run/hald/dbus-1dLIYbbMZV
unix  2      [ ACC ]     STREAM     LISTENING     8232     /tmp/orbit-devilman13/linc-582-0-684290ca23828
unix  2      [ ACC ]     STREAM     LISTENING     8234     /tmp/orbit-devilman13/linc-586-0-682fc15239a0
unix  2      [ ACC ]     STREAM     LISTENING     8450     /tmp/orbit-devilman13/linc-58a-0-38cd1383344a0
unix  2      [ ACC ]     STREAM     LISTENING     8463     /tmp/orbit-devilman13/linc-5b4-0-59192d018291
unix  2      [ ACC ]     STREAM     LISTENING     4842     /var/run/apache2/cgisock.960
unix  2      [ ACC ]     STREAM     LISTENING     7331     @/tmp/.ICE-unix/1349
devilman13@UbuntuServ:~$ 

```

I made sure to update my no-ip DNS as well by the way.

---

### Post by CharlesA on 2011-08-18
Ok, they look like they are open and no firewall is in place.

How do you have port forwarding set up on the router? Did the IP of that box change or is it static?

---

### Post by Devilman13 on 2011-08-19
The machine has a LAN static address of 192.168.1.60
This hasn't changed. My network does not have a static WAN IP.

I connect from the outside via a free no-ip.org DNS that I keep updated. This client [http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html]("http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html") has been in place for some time to make sure that my URL is resolved to the current WAN IP.

All ports needed (80, etc) are forwarded to 192.168.1.60 in my router.

Now one thing I just realized that I haven't checked is if I can connect to the current WAN IP. If I could, that would tell me it's just an unknown DNS issue. I will run that test when I get home from work this afternoon.

---

### Post by CharlesA on 2011-08-19
Try going to canyouseeme.org to see if those ports are exposed to the internet.

---

### Post by Devilman13 on 2011-08-20
The WAN IP test worked.

This whole issue was due to DNS horsecrap. Thanks for your time.

---

