---
title: "I can do this using Windows But I can't do it with ubuntu!!"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by ibrahim.k on 2009-12-12
Hi,
I can't use ethernet and wireless at the same time .. can I fix this ?
I can do this using windows.

I need it because at work we use wireless for internet at the same time i need the ethernet cable rj45 to connect to a local server please help me regarding this since its important

sory to prolong on you guys

---

### Post by earthpigg on 2009-12-12
couple things i would try:

1 - try using WICD instead of the default NetworkManager.

2 - use neither WICD nor NetworkManager and connect to both via CLI.

i've never done this, so i cant give detailed instructions... but the two above are the first two places i would start looking if i where in your shoes.

---

### Post by coffeecat on 2009-12-12
I believe you can do this using Network Manager. Right-click on the Network Manager applet icon and select 'edit connections'. Select the 'wired' tab and highlight your ethernet connection - probably 'Auto eth0'. Click the 'Edit' button and select the 'IPv4 settings' tab in the new window. Under 'method', drop down the list and select 'Manual' You can now enter the local server gateway IP address and netmask. Of course, you'll have to select a manually defined IP address. If you're using DHCP with the local server, this might be a problem. There are some other options under 'method' - you could see if any are of use to you.

And all these options are available for your wireless connection as well.

---

### Post by ibrahim.k on 2009-12-12
[SIZE=5][SIZE=3]I am currentrly using manual methode ipv4 otherwise i cant connect to the server
192.168.10.1 
255.255.255.0
192.168.10.1[/SIZE]

[/SIZE]

> **coffeecat said:**
> I believe you can do this using Network Manager. Right-click on the Network Manager applet icon and select 'edit connections'. Select the 'wired' tab and highlight your ethernet connection - probably 'Auto eth0'. Click the 'Edit' button and select the 'IPv4 settings' tab in the new window. Under 'method', drop down the list and select 'Manual' You can now enter the local server gateway IP address and netmask. Of course, you'll have to select a manually defined IP address. If you're using DHCP with the local server, this might be a problem. There are some other options under 'method' - you could see if any are of use to you.

And all these options are available for your wireless connection as well.

---

### Post by ibrahim.k on 2009-12-12
Thank you earthpigg i will try it 



> **earthpigg said:**
> couple things i would try:

1 - try using WICD instead of the default NetworkManager.

2 - use neither WICD nor NetworkManager and connect to both via CLI.

i've never done this, so i cant give detailed instructions... but the two above are the first two places i would start looking if i where in your shoes.

---

### Post by Iowan on 2009-12-12
On occasion, my Jaunty laptop connects to both my wired network and my neighbor's wireless... but ordinarily dthe procedure has been to let NM handle one connection, and set up the other one in */etc/network/interfaces*.

---

### Post by Iowan on 2009-12-16
A direct connection to the server will require a hub, switch, or crossover cable. Is the server running a DHCP server, or will you be setting up static address? What is the server using for IP address (192.168.10.1?)?

---

### Post by ibrahim.k on 2009-12-17
I connect to the server using terminal server address 192.168.10.30
on windows i was using static ip tryed it on ubuntu but didn't work




> **Iowan said:**
> A direct connection to the server will require a hub, switch, or crossover cable. Is the server running a DHCP server, or will you be setting up static address? What is the server using for IP address (192.168.10.1?)?

---

### Post by Iowan on 2009-12-17
Can you access the DHCP server to see what it uses for address range?
From a terminal, check **cat /etc/network/interfaces** Ordinarily it contains only two lines defining "lo". You should be able to define one of the interfaces here. If the DHCP server works, change */etc/network/interfaces*: ```
auto lo
iface lo inet loopback

auto eth0
inface eth0 inet dhcp
``` reboot and see if both interfaces come up.

---

### Post by ibrahim.k on 2009-12-19
After typing **cat /etc/network/interfaces **in a terminal I got this
[B]
auto lo
iface lo inet loopback



[/B]But I can't edit this address or add anything to it */etc/network/interfaces*: 
what should I do now
Thank you very much

---

### Post by Iowan on 2009-12-19
> **ibrahim.k said:**
> But I can't edit this address or add anything to it */etc/network/interfaces*: 
what should I do now```
sudo nano /etc/network/interfaces
```If you'd prefer a graphical editor:```
gksudo gedit /etc/network/interfaces
```

---

### Post by ibrahim.k on 2009-12-19
I have edited the contents successfully but still having the same problem
is there anything else that I should do


but I have to tell you that my eth0 has a manual proxy config
thank you very much

---

### Post by ibrahim.k on 2009-12-22
How to setup Networking (Wired and Wireless) Important

I can only use one of them I can't use both of them at the same time
hp-dv6 1045
All the drivers are installed

---

### Post by cariboo on 2009-12-22
Depending on what version you are using editing /etc/network/interfaces doesn't work any more in Jaunty and newer. You have to set your static ip addresses in Network-Manager. Just set the method on the IPv4 tab to manual, and enter your ip address, netmask and gateway. Then manually enter your dhcp server ip address.

I have had both interfaces working at the same time using dhcp, I haven't tried it with static ip addresses, but it should work the same way.

**Edit:** Please don't create multiple threads on the same subject, I have merged your two threads

---

### Post by ibrahim.k on 2009-12-22
I can only use the dhcp mode with the wirless connections so i can browse internet and for the wired connection I have already used manual ip configuration ip sub net mask and gateway but also didn't work ....when using wireless and i plug in the ethernet cable I lose the wireless connection immediatley !!




> **cariboo907 said:**
> Depending on what version you are using editing /etc/network/interfaces doesn't work any more in Jaunty and newer. You have to set your static ip addresses in Network-Manager. Just set the method on the IPv4 tab to manual, and enter your ip address, netmask and gateway. Then manually enter your dhcp server ip address.

I have had both interfaces working at the same time using dhcp, I haven't tried it with static ip addresses, but it should work the same way.

**Edit:** Please don't create multiple threads on the same subject, I have merged your two threads

---

### Post by zaphod777 on 2009-12-23
I think the problem may be that you can only have one default gateway not 2 so you need to choose 1 network that will have the default. 

You can still access the other with no default gate way but you probably can't access anything outside of the LAN segment that has no default gateway. 

for example:

you have 2 networks one with a few local servers on 192.168.11.x the other that has internet using 192.168.1.x I would set the default gateway to the one with the the internet connection however the network with no gateway you can't browse outside of the 192.168.11.x network.

I can do some testing maybe tomorrow when I have time but its a bit late here in Japan. ;-)

---

