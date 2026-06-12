---
title: "How to connect Ubuntu and Windows 98?"
date: 2005-12-09
forum: Networking &amp; Wireless
---

### Post by samoth on 2005-12-09
My office is using Windows 98 as a server running through a hub connected to 4 PCs using Windows XP. So I got this new PC, I figured I wanted to try using linux on my PC. I installed Ubuntu 5.10 flawlessly, everything is good except for the networking part. I cannot connect to the office server. I checked the network card using mii-tool command, and it said that the link is OK. That means I am connected to the hub. However, this linux pc is not assigned an IP Address, which on my other PCs I usually ticked the "automatically assign IP Address" option, and they run fine. So I figured I'd choose the DHCP option in the "system - administration - networking" section instead of Static IP Address. It still won't work (still no IP Address). Then I looked at the smb.conf file and the workgroup written there was "MSHOME". Then I changed it to "PRIMA" since that's the workgroup my office is using. It still won't connect to the server. 

I admit that I'm a newbie to this Ubuntu, please please help me because I want to be able to use this OS and my plan for the future is to run Ubuntu on my Office PCs (because we are using pirated Windows right now except for the server).

thanks for the help

---

### Post by amohanty on 2005-12-09
Hubs _cannot_ assign IP addresses. I suggest that you spend some bucks and get a router so that you can work with _real_ ip addreses. The reason DHCP does not work is because it needs a DHCP server, which you dont have.

AFAIK the only thing you can try the following:

On any of the windows box:
Start->Run->cmd
in the terminal type ipconfig /all
get the highest IP address, the largest last 3 digits add 1 to it (as long as it is less than 255) and assign that as the static IP of your linux box and try again.

> (because we are using ....... Windows right now except for the server)

Please _never ever_ say that on a public forum, unless of course you are in India or China - and no its not racist. I am Indian, I do know how it goes.

HTH

---

