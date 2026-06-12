---
title: "Network Manager is not running in 9.04"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by jaxxm on 2009-06-10
Hi all

I've been wondering if anyone can help with this. On my laptop I have upgraded to Ubuntu 9.04 over the weekend. Network Manager seemed to work fine over the weekend but on monday when i got to work it stopped. I cannot get Network Manager to run permanently. I seems to fall over after I start it. I run:

  sudo  /etc/init.d/NetworkManager status 

and get

  * NetworkManager is not running

I then run 

  sudo  /etc/init.d/NetworkManager start 

and the Network Manager starts up. It tells me it detected the network.

I then run immediately
  
  sudo  /etc/init.d/NetworkManager status

and get 
 
  * NetworkManager is not running.

I have reinstalled Network manager, and restarted the system. does the same. chkconfig --list NetworkManager shows it is on for runlevel 2345.

I don't have anything but lo in the /etc/network/interfaces file.

Can anybody help. Why is my NetworkManager not staying on.

thanks


update:

in a brief moment inbetween starting Network Manager and it shutting itself off i disabled the wireless connection. After this the Network Manager stayed running. I am investigating the possibility that my driver might be faulty or wrong. The wireless adapter I have installed is the Atheros AR242x. I have the madwifi-hal-0.10.5.6-r4031-20090529 driver. It used to work fine before the upgrade. will try to download again and reinstall.

---

### Post by superprash2003 on 2009-06-10
are you using wicd?

---

### Post by jaxxm on 2009-06-11
thanks for replying. No I don't. I will give it a try. Just strange that at home i can pickup the wifi of a neighbor but at work my wifi kills Network Manager. I have since tried to remove Madwifi and use ath5 for the driver, does the same thing. of course trying to trouble shoot a home is a pain cos it seems to work there. Network Manager does ask for my WPA password at home. Since i don't have a password for their network i just cancel. How can I remove the Password i have saved for work and reinsert?

---

### Post by firefold003 on 2009-06-11
Jaxxm, Do you have Fedora???
NetworkManager requires Fedora to have drivers for the wired and wireless interfaces on the computer.
 Many manufacturers of modems and wireless devices provide limited support for Linux. You may need to install additional drivers or firmware on your Fedora system in order to activate these interfaces. 

Please check that....


[Fire Fold]("http://www.firefold.com/Cat5E-Keystone-Jacks-C213.aspx")

---

### Post by jaxxm on 2009-06-11
I have Ubuntu 9.04. and wicd is worse. I cannot even get on the wired network with that one. will have to see if it works to download and install new madwifi drivers. Maybe there is a wireless driver corruption. mmmmmm frustrating.

---

### Post by jaxxm on 2009-06-23
got it!!!:D 

This morning i was doing my usual thing of starting up Netmanager with /etc/init.d/NetworkManager start, and I saw there was a folder called Network Manager under /etc/. In this folder is a file called nm-system-settings.conf. I opened the file 
 
$ sudo vim nm-system-settings.conf

and saw
  
$ managed=false

I changed it to 
  
$ managed=true

restarted network manager

$ sudo /etc/init.d/NetworkManager start

and it worked.

I'm not sure how this got changed but it seemed to work for me, so I hope it helps some one else.

---

### Post by jaxxm on 2009-08-27
sorry also not working. been too busy to check here. Seems no answer for me. It does work when i boot of the live cd.:confused:

any other ideas.???

---

### Post by jaxxm on 2009-08-27
I wish to humbly apologize to superprash2003.. wicd does work. as i thought a long time ago it must be network manager that does not work. for now i will use wicd. 

I think I must have been too stressed out to check it out properly.

thanks superprash2003. 

:redface:

---

