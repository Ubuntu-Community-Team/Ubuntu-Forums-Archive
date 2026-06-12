---
title: "Samba server problem"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by lidra on 2009-09-01
Hi All, 

I hope  you can give me a hand with my Samba installation. 
I have used samba server for a couple of weeks without issues. Sharing a folder would instantly be accessible from Windows or Ubuntu. Last week after doing some cleaning (remove VMware server at somt point) Samba stopped to work. 

I cant access any of my share or browse the available share over network. 
The behaviour I am getting is that if I try to map or browse from Windows I get the following message: The specified network name is no longer available. 
If I try from Ubuntu (same box as the Samba server) using Places \ Network, I can see my Ubuntu server there, when I double click I get : Unable to mount location  (this is on the server name). 
If I try to do smb://server/share_name, I get a login prompt, but whatever user/password I use, I am still asked for password. 
If I close the window, I get Access was denied. 

I tried and removed all the Samba related packages, and reinstall them. No luck, same behaviour. 
I tried diffrent smb.conf options from numerous HOW TOO, but same behaviour over and over again. 

At this point the only thing I see in the syslog is this:

Sep  1 23:29:10 Lidrux kernel: [ 2348.363722] gvfsd-smb-brows[5260]: segfault at 7f138e4d74d8 ip 00007f138ecdf0ee sp 00007f138e4d74e0 error 7 in libnss_files-2.9.so[7f138ecda000+c000]

From what I seen it happens when I try to loggin from network. 
Nothing gets logged in /var/log/samba that is usable. 

The way I share folders using Nautilus  is right click on the folder Sharing Options and then I select the 3 options: Share this folder with Share name, Allow other people to write in this folder and Guest access (for people without a user account). 

System details: 

Ubuntu version 9.04
Samba 2:3.3.2-1ubuntu3.1 
testparm as below:
:/var/log/samba$ sudo testparm /etc/samba/smb.conf
[sudo] password for user: 
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    passdb backend = tdbsam
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

Any help would be really apreciated. 
Please be kind, I am new to Ubuntu. 

Regards, 

Lidra

---

### Post by lidra on 2009-09-01
bump. 

Just an update, I dont necessary want to find what is wrong, any idea how to completely remove Samba and all the configuration files that might be implicated. 

I already tried to remove Samba, and also created clean smb.conf. 

Any idea would do. 

Cheers, 

Lidra

---

### Post by lidra on 2009-09-03
bump

---

### Post by superprash2003 on 2009-09-04
when you do smb://server/share_name , do you use server hostname or server ip?

---

### Post by lidra on 2009-09-04
> **superprash2003 said:**
> when you do smb://server/share_name , do you use server hostname or server ip?

Both. Also the Samba server has static IP. 

I tried to remove samba and related packages completly (including configuration files) , rebooted and then installed again. Same behaviour. I begin to believe it is kernel related (see the errors above). 

I am at the point of giving up and reinstall ubuntu from scratches, even I hate doing M$ behavior. But on the other hand this samba server holds all my media center content, so my HTPC is not happy.

I will post my kernel version in a bit.  

Lidra

---

### Post by bregale on 2009-09-04
i have the similar problem that i cannot share files from my samba system the only way i can see the files on my network is if i disable my firewall then i can see the files even on windus.:D

---

### Post by lidra on 2009-09-04
> **bregale said:**
> i have the similar problem that i cannot share files from my samba system the only way i can see the files on my network is if i disable my firewall then i can see the files even on windus.:D

First when I read your post I was about to respond that its not my case, but then I thought lets test a little. 

So imagine my surprise when I try to mount locally (fstab cifs mount) using the 127 address and the public ip address and the mount  works. 

I jumped and tested mount from another linux box (a server) in the network (using fstab cifs mount) using the ip address and it woks. 

So now I am more confuse as before, as trying to access the local share from Nautilus is not working, trying to access the share (both name or ip) from Windows is not working.

Also smb://ip_address/Share in Nautilus is not working (asking for user name and password, and if i use the same credentials that I use when I mount them in fstab is asking for password again). 

On Windows if I go \\IP_ADDRESS\Share  I get "\\ip\share is not accessible. You might not have permision to use this network resource. Contact your administrator bla bla. The specific network name is no longer available." 

If I try to map the share as a network drive, using \\ip_address\Share , then using different username I get: The specific network name is no longer available. 

The above windows behaviour happens both on Vista and windows 2003. 

So what firewall are you talking about ? 

Cheers, 

Lidra

---

### Post by lidra on 2009-09-05
bump

---

### Post by lidra on 2009-09-07
bump

---

### Post by Iowan on 2009-09-07
> **lidra said:**
> So what firewall are you talking about ? Firestarter or UFW?

---

### Post by jward3010 on 2009-09-07
1. Firstly what happens when you ping the hostname of your Buntu box, not the IP.

2. Have you changed anything on your router / DSL modem recently.

3. When you say you removed VMWare, do you mean off your Ubuntu machine?

> **lidra said:**
> So imagine my surprise when I try to mount locally (fstab cifs mount) using the 127 address and the public ip address and the mount  works.
How do you mean you used a public IP address? 

> **lidra said:**
> I jumped and tested mount from another linux box (a server) in the network (using fstab cifs mount) using the ip address and it woks.
Are you now saying the difference is that in this scenario you're using "mount" as opposed to whatever Nautilus uses, and it works?

> **lidra said:**
> On Windows if I go \\IP_ADDRESS\Share  I get "\\ip\share is not accessible. You might not have permision to use this network resource. Contact your administrator bla bla. The specific network name is no longer available."
When this happens, what happens if you try and ping that IP, is it accessible?

I'm going to start getting into silly questions about subnetting in a minute, so answer that stuff and see how we go!

---

### Post by lidra on 2009-09-07
> **jward3010 said:**
> 1. Firstly what happens when you ping the hostname of your buntu box, not the ip.

2. Have you changed anything on your router / dsl modem recently.

I dont know the answer to 1, I will post the answer as soon as I get home. 
For 2. No, I didn't change anything in the router lately. 

> **jward3010 said:**
> 
3. When you say you removed vmware, do you mean off your ubuntu machine?

Yes, my Ubuntu machine had VMware server 2 installed on it, and I noticed the samba issues hours after the VMware remove. It is true I did a number of other actions between VMware remove and seeing the issues, but the reason why I mention VMware is because I read someting about VMware providing some Samba modifications.
I dont know if it is related to VMware remove or not. 

> **jward3010 said:**
> 
how do you mean you used a public ip address? 

Sorry for the confusion on this one, I was trying to say the eth1 ip addres (I dont use eth0, I can move the network cable so I use eth0, but at the moment the network traffic for Ubuntu server goes eth1). So to be clear, I am talking only inside my network, I am not trying to acccess anything from outside my network. I am not aware of any firewall on Windows (disabled) or on Ubuntu (it might be one ....please let me know how I can check). 

> **jward3010 said:**
> 
are you now saying the difference is that in this scenario you're using "mount" as opposed to whatever nautilus uses, and it works?


Yes, this is true. At the moment if I use fstab mount + mount -a, I can successfully access the share both from local Ubuntu and also from another Linux box (CentOS) in the same network. 

What I cant do at the moment (and it is what I am after) is to access the share from Windows boxes (I have XP, Vista and 2003 available in the same network and all behave the same way) 

> **jward3010 said:**
> 
when this happens, what happens if you try and ping that ip, is it accessible?


The ping to ip address of the Ubuntu box works (aka ping 192.168.1.100). Also Ubuntu box has static IP address. 

> **jward3010 said:**
> 
i'm going to start getting into silly questions about subnetting in a minute, so answer that stuff and see how we go!
[/quote]
Before you do that, this whole story happens in one network, 192.168.1.x . Windows boxes have DHCP IP addresses and the linux boxes have statis IPs. 

Hope the above helps, the only thing I dont know at the moment what happens when you ping the host name. I can assume it works as I can see it in the network browse, but I never tried to ping it. I will update this post in 2 hours or so, when I get back from work.

Also I tried to share the path both by adding the smb.conf options, and also by using Nautilus. 

What confuses me, is where is Nautilus keepeing the configuration of the folders shared in network ? Because if I remove the part where I share the folders in smb.conf, and enable the share using right click on the folder name on Nautilus, it still works, but I cant see anything in smb.conf. So I am questing Nautilus is keeping samba configuration somewhere else. 

I think I mentioned before, I removed all Samba related packages with "remove configuration files" several times already. Including the package for Nautilus (I think it is call smb-nautilus or something). 

After remove, restart and apt-get update, I installed Samba packages again, and same behaviour as before. 

I think I will be left out of hair with this one. But I am not giving up just yet.

Cheers, 

Lidra

---

### Post by lidra on 2009-09-08
If I ping the name of the Ubuntu box from Windows, I get a reply from the IP address.

Cheers, 

Lidra

---

### Post by jward3010 on 2009-09-09
Thanks for all the info above you gave me back. Your network seems in good nick.

Have you posted your smb.conf yet, I can't remember back to the start of the post.

---

### Post by lidra on 2009-09-09
Hi jward3010, 

Thank you for your time. 
This is the actual conf at the moment:


root@Lidrux:~# testparm /etc/samba/smb.conf
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    passdb backend = tdbsam
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

---

### Post by lidra on 2009-09-09
As you can see there is nothing about the active share, but the mount below works on my linux box, but not on my windows:

//192.168.1.100/Movie on /home/lidra/Movie type cifs (rw,_netdev,username=xxxxx,password=xxxxxx,uid=1000,gid=100,rsize=8192,wsize=8192)

Cheers, 

Lidra

---

### Post by lidra on 2009-09-11
I would like to thank you all for your time. 
I have reinstalled Ubuntu and Samba is working flawlessly now. 

Cheers, 

Lidra

---

### Post by jward3010 on 2009-09-11
Just about to do the same thing myself, for completely different reasons.

Best of luck with the new setup.

---

