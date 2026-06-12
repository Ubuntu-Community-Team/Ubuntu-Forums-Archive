---
title: "network share on bootable usb drive"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by andrew_g on 2010-04-05
Hi, I have ubuntu 9.04 installed on a usb hdd. I use it as a portable operating system which I can boot from on several computers.

But I have a slight problem when it comes to networking.

I can see the computer listed on the network (places network) when I boot from the machine I originally installed it on but NOT when I boot it from any other machine, the shared folders and remote desktop only appear when booted from the original machine.

I have set home/andrew/music folder as shared,

scenario 1
USB-drive boots Ubuntu on machine A (original), I can see this computer and its shared folders on the network (from all machines) I can also see other computers on the network

scenario 2 (I boot same installation from usb drive on machine B)
USB-drive boots Ubuntu on machine B, I CAN NOT see this computer or its shared folders on the network (from this or any other computer) I can see other computers on the network though.

Many thanks

---

### Post by dannyboy79 on 2010-04-05
> **andrew_g said:**
> Hi, I have ubuntu 9.04 installed on a usb hdd. I use it as a portable operating system which I can boot from on several computers.

But I have a slight problem when it comes to networking.

I can see the computer listed on the network (places network) when I boot from the machine I originally installed it on but NOT when I boot it from any other machine.

What do I need to do?

Many thanks
you're saying that it doesn't show up to other computers within their network places pulldown? well, how long are you waiting from teh last time you connected it to that machine? also, is it setup with dhcp or static ip? is it's hostname registered with a dns server within the network? the problem is going to be that the MAC address of the network card on the various computers you're connecting the usb hdd to will be different. if you're going to move it all the time, you're better off using a live usb install not a permanent install. certain things get purged each reboot like hostname and ip address assignment etc etc.

---

### Post by andrew_g on 2010-04-05
Thanks

> the problem is going to be that the MAC address of the network card on the various computers you're connecting the usb hdd to will be different. if you're going to move it all the time, you're better off using a live usb install not a permanent install.

That seems a reasonable explanation and also like the solution. Would a live install be a persistent install as far as certain settings and additional apps are concerned. Also would relative shares be recognised, eg home docs etc

Also Many thanks

---

### Post by dannyboy79 on 2010-04-05
> **andrew_g said:**
> Thanks



That seems a reasonable explanation and also like the solution. Would a live install be a persistent install as far as certain settings and additional apps are concerned. Also would relative shares be recognised, eg home docs etc

Also Many thanks

a live install can be made several ways, i have only done it with a 4gb fat32 partition on a 16 gb stick. so after the OS and added apps, you have around 3 gb to save stuff to like movies, docs, and such. I am not sure about the whole network sharing thing. i know you can install apps (samba) but am not sure if they'll be recoginized by windows netbios discovery. you could always just connect to server within windows and use an ip address. you'll have to try it. I would think if you wanted to share you could use dropbox for free up to 2gb if you really wanted to store stuff in your live usb install that you wanted to access from other computers. it may be better to mount a network server share and store all info there, tehn wherever you boot your live usb install, you can just mount that share. 

good luck

---

### Post by andrew_g on 2010-04-05
Hi, many many thanks for your help and suggestions, it all makes common sense! I'll look in to it all further now you've pointed me in the right direction. Thanks again.:p

---

