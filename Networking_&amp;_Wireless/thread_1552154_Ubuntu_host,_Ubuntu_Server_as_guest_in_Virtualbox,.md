---
title: "Ubuntu host, Ubuntu Server as guest in Virtualbox, internet access?"
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by SR41 on 2010-08-13
I'm sure other people have had this problem too but I can't find a working solution. As both OSes are Ubuntu I thought it more appropriate to post here. 

I'm running Ubuntu 10.04 (fully updated). I connect to the internet either via wifi or ethernet. I have Ubuntu Server 10.04 installed in Virtualbox 3.2.8. How can I get the ubuntu server installation to connect to the internet?

---

### Post by tranduyhung on 2010-08-13
Just configure your Ubuntu Server's network adapter attach to NAT or Bridged. You can google to find out what the differences between NAT and Bridged and others are.

---

### Post by SR41 on 2010-08-13
> **tranduyhung said:**
> Just configure your Ubuntu Server's network adapter attach to NAT or Bridged. You can google to find out what the differences between NAT and Bridged and others are.

This is the problem. I don't know how to configure NAT correctly in Ubuntu Server. Any ideas? Most of the results online are for older versions of ubuntu or virtualbox which are, according to some, no longer valid. I've tried setting up packet forwarding- that didn't work either. I

---

### Post by tranduyhung on 2010-08-16
In Virtualbox main window, you choose your machine on the left list, right click and choose "Settings", a new window will be opened, you go to "Network" to configure adapters.

---

### Post by SR41 on 2010-08-20
> **tranduyhung said:**
> In Virtualbox main window, you choose your machine on the left list, right click and choose "Settings", a new window will be opened, you go to "Network" to configure adapters.

I know how to set up NAT in Virtualbox. I need to know what to do in Ubuntu Server, using ifconfig etc. Does anyone know what settings I should use?

---

### Post by tranduyhung on 2010-08-26
If you chosed NAT for your Ubuntu Server virtual machine, your server (or any distro, any operating system) could connect to internet automatically after installing, you don't need to deal with ifconfig. You can search "ubuntu server virtualbox" on Youtube, then watch the videos there to figure out what's wrong with your Ubuntu Server installation or Virtualbox's configuration. Hope this could help.

---

