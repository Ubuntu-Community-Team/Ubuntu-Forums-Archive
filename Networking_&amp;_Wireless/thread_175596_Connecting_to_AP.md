---
title: "Connecting to AP"
date: 2006-05-13
forum: Networking &amp; Wireless
---

### Post by richardkemp on 2006-05-13
Hey there, after much trial and error I successfully got to the stage where my wireless PCI card (Belkin F5D7000) is recognised by ubuntu's network manager thing.

It can see my network, but seemingly cannot connect to it. I have tried with WEP on and off, doesnt work either way. Can anyone please suggest anything for me, is there a command-based way to force a connect?

Thanks all!

---

### Post by richardkemp on 2006-05-14
Bump!

If I use the iwconfig command to try and change settings for eth0 (my wireless adapter) it gives an error - settings cant be changed. Is this normal?

---

### Post by richardkemp on 2006-05-15
RE-bump!

Some help would really be appreciated here.. I dont know the first thing about linux yet and theres no way I can switch from XP if I dont get my ethernet up and running. This is the clincher guys..

---

### Post by crankcaller on 2006-05-15
Try turning off all security, broadcast the SSID and reboot both your pc and router.  
Is it DHCP or a static IP?  try both...

How do you get on?

---

### Post by mikesull on 2006-05-15
I have the same problem. When I don't use Network Manger I can connect to my router fine, even with WEP. Not sure if it has to do something with the version of ubuntu or the type of wireless card (maybe Network Manager only supports some cards?). I'm currently using Dapper Drake and have a card with the TI acx111 chipset.
Suggestions anyone?

JUST A SIDE NOTE richardkemp: If no one can help us out, I would try another program like GTKwifi and uninstall network manager. Or you might just try uninstalling network manger and using the network administrator app (unser System --> Administration --> Networking).

---

### Post by mikesull on 2006-05-16
I gave up on network manager, and I'm using kwifi, which works just fine.

If you want it just open up a terminal and type;

sudo apt-get install kwifimanager

After installation it will be under Applications --> Internet

---

### Post by richardkemp on 2006-05-16
I have no net connection in ubuntu at the moment, will that still work (is it packaged with the basic install?)

I've tried without security and a restart on both sides... SSID is broadcasted. I can see it - I just cant get the connection to connect ](*,) 

I ahve also tried both DHCP and static IP, neither of those work, and I dont think I have a network manager problem since I cant connect using the terminal commands either, like I said it throws up an error when I try to configure my device at the terminal.

---

### Post by etosamoe on 2006-05-17
Same Problem here. Dell D610 with Broadcom wireless card. Trying to connect to a Netgear AP. Network is visible, NM even properly detects the security setup, signal strength, everything. Very frustrating. I haven't seen any other threads on this. I'm going to try kwifimanager too.

---

### Post by dartakaum on 2006-06-03
[QUOTE=richardkemp]

I've tried without security and a restart on both sides... SSID is broadcasted. I can see it - I just cant get the connection to connect ](*,) 

[/QUOTE]

just like me...

---

