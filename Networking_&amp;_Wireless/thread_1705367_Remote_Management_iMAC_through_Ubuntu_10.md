---
title: "Remote Management iMAC through Ubuntu 10"
date: 2011-03-12
forum: Networking &amp; Wireless
---

### Post by sumitk on 2011-03-12
Hi,

I have been trying to use the Terminal Server Client to connect to my MAC but I am not able to do so. I searched the forums and tried the following: [AppleRemoteDesktop]("https://help.ubuntu.com/community/AppleRemoteDesktop") but not successful.

Firstly I couldn't find the "Apple Remote Desktop" in my MAC, I think they changed its name to Remote Management. So I opened it and configured the VNC with a new password.

After this I started the "Terminal Server Client" on Ubuntu, entered the IP as Computer Name and Protocol as VNC, User Name as the MAC username... but when I press Connect, a password screen appears but I can't enter anything. 

Attached is a screenshot   [ATTACH]185812[/ATTACH]. I press enter nothing happens but when I close it then this message appears [ATTACH]185813[/ATTACH].

I am not able to find what the problem is. Could anyone help.

Thanks
Sumit

---

### Post by steaksauce on 2011-03-12
I use a VNC server on a Windows 7 machine and can access it through Applications > Internet > Remote Desktop Viewer.

From there I click connect and then I input the info it needs.

Download a VNC server for your Mac (this article talks about a few [http://macapper.com/2007/03/19/vnc-remote-desktop-for-free/](http://macapper.com/2007/03/19/vnc-remote-desktop-for-free/)) and configure it. You need to know the Mac's IP address (if you're behind a router or something the DHCP service will assing it,for instaance my router assigns 192.168.5.0 for one machine and 192.168.2.0 for antoher). This atricle can tell you how to get the IP addy on a Mac since I'm not sure off hand [http://www.ehow.com/how_2068589_check-macs-ip-addresscheck-macs-ip-address.html](http://www.ehow.com/how_2068589_check-macs-ip-addresscheck-macs-ip-address.html).

Now back to the Ubuntu machine, the info you need to connect is
Protocol: VNC
Host: <insert Mac's IP addy here>
And set some preferences.

That should do it :)

---

### Post by sumitk on 2011-03-12
> **steaksauce said:**
> 

Download a VNC server for your Mac (this article talks about a few [http://macapper.com/2007/03/19/vnc-remote-desktop-for-free/](http://macapper.com/2007/03/19/vnc-remote-desktop-for-free/)) and configure it. 

That should do it :)

Thanks,

I will try it now.

---

### Post by sumitk on 2011-03-13
I did it by just checking the VNC option on MAC Remote Management and then using Remote Desktop Viewer using the protocol VNC.

It is not very fast though. Is there any better method.?

---

### Post by steaksauce on 2011-03-15
> **sumitk said:**
> I did it by just checking the VNC option on MAC Remote Management and then using Remote Desktop Viewer using the protocol VNC.

It is not very fast though. Is there any better method.?

SSH if your handy with command lines. I don't know much about it though.

---

