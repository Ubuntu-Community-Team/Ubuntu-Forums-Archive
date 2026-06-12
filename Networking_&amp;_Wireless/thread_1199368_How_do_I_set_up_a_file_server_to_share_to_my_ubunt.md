---
title: "How do I set up a file server to share to my ubuntu laptop?"
date: 2009-06-28
forum: Networking &amp; Wireless
---

### Post by cody7002002 on 2009-06-28
My desktop runs windows vista and I'd like to make it so that I can access the files on my desktop remotely from my laptop that is running ubuntu. What programs do I need to download for this? Can anyone recommend a good tutorial?

---

### Post by Boondoklife on 2009-06-28
Well if you are talking about on the same network then samba it is, If you are trying to do it remotely then you could check out one of the many ftp apps out there or try to setup a vpn so you can still access your windows shares.

---

### Post by philcamlin on 2009-06-28
hi

try this 

[http://www.cyberciti.biz/faq/ubuntu-linux-openssh-server-installation-and-configuration/](http://www.cyberciti.biz/faq/ubuntu-linux-openssh-server-installation-and-configuration/)

if you need more help just ask :popcorn:

or you could try apache as a web file server 

sudo apt-get install apache2

---

### Post by cody7002002 on 2009-06-28
I mean on the same network. Just so I can transfer files between the computers in my home

---

### Post by philcamlin on 2009-06-28
samba is good for that :popcorn:

---

### Post by cody7002002 on 2009-06-28
could you elaborate? I'm wanting to use my desktop which is running vista as the server. What do I need to do desktop-side to enable this? I'm assuming samba is the ubuntu app I can use to access the server?

---

### Post by philcamlin on 2009-06-28
this sould help you out :)

[http://librenix.com/?inode=10453](http://librenix.com/?inode=10453)

---

### Post by Boondoklife on 2009-06-28
On the windows box simply right click and share files, make sure that you either make it readable/writeable to all or setup a user on the windoes box to match your ubuntu box.

Then on the laptop just browse network or try smb://windoesIP to browse the windoes shares.

---

### Post by alphacrucis2 on 2009-06-28
> **cody7002002 said:**
> could you elaborate? I'm wanting to use my desktop which is running vista as the server. What do I need to do desktop-side to enable this? I'm assuming samba is the ubuntu app I can use to access the server?

Just share a folder on your Windows machine using Windows Explorer. Right click on the folder you want to share and select share from the list. Then specify the permissions. You may have to enable file and print sharing on Vista if you haven't done that already. On Ubuntu just select Places --> Connect to Server and select Windows share as the service type. You then enter the ip address (or a name if that will resolve) of the server. You will also need to tell it a usercode and password that Vista will accept.

---

### Post by dmizer on 2009-06-28
> **alphacrucis2 said:**
> Just share a folder on your Windows machine using Windows Explorer. Right click on the folder you want to share and select share from the list. Then specify the permissions. You may have to enable file and print sharing on Vista if you haven't done that already. On Ubuntu just select Places --> Connect to Server and select Windows share as the service type. You then enter the ip address (or a name if that will resolve) of the server. You will also need to tell it a usercode and password that Vista will accept.

In addition to that, you may want to take a look here too: [http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877)

---

### Post by cody7002002 on 2009-06-28
> **alphacrucis2 said:**
> Just share a folder on your Windows machine using Windows Explorer. Right click on the folder you want to share and select share from the list. Then specify the permissions. You may have to enable file and print sharing on Vista if you haven't done that already. On Ubuntu just select Places --> Connect to Server and select Windows share as the service type. You then enter the ip address (or a name if that will resolve) of the server. You will also need to tell it a usercode and password that Vista will accept.

Ok so I think i'm missing a step here. My ubuntu laptop is not already in my network i guess? When I got to a folder and click share it asks me to pick users to share with. It then shows the user profiles of the accounts that are set up on this windows computer. How can I connect the laptop?

---

### Post by alphacrucis2 on 2009-06-28
> **cody7002002 said:**
> Ok so I think i'm missing a step here. My ubuntu laptop is not already in my network i guess? When I got to a folder and click share it asks me to pick users to share with. It then shows the user profiles of the accounts that are set up on this windows computer. How can I connect the laptop?

You could add a new user to Vista which would be used only by Ubuntu but you don't need to do that unless there is a particular reason. When you tell Ubuntu to connect to the share, just type in any existing Vista account (usercode and password) that you have given the appropriate permissions to access the share you created on Vista.

---

### Post by cody7002002 on 2009-06-28
ok when I got to connect to server, in ubuntu. I choose windows share for service type correct? then in the server field I put the windows computer's ip address? Then it has fields for share, folder, user name, and domain name. What do I put in the share field? In the folder filed do i put the folder im wanting to share? and Username the vista username that the folder is on? What about domain name?

---

### Post by dmizer on 2009-06-28
> **cody7002002 said:**
> Ok so I think i'm missing a step here. My ubuntu laptop is not already in my network i guess? When I got to a folder and click share it asks me to pick users to share with. It then shows the user profiles of the accounts that are set up on this windows computer. How can I connect the laptop?

Perhaps this will help: [http://technet.microsoft.com/en-us/library/bb727037.aspx](http://technet.microsoft.com/en-us/library/bb727037.aspx)

---

### Post by alphacrucis2 on 2009-06-28
> **cody7002002 said:**
> ok when I got to connect to server, in ubuntu. I choose windows share for service type correct? then in the server field I put the windows computer's ip address? Then it has fields for share, folder, user name, and domain name. What do I put in the share field? In the folder filed do i put the folder im wanting to share? and Username the vista username that the folder is on? What about domain name?

The share name is whatever you told Vista to share the folder as. It usually defaults to the folder name. Domain name isn't needed unless you are running a Windows Domain (usually only done by corporate sites).

---

### Post by cody7002002 on 2009-06-28
This all seems to be much more trouble than it's worth X(

---

### Post by alphacrucis2 on 2009-06-28
> **cody7002002 said:**
> This all seems to be much more trouble than it's worth X(

How do you mean. It's no different to sharing folders between Windows PC's.

---

### Post by cody7002002 on 2009-06-28
but I've never done that either. I'm rather inexperienced with networking and such

---

### Post by cody7002002 on 2009-06-29
I just installed and configured samba using a tutorial I found online. After doing this I went to the network section under the places tab and connected to Windows Network, Then Workgroup, then server, then Myshare I click on Myshare and there is nothing in this folder. Am I supposed to create a folder on my Windows Computer with files I want to share in it? I'm confused as to what i'm supposed to do next

---

### Post by dmizer on 2009-06-29
> **cody7002002 said:**
> Am I supposed to create a folder on my Windows Computer with files I want to share in it?

Yes, see this post: [http://ubuntuforums.org/showpost.php?p=7532614&postcount=14](http://ubuntuforums.org/showpost.php?p=7532614&postcount=14)

---

