---
title: "OpenDNS settings for pppoe  with usb adsl modem"
date: 2012-12-03
forum: Networking &amp; Wireless
---

### Post by magis3xludi on 2012-12-03
hi to all,I have an old speedtouch usb modem (speedtouch 330 revision 0) and on my desktop with  xubuntu 12.04 I've configured a pppoe connection. I can connect and I see that my  ISP assign an IP address and the DNS (I don't know why the primary DNS address is not  reachable by ping while the secondary yes) but no address is resolved then I  can't surf the web. Then I want to set the open DNS but there is no way,  if I change manually /etc/resolv.conf it is rewrited by some script  (there is the flag **usepeerdns** on the configuration  script, if I exclude it there is no way to assign any DNS server because  for some reason /etc/resolv.conf is not read, I think) also if I set not writable the file changing  the default permission. I changed dhclient.conf with the code
```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```
and now if I connect by a wifi connection to my router I'm using openDNS  server but ppp does not use this script as long as I can see and the  DNS server is always setted by my ISP. How can I use set DNS manually to  a PPP connection? Is there any way to change it after the connection?  Why NetworkManager is not able to manage my dsl connection, it seems not  able to manage the dsl usb cable modem? If I use pppoeconf NetworkManager doesn't start and I have to manually  delete the lines added to /etc/network/interfaces because the system is  not able to start with full configuration of network If I connect a modem-router to the same line I can surf with the DNS  server assigned by my ISP (the primary is not pingable, also in this case), I can't figure why. Some suggestion? Thanks  to all

---

### Post by magis3xludi on 2012-12-05
I definitely assume that I don't have to use the string **usepeerdns** because I don't want that the DNS supplied by my ISP are used. Then how can I set the DNS I want? Is there any other command that I can use for pppd? I don't understand why resolv,conf is not read.
Also another strange signal: if I comment **usepeerdns** then for some reason if I check with **nslookup** how the domain is resolved then is the loopback address 127.0.0.1 that tells to me *REFUSED. *Why? Where does pppd read the configuration of loopback interface? If I could know that I can change this script. Please, some suggestion?
Thanks and regards

---

