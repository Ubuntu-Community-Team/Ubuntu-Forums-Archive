---
title: "Asking Samba for permission"
date: 2010-12-24
forum: Networking &amp; Wireless
---

### Post by mikeobeda on 2010-12-24
Hello all,

I've been trying to set up a media server using Ubuntu server, following the instructions from havetheknowhow.com.  I am trying to access the server from a windows 7 pro laptop.  I can see my media server on the network.  I can see the folder vol1 which I want to access, but when I double click on it, I am given an error message saying it is not accessible and I don't have permission to access it.  I can access the server using webmin, and I can access its terminal with putty.  I just don't know what settings to tweak.  Any help would be very appreciated.

---

### Post by luvshines on 2010-12-25
Can you post the output of ```

testparm -s
``` command on the Ubuntu server. Also mention the user with which you are trying to access the server

---

