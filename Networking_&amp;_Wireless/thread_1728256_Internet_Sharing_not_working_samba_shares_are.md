---
title: "Internet Sharing not working samba shares are?"
date: 2011-04-13
forum: Networking &amp; Wireless
---

### Post by Gcottrell on 2011-04-13
Okay.

I have internet on my ubuntu machine (eth0) I am sharing with (eth1) 

My windows computers are getting IP addresses via DHCP from the Ubuntu Machine, and I can see (and use) samba/windows shares on all computers. Internet connection is not working on any of the windows computers.

I have eth1 set to "shared to other computers"  under the IPv4 settings

Any suggestions on how to get the internet connection sharing working?

---

### Post by josephmills on 2011-04-13
don' know if this will help but [http://www.youtube.com/watch?v=Bo9HOadl-YM&feature=related](http://www.youtube.com/watch?v=Bo9HOadl-YM&feature=related) give it a shot

---

### Post by Gcottrell on 2011-04-13
It's a good tutorial, but my problem is with internet connection sharing. I'm using samba as an example of the network connections working. I could use terminal services too.

---

### Post by alienprdkt on 2011-04-13
My guess is that if you are able to see your samba shares then your issue is probably with NAT. Look into setting up NAT on Ubuntu.

---

### Post by Jason0885 on 2011-04-13
I did something similar to this with IP Tables. This is what I done. 
The setup is using CENTOS 5.6, it is a basic pppoe conenction. The modem was in bridging mode. I bridged the pppoe interface and the eth1 interface. eth1 went to a wireless hotspot. 

In terminal type
1.) sudo iptables -A INPUT -i lo -j ACCEPT

2.) sudo iptables -A OUTPUT -o lo -j ACCEPT

3.) sudo iptables --table nat --append POSTROUTING --out-interface <interface> -j MASQUERADE

<interface> is your output interface. IE the one for your router. In my case eth1. Do not use the < and > signs if your if is eth1 just put eth1.

4.) sudo service iptables save

5.) Sudo nano /etc/sysctl.conf
nano is the name of your text editor. I used nano for this machine.

6.) Add the following line to enable packet forwarding for IPv4:
net.ipv4.conf.default.forwarding=1

Save the file

sudo service network restart

When the computer reboots you may have to restart iptables by running
sudo service iptables restart

It should be similar, or even the same way. It should be at least in the right direction. I believe the term is called MASQUERADEING.

---

### Post by Gcottrell on 2011-04-13
Apparently iptables isn't compiled in my kernel.

I just booted with the live cd, installed gnome-commander, and deleted all the files except my home directory in / and reinstalled ubuntu.

Now it works flawlessly.

Bummer I had to reinstall, but it worked.

---

