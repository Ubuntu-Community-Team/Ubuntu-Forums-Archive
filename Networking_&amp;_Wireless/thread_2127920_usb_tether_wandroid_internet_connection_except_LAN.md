---
title: "usb tether w/android: internet connection except LAN/local network sharing n/a"
date: 2013-03-21
forum: Networking &amp; Wireless
---

### Post by oetepetoetje on 2013-03-21
Hello,

I've got an Ubuntu 12.04 LTS pc. This desktop is connected with the internet with a android phone, using the option usb-tethering(WiFi &router). This is working fine, except for one thing: I can't acces my local (LAN) network. If I connect this ubuntu pc with the router using an (direct) internet cable it works fine. Samba file sharing etc are also running fine, when directly attached too the router. The cables I've got aren't long enough.
The connection through the android phone is clearly the problem, but is there any way to solve this conflict? 

Thanks,
oetepetoetje

---

### Post by cortman on 2013-03-21
I'm not sure I fully understand your question, although the post caught my eye as I tether with my Android phone a lot myself.
Is it that you can't connect to both networks simultaneously?
Perhaps [this post]("http://ubuntuforums.org/showthread.php?t=1968394") has some relevant info.

---

### Post by oetepetoetje on 2013-03-21
Well, my problem is that with a direct wired connection to my router I can use samba and file sharing on my local network (so with other computers linked with the router),
while using a usb-tether with my android phone, all connection I do have, is a internet connection. While using usb-tether, connecting with other computers on my local network seems to be impossible. My Ubuntu pc isn't even visible on my local network, while other devices are. Using the ubuntu pc, I couldn't use a direct connection too other local network pc's.

---

### Post by gordintoronto on 2013-03-21
Let's see, you use your phone to connect to the Internet, and you are not connected to your LAN in any way whatsoever. Is that correct?

Does your LAN have WiFi? That's the normal way to connect to a LAN when you can't run cables. You can get a USB WiFi adapter for less than $20. Just make sure it's going to work with Linux before you spend money.

The other way to connect to your LAN would be through the Internet, which means possibly exposing your LAN to bad guys. If you're a security expert, you can make it safe, but I think you would need to spend dozens of hours reading about how to do it.

---

### Post by cortman on 2013-03-22
So it seems that you can't connect with the wired connection and the USB tethering connection at the same time?
I haven't tried it myself yet since I don't have a wired network at home.
Here's [another link]("http://forums.opensuse.org/english/get-technical-help-here/network-internet/480023-need-help-2-network-adapters-tethered-usb-eth.html") for you that may be of some benefit.

---

### Post by oetepetoetje on 2013-03-22
My phone uses the same network as my other devices hooked to my router, so I don't use an external connection. The connection between my phone and my router is not the problem: I can login in my router using it's ip-adres ([http://192.168.1.254](http://192.168.1.254)), while using the usb-tether option on my phone. A solution could be buying a usb WiFi adapter, or a very long internet cable to get a internet connection upstairs.
My laptop uses the same WiFi signal as my phone, however media sharing using LAN is working. The phone used for usb-tether can also acces the local network (using ES File Explorer app) and share, stream +view files with several devices on the local LAN. 

If I use the lookup function (in Network Tools @ubuntu) and I lookup the IP-adres of my laptop, the program sees the laptop on the LAN:
Name:18.1.168.192.in-addr.arpa. laptop.lan.
TTL=0
Adress type=IN
Record type=PTR
Adress: laptop.lan
The only way ubuntu could have gotten this information is using the LAN network, so ubuntu knows there is a LAN network, but just can't connect with it using Network (@ubuntu).
My laptop doesn't have such a tool and can't see my ubuntu pc while using usb-tether.
The only way now to acces my ubuntu pc with LAN is a cable connection with the router (or buy a usb WiFi adapter), but the ubuntu pc is upstairs, so I would have to get a long cable across the stairs, wich is not a permanent solution.
There are a few possibilities I can think of: because the phone has it's own IP-adress and MAC as well as the ubuntu pc has both there could be a conflict between those two. I am not using a static IP adres.
I've adjusted my settings in my router, so as wel as my phones' IP&MAC as my ubuntu pc IP&MAC are allowed on the routers' network, so that should not be a problem.

---

### Post by oetepetoetje on 2013-03-22
The problem seems to be complicated:
My setup:
router (with internet connection, WiFi and LAN routing) connected with: my phone (WiFi), my laptop (WiFi) and some other devices. 
- laptop is connected with www and LAN: I can browse internet (www) & use LAN (streaming movie's etc to my tablet, so that works)
- My phone is connected with www and LAN: internetbrowsing and LAN are available and works like it should with the laptop and other devices (so internetbrowsing and LAN while using the same WiFi from the router)
-My ubuntu pc is only connected with my phone using a usb-cable. By using the usb-tetheroption on my phone I also have an working internet connection and I can browse the www with my ubuntu pc.
The only thing that fails is browsing the LAN with my ubuntu pc using usb-tether. But this only happends when using usb-tether. If I use a direct cable connection with my router and my ubuntu pc: LAN sharing and internet browsing does work. I can't use this direct connection.

---

