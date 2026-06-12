---
title: "Accessing NAS outside LAN"
date: 2012-05-16
forum: Networking &amp; Wireless
---

### Post by acrocephalus on 2012-05-16
Hello!
I have recently purchased a Conceptronic CH3HNAS and I would like to be able to access it from outside my home LAN. The device has an FTP server. I tried to install the Funplug package as described in [http://nas-tweaks.net/256/installation-of-the-conceptronic-fun_plug-on-the-conceptronic-ch3hnas/]("http://nas-tweaks.net/256/installation-of-the-conceptronic-fun_plug-on-the-conceptronic-ch3hnas/") in order to install SFTP on my NAS, but I didn't succeed (see [http://ubuntuforums.org/showthread.php?t=1971954]("http://ubuntuforums.org/showthread.php?t=1971954")), so I'm not sure I can install SFTP. Could anyone help me on accessing to my NAS from outside my home LAN in the safest way possible? I'm a networking newbie (I have no idea on port forwarding and other things), so step by step instructions will be really appreciated! Just to provide more information, I'm running Ubuntu 11.10 and my modem is a Cisco EPC3825.
Thank you so much!!

Dani

---

### Post by acrocephalus on 2012-05-17
> **acrocephalus said:**
> Hello!
I have recently purchased a Conceptronic CH3HNAS and I would like to be able to access it from outside my home LAN. The device has an FTP server. I tried to install the Funplug package as described in [http://nas-tweaks.net/256/installation-of-the-conceptronic-fun_plug-on-the-conceptronic-ch3hnas/]("http://nas-tweaks.net/256/installation-of-the-conceptronic-fun_plug-on-the-conceptronic-ch3hnas/") in order to install SFTP on my NAS, but I didn't succeed (see [http://ubuntuforums.org/showthread.php?t=1971954]("http://ubuntuforums.org/showthread.php?t=1971954"))

Finally I managed to install OpenSSH followinh the guidelines here [http://nas-tweaks.net/256/installation-of-the-conceptronic-fun_plug-on-the-conceptronic-ch3hnas/]("http://nas-tweaks.net/256/installation-of-the-conceptronic-fun_plug-on-the-conceptronic-ch3hnas/") to install the Funplug package and here [http://visscher.dyndns-home.com/]("http://visscher.dyndns-home.com/") to install OpenSSH, so my problem is partially solved. Now, how can I connect from outside my home LAN? Please, help me, it is very important for me!! I need to connect during my travels to backup all the pictures!!
Cheers!

Dani

---

### Post by Lars Noodén on 2012-05-17
Excellent.

You'll need to set up [port forwarding](http://portforward.com/english/routers/port_forwarding/) to the machine running the OpenSSH server.  That way a connection from the outside to a specific port on your router (usually 22/ssh) is forwarded to your NAS.  The specifics vary from router to router.

You might also need to set it so your NAS gets the same IP address each time from the DHCP server or else uses a static address.

---

### Post by acrocephalus on 2012-05-17
Thank you so much Lars. However, I have a couple of questions. First, looking at your link, it tells me to set up a statip ip address. How can I do it in Ubuntu 11.10? I think the rest of the procedure is pretty straight forward if I manage to set up an static ip. Second, the second part of your explanation:

> You might also need to set it so your NAS gets the same IP address each time from the DHCP server or else uses a static address.

I have no idea on how to do it. Could you give me a hint?
Cheers!

Dani

---

### Post by Lars Noodén on 2012-05-17
I don't have 11.10 anywhere handy, but on 12.04 you could do the following:

System Settings -> Network -> Wired -> Options -> IPv4 Settings -> Method: Manual

It should be something close.

Or you could look in your router's configuration and get it to serve the same IP number to your machine.  Again, that varies from router to router.  You might need your MAC address.  The fast way to get that is to look at :

System Settings -> Network -> Wired

Note that it is trivial to change the MAC address so this is a convenience thing, not a security measure.

---

### Post by acrocephalus on 2012-05-17
Thanks Lars. It was pretty easy endeed. I could do it easily from my NAS web manager. Now I should try it!

Dani

---

### Post by acrocephalus on 2012-05-17
Just a last (probably stupid) question. I have been testing the SSH connection using SFTP from Filezilla, setting the host as my external IP and the port 22 and it works. If I'm able to connect using these settings from inside my LAN I should be able to connect from outside as wll, isn't it? If so, I will mark the thread as solved!
Cheers!

Dani

---

### Post by Lars Noodén on 2012-05-18
Yes, in general if you can access the external IP from the inside, it should also be available from the outside.  Just be sure to use good, solid passwords or better yet disable passwords and use [keys](https://wiki.archlinux.org/index.php/SSH_Keys) for authentication.

---

### Post by acrocephalus on 2012-05-18
Thank you so much Lars! I'll work on that. If I have some problem I'll work on that!
Cheers!

Dani

---

