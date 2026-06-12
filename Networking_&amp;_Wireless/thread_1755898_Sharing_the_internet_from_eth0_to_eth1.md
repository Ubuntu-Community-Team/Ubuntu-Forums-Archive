---
title: "Sharing the internet from eth0 to eth1"
date: 2011-05-11
forum: Networking &amp; Wireless
---

### Post by Dumle29 on 2011-05-11
hi, im a linux noob dont get techy ill die of brain fry ;)

im running a craft bukkit minecraft server on my 11.04 ubuntu server.

however the server uses my only 10m Ethernet cable that i normaly use for my ps3 (i will NOT go wireless. i hate it (or dont like it))

therefor i found an old PCI NIC in an old computer, its a 10/100 realtek one. ifconfig detects it (after two commands: ```
ifconfig eth0 up
dhclient eth0
```
)

now i need to send the internet to my ps3 too. i know the connection wont be blazing fast but isnt it okay?

it musn´t  interrupt the minecraft server.

if you need info just ask. ill try and provide them.

hope someone can and will help me :)

---

### Post by Iowan on 2011-05-11
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is an article that *might* help. Like a lot of my bookmarked help pages, it's getting a li'l old.

---

### Post by spindler on 2012-05-05
I have internet set up through my USB port (clear wire 4G hub) and I have a router set up on eth0.

I need to provide internet to eth0 so that my other computers can access the internet. I followed the instructions to set up port sharing by looking at this article. 

[https://help.ubuntu.com/community/In...nectionSharing](https://help.ubuntu.com/community/In...nectionSharing)

I followed the instruction under the title. "GUI Method via Network Manager (Ubuntu 9.10 and up)"

My Linux version is 11.04.

I cannot access the internet through port eth0. How do I provide internet through port eth0?

---

