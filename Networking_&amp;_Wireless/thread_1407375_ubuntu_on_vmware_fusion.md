---
title: "ubuntu on vmware fusion"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by dagobert39 on 2010-02-15
I have been trying now for days to get Samba working on Ubuntu but to no avail. Here is my situation.

I am running Ubuntu as a guest system via latest version of VMWare Fusion installed on an iMac. The network option is set to "bridged" and the network adaptor properties are set manually (fixed IP). Internet works and so does file teansfer between Mac and Guest using gFtp.

Next, I am trying to use Samba via the network browser. Three icons relating to the Mac appear together with an icon labelled Windows network. The 3 Mac icons can be opened: the first relates to the shared folders on the Mac (windows shares), the second can be opened using the Mac PW and contains a mixture of personal files both on the Mac and the Ubuntu server, and the third relates to anonymous login (not tried). Nowhere is there an icon relating to the Unix server which I call Ubuntu, also when I doubleclick on Windows network. In doing so I would expect an icon relating to the work group, and double clicking that one the server name Ubuntu should appear. This doesn't happen.

What have I done wrong? My smb.conf file is attached.

Appreciate your help.

---

