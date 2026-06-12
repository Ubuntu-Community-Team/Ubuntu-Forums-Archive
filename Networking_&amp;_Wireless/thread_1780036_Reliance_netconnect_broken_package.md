---
title: "Reliance netconnect broken package"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by duffmckagan on 2011-06-11
I had installed the crossplatformui package provided by Reliance netconnect - ZTE modem, but now after installing it and removing it a couple of times, it has started giving me this error - 


> amitj@amitj:~$ sudo apt-get -f remove crossplatformui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  crossplatformui
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 176195 files and directories currently installed.)
Removing crossplatformui ...
ztemtvcdromd: no process found
dpkg: error processing crossplatformui (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 crossplatformui
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can somebody help me fix this? Its causing a lot of problems while installing other packages - turns out i don't need this no more as I figured out a way to configure the USB internet stick out of the box.

---

### Post by duffmckagan on 2011-06-11
As already mentioned above, I have configured ubuntu so that the reliance netconnect ZTE modem will run out of the box AND IT DOES!!

However, there is a slight problem. It takes a lot of time (at least 15 min) for the Reliance Connection menu to appear in the available networks. Is there any way to make my modem get detected right away?

So if I disconnect it for some reason or restart my computer, I have to wait for another 15 min till I can have internet running on the laptop.

Please help.

---

### Post by duffmckagan on 2011-06-15
Anybody facing a similar problem?

---

### Post by sampath sree on 2011-10-25
could anyone plz help me with how to remove crossplatformui which is installed by reliance modem..
its giving error

E: crossplatformui: subprocess installed post-removal script returned error exit status 1

i'm not able to install other packages.. :(

---

### Post by supraa on 2013-05-05
I am also facing the same problem..Reliance crossplatformui is killing me..anybody can solve my problem..now i connect reliance modem with help of ubuntu pre installed Network connection setup,it is working fine..

jeeva@jeeva-desktop:~$ sudo apt-get --purge remove crossplatformui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  crossplatformui
0 upgraded, 0 newly installed, 1 to remove and 12 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 253487 files and directories currently installed.)
Removing crossplatformui ...
ztemtvcdromd: no process found
dpkg: error processing crossplatformui (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 crossplatformui
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by supraa on 2013-05-11
hai... i have solved ''Reliance crossplatformui'' problem.. follow the following link 

[http://askubuntu.com/questions/136423/crossplatformui-error](http://askubuntu.com/questions/136423/crossplatformui-error)

---

