---
title: "Connection to school network"
date: 2010-12-13
forum: Networking &amp; Wireless
---

### Post by tudor117 on 2010-12-13
Hi, my laptop is running BackTrack 4 R2.
I'd like to connect to my school network which has a WPA authentication and requires a unique (different for each student) username and password.
Backtrack comes with Wicd installed by default. I have tried numerous things including changing the connection templates but to no avail.
I took out the cert option in the template and tried to connect but it didn't work. Here is the output:
```
wicd --no-daemon
Starting automatic reconnect process
Starting automatic reconnect process
Starting automatic reconnect process
Starting automatic reconnect process
Throttling autoreconnect
Throttling autoreconnect
Throttling autoreconnect
Throttling autoreconnect
Throttling autoreconnect
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:04:23:6c:d0:cd
Sending on   LPF/eth1/00:04:23:6c:d0:cd
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.168.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Nothing to flush.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:11:43:f2:4e:78
Sending on   LPF/eth0/00:11:43:f2:4e:78
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Nothing to flush.
Throttling autoreconnect
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:04:23:6c:d0:cd
Sending on   LPF/eth1/00:04:23:6c:d0:cd
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.168.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
Nothing to flush.
ioctl[ATMEL_WPA_IOCTL_PARAM]: Bad address
ioctl[ATMEL_WPA_IOCTL_PARAM]: Bad address
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; Operation not supported.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:04:23:6c:d0:cd
Sending on   LPF/eth1/00:04:23:6c:d0:cd
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.168.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
Throttling autoreconnect
Throttling autoreconnect
Throttling autoreconnect
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:04:23:6c:d0:cd
Sending on   LPF/eth1/00:04:23:6c:d0:cd
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.168.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Nothing to flush.
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:11:43:f2:4e:78
Sending on   LPF/eth0/00:11:43:f2:4e:78
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Nothing to flush.
Throttling autoreconnect
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:04:23:6c:d0:cd
Sending on   LPF/eth1/00:04:23:6c:d0:cd
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.168.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
Nothing to flush.
ioctl[ATMEL_WPA_IOCTL_PARAM]: Bad address
ioctl[ATMEL_WPA_IOCTL_PARAM]: Bad address
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; Operation not supported.
^CTraceback (most recent call last):
  File "/usr/share/wicd/daemon/monitor.py", line 389, in <module>
    main()
  File "/usr/share/wicd/daemon/monitor.py", line 385, in main
    mainloop.run()
KeyboardInterrupt

```
What I'm ultimately looking for is a network manager that will detect the authentication type automatically (I really have no idea what my school uses) and that will hopefully be in BT4's repos. Other that or to make Wicd work.
Any suggestions?

---

### Post by tudor117 on 2010-12-15
So what I really want is to know what program is able to detect the type of protection automatically (PEAP/EAP/etc) and to be able to use it.

---

### Post by Megaptera on 2010-12-16
You say "I'd like to connect to my school network which has a WPA authentication and requires a unique (different for each student) username and password."

Have you asked your school admin / tech support people for their help? They should be able to sort you out a p/w etc surely?

---

### Post by tudor117 on 2010-12-16
I already have my own username and password.
However, all the instructions for connecting are for windows/mac/iphone.
They are pretty much:
1. Click on the network
2. Put in your username and password

Also, I have no idea who to ask.
All I'm looking for is (hopefully) a gui that automatically detects the type of authentication and connects using supplied user/pass.

---

### Post by grahammechanical on 2010-12-16
What is Backtrack? Do not worry I just googled it. On their web site there are tutorials, I found this:

Under Re: How to start networking in Backtrack

> for connections and GUI tools you could start "wicd Network Manager" 
# /etc/init.d/wicd start 
then use wicd-client to configure your wireless interface(s) look under the [Internet] menu I hope this helps. It seems that you are using a Linux OS that does not put a lot of effort into easy user experience. This is why I use Ubuntu.

Regards.

---

### Post by tudor117 on 2010-12-16
LOOOL. Backtrack is based on Ubuntu; it's just customized to include specific packages, features and tools. I know how to start networking. My problem is that WICD does not connect.
It tells me it was unable to authenticate.

---

### Post by Megaptera on 2010-12-17
> **tudor117 said:**
> I already have my own username and password.
However, all the instructions for connecting are for windows/mac/iphone.
They are pretty much:
1. Click on the network
2. Put in your username and password

Also, I have no idea who to ask.
All I'm looking for is (hopefully) a gui that automatically detects the type of authentication and connects using supplied user/pass.

Well if it was me I'd ask whoever it was that gives out user names and passwords.
There must be IT support for users/pupils 'cos even Windows/Mac users may need help sometimes. Is there not a school directory? Are there teachers? Why not ask one of them who you need to speak to.

---

### Post by tudor117 on 2010-12-17
In the cafeteria there are instructions posted on the wall. For windows xp, vista and 7. Also for mac and ipod. 
The passwords are given out by the teachers, (who have all the students' passwords from a database).
I think there might be mac filtering which would explain it.
I'd have to go to the office and fill out a form. I haven't thought about that yet...

---

### Post by Megaptera on 2010-12-18
Probably the best way to go, you can't be the first Ubuntu user there and getting their help early on avoids any misunderstandings later.

---

### Post by spiky001 on 2010-12-18
**Tudor117**  Dose wicd work ok on other networks /"connect" i,e at home or is it just there?

---

### Post by tudor117 on 2010-12-18
Wicd works on other connections. It works at home, on wired, and wireless with wep. I've also used it in hotels with wep and I believe also with wpa. However none of these used unique usernames and passwords. I think that's called EAP or PEAP... but I have no idea.

---

