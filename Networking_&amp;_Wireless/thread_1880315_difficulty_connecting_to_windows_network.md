---
title: "difficulty connecting to windows network"
date: 2011-11-13
forum: Networking &amp; Wireless
---

### Post by Dave the Rave 4 on 2011-11-13
I am a new user just installed UBUNTU 11.10 so please be patient!
I have my computer up and running with ubuntu. I connect through a belkin router to the internet, That works fine.
When I browse my network (windows network called MSHOME running XP machines and a network attached drive) I get the message
"unable to mount location" Failed to retrieve list from server
 
I have installed samba
However when I use Google chrome and enter the IP address of the router or the network attached storage drive I can see them ok.
 
I want to look at and use files from the windows machines on the ubuntu computer.
 
Any help gratefully recieved
THe firewall on ubuntu is not enabled.
 
what info does anyone need to help me solve this problem?
 
Many thanks
 
Dave the Rave

---

### Post by 2F4U on 2011-11-13
Maybe firewall settings on the Windows machine? Can you ping from both Windows to Ubuntu and vice versa?

---

### Post by Dave the Rave 4 on 2011-11-13
Thanks for speedy reply.
I can ping from ubuntu machine to windows machines and vice versa.
I have turned off the firewall on my router. When I open the MSHOME network folder I can now see the individual machines but still get the error message "unable to mount location" failed to retreive share list from server. There are definitely some shared files on the windows machines.
Any further ideas?
thanks

---

### Post by simsym05 on 2011-11-13
> **Dave the Rave 4 said:**
> Thanks for speedy reply.
I can ping from ubuntu machine to windows machines and vice versa.
I have turned off the firewall on my router. When I open the MSHOME network folder I can now see the individual machines but still get the error message "unable to mount location" failed to retreive share list from server. There are definitely some shared files on the windows machines.
Any further ideas?
thanks
Goodevening Dave;

First, check your devices hostname (under ubuntu it is located n :  /etc/hosts or /etc/hostname and check if you don't have the same hostname, check you DNS and if it is routable in the router (sorry i can't help you because i use cisco routers)
Second, check Samba configuration,
Third, check the shared folder permission
fourth,  you have to check your IP Addresses if it is in the same network or if it is correctly routed (normally it is ok because you can pingbut better to check all again);

watng for your check

---

### Post by Dave the Rave 4 on 2011-11-14
Thanks you for taking time to reply.
I think I have found a work round
If I use nautilus to enter the IP  address, I can open the folder mount it and then bookmark for future use.
This isn't ideal but lets me have access to the windows share folders.
Will use it like this for the time being but curiosity will make me do the suggestions you have made!
Thank you again

---

### Post by capscrew on 2011-11-14
> **Dave the Rave 4 said:**
> Thanks you for taking time to reply.
I think I have found a work round
If I use nautilus to enter the IP  address, I can open the folder mount it and then bookmark for future use.
This isn't ideal but lets me have access to the windows share folders.
Will use it like this for the time being but curiosity will make me do the suggestions you have made!
Thank you again

See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1861985") and [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1879527") for the solution to browsing for network shares.

---

