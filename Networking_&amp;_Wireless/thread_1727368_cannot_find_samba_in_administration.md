---
title: "cannot find samba in administration"
date: 2011-04-12
forum: Networking &amp; Wireless
---

### Post by vineeshvs on 2011-04-12
[FONT=Tahoma]installed samba by. but i cant find samba in system -> administration ?  Should I use ```
sudo apt-get install samba4
```? Thanks [/FONT] ):P

---

### Post by Morbius1 on 2011-04-12
You need the package: system-config-samba

And you [COLOR=Blue]do not[/COLOR] want to install Samba4.

---

### Post by vineeshvs on 2011-04-12
i installed GUI. thanks... one more doubt. can I use samba for conncting two computers using ubundu? or it is only for windows-ubundu connection? ):P

---

### Post by Morbius1 on 2011-04-12
You can use samba linux-linux, linux-osx, linux-unix, linux-windows, linux-whatever.

---

### Post by pricetech on 2011-04-12
but no need to.  You can connect your Linux boxen to one another using SSH.  Look for Places - Connect to Server.  Choose SSH for the Service Type.  Fill in the blanks for IP, Port, etc. and connect.

---

### Post by vineeshvs on 2011-04-12
thanks..  But connecting with using SSH gives me many errors like 'route not found'. Is there any other information other than IP address mandatory to be filled. (other inf are shown as optional, thats why). :p

---

### Post by vineeshvs on 2011-04-14
> On Computer A:
3. It is time to connect, and it is in the form
ssh <username>@<ip-address>
Code:

ssh john@192.168.1.17

just to mention: if you only have one computer but still want to learn, it it possible to issue a ssh connection to yourself, with openssh-server installed you just choose your own username as username and “localhost” as ip-address.

4. then you need accept the RSA fingerprint (just write yes, it only happens once for every connection) and write the password for the user.

that is it, you are connected.
 The error displayed is
> vs@vs-desktop:~$ ssh vineeth@192.168.1.2
The authenticity of host '192.168.1.2 (192.168.1.2)' can't be established.
RSA key fingerprint is f2:00:7d:1a:c3:ba:7c:ea:61:87:7b:82:bc:b4:09:87.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.1.2' (RSA) to the list of known hosts.
vineeth@192.168.1.2's password:
Permission denied, please try again.

what to do? i have entered the pasword of the computer which is to be connected to this computer. Help please

---

### Post by vineeshvs on 2011-04-14
hi guys anybody der for help?

---

### Post by vineeshvs on 2011-06-11
[FONT=Tahoma]I connected my lap and desktop using SSH.
steps:
1. set the lap ip 192.168.1.1
2. set desktop ip 192.168.1.2
3. lap username - vineesh, desktop user name - vs
do the following things in lap (or desktop)
1. places -> connect to server 
2. set 'service type' to 'SSH'
3. In the place of 'server' enter the ip of your desktop
4. in the place of 'username' enter the user name of your desktop
now you got connected.... dats it [/FONT]:D:popcorn:

---

### Post by Morbius1 on 2011-06-11
That's great !

Quick question. Do you trust the user on the laptop? 

He now has read / write / execute access to everything you do on the desktop machine. I guess it really doesn't matter. He's using your login password so he can always walk over to your machine while you're away and access things directly.

---

### Post by vineeshvs on 2011-06-11
we can use it at home only... :)

---

### Post by chinnappan on 2011-06-12
Hi, 

I have install samba with Windows ADS, its working fine,i want give the access through windows system on Linux folder.

what is the step to add the domain user on linux share folder from windows.

---

