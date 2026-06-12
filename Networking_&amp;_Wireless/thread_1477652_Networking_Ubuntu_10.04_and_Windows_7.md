---
title: "Networking Ubuntu 10.04 and Windows 7"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by jediken21 on 2010-05-09
Hi, I'm trying to connect to my windows 7 computer via network from ubuntu 10.04. I get as far as this screen:

[IMG]http://img541.imageshack.us/i/screenshotbq.png[/IMG]

My problem is it always says I've entered the wrong password. I've tried the administrator account password and also the long windows 7 homegroup password. 

tl;dr: what kind of password is it looking for?

---

### Post by jediken21 on 2010-05-09
Cant get the screenshot to show for some reason.

---

### Post by peter72 on 2010-05-09
When you say you're trying to connect, do you mean by remote desktop or by a network share?

---

### Post by kapetanot on 2010-05-09
Hello to everybody
 
I have a desktop with windows 7 and laptop with edubuntu 10.04, booth computers work fine, and intrnet, but I can't get  them to connect in home network, so if anybody can help me how to establish a home network between them. I have a router Speedport W503V if that is of some use 
 
thank you

---

### Post by garvinrick4 on 2010-05-09
Have to make a Workgroup not a Home network, Homegroup network is between Windows 7 installs and Workgroup is in between All varietys of OS's. Need samba in Linux to set up
Workgroup with Windows. It will more or less do it itself, need to setup printer in workgroup also takes about a minute or two.

---

### Post by ltpg97 on 2012-03-29
The solution is quite simple. 

1. Change your Windows 7 workgroup name to something unique other than WORKGROUP and HOME. Otherwise sharing folders and files will not work.

2. Reboot the machine.

3. On your Ubuntu machine open Terminal and then type in the following command:
sudo gedit /ect/samba/smb.conf

4. Type in your password.

5. The smb.conf file will appear. Scroll down until you see workgroup = WORKGROUP.

6. Change WORKGROUP to the name you changed in Windows 7 and the click save. 

7. Now you should be able to access your shared folder and files.

----
Patrick
[http://www.homecomputerdoctor.org](http://www.homecomputerdoctor.org)

---

### Post by mws604 on 2012-03-31
--> Change your Windows 7 workgroup name to something unique other than WORKGROUP and HOME. Otherwise **sharing folders and files will not work.**

Why doesn't this work?  Big hassle if you have several PCs running Win7.

Also, is this the only way to connect or just the easiest way?

Thanks in advance for a response.

---

