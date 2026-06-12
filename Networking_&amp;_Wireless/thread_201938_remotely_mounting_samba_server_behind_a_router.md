---
title: "remotely mounting samba server behind a router"
date: 2006-06-22
forum: Networking &amp; Wireless
---

### Post by kbayly on 2006-06-22
I'm not really sure where to start with this one, but here it goes:

I have a samba server set up on my home network that i would like to access remotely from work. The server sits behind a d-link router, so I assume port forwarding would be involved. I have successfully set up port forwarding with SSH and VNC, but I can't seem to get Samba to work. 

I have a registered domain name mirrored with dyndns. My router currently has ports 137-139, and 445 forwarded to my server, in hopes that these would be the correct ports for Samba, but I'm not sure if this is correct.

is there some setting for remote access that i may have overlooked in smb.conf?

Despite tinkering with it for days on end, i have had no success. Everything works fine on my LAN, but remote access to my samba server just doesnt seem to work. i would like to mount the samba shares with both windows and osx.

any help would be much appreciated!

---

### Post by jferrando on 2006-06-22
For me, a very good alternative is using "openvpn". You should set up openvpn server at home, then setup certificates and use an vnc client on your linux or windows cliente at work. Openvpn can be setup to use only port udp/1194, an can traverse firewalls.

With this setup, you get a remote virtual ip at your work's client that has full access to your server. Also openvpn uses X.509 certificates, which makes it a very secure solution (samba does not encrypt traffic on the network, btw).
Hope you enjoy my suggestion.

---

### Post by jferrando on 2006-06-22
use an [COLOR="Red"]**vnc**[/COLOR] client on your linux or windows cliente at work

I meant "**[COLOR="Navy"]openvpn[/COLOR]**" client. Sorry.

---

### Post by nemesa on 2006-06-22
With hamachi you can read / write your samba shares through any router between your two computers...

You should read:
[http://ubuntuforums.org/showthread.php?t=135036&highlight=howto+hamachi](http://ubuntuforums.org/showthread.php?t=135036&highlight=howto+hamachi)

And:
[http://www.hamachi.cc](http://www.hamachi.cc)

---

### Post by kbayly on 2006-06-22
In a perfect world i would like to use Putty to securely tunnel my samba traffic. 

VPN may be a good alternative, however, how will setting up a VPN server give me access to files if i can't mount share folders remotely? I am not entirely clear on this concept.

Thanks for the help!

---

### Post by kbayly on 2006-06-23
After much tinkering, and extensive googling of the matter i was able to piece this one together from various sources. Adjustments need to be made on the router ports, putty settings, and windows host files (for osx you can do everything easily from the terminal).

This is a working method to remotely mount a samba share securely through ssh on a server behind a router...

1. Forward the necessary ports on your router to the ip address of your local machine. For ssh the port is 22. For samba the port is 139.

2. Properly configure your samba server and your ssh server settings on your local machine. There are plenty of tutorials out there for this, and remoting doesnt require any special configurations.

3. Get a static domain name from dyndns.org. This service synchs with your ISP's dynamic IP and updates as the IP changes.

4. **For WINDOWS**: Download Putty, an easy and powerful ssh client ([http://www.chiark.greenend.org.uk/~sgtatham/putty/)](http://www.chiark.greenend.org.uk/~sgtatham/putty/)). 

- create a new Putty session. the host name should the dyndns.org domain that you registered. name the session whatever you want. 

-tunnel your samba traffic. choose Connection > SSH > Tunnels. Check Local ports accept connections from other hosts. Check Remote ports do the same (SSH-2 Only). Source port is 139. destination is yourhostname:139 (whatever you registered with dyndns.org, followed by :139). Click "Local" and "Auto". Go back to Session and click "save"

-Connect to your machine through ssh/putty. 

*Now that you can ssh, here's the tricky stuff. *Since windows uses port 139 for windows file sharing, you need to disable this service. open a command prompt and type "net stop server". if you want to restart it later after you close your SSH tunnel, just type "net start server".

Next tricky part- you need to modify your "hosts" and "lmhosts.sam" file located in C:\WINDOWS\system32\drivers\etc.  

Open the C:\WINDOWS\system32\drivers\etc\windows\hosts file and add the line:

    * 127.0.0.1   localhost

Open the C:\WINDOWS\system32\drivers\etc\windows\lmhosts file and add the line:

    * 127.0.0.1   sambaserver

Alright, ssh to the server with Putty, and then mount your network drive like so:

Windows Explorer > Tools > Map Network Drive

\\127.0.0.1\sharedfolder

It's more convenient if you windows username and samba username are the same, otherwise you will need to choose the "log in as different user" option.

Give it a second, and the drive should map! you need to map a drive for each sharedfolder you have on your samba server.

**FOR MAC OSX**:

This is MUCH simpler. 

open a terminal and type:

ssh -L 139:localhostip:139 dyndns.orghostname -l username

the local host ip is whatever local IP you forwarded ports 22 and 139 to. The dyndns.orghostname is whatever domain name you got from dyndns.org. username is whatever your username is on the samba server.

for example:

ssh -L 139:192.168.0.13:139 joesmith.dyndns.org -l jsmith

oh yeah, to open ports you need to have root priveledges, so either login as root with su, or preface the command with sudo.

then mount your drive- 
Finder > Go > Connect to Server

Server address - smb://127.0.0.1/sharedfolder

you should be ready to rock!

---

### Post by airtonix on 2006-07-13
nemesa : mate hamachi is great and easy and all, but i dont trust a so called secure client that requiresa thrid party to mediate the connection.....sounds like an elaborate phishing scam to me.

Besides, openvpn is showing itself to be doing a better job.

---

