---
title: "Turning Ubuntu Server into Router"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by harry71194 on 2009-12-31
I have an Ubuntu desktop. I plug it directly into my SBV5220, via ethernet. Firmware, 17.6.4-SCM-12.

Problem being, when I ifup eth0 (what the ethernet is plugged into), it fails to get a DHCP address. I have no idea why. My current dd-wrt WRT54GL router gets it fine from DHCP. I have tried on all my Ubuntu desktops, they ALL fail to get DHCP IP addresses.

Could someone help me setup a static IP on the Ubuntu server, so I can turn my Ubuntu box into a Wireless Router? My dongle doesn't support master-mode I think, so I'd use ad-hoc. I don't require anything special, except for people being able to go to my IP and get directed to my server.

This is what my dd-wrt says:
> Connection Type Automatic Configuration - DHCP     Login Status
     
  Connection Uptime 0:38:15  

  IP Address 24.59.85.xx  

  Subnet Mask 255.255.254.0  

  Gateway 24.59.84.1  

  DNS 1 208.67.222.222  

  DNS 2 208.67.220.220  

  DNS 3 209.18.47.61  

   Remaining Lease Time 0 days 23:21:29 


Replaced last subnet in IP with xx.

Help me please, this is stumping me! ;_;

---

### Post by Iowan on 2009-12-31
See if [this]("http://ubuntuforums.org/showthread.php?t=1156441") helps (probably won't). I'd never thought that a DHCP server might discriminate against non-M$ machines, but just in case - see if this helps:> 
Bee said on 2009-12-26:

Well thanks to everyone, but problem was actually solved by editing dhconfig.conf file: i added a string

send vendor-class-indentifier "MSFT 5.0";

That solved the problem, and now my linux is masking under windows when log in.


---

### Post by harry71194 on 2010-01-01
Didn't work.

Problem was, that ISP limits per MAC address of clients. I had to call them and have them reset the limit.

Thanks anyways!

---

