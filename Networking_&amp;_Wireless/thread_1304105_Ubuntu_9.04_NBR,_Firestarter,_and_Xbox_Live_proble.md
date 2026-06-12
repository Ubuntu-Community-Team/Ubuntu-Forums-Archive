---
title: "Ubuntu 9.04 NBR, Firestarter, and Xbox Live problems"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by indyjayess on 2009-10-28
Hi all, 

I am having some issues using my laptop to access Xbox Live through my 360. 

I have a Dell Mini 9, running Ubuntu 9.04 Netbook Remix. I installed Firestarter as well. I also have DHCP installed as well. I receive an error whenever trying to open Firestarter or start the firewall when I have checked the option to share connections. 

I have been soliciting help elsewhere, but we haven't been able to figure it out yet. I'll try to run down everything we've tried thus far.

Opening Firestarter gives me an error box that says an "unknown error has occurred" and asks me to check my settings/connections. Please see attached image titled "**error1**". This error does not present when "Enable internet connection sharing" is unticked in the options. 

Clicking out of that box shows Firestarter, as seen in attached image "**Firestarter2**". Eth0 is the connection to my Xbox by ethernet cable. It only shows any activity when I try to test my connection through the Xbox's console, and even then it only shows from 0.0 Kb/s to 0.2 Kb/s. Eth1 is my wireless connection. It was not under load in the screenshot, but it does show activity when it is. Pan0 is unknown, and I never see any activity on it, so I don't know what that does.

I used the "ifconfig" command to see the status of local device's IP. I then used the command 
```
sudo ifconfig eth0 192.168.5.1
```to establish an IP address for the local device. This was confirmed by "ifconfig" command. I then entered the Firestarter settings and established this range of IP addresses: 
Lowest: 192.168.5.2
Highest: 192.168.5.10


 This still gave me the unknown error. I also noticed that even after clicking "apply" if I went back into Firestarter's settings, they had reverted to the automatic setting.

I then checked my DHCP status via this command and this result:
```
nick@tiny-laptop:~$ sudo apt-get install dhcp3-server
[sudo] password for nick:
Reading package lists... Done
Building dependency tree
Reading state information... Done
dhcp3-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```I then tried restarting Firestarter via terminal with the following command and response:
```
sudo /etc/init.d/firestarter restart
 * Stopping the Firestarter firewall...                                            [ OK ]
 * Starting the Firestarter firewall...                                            [[COLOR=Red]fail[/COLOR]]
```
I am at a complete loss. Any advice would be greatly appreciated. I have Googled and searched and followed guide after guide, and cannot make any headway. It was so easy on my Vista laptop! :(

---

### Post by indyjayess on 2009-10-29
*bump*

No help? I even took screenshots and laid out every step I've taken.

---

