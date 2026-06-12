---
title: "Wirelessly sharing internet connection"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by Quaxo76 on 2009-06-04
Hello,
I have a laptop that I use at work, and that is connected to the Internet through a hsdpa USB modem. 
I also have a small netbook, which I would like to put online, too. Both have a wireless card. What I would like to do, is to "bridge" the available Internet connection to the netbook, using the wireless card (adding an "access point" functionality to my laptop). Is this possible at all? The laptop is running Jaunty, while the netbook is running Linux4One (a modified Hardy).
Everything should not impair the laptop's ability to connect normally through wireless when I'm at home.
Thank you in advance,
Cristian

---

### Post by vyvee on 2009-06-04
You should be able to do it simply with the NetworkManager... check this:
[http://ubuntuforums.org/showthread.php?p=7398527](http://ubuntuforums.org/showthread.php?p=7398527)
and this:
[http://jeremy.visser.name/2009/03/24/simple-internet-connection-sharing-with-networkmanager/](http://jeremy.visser.name/2009/03/24/simple-internet-connection-sharing-with-networkmanager/)

---

### Post by Quaxo76 on 2009-06-05
OK, I added a new wireless connection, and set it as shared. Now the laptop transmits to the netbook and both are online. But what will happen when I'm at home where there's a wireless router? Will my laptop understand that, and act accordingly (connecting to my router's SSID)?

---

### Post by vyvee on 2009-06-05
So what you need is:
If detect your router's SSID, then connect to it; Else, share with other computers.
I'm not sure if NetworkManager is able to handle such 'conditional' behavior or not. If you want to try out, you may want to try to create two accounts in NetworkManager, one for your router & another for sharing, probably play around with their order, and the options 'Connect Automatically'.
If it fails, then you may have to do some scripting for this...

---

