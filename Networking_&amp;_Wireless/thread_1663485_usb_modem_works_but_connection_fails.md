---
title: "usb modem works but connection fails"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by raysa on 2011-01-09
I have a usb modem which I plug into my ubuntu 10.10 system for a dial-up service. The modem is recognised by wvdial and dials properly, but the connection is not established.
I get "Unable to run /usr/sbin/pppd" (although pppd is certainly in /usr/sbin), followed by "Check permissions of specify a 'PPPD Path' option in wvdial.conf", and finally "Connected, but carrier lost", then it gives up.

Any suggestions for making this work?  Thanks.

---

### Post by PatchesTheCaveman on 2011-01-10
Try running wvdial as administrator. e.g. 
```
sudo wvdial
```

If that works, you should be able to run it as a normal user if you add yourself to the *dip* group:
```
useradd -G dip *<your username>*
```

---

### Post by raysa on 2011-01-10
Many thanks - that gets the pppd going OK and the connection opened, but now there's a new problem. 
Message reads: "Connection attempt failed with 'EAI_NONAME' - Neither nodename nor servname provided, or not known."

Is this something to raise with the ISP, or is there anything I can do here?

Thanks again, Ray

---

### Post by PatchesTheCaveman on 2011-01-11
Does that go away if you run these commands after you connect?
```
sudo bash -c "echo nameserver 8.8.8.8 > /etc/resolv.conf"
sudo bash -c "echo nameserver 8.8.4.4 >> /etc/resolv.conf"
```

NOTE:  this configures your computer to use Google Public DNS, a free DNS service from Google.  All hostnames your computer attempts to resolve will be sent to Google.  If you have a problem with this, you need to figure out your ISP's DNS servers and use them above or use IP addresses from another provider such as OpenDNS.  For more information on this service, visit [http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/)

---

### Post by raysa on 2011-01-11
I've discovered that permission into the server is being denied because my pap-secrets and/or chap-secrets can't be modified because of permission denial.
How can I give permission for those folders to be modified by the connection?
Thanks, Ray

Fixed it - went into the pap-secrets and chap-secrets files and found they had somehow inserted stray characters into the usernames. Corrected this and saved files.

Also found an empty DNS box in the network area of gnome-ppp, and put the IPS domain name in there.

All works OK now.

---

