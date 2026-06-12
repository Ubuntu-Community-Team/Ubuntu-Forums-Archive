---
title: "Help with Samba"
date: 2009-03-16
forum: Networking &amp; Wireless
---

### Post by null_x86 on 2009-03-16
Sorry if this is in the wrong spot, but i need help. Im trying to set up Samba on my Ubuntu 8.10 machine to do file and print sharing. I have tried using GADMIN-SAMBA and the System app Samba (System > Administration > Samba) and so far nothing has worked. I created users in Ubuntu and the conf file for samba, but when i try to connect to the shares from windows, it tells me that its not a valid hostname. I previously had samba working but it was just a basic few shares, and only one user. The way this one is setup is to allow multiple users, all wit their own share and all with a few common shares. The box has internet (im posting from it, and Transmission is working via WebUI/Clutch) so I know its not anything like an IP problem (speaking of, can someone show me the correct way of static ip setup in 8.10? ive tried to set it up and it keeps messing up my connection, disconnecting it; i might just have the order of the numbers backwards...). Anyone who can help me with this it would be greatly appreciated! Thanks In Advance!

---

### Post by warrend405 on 2009-03-16
There are several ways to set your ip address.

Go to system>network which will bring up a screen showing your connections.  Click on unlock and enter your password.  Enter the ip address you want (should look like 192.168.1.1), your subnet mask (usually 255.255.255.0) and your gateway address.  

If you want to try it manually you can go to a prompt and get into root (I use sudo -i) and go to /etc/network.  Open interfaces and you will see the interfaces on the computer.  Change the one you want to make static to ethx inet static.  On the next lines enter address xxx.xxx.xxx.xxx (correct address) then netmask 255.255.255.0 and gateway on their own lines.  

In either case restart the network or reboot to make sure it gets the right address.

---

### Post by null_x86 on 2009-03-16
> **warrend405 said:**
> There are several ways to set your ip address.

Go to system>network which will bring up a screen showing your connections.  Click on unlock and enter your password.  Enter the ip address you want (should look like 192.168.1.1), your subnet mask (usually 255.255.255.0) and your gateway address.  

If you want to try it manually you can go to a prompt and get into root (I use sudo -i) and go to /etc/network.  Open interfaces and you will see the interfaces on the computer.  Change the one you want to make static to ethx inet static.  On the next lines enter address xxx.xxx.xxx.xxx (correct address) then netmask 255.255.255.0 and gateway on their own lines.  

In either case restart the network or reboot to make sure it gets the right address.

can you give me a graphical idea of that? sorry im a bit of a noob with linux :P Any idea on how to get samba working?

---

