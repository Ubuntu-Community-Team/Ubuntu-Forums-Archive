---
title: "Copying files from Vista"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by sandy8925 on 2009-01-01
Hi, I have Intrepid running on a desktop and Vista Home Premium on a laptop. I want to copy some files over from the laptop through a LAN. Can anyone please tell me whether that's possible and how I can do so ? I think I'm supposed to use Samba but I'm not sure.

Thanks for your help!

---

### Post by SuperSonic4 on 2009-01-01
I think this post will be helpful. Just remember that vista will be the server and ubuntu the client

[http://ubuntuforums.org/showpost.php?p=6468298&postcount=4](http://ubuntuforums.org/showpost.php?p=6468298&postcount=4)

---

### Post by superprash2003 on 2009-01-01
you wouldnt need to install samba server.. as you wish to access files from the laptop.. this should help [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by risu_vk on 2009-01-01
if it is some simple files like videos etc easiest way is to run a program like hfs ( [http://www.rejetto.com/hfs/](http://www.rejetto.com/hfs/) ) on windows machine ; it can even be run from a USB drive. The  files can be accessed from linux machine with the firefox browser. Its easy to use and set up.

---

### Post by sandy8925 on 2009-01-02
I'm able to ping desktop(Intrepid) from the laptop(Vista) but not the other way round.(????????)

Also I should mention that the two are connected through a network switch. Should I connect them directly instead? And also can I copy the files if I boot ubuntu on the laptop through pendrive and then try ?

---

### Post by superprash2003 on 2009-01-02
its probably windows firewall blocking.. have you selected your network as Home or work or public network? .. are you pinging by ip or hostname?

---

### Post by sandy8925 on 2009-01-08
I've set the network to private network in Vista so that it allows discovery of other devices and all. Also I pinged using ip address.

---

### Post by superprash2003 on 2009-01-08
strange.. disable firewall for like 1 min.. and then try pinging..

---

### Post by sandy8925 on 2009-01-15
Well I ended up using a pendrive to transfer the files. But I still want to know how to do this. Is there some sort of howto or guide you can tell me about ?

---

