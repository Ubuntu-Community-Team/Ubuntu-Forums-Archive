---
title: "Block access to all IP's except two.. 10.04?"
date: 2012-05-11
forum: Networking &amp; Wireless
---

### Post by K34nu on 2012-05-11
Hi there,

I've recently purchased a VPS and installed Ubuntu 10.04. I was wondering if it is possible to block out every IP except from two (Mine and a friends) from having access to it / the SQL database on it...

Basically what I want to do is run a SQL database that only a few users can connect to if I have a copy of their IP. I've read up on it via google but i'm still not all too sure on what i'm doing and I don't want to completely block access for myself so I thought I would query it first. Reason i'm not sure is because i've seen several different ways of doing it.. Whether its IPTables, UFW, apparmor, VPN, DenyHosts, etc.. I'm Really not sure.. I basically want to make the VPS securer than a nun wearing a chastity belt :lolflag:... I want to block off HTTP/HTTPS, FTP/SFTP and all the others except SSH and SQL..

I'm going to be reading up on how to make the SSH into sSSH (I think thats what its called..) aswell along with a secure way of SQL as well. Just really want to block off ALL access to it unless I allow their IP address in something or MAC Address.

Thanks for reading and I hope for a quick reply! =D
-Keanu

Oh! p.s. I would also like to know what the best O/S for running MySQL on is? I've got access to; CentOS 5 32/64, CentOS 6 32/64, Debian 6 32/64, Fendora 16 32/64, Scientific 6 32/64 (Never heard of that one before!), Ubuntu 10.04 32/64 and finally Ubuntu 11.10 32/64? Which one runs with the least RAM load along with running MySQL with the least RAM Load? - (This is a PS, so if it doesn't get answerd then i'ts no biggie just wondering really)

THANKS! =D

P.s.s. Only really have access via SSH and would like to try to keep it that way.. So if you could make any commands / something to do terminal friendly that would be GREATLY appreciated.. (I can kinda translate between GUI / Terminal just don't want to have to install a GUI because I won't ever use it.)

> 
[http://1000umbrellas.com/2010/04/29/how-to-set-up-the-firewall-using-ufw-on-ubuntu-lucid-lynx-server](http://1000umbrellas.com/2010/04/29/how-to-set-up-the-firewall-using-ufw-on-ubuntu-lucid-lynx-server) - How to set up the firewall using UFW 
[http://www.basicconfig.com/security/setup_firewall_ubuntu_using_ufw](http://www.basicconfig.com/security/setup_firewall_ubuntu_using_ufw) - Setup firewall Ubuntu using UFW
[http://guides.webbynode.com/articles/security/ubuntu-ufw.html](http://guides.webbynode.com/articles/security/ubuntu-ufw.html) - Another setup guide
[http://www.andrewault.net/2010/05/17/securing-an-ubuntu-server/](http://www.andrewault.net/2010/05/17/securing-an-ubuntu-server/) - Liked this one, indepth.
[https://help.ubuntu.com/community/UFW#Introduction](https://help.ubuntu.com/community/UFW#Introduction) - Just a quick look at UFW along with a few helpful commands
[http://www.zimbio.com/Ubuntu+Linux/articles/SJz1F33UolY/Tutorial+How+Install+Configure+Uncomplicated](http://www.zimbio.com/Ubuntu+Linux/articles/SJz1F33UolY/Tutorial+How+Install+Configure+Uncomplicated) - Got sent this by my host.

(Several different ways to set up UFW and secure Ubuntu!

---

### Post by kd5vdo on 2012-05-12
Howdy, I have tackled this issue myself a few times. If you are like most people, you have a dynamic IP address and it will be fairly difficult to block all but two IP addresses and still allow yourself and your friend if your IP addresses change. One solution to this is to set up a VPN and open ports you need only for IP addresses on the VPN. If this is not practical, the best I can think of is just blocking access to all but the essential services and changing the ports they operate on.
Assuming you and your friend have static IP's, I recommend using UFW. Here are the commands you would need to run:
```
sudo ufw allow from <ip of you or your friend> to tcp port 22
```
to allow SSH and
```
sudo ufw allow from <up of you or your friend> to tcp port 3306
```
to allow MySQL.
You can check the Ubuntu Wiki, Server Documentation or [https://debdistrosdoneright.com/16-networking/7-ubuntu-firewall]("https://debdistrosdoneright.com/16-networking/7-ubuntu-firewall") for more on UFW.
As far as your operating system question, I have tried CentOS and Ubuntu. CentOS is great for certain things, it has an "it just works" quality when setting it up to do only one task. I found it very difficult to repurpose though if I wanted to use it for something else. I personally prefer Ubuntu because of the package management and the ease I had in changing what tasks I had it do, but it is a matter of personal preference really.

The more I think about it, the better OpenVPN seems to be for this job. Set up a VPN following the excellent guide in the Ubuntu server manual, but, in the server.conf file, uncomment ```
client-config-dir ccd
```

You can then make a directory /etc/openvpn/ccd, and place in there configuration files using the CN of each of your clients as a file name. Inside the file just put one line specifying the IP address of the client, e.g. ```
ifconfig-push 10.8.0.14 10.8.0.13
```

Let me know if this works out for you or if you need any more information.

---

### Post by K34nu on 2012-05-13
Hi kd5vdo,

Thanks for your quick reply. I took a look at the OpenVPN however i'm currently running a windows partition. I've got the server running: "Ubuntu 10.04 LTS 64bit" but it seems that you need a linux O/S to connect to it? I'm not all too sure, I ran through a guide on how to set it up and everything which went fairly smoothly. If anyone wants to take a look at the guide, its located here: 
> [http://www.linuxlog.org/?p=81](http://www.linuxlog.org/?p=81)

So i'm now taking a look at the IPTables way and i've encountered a problem... I installed a fresh copy of ubuntu 10.04 onto the VPS and typed this:
> 
sudo apt-get update
sudo apt-get install ufw
sudo ufw allow from MYIP to tcp port 22 - I then get;
ERROR: 'Bad destination address'

If you could shed any light onto my situation it would be greatly appreciated. I only really want to allow access fully to my IP address, then SQL access to several others and completely block the rest unless I put them into the iptables? - If someone has a Static IP address, couldn't you just put their MAC address? (Haven't searched that yet, just thought of it now)

//=================================================================================================

I'm also getting the error: ERROR: problem running ufw-init
when I try sudo ufw enable

//==================================================================================================

Okay, somehow i've managed to get UFW working! Yay! When I type UFW status I get this:

> 
root@serv:/etc/ufw# ufw status
Status: active

To                         Action      From
--                         ------      ----
Anywhere                   ALLOW       MYIP
Anywhere                   ALLOW       127.0.0.1 (Had to do this so that it would allow downloading of apps via apt-get I believe???)


I'm now just wondering how i'd block ALL other inbound connections.. Like 

> ufw allow deny from * but that doesn't work... So is there any other command I can use LIKE that?

> 
[http://www.lokkju.com/blog/archives/150/comment-page-1#comment-84618](http://www.lokkju.com/blog/archives/150/comment-page-1#comment-84618)
[http://savvyadmin.com/ubuntus-ufw/](http://savvyadmin.com/ubuntus-ufw/) (Two websites I used when trying to get UFW working, ignore my comment on lokkju because I got it working, but it STILL displays that error???)

Thanks in advance!
-Keanu

---

### Post by kd5vdo on 2012-05-13
Looks like I made a mistake in my code there, sorry. It should be ```
sudo ufw allow from <your IP> to any port 22 proto tcp
```

Also, UFW has defaults set in the /etc/ufw/before.rules file which already make sure everything on 127.0.0.1 is allowed, so there is no need for that rule, although I doubt it will hurt to include it. Also, by default, UFW blocks all inbound connections, so no need to block everything else.

As far as OpenVPN on windows, you can download and install OpenVPN from their website here: [http://swupdate.openvpn.org/community/releases/openvpn-2.2.2-install.exe]("http://swupdate.openvpn.org/community/releases/openvpn-2.2.2-install.exe"). To set up an OpenVPN connection on Windows, I recommend starting from scratch:
```
sudo apt-get purge openvpn && sudo apt-get autoremove && sudo rm -rf /etc/openvpn/
```

Be aware that this command will remove OpenVPN and its configuration folder, so use it with care. Once it's removed, try following these directions from the official Ubuntu documentation: [https://help.ubuntu.com/12.04/serverguide/openvpn.html]("https://help.ubuntu.com/12.04/serverguide/openvpn.html")
The directions may seem convoluted, but if you follow them step by step, you will have a nice working setup.

At the bottom of that guide it explains how to set up a Windows client with a configuration file. You might have to delete these two lines from the config file: ```
auth-user-pass
auth-retry interact
``` Place that configuration file, your client key, client certificate, and server certificate (probably ca.crt) in the same folder, right click on the configuration file and select the option that is along the lines of "Run OpenVPN on this file." One heads up, to get OpenVPN running on Windows, you will need to edit preferences of the OpenVPN binary to allow it to run as an administrator. I'm not too familiar with Windows, so I can't offer specifics on how to do that.

Assuming you didn't change the VPN subnet or port and protocol from the defaults when setting it up, the only rules you will need to add to UFW are:

```
sudo ufw allow 1194/udp
sudo ufw allow from 10.8.0.0/24 to any port 22 proto tcp
sudo ufw allow from 10.8.0.0/24 to any port 3306 proto tcp
```

This will allow SSH and MySQL from anyone on your VPN, and attempts to connect to your VPN from anyone. Assuming you are using the authentication method provided in the Server Guide, this should be very safe. Also, until you have tested this setup to make sure it works, maybe allow SSH so that you don't lock yourself out:
```
sudo ufw allow 22/tcp
```

Your error starting UFW sounds like there is an error in one of the files in /etc/ufw. Maybe try purging and reinstalling UFW if it still doesn't work. Even though it appears to be working, from my experience, when you see that ufw-init error, your firewall is not properly configured.

Hope this helps!

---

### Post by K34nu on 2012-05-14
Thank you very much for your quick reply! =D I think im going to stick with the UFW route because I may need to allow other users to access the SQL at a later date which would cause hastle installing OpenVZ on their PC's. The command you posted at the top worked =D However I am still having a few problems connecting to my SQL database With UFW enabled. (I've set it up so it allows remote access) this is my current "verbose" readout;

> 
3306/tcp                   ALLOW IN    my ip
Anywhere                   ALLOW IN    my ip
22/tcp                     ALLOW IN    my ip
3306/udp                   ALLOW IN    my ip <-- Thought not having udp enabled might of been the problem.

Still happens if I type "ufw allow mysql".. Can only access it remotely if the UFW is disabled. 

Also when I type "sudo apt-get upgrade" it says "Failure to resolve" unless I turn off UFW?... (If its any help, I did follow this guide to set it up:

> [http://guides.webbynode.com/articles/security/ubuntu-ufw.html](http://guides.webbynode.com/articles/security/ubuntu-ufw.html)

and it states

> $ ufw default deny
Default policy changed to 'deny'
(be sure to update your rules accordingly)

But because I re-enabled it with "myip to 3306" and also "ufw enable mysql" it should be working?... 

Apart from that, I can access the SSH and everything which works well! :D This should be the last thing on the list! :P

Thank you very much for all the help so far! (I will be posting all links I used that possibly helped me in any single way on the first post of this thread)
-Keanu

---

### Post by K34nu on 2012-05-20
Bump?... Anyone?...

---

### Post by kd5vdo on 2012-06-14
As far as I can tell, everything looks fine, but I'm no expert here. UFW logs to /var/log/syslog, I believe, so try to access mysql from your machine, and then try ```
cat /var/log/syslog | grep UFW
```

That should give you an idea of whether UFW is blocking access, and, if it is, it might give a hint what rule is blocking it.

Also, try ```
sudo dpkg-reconfigure mysql-server
``` If I remember correctly, there is an option when you do that to enable remote access to the database. I may be wrong on that though.

Let me know if this helps any. Sorry I disappeared for a month.

---

