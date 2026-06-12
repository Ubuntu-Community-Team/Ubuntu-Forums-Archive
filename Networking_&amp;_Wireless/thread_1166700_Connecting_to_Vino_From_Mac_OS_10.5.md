---
title: "Connecting to Vino From Mac OS 10.5"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by Zerocool3001 on 2009-05-22
I'm trying to use vino-server running on Ubuntu 9.04 to control the box from a Mac OS 10.5. I can see the service listed by Avahi (along with the hardcoded string bug). But whenever I try to connect it just says "contacting" until I cancel the operation. I've tried using "Screen Sharing" from the Finder and Remote Desktop, but both give the same result. I've also tried connecting directly to the box by IP address. Any help would be much appreciated.

Just to note I can connect to other network services on the box and the firewall is off.

---

### Post by superprash2003 on 2009-05-22
are the two machines able to ping each other??

---

### Post by Zerocool3001 on 2009-05-22
> are the two machines able to ping each other??
Yes, the two machines can see eachother. I have AFP and SMB working between the two machines. I can also use vino viewer on another Ubuntu machine to control the desktop. However, I cannot connect to the vino server using any of the Macs on the network.

---

### Post by fld on 2009-05-27
> **Zerocool3001 said:**
> Yes, the two machines can see eachother. I have AFP and SMB working between the two machines. I can also use vino viewer on another Ubuntu machine to control the desktop. However, I cannot connect to the vino server using any of the Macs on the network.

works here. try with the password option, then typing the vnc://... address in the connect to server window (finder menu). if the port is 5900, you may leave it away on the mac. the used user must be logged in on ubuntu but I guess you know that...

---

