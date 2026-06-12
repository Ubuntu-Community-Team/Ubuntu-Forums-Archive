---
title: "Internet Connection Issue"
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by Hamza Humayun on 2009-10-06
Hi,
 
I am using Dsl connection. Just changed a few modem settings and don't know why the connection is not working in ubunto 9.04 though i haven't got a problem in Win XP. Earlier i was using the internet connection in Bridge mode so i had to connect to internet via dialing in xp and running " sudo pppoeconf" command in ubuntu but to connect multiple computers i have changed modem settings to automatic(pppoe) now in xp i am connected to internet when computer is turned on but can't seem to access it in ubuntu. 
 
I am using dual OS (as u must have figured it out:-)) and it is a wired connection with dsl modem connecting to computers via switch
 
Thanks in advance
 
Hamza

---

### Post by pricetech on 2009-10-06
Is your DSL modem a router or just a modem.  It sounds like your problem may just be something basic like trying to connect two computers via one connection without routing in between.

More information please.

---

### Post by Hamza Humayun on 2009-10-06
Well may be i am not properly phrasing it because i frankly don't know what is required. So you ask for more details but i don't know which details.
 
As i mentioned i am using a dual boot OS, so right now i am in Win XP and using internet but if i switch to ubuntu, i can't. So what i want to know is if there are any configuration changes or file editing required in ubuntu for using internet. 
 
the internet connection i am using is DSL (modem has the router capabilities as i am able to use internet on two computer simultaneously)
Few days back the dsl configuration was in Bridge mode so in ubuntu i had to run sudo pppoeconf command and i was able to use internet. Likewise in win xp i had to dial, now the connection is in auto mode, i no longer have to dial (user name and password)   in xp so i am assuming same for ubuntu but do i have to configure(ip /dns/defualt gateway/subnet mask etc?) for ubuntu?
 
Thanks

---

### Post by Hamza Humayun on 2009-10-07
I just tried to access modem in firefox using address 192.168.1.1 but it failed,
typing ifconfig didn't return any ip even though i tried to give it an ip using network tool.
any ideas now?

---

### Post by ShapeShiftme on 2009-10-07
Did the connection originally work. In other words was your network card working

What happens when you active DHCP on your network card.

---

### Post by Iowan on 2009-10-07
What is in your */etc/network/interfaces* file? (It should only have a couple of lines defining "lo").

---

### Post by Hamza Humayun on 2009-10-08
There isn't any network card issue as i already told you i have dual OS and am infact using internet just now using XP. I know it is something basic i am overlooking.
 
The file contents of /etc/network/interfaces are more then 2 lines, it is as follows:
 
[FONT=Courier New][SIZE=3]auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual
 [/SIZE][/FONT]

---

### Post by Iowan on 2009-10-08
You might try commenting out all but the first two lines in */etc/network/interfaces*. Restart/reboot to see if NM connects to the modem.

---

### Post by Hamza Humayun on 2009-10-09
Thanks, 
it is working now, i commented all the lines related to dsl -provider and changed eth0 interface to dhcp. 

How ever i am wondering what's the significance of network manager tool then, i mean when i was changing different parameters using it why wasn't the file /etc/network/interfaces getting updated? even now when i click on the "connection information" a message pops up that no valid active connection found( i am talking of the icon on the top right most corner)

Thanks once again

---

