---
title: "Simple File Server 12.04, in need of help"
date: 2012-11-29
forum: Networking &amp; Wireless
---

### Post by Greenirishman on 2012-11-29
I am attempting to setup a server for my office. My boss has purchased a dedicated server through fdcservers.net with ubuntu 12.04.1 LTS installed on it with ssh and remote access available. Here are the speces of the server:
Intel Dual Core ATOM ( 2 x 1.6Ghz )
2GB RAM 250GB HDD
10Mbps, 100Mbps, 1Gbps, 10Gbps

I need to setup a simple file sharing server for windows clients. We need to be able to access the server anywhere over the internet. I was thinking of using samba but I am having trouble finding information on how to set up a server that can be access via the internet. Any help would be greatly appreciated.

---

### Post by dannyboy79 on 2012-11-29
run openvpn on the server and samba

---

### Post by lykwydchykyn on 2012-11-29
Samba is not really designed for use over the internet.  The simplest solution I would recommend installing WinSCP on the clients and just using the SSH service that's already available.

---

### Post by Greenirishman on 2012-11-29
> **lykwydchykyn said:**
> Samba is not really designed for use over the internet.  The simplest solution I would recommend installing WinSCP on the clients and just using the SSH service that's already available.
This works really well! 
Now this works just fine for me but I have some technologically impaired coworkers who are used to a cloud storage mounted drive on their computers. Is there anyway to mount shared directory or the server hardrive to the windows clients?

---

### Post by dannyboy79 on 2012-11-29
> **Greenirishman said:**
> This works really well! 
Now this works just fine for me but I have some technologically impaired coworkers who are used to a cloud storage mounted drive on their computers. Is there anyway to mount shared directory or the server hardrive to the windows clients?if you wanted to mount the shares locally, that would be samba thru openvpn.

---

### Post by Greenirishman on 2012-11-29
> **dannyboy79 said:**
> if you wanted to mount the shares locally, that would be samba thru openvpn.

OK Great Thanks for all the help! :)

---

### Post by Greenirishman on 2012-11-29
> **dannyboy79 said:**
> run openvpn on the server and samba
Do you have a link to any tutorials on that?

---

### Post by TheFu on 2012-11-29
Using samba without a VPN is just asking for security failures.  Hopefully the ISP would block those ports to protect you from yourself.

OpenVPN is probably the best solution, but setup is non-trivial. The server AND client-side setups can become complex. Do you really want to manage certs for every client and get hassled when their iphone can't access the files?

Using WinSCP is probably the best answer for your end-users. Tell them it is much more secure than other alternatives, which is 100% true.  Any client that uses ssh, scp and/or sftp can be used.

Someone might suggest WebDAV as another alternative. This is a security breach just waiting to happen as well, like Samba over the internet.

As to tutorials, google is your friend, but you might want to start at howtoforge.com to setup samba first, get that working on the LAN (**never over the WAN**), then find an openvpn howto there.  This is not a point-n-click solution, especially if you want it to be secure too.  Just be aware that I haven't had to setup samba in many years, it sorta just works and migrating a /etc/samba/smb.conf file for the last decade with just a few tweaks is all that I've done.

help.ubuntu.com has good how-to guides as well.

BTW, I only allow key-based ssh access to my company network, so I know this ssh-only policy can work. There are ssh-clients for almost every OS out there.

You didn't ask about integration with ActiveDirectory or LDAP. Does that interest you? That can complicate samba authentication beyond what most self-taught Linux admins are ready to conquer.

Good luck and you were smart to ask for help here before trying to solve this yourself.

---

### Post by Greenirishman on 2012-11-29
> **TheFu said:**
> Using samba without a VPN is just asking for security failures.  Hopefully the ISP would block those ports to protect you from yourself.

OpenVPN is probably the best solution, but setup is non-trivial. The server AND client-side setups can become complex. Do you really want to manage certs for every client and get hassled when their iphone can't access the files?

Using WinSCP is probably the best answer for your end-users. Tell them it is much more secure than other alternatives, which is 100% true.  Any client that uses ssh, scp and/or sftp can be used.

Someone might suggest WebDAV as another alternative. This is a security breach just waiting to happen as well, like Samba over the internet.

As to tutorials, google is your friend, but you might want to start at howtoforge.com to setup samba first, get that working on the LAN (**never over the WAN**), then find an openvpn howto there.  This is not a point-n-click solution, especially if you want it to be secure too.  Just be aware that I haven't had to setup samba in many years, it sorta just works and migrating a /etc/samba/smb.conf file for the last decade with just a few tweaks is all that I've done.

help.ubuntu.com has good how-to guides as well.

BTW, I only allow key-based ssh access to my company network, so I know this ssh-only policy can work. There are ssh-clients for almost every OS out there.

You didn't ask about integration with ActiveDirectory or LDAP. Does that interest you? That can complicate samba authentication beyond what most self-taught Linux admins are ready to conquer.

Good luck and you were smart to ask for help here before trying to solve this yourself.

Thankyou for your input. I have decided to use ssh access only as we need the best security option possible as our data is financially sensitive. If my boss decides he wants something easier or more familiar to a mounted drive then I will just look into purchasing other server software. Thanks again.

---

### Post by lykwydchykyn on 2012-11-29
> **Greenirishman said:**
> This works really well! 
Now this works just fine for me but I have some technologically impaired coworkers who are used to a cloud storage mounted drive on their computers. Is there anyway to mount shared directory or the server hardrive to the windows clients?

With the disclaimer that I've never actually used any of them and can't vouch for them, there are products that will let you map a drive using SFTP.

See this page for some options:

[http://superuser.com/questions/66470/mapping-an-sftp-connection-to-a-windows-drive](http://superuser.com/questions/66470/mapping-an-sftp-connection-to-a-windows-drive)

If you want to do something more hip and trendy, maybe look into owncloud, which will give you your own Dropbox-esque service.

---

### Post by dannyboy79 on 2012-11-29
openvpn setup guide: [http://askubuntu.com/questions/104834/set-up-a-vpn-route-samba-over-it](http://askubuntu.com/questions/104834/set-up-a-vpn-route-samba-over-it)

---

### Post by Greenirishman on 2012-11-29
> **lykwydchykyn said:**
> With the disclaimer that I've never actually used any of them and can't vouch for them, there are products that will let you map a drive using SFTP.

See this page for some options:

[http://superuser.com/questions/66470/mapping-an-sftp-connection-to-a-windows-drive](http://superuser.com/questions/66470/mapping-an-sftp-connection-to-a-windows-drive)

If you want to do something more hip and trendy, maybe look into owncloud, which will give you your own Dropbox-esque service.

thanks this is a great solution I will look into. ExpandDrive seems to be the best program so far....

---

### Post by TheFu on 2012-11-29
> **Greenirishman said:**
> Thankyou for your input. I have decided to use ssh access only as we need the best security option possible as our data is financially sensitive. If my boss decides he wants something easier or more familiar to a mounted drive then I will just look into purchasing other server software. Thanks again.

Be certain to lock down the ssh access appropriately.  There are many ssh-security guides out there.  Here's mine: [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)

Leaving ssh as the default installs it is asking for trouble over time.

I do not believe there is any more secure, yet fairly simple, method for remote access than ssh/scp/sftp, so you've already started with the best answer, overall.  Any other solution should really begin with installing OpenVPN or an IPSec-based VPN.  Whatever you do, avoid PPTP and lighter VPNs.

---

