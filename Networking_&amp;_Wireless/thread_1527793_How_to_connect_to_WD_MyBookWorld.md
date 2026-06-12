---
title: "How to connect to WD MyBookWorld"
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by randominion on 2010-07-09
Hi. I've just installed Ubuntu 10.04, which I'm running at the moment.

I've also just bought a WD MyBookWorld networked storage device.

[http://www.wdc.com/en/products/products.asp?driveid=586](http://www.wdc.com/en/products/products.asp?driveid=586)

I've connected successfully from my Windows computer and have backed up files to the share drive on the MyBookWorld.

I'd like to do be able to connect to the share drive in Ubuntu as well. 

I can access the MyBookWorld's web interface by typing its IP address (192.168.0.2) on the network into my web browser, so I know it's working. 

I can also see the MyBookWorld in my file browser. It shows as an icon with the description 'Windows Network'. However, when I double click on the icon, I get the message 'Unable to mount location - Failed to retrieve share list from server'.

I've done some checking on this forum, but I can't find the exact answer. I've checked whether a firewall is blocking my access using the iptables command, but this shows that I'm not running a firewall.

I'd like to be able to access the share drive as simply as possible - I just want to occasionally access files that have been backed up from my Windows computer. 

Let me know if you need any more information.

Thanks 

Dom

---

### Post by randominion on 2010-07-09
Hello :D

I just did a little more searching on the forum and found the answer. Let me explain.

In the file browser, in the Go menu, select Location...

In the box that appears, type:

**[FONT=Courier New]smb://192.168.0.2/[/FONT]**

replacing the IP address with the IP address of your MyBookWorld.

The file browser then shows the shares and you can browse away.

Simple

Dom

---

### Post by randominion on 2010-07-09
You can also do:

**[FONT=Courier New]smb://mybookworld/[/FONT]**

replacing 'mybookworld' with the device name.

Dom

---

### Post by Boondoklife on 2010-07-09
You may want to check your samba settings on the mybook or you might need to just update to a newer version of samba. I had the same issue with mine and a simple update of samba worked fine.

Check this out for some more info on hacking the MyBook to do all kinds of good stuff. [http://boondoklife.blogspot.com/2010/05/wd-mybook-world-edition-mini-server-i.html](http://boondoklife.blogspot.com/2010/05/wd-mybook-world-edition-mini-server-i.html)

---

### Post by bayvista on 2012-12-14
Hi Boondocklife. Thanks for the info. I want to backup files from Ubuntu to MyBookWorld. I have setup the mount in fstab OK. However, I can't write to my private share I think this is a permissions problem because the user on MBW is shown as 'root' and chown won't change that. Also, MBW creates a strange Group called 'jewab'

I can write to the Public share ok.

Thanks

---

### Post by Boondoklife on 2012-12-15
Yea the user information on the MBW is determined by the MBW not the Ubuntu machine. If you are looking to gain fine grain control over the MBW I would suggest enabling SSH on it and editing you smb.conf by hand.

---

### Post by howefield on 2012-12-15
Old thread back to sleep.

---

