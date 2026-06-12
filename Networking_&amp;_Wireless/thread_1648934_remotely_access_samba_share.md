---
title: "remotely access samba share"
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by rensell on 2010-12-19
Hi all. My work uses an internal software suite where the data is hosted with a linux server. It uses mysql and samba shares. We are currently opening a new location and need to be able to access the samba shares. We are able to access the mysql databases. The samba shares are used to store various files for the software such as updates, invoices (as pdf files), etc. 

I've setup vpn connections using windows servers in the past but I can't, for the life of me, get a VPN server setup on our linux server that windows will connect to. I've tried openvpn and pptp. I'd prefer to use the built in windows client to connect. or any other suggestions that anyone may have. 

Please let me know if I haven't been clear enough on anything, I'm swamped with getting things together today.

Thank you for your help in advance,

-R

---

### Post by TSJason on 2010-12-20
For optimum results I would highly suggest considering a site-to-site VPN solution that works at the router level. That way all traffic can be passed between both locations as if it were the same office. 

There are several ways to accomplish this. If I were implementing it I would probably use OpenVPN. Googling a bit should give you a viable option with the hardware you have available.

---

### Post by gordintoronto on 2010-12-20
Windows won't connect? From where? Have you set up port forwarding?

---

### Post by SeijiSensei on 2010-12-21
I second TSJason's suggestion.  Put Ubuntu on an old PC in the remote office and use OpenVPN to set up a full-time tunnel back to the home office.  Set up routing on the remote box so that requests for home resources are sent through the tunnel.

---

### Post by CharlesA on 2010-12-21
> **SeijiSensei said:**
> I second TSJason's suggestion.  Put Ubuntu on an old PC in the remote office and use OpenVPN to set up a full-time tunnel back to the home office.  Set up routing on the remote box so that requests for home resources are sent through the tunnel.

Another +1 for that. It's not a good idea to allow Samba direct access to/from the internet.

---

### Post by rensell on 2010-12-24
I have played around with this a little bit more. I have installed pptpd so that the native windows client can be used rather than installing additional software on machines. Using a local machine, VPN connects by using the local IP address or host name (192.168.1.190) but using VPN.MyDomain.com does not connect, even though VPN.MyDomain.com is setup to direct to my server and my firewall forwards ports to the machine. I can access a "landing page" that i created on the same server. So, I'm not sure what is wrong. I'm new to setting this up with Linux. I've set up many VPN server\clients with XP pro. I'm thinking about looking at getting another server to serve as just a VPN server, what is the thought on that?

I like the idea about have all request sent through the remote machine, but how do I set that up? basically the program we use access data at \\Server\Program so at remote location I want to VPN in so that \\Server\Program still works.

Thanks again to everyone for your help. I may not be toying with this very much for the next couple days, but will be back to it early next week. 

-R

---

### Post by rensell on 2010-12-24
I also meant to ask if anyone knows of a way to use the Linux usernames instead of adding user names and passwords to the chap file? I'd much rather have a VPN users group and add my linux user names to that group because I have users setup on the server for restricting file access for samba shares as is. So it would be much simpler to maintain to add and remove users from a VPN group than to manually edit the chaps file everytime someone needs access or no longer needs access.

-R

---

### Post by rensell on 2010-12-24
I got the VPN connection to work, it's still a little hit or miss, but I'm assuming that it is because I'm consistently connecting\disconnection while setting up the connection. 

Now, I'm wondering if anyone knows how to use Linux Usernames and Passwords instead of the secret-chaps file, as mentioned in my earlier post.

Thanks.

-R

---

### Post by dave37 on 2011-02-25
I am interested as well, I am in testing phase on our SOHO Ubuntu 8.04 file server.  I have set up openvpn on it, have successfully connected, have shared the samba shares.  
However, if I set openvpn to use PAM authentication the user with full access to the samba shares can connect. No other users can.  If I set openvpn to use Local user authentication all the users with the lesser permissions connect but not the user with top level permissions to the shares.

Additionally, the shares are set up with folder A, with B, C subfolders.  Primary user has full permissions to all folders.  All other users can only read and write to subfolder C.

On the local LAN this works fine so I'm not sure if it's a openvpn thing or not.  Last question, is it worth the trouble once beyond testing phase to setup openvpn on the backup server instead of the primary server to increase security?

I will be happy to explain in detail how I have setup openvpn with ubuntu and samba, on a soho router, if anyone needs it.

---

