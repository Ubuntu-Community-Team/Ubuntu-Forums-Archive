---
title: "Setting up a home network"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by llemes4011 on 2009-12-05
Hello, I finally convinced my parents to install Ubuntu on their desktop computer.  I've used Ubuntu before and I've found it quite nice (I only use Windows for Photoshop and Windows Programming).  Anyways, I told them we should try to use it as a printing server as well, since we only have 1 printer and 3 laptops.  I then realized that we'd have to set up a home wireless network to be able to print from any of the computers.  How do I go about doing this on Ubuntu?  Is there a way that I can set it up without making a home network?  Thanks for any help you can give me =)

---

### Post by gordintoronto on 2009-12-05
You already have a home network, all you are doing is adding a shared printer to it.

First step: make sure all computers specify the same workgroup in /etc/samba/smb.conf.  (For Windows, it's a property of My Computer.)  Then search the forums for "sharing a printer."

---

### Post by llemes4011 on 2009-12-05
But we don't have a home network.  Every guide I found required that we plug a USB drive into the router to install networking stuff, but our router doesn't have a USB port on it...

---

### Post by headvampyre@hotmail.co.uk on 2009-12-05
go to terminal and type sudo apt-get install samba smbclient swat
then go to localhost:901 and cofigure samba to do it via that then connect to server and if u need more help i will give some

---

### Post by oldfred on 2009-12-05
I think you must have been looking at instructions for a bare linux computer set up as a router and using a usb key as the drive. I have never heard of plugging in a usb drive to a standard router. Although I just saw a new one that does allow that for backup.

If you have a wireless router you have a home network as said above. The issue may be you only have portable computers. You need to have one always on and plugged into the printer to make it convenient to use. It then should also have a fixed ip address  rather than using DHCP. That is not difficult to set up. Log into your router and see what the range it is using for DHCP and assign a port for the computer used as the print server. Usually the router is 192.168.1.1 and then you assign servers to then next 10 or 20 numbers and only allow DHCP to use numbers above that so their is no conflict.

---

