---
title: "Conect at same time wireless and wired network card."
date: 2011-10-28
forum: Networking &amp; Wireless
---

### Post by Taheer Amad Mitha on 2011-10-28
Im using ubunto 10.04 on HP 500b with two network card one wireless and other wired. 
 
Problem faced:
1- If i conect one of them other automativaly switch off.
 
objective:
1- i want both network card to be conected at same time.

---

### Post by jonobr on 2011-10-28
Silly question on my part,

why would you want both to be active.

If its within the same subnet that's going to cuase an issue.

On my setup when I disconnect wired, wireless kicks in
its already connected, it just becomes the active route.

When I plug back in wired again, I go back onto wired.

I would not expect my machine to have both interfaces working at the same time unless I was doing some type of interface bonding, or wanted some high availability ip fail-over access where one interface is active the whole time and I dont need to know which, i.e. using 
[hearbeat and pacemaker]("http://bit.ly/d5a3qb")

---

### Post by deloquencia on 2011-10-28
For me it sounds reasonable :)

Check the setup with **ifconfig -a** and the file **/etc/network/interfaces**. Tell us some more details about your current network setup. Do you use static IPs or dynamic assign IPs delivered by DHCP?

In genereal with auto <interface> in /etc/network/interfaces you can bring both interfaces up. Just try when you switch from wired to unwired network to run **sudo ifup ethN** in a terminal, where N is corresponding to your Ethernet device.

---

### Post by Taheer Amad Mitha on 2011-10-28
I need to join an ubunto 10.04 to a windows network workgroup and create a shared folder on ubunto with samba visible on windows pc .The Ubunto pc must conect with to networks wirless and wired network( the wirless network with workgroup: workgroup,DHCP(IP: 192.168.1.x )and the wired network with workgroup: delta, Static IP(IP: 199.199.0.59), both with subnet Mask:255.255.255.0).I installed samba on ubunto and follow all the steps to create a shared folder.
 
Problems faced:
 
1-when wired card and wirles card are on i cante acess internet trough my wirless network only if wired is off.
 
2-I Cant see this ubuntu shared folder or pc on a windows pc but from ubuntu pc I can see windows PC´s from both workgroup(from wired and wirless windos network) and i can´t access none of them.
 
objectives:
 
1- computer from both network can share data trough the ubuntu shared folder;
2-The ubuntu user must have acess to the wired network to acess some files on the wired lan and be able to surf internet trough the wirless network.
NOTE: The ubunto pc must work as a point of share betwen user of two networks.

---

### Post by jonobr on 2011-10-28
Ok, so your not connecting two interfaces on the one network, cool,

The details really helps out a lot more

As deloquencia said more information on your configuration may help

Cheers

---

### Post by deloquencia on 2011-10-28
First lets turn to your networking problem, than afterwards lets turn to your samba sharing problem, okay?

> 1-when wired card and wirles card are on i cante acess internet trough my wirless network only if wired is off.]

This sounds like a routing problem.
When both interfaces are active run **sudo route** in a terminal and forward us here the output.

There's a lot more of information, but still please submit here your /etc/network/interfaces, without it it will be a little bit like searching for interfaces in a haystack ;)

---

### Post by Taheer Amad Mitha on 2011-11-02
[attach]206109[/attach]

[attach]206110[/attach]

[attach]206111[/attach]

[attach]206112[/attach]

[attach]206113[/attach]

---

### Post by Taheer Amad Mitha on 2011-11-02
[attach]206114[/attach]

[attach]206115[/attach]

[attach]206116[/attach]

[attach]206117[/attach]

[attach]206118[/attach]

---

### Post by Taheer Amad Mitha on 2011-11-02
[ATTACH]206120[/ATTACH]

I made a print screen of all details. Thanks for your patience and attention

---

### Post by Taheer Amad Mitha on 2011-11-04
Please can any one help me with this issue.

---

### Post by Taheer Amad Mitha on 2011-12-19
hi please im still waiting for your instruction.

---

### Post by jonobr on 2011-12-19
Hey

The last requests were for 

```
cat /etc/network/interfaces
```
also

```
 ifconfig 
```
would help,

also rerunning the route command would be good.

where did you get the 199 address from? for one of your ethernet interfaces?

You do know that this is a valid IPV4 address and not an internal networking one. 

In terminal grab them by highlighting them and control c to copy and control v to paste here.

Screen captures and graphics are hard to work with.

Also, when you post on this thread I get an email. No need for PM.

---

