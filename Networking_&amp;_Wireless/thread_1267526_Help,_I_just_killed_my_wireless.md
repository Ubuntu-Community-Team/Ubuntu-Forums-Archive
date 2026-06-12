---
title: "Help, I just killed my wireless"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by JakP on 2009-09-15
Hi done something not very clever,  terminal suggested that 'evolution-common' was no longer needed and could be removed with 'apt-get autoremove' so i entered "sudo apt-get autoremove" (no quote's) into terminal and it removed.  Instant this finished i can no longer see any wireless networks and am completely disconnected.  Know it's there 'cause this computer working fine.  Will connect through ethernet, tried re-installing 'evolution-common' but hasn't helped.

iwconfig shows network details including sssid, says access point not-associated?

iwlist wlan0 scan says no scan results

ifconfig says wlan0 link encap: ethernet

lshw says -netwiork:0-desciption wireless interface
                               -physcal id:1
                               -logical name: wlan0
                               -serial:  6e:35:f5:b9:4f:5e
                               -capabilities: ethernet physical
                               -configuration:  broadcast=yes  multicast=yes 
                                                      wireless=ieee 802.11bg

anyone Know what i've done, and more importantly how i can put it right?

Many thanks

---

### Post by uylug on 2009-09-15
Try this:

```

[I]sudo ifconfig wlan0 down 
sudo dhclient -r wlan0 
sudo ifconfig wlan0 up 
sudo iwconfig wlan0 essid "YOUR_AP_NAME" 
sudo iwconfig wlan0 mode Managed 
sudo dhclient wlan0 [/I]
```

---

### Post by JakP on 2009-09-15
Sadly nothing

---

### Post by uylug on 2009-09-15
What is... nothing?

Do you think you could post the output of the commands i wrote? :D

---

### Post by JakP on 2009-09-15
Sorry, had to run arround abit to connect this comp. physically, results are:

jak@jak-laptop:~$ sudo ifconfig wlan0 down
jak@jak-laptop:~$ sudo dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 6405
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:90:4b:de:2f:11
Sending on   LPF/wlan0/00:90:4b:de:2f:11
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
 * Reloading /etc/samba/smb.conf smbd only
No process in pidfile `/var/run/samba/smbd.pid' found running; none killed.
   ...done.
jak@jak-laptop:~$ sudo ifconfig wlan0 up
jak@jak-laptop:~$ sudo iwconfig wlan0 essid TalkTalkk8kek
jak@jak-laptop:~$ sudo iwconfig wlan0 mode Managed
jak@jak-laptop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:90:4b:de:2f:11
Sending on   LPF/wlan0/00:90:4b:de:2f:11
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Reloading /etc/samba/smb.conf smbd only
No process in pidfile `/var/run/samba/smbd.pid' found running; none killed.
   ...done.
jak@jak-laptop:~$

---

### Post by uylug on 2009-09-16
> **JakP said:**
> Sorry, had to run arround abit to connect this comp. physically, results are:

jak@jak-laptop:~$ sudo ifconfig wlan0 down
jak@jak-laptop:~$ sudo dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 6405
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:90:4b:de:2f:11
Sending on   LPF/wlan0/00:90:4b:de:2f:11
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
 * Reloading /etc/samba/smb.conf smbd only
No process in pidfile `/var/run/samba/smbd.pid' found running; none killed.
   ...done.
jak@jak-laptop:~$ sudo ifconfig wlan0 up
jak@jak-laptop:~$ sudo iwconfig wlan0 essid TalkTalkk8kek
jak@jak-laptop:~$ sudo iwconfig wlan0 mode Managed
jak@jak-laptop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:90:4b:de:2f:11
Sending on   LPF/wlan0/00:90:4b:de:2f:11
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Reloading /etc/samba/smb.conf smbd only
No process in pidfile `/var/run/samba/smbd.pid' found running; none killed.
   ...done.
jak@jak-laptop:~$

No offers... hmm.. Run this command:

```
sudo iwlist scan
```

---

