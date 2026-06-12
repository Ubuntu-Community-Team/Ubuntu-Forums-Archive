---
title: "Assigning ip at terminal"
date: 2005-12-25
forum: Networking &amp; Wireless
---

### Post by Connollyir on 2005-12-25
This seems like a fairly simple thing to do, and it is when you rely on Ububtu's GUI but I need to establish a static ip address for a FTP server I made for my lan and I don't have a GUI to do it in. How do I make the server take a static ip address from the terminal? I need static for configuring the rest of my modules and SSH logging into the box itself.

Thanks

-Ian

---

### Post by Koybe on 2005-12-25
It's quite simple, yu juste need to know the file. ;)

/etc/network/interfaces ```

auto eth0 
iface eth0 inet static 
  address 192.168.1.10
  netmask 255.255.255.0
  network 192.168.1.0
```

Restart your network service and check it with ifconfig
```
/etc/init.d/networking restart
ifconfig
```

---

### Post by Lambert on 2005-12-25
Koybe is correct, use nano or vi to edit that file adding those. or you can use the command ifconfig to configure your settings

example

sudo ifconfig eth0 address 192.168.1.1

---

### Post by Connollyir on 2005-12-25
Ok so I changed my ip but now I've lost internet connectivity, and I cannot ssh into the computer.... i use ssh <user name>@192.168.1.10 but it just runs on and never gets anywhere. I have installed the ssh server and I did ssh into the computer before reconfiguring eth0 just to try it out and it worked so it can be done as it is set up now. Also - I just restarted the computer and it reverted back to the old ip from before.

Thanks

-Ian

---

### Post by Connollyir on 2005-12-25
Since I couldn't get the ip to stick to the computer, I figured it had something to do with the router assigning the ip over what I entered. I went into my router's settings and was able to set a static ip for the computer with its MAC address. Works well now on the LAN, but my question is will I still be able to ssh into the system when I connect it computer to computer with a crossover cable?

Thanks

-Ian

---

### Post by harisund on 2005-12-26
Yes, SSH does work that way too. But then the ip addresses wouldn't be what you expect. Especially if one machine is a Windows machine, you would get something like "Automatically assigned private address." Use ipconfig /all on a Windows machine and ifconfig on a linux machine to get the exact ip address and then ssh to that ip address.

---

### Post by Connollyir on 2005-12-26
[QUOTE=harisund]Yes, SSH does work that way too. But then the ip addresses wouldn't be what you expect. Especially if one machine is a Windows machine, you would get something like "Automatically assigned private address." Use ipconfig /all on a Windows machine and ifconfig on a linux machine to get the exact ip address and then ssh to that ip address.[/QUOTE]

This is going to be a Linux to Linux connection (two Ubuntu boxes, server and desktop installations), and I was worried that once I took the server off the LAN (I built it by putting the hard disk in another computer with network access and similar hardware so that I could install the operating system and packages easier) and put it in the box it will be going in I wouldn't be able to log into it. The reason this is important to be is because the box will not have a monitor output - its a 2u case with no onboard monitor out. 

I thought that I could assign the same ip that the router gave using ifconfig eth0 192.168.0.x and I would be guaranteed a static ip.

Ideas?

-Ian

---

### Post by harisund on 2005-12-26
Uh oh .. not good.. what you could do is enable a DHCP server.. that is the only idea coming to my mind right now.. could you do some reading on it? I have never tried out linux to linux cross over connection..seems interesting.. DHCP server on the one with the monitor will be able to get you what you want.. do check..

There is a package dhcp3-server .. you could use that..

---

### Post by Connollyir on 2005-12-26
[QUOTE=harisund]Uh oh .. not good.. what you could do is enable a DHCP server.. that is the only idea coming to my mind right now.. could you do some reading on it? I have never tried out linux to linux cross over connection..seems interesting.. DHCP server on the one with the monitor will be able to get you what you want.. do check..

There is a package dhcp3-server .. you could use that..[/QUOTE]


Funny thing is that right before I got this reply I read a bunch of information on DHCP. I'll definitely look into it, and then ask some more questions.

Sweet

-Ian

---

