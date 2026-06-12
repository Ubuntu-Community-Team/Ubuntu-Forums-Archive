---
title: "Telnet into 9.10 box from within network"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by mparker1113 on 2010-03-02
I have Ubuntu 9.10 hooked up to my router through a wired NIC, and a couple of windows machines that are connected to the router through wireless cards.

I want to telnet or ssh into the ubuntu box using putty on one of the windows machines. I have attempted to do this using the ubuntu ip address and the name of the box, and neither approaches have worked.

Can someone give me some direction for getting this to work ?

---

### Post by chili555 on 2010-03-02
On the Ubuntu box, do:```
sudo apt-get install ssh openssh-server
```I don't remember much about Putty, but on any other Ubuntu machine, you should be immediately able to do:```
ssh -l username 192.168.1.whatever
```If the IP address is DHCP and always changes, you may find it convenient to set up the Ubuntu machine with a static IP address.

---

