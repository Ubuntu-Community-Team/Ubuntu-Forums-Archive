---
title: "Ocelot server and Belkin router"
date: 2012-03-01
forum: Networking &amp; Wireless
---

### Post by mikeservis on 2012-03-01
I recently built a home server. Installed 11.10 with Apache, Samba, php, mysql. I set the thing to run a static ip address of 192.168.2.8 and then went to my belkin router under firewall/virtual servers and added that ip. I can log into a local machine and see the web page fine, I also have ftp working. I used filezilla to upload a simple web page, I installed curl on it and did a: curl ifconfig.me to get a public ip address of: 208.53.83.195 which gets me nothing. HELP!
ciao Mike

---

### Post by mikeservis on 2012-03-02
I'm pretty new also with a similar setup. I changed my eth to static too. My interfaces looks like this:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.2.8
netmask 255.255.255.0
gateway 192.168.2.1
filezilla connects fine - you need to use sftp not ftp. I can also view the webpage I uploaded to the server var/www. Maybe I shouldn't say uploaded. It's only 10 feet away. I can view the web page by putting in the static address of 192.168.2.8 locally, but I can't view it from outside my local network.I googled around and learned (I think) that in order to find my public ip I needed to install an app called curl on the server - which I did.when I do curl ifconfig.me it gives me an address of 208.53.93.237 but it doesn't work locally or public. I went into my Belkin router and set up port forwarding with the static address of 192.168.2.8 but that made no difference. I'm working locally with the interfaces above, but I can't see it on the web so I'm confuseled Attached is a screen shot of my router[IMG]http://www.mikeservis.com/images/BelkinCapture.JPG[/IMG]

---

### Post by Iowan on 2012-03-02
I merged your posts into this thread. From the Code of Conduct:
> Do not cross post, or post the same thing in multiple locations.Although your problem might be similar to the other thread, this separate thread will let others work on your specifics.

The 208. address probably won't be accessible from inside the network. I presume you are trying to access the external address from outside of your network.

---

