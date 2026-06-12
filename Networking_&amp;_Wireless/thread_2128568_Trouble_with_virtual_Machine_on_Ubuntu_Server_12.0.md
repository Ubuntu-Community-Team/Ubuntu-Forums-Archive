---
title: "Trouble with virtual Machine on Ubuntu Server 12.04"
date: 2013-03-23
forum: Networking &amp; Wireless
---

### Post by psyllex on 2013-03-23
I'm running a Ubu server on my network.  I have a VM on there, that has a Windows desktop that is running IIS as a web server.  We're doing some testing and trying to knock over the Windows Box.  But I  need to do some monitoring on the 'Ubuntu Server' which has a IP address of <myIp-A.com>  Since I'm monitoring the Windows desktop I'm trying to do an ajax call to the IP address of <myIp-A-virtual-machine.com>.  

This is causing issues becasue 'I think' this is technically a cross site issue.  My ajax's call response is '404' on any of my calls from the Ubuntu Server to the VM Windows Server.  Is there some way around this?  I've moved the page I was using to monitor onto the web server on the virtual machine, so that solves half of the problem.  But I still need to make a simple call to the virtual machine's IP address from my Ubuntu server address.  Someone please help...I would be very grateful.

---

