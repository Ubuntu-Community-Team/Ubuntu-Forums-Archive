---
title: "remote administration"
date: 2010-04-12
forum: Networking &amp; Wireless
---

### Post by foxy123 on 2010-04-12
My mother has bought her first laptop and I happily installed Lucid beta 2 for her. Since she lives in a different city (actually a different country) I need a remote access to the laptop in case something's wrong with it (given it still can be connected to the Internet). What is the best way to set it up when I still have an access to the laptop?

---

### Post by rg_stephens on 2010-04-12
A VNC server seems the best way to go. 9.10 has *Remote Desktop* on the System --> Preferences menu. I assume Lucid is similar. You'll need to install a VNC client on your computer. If she's using a router/firewall, you'll need to open the appropriate port.

You'll need a good internet connection for VNC to work good. Here in Guatemala, bandwidth is terribly unreliable.

Edit: Port 5900 is the default listening port for VNC

---

### Post by 98cwitr on 2010-04-12
^^^I would deter you from doing this. First the router would have to allow a VPN connection. Just opening ports would have her wide open, and that's a bad bad BAD idea. VNC, on a properly configured network, is only going to be good for a LAN to LAN connection. You need VPN software...enter Hamachi: 

Best soft-VPN ever

[http://www.supware.net/HamachiUbuntuHowto/](http://www.supware.net/HamachiUbuntuHowto/)

Hamachi is fast, lightweight, and most importantly secure. It takes a little configuring, but once you get it running it's the only way to go for VPN (and it's FREE).

---

### Post by rg_stephens on 2010-04-12
You're right, passwords are unencrypted, brute force is possible, etc...  VNC tunneled through a VPN network is much more secure. Port-forwarding your router is not that dangerous, as long as there is nothing for it to connect to.

But the nice thing about VNC is that it can (or should) be enabled only as needed. Your mom could turn it on as needed, or choose to accept the incoming connection.

---

### Post by 98cwitr on 2010-04-12
no no, i'm not talking about port forwarding, I'm talking about actually opening the ports on the router for these transmissions to enter and exit through. All someone would have to do is scan for open ports on the external IP, get through the router firewall, and then they have total access to the network, including the machine in question. Port forwarding would be "kinda" safe, using "uncommon" ports...but I can nmap just about any linux box or external IP for that matter; not running ping blocking software (like psad), and find out all open ports 1-65535 in about 10 minutes.

---

### Post by 2hot6ft2 on 2010-04-12
I would suggest SSH and FreeNX. See the how to in my sig. below. It's secure and fast.

---

### Post by pricetech on 2010-04-12
I concur with 2hot, use SSH.

I use NX from No Machine.

---

### Post by foxy123 on 2010-04-12
She does not have a router. The network cable goes straight from a socket. I am not sure how it works. But I have all her settings like DNS etc.

---

### Post by rg_stephens on 2010-04-12
Many people have routers because of the convenience, and the extra firewall gives more security, rather than connecting directly to the net. 

I like 98cwitr's idea; he understands networks better than me, but basically any server-type program must be able to listen for external connections by opening a firewall port, and this is a security risk. I was trying to suggest a simple solution, but I don't want to put the computer at risk. More info would be helpful...

---

### Post by foxy123 on 2010-04-13
I think that there is a one big router for a whole apartment block. They provided IP address, mask, gateway and DNS.

---

### Post by rg_stephens on 2010-04-15
that's entirely possible. if so, you probably don't have any control over it. You're at the mercy of the person who manages the network, which can be a scary situation. Make sure the firewall is working and no file-sharing enabled. 

I'm not sure what you exactly want to do, but do you guys use Skype? It's the most popular (and best) way to make international calls; voice, video, etc. The latest version has screen sharing, so you could *see* each others desktop, even without a camera. Thats sometimes helpful for diagnosing a problem, or tutoring someone who is having trouble with their computer. Skype is Ubuntu compatible, and you don't have to mess with the network settings :->

---

### Post by foxy123 on 2010-04-15
> **rg_stephens said:**
> that's entirely possible. if so, you probably don't have any control over it. You're at the mercy of the person who manages the network, which can be a scary situation. Make sure the firewall is working and no file-sharing enabled. 

I'm not sure what you exactly want to do, but do you guys use Skype? It's the most popular (and best) way to make international calls; voice, video, etc. The latest version has screen sharing, so you could *see* each others desktop, even without a camera. Thats sometimes helpful for diagnosing a problem, or tutoring someone who is having trouble with their computer. Skype is Ubuntu compatible, and you don't have to mess with the network settings :->

I did not know about desktop sharing. In that case I will need sshaccess in addition to Skype to perform admin tasks. I have enabled the firewall and open port for ssh. We'll see this weekend if it works.

---

