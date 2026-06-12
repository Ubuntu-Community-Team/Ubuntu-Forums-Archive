---
title: "Server does not respond to traffic from Internet"
date: 2011-03-03
forum: Networking &amp; Wireless
---

### Post by echrisman on 2011-03-03
I am a beginner at Linux.
I have Ubuntu Server 10.10.  I enabled SSH Server and Web Server on it.
I tested in on at test network before installation and SSH and HTTP access to the server worked well.
I now have installed the Server on the DMZ segment of my firewall.  I can SSH and HTTP to the Server from another host on the DMZ or from the LAN network, but am not able to access it from the Internet.  I have verified that the Server Gateway is set correctly, as I am able to access the internet from the server.  I have checked firewall logs and the logs show my connection attempts from the internet passed through to the internal DMZ host address of the Server, but I see no return traffic from the Server in my firewall logs.  If I initiate a connection from the server out to a host on the Internet this shows up in my logs.  Is there something in Linux Ubuntu that would cause no response from the server if source is from the Internet, when it works fine if I access it locally or from my LAN network?  Thank You for any assistance..

---

### Post by gsgleason on 2011-03-03
You need to set up port forwarding in your router to send incoming traffic to the server for the various services.

---

### Post by echrisman on 2011-03-04
Port forwarding is set up.  As I mentioned, in my firewall logs I do see the SSH or HTTP connection going from the Internet through my firewall to the Linux server, but I see no traffic or reply back from the Linux Server.  The strange thing is that I do see traffic from the Linux server in my firewall logs if I ping out to the Internet from the Server.  So I know it is not my default gateway, or an issue with port forwarding on my firewall.

Is there anything else that would cause the server to not send any packets if the source is from the Internet instead of from my LAN or DMZ.  The Server is on the DMZ interface of my firewall.  I know how crazy this sounds, but although I am a novice with Linux, I am an expert on firewalls.  thanks for any help.

---

### Post by echrisman on 2011-03-04
Issue resolved.  Issue was not a Linux problem, but was instead a oversight on my Cisco ASA.
The problem was my static NAT entry on my Cisco ASA was set as "static (inside,outside) public_ip private_ip" instead of "static (dmz,outside) public_ip private_ip".
Needed to be to the DMZ since that is the interface the server is.
Thanks.

---

