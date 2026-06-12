---
title: "problem with remote desktop in 10.04: connection refused"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by rrofes on 2010-05-05
I updated my PC to 10.04 from 9.10 keeping /home directory.
In Karmic I had gnome remote desktop set up & working, and router port configured all right.
After the update rem desk does not work, I get "connection refused" or "timed out" message.

I have checked/tried:
- I have no firewall installed (firestarter)
- I made "sudo ufw disable" & rebooted
- checked router configuration
- checked gnome remote desktop configuration

The output of netstat -l: (Seems that something is listening in port 5923, which is what I use for remote desktop):

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN     
tcp6       0      0 [::]:5923               [::]:*                  LISTEN     
udp        0      0 *:bootpc                *:*                                
udp        0      0 *:mdns                  *:*                                
udp        0      0 *:55916                 *:*                                
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     13685    /tmp/orbit-roger/linc-63e-0-79c0614a6a6fd
unix  2      [ ACC ]     STREAM     LISTENING     12209    @/tmp/.ICE-unix/1488
unix  2      [ ACC ]     STREAM     LISTENING     14269    /tmp/orbit-roger/linc-664-0-5f2ea4a1156c8
unix  2      [ ACC ]     STREAM     LISTENING     15763    /tmp/orbit-roger/linc-68a-0-5f4ebe7774af
unix  2      [ ACC ]     STREAM     LISTENING     25326    /tmp/orbit-roger/linc-6b9-0-19ff9bd44fc1b
unix  2      [ ACC ]     STREAM     LISTENING     14284    /tmp/orbit-roger/linc-665-0-693bba441b704
unix  2      [ ACC ]     STREAM     LISTENING     5429     @/tmp/gdm-session-nGAKsuPC
unix  2      [ ACC ]     STREAM     LISTENING     12181    @/tmp/dbus-nCnWK40VvU
unix  2      [ ACC ]     STREAM     LISTENING     4659     /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     2700     @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     12934    /tmp/orbit-roger/linc-612-0-34645c629ef25
unix  2      [ ACC ]     STREAM     LISTENING     13108    /tmp/orbit-roger/linc-613-0-38990bd7b3b71
unix  2      [ ACC ]     STREAM     LISTENING     13187    /tmp/orbit-roger/linc-615-0-32f01f94ba994
unix  2      [ ACC ]     STREAM     LISTENING     4931     /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     13227    /tmp/orbit-roger/linc-614-0-21572c76bc77c
unix  2      [ ACC ]     STREAM     LISTENING     13287    /tmp/orbit-roger/linc-619-0-18583d4cddd14
unix  2      [ ACC ]     STREAM     LISTENING     12544    /tmp/keyring-bRwWXL/control
unix  2      [ ACC ]     STREAM     LISTENING     25143    /tmp/orbit-roger/linc-6ab-0-4c2f9c5ccf1f3
unix  2      [ ACC ]     STREAM     LISTENING     4955     /var/run/samba/winbindd_privileged/pipe
unix  2      [ ACC ]     STREAM     LISTENING     34457    /tmp/orbit-roger/linc-6d8-0-4ce7e03ada245
unix  2      [ ACC ]     STREAM     LISTENING     5283     @/tmp/gdm-greeter-lfbZXelu
unix  2      [ ACC ]     STREAM     LISTENING     4648     @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     4649     /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     4223     /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     25260    /tmp/orbit-roger/linc-6b6-0-3e820cc0215fd
unix  2      [ ACC ]     STREAM     LISTENING     4953     /tmp/.winbindd/pipe
unix  2      [ ACC ]     STREAM     LISTENING     13291    /tmp/orbit-roger/linc-61d-0-37872554de049
unix  2      [ ACC ]     STREAM     LISTENING     13324    /tmp/orbit-roger/linc-61f-0-6751ba30e92ec
unix  2      [ ACC ]     STREAM     LISTENING     13493    /tmp/orbit-roger/linc-62a-0-1e23234d1ec69
unix  2      [ ACC ]     STREAM     LISTENING     12578    /tmp/keyring-bRwWXL/pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     12582    /tmp/keyring-bRwWXL/ssh
unix  2      [ ACC ]     STREAM     LISTENING     12605    /tmp/orbit-roger/linc-602-0-507b95bf8c279
unix  2      [ ACC ]     STREAM     LISTENING     12168    /tmp/ssh-tqdLPz1488/agent.1488
unix  2      [ ACC ]     STREAM     LISTENING     46308    @/org/wrapper/NSPlugins/libflashplayer.so/1578-1
unix  2      [ ACC ]     STREAM     LISTENING     12210    /tmp/.ICE-unix/1488
unix  2      [ ACC ]     STREAM     LISTENING     12445    /tmp/orbit-roger/linc-5d0-0-6cc436fede206
unix  2      [ ACC ]     STREAM     LISTENING     6141     @/var/run/hald/dbus-Y0RhTuzj6o
unix  2      [ ACC ]     STREAM     LISTENING     12230    /tmp/orbit-roger/linc-5f9-0-12674abddb080
unix  2      [ ACC ]     STREAM     LISTENING     4308     /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     14364    /tmp/orbit-roger/linc-669-0-58775ee735a11
unix  2      [ ACC ]     STREAM     LISTENING     14372    /tmp/orbit-roger/linc-668-0-70412ec43620a
unix  2      [ ACC ]     STREAM     LISTENING     13608    /tmp/orbit-roger/linc-631-0-145befd259239
unix  2      [ ACC ]     STREAM     LISTENING     14585    /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     14588    /home/roger/.pulse/b1ede5c4a1d2d208488e65d14be0521b-runtime/native
unix  2      [ ACC ]     STREAM     LISTENING     14659    /tmp/orbit-roger/linc-67a-0-16e4109fa0981
unix  2      [ ACC ]     STREAM     LISTENING     12762    /tmp/orbit-roger/linc-60e-0-4b9011248d67e
unix  2      [ ACC ]     STREAM     LISTENING     6135     @/var/run/hald/dbus-4ERbJVkyXj

The output of "nmap localhost":

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-05-05 20:36 CEST
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 999 closed ports
PORT    STATE SERVICE
631/tcp open  ipp

Nmap done: 1 IP address (1 host up) scanned in 0.20 seconds

Can someone help? I don't know what else to control...
Thank you!

---

### Post by tti_7 on 2010-05-06
Could be the host is stuck at the keyring password dialog popup, a bug I am stuck with.

---

### Post by rrofes on 2010-05-07
thanks tti_7, it is already solved! after installing lucid lynx i didn't realise that network configuration changed: my pc got assigned another ip but the ports configuration of the router was the original. ehm... sorry to make you lose time, and thanks to read my post

---

### Post by chowder on 2010-05-07
> **tti_7 said:**
> Could be the host is stuck at the keyring password dialog popup, a bug I am stuck with.

Did you ever get a work around this?  I'm also getting the keyring dialog popup when I try to remote in

---

### Post by tti_7 on 2010-05-07
> **chowder said:**
> Did you ever get a work around this?  I'm also getting the keyring dialog popup when I try to remote in

yes, but it's a non-elegant workaround, by setting the keyring password to blank, you'll get a warning for it being unsafe.

remove the old keyring first
```
rm ~/.gnome2/keyrings/login.keyring
```
then set the password for remote desktop again.

---

### Post by andrewbrown22 on 2010-05-17
I'm really interested in finding a solution to this same problem as the previous two posters mentioned.

Any luck without removing the keyring password?

---

