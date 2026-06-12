---
title: "Trouble Remote Accessing Windows XP"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by BJ_Covert_Action on 2009-07-18
Howdy Everyone,

I am trying to remote login to a Windows XP laptop from my Ubuntu PC (version 8.04) so that I can take some of the pictures off the laptop before wiping it (yes, I am so old that I don't have a USB stick greater than 256 Mb, get off my lawn). Right now, I have both computers connected to my router. My Ubuntu box is wirelessly connected with a static IP and the laptop is hardwired to the router with an auto-assigned IP address. I can see both boxes connected to my LAN when I log into my router. 

I have enabled remote assistance login in the windows laptop. It does not, however, appear to have the option for Remote Desktop (it's old). I also opened up port 5900 for UDP and TCP and I checked to ensure that port 3389 was enabled to allow TCP connection for the Remote Assistance program. 

The laptop has two user accounts: Owner, with no password, and Account2 with limited user access and a password.

I am trying to connect to the laptop either through Terminal Server Client, or through Gnome-RDP.

The settings I have been putting in for the connection are as follows:
Computer: 192.xxx.x.xxx <--- the IP of the laptop as given by my router
Protocol: RDP
Username: Owner
Password:  ____   <--- blank since the account has no password
Domain: ____ <--- blank
Client Hostname: _____ <---- blank
Protocol File: _____   <---- blank

So far as I can tell from reading [this thread](http://ubuntuforums.org/showthread.php?t=327984) and [this abstract](http://ubuntu-unleashed.com/2008/05/howto-login-to-windows-nt2000xp-remote-desktop-within-ubuntu-linux.html), I am setting everything up right. Yet, when I click connect, I am getting an immediate error which tells me the connection was refused. 

I was wondering if, perhaps, my router is blocking the connection. Do I need to add the router IP as a domain or host in the connection settings? Or maybe there is some value that I am supposed to put in the password field for connecting to an account without a password? Also, I am logged in, manually, to the Owner account on the laptop. Do I need to log out in order to connect remotely? If so, how do I ensure that the laptop stays connected to the router (it drops off the client's list once I log out).

Can anyone think of anything else that might help me troubleshoot this?

Thanks in advance for input guys and let me know if you need anything else (some kind of log output for example).

I am hoping to network a few more computers within my condo so remote logins are going to be essential for me in the future, any information you guys can give me on this topic would also be helpful.

Cheers,
Brady

---

### Post by BJ_Covert_Action on 2009-07-19
24 Hour Bump

---

### Post by moe19790 on 2009-07-19
> **BJ_Covert_Action said:**
> 

I am hoping to network a few more computers within my condo so remote logins are going to be essential for me in the future, any information you guys can give me on this topic would also be helpful.



have you considered using VNC? it will do the job for remote access!

---

### Post by BJ_Covert_Action on 2009-07-20
Uuuum, I have heard VNC mentioned, and it is on my to-do list of things to learn about. But as I have not yet had a need for it (that I know of) I haven't started trying to implement it. Perhaps now would be a good time for that....

---

