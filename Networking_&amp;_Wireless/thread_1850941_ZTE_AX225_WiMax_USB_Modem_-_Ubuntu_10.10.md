---
title: "ZTE AX225 WiMax USB Modem - Ubuntu 10.10"
date: 2011-09-27
forum: Networking &amp; Wireless
---

### Post by AEiMBAK on 2011-09-27
Hi, I'm new here. I've just managed to get the ZTE AX225 modem working in ubuntu 10.10 using Sprint4G Developer Pack driver (drxvi314).
The modem get recognized after I load the module drxvi314 manually, I get new adapter eth1, I start connection manager (wimaxd - wimaxc) establish connection and I have internet access.

My questions are:
How can I make the module drxvi314 load automaticly durring boot or after I insert the usb modem?
How can I start the wimaxd daemon at start up?

After I get connected, the network manager doesn't show eth1 - How can I make eth1 shows there and be able to see its status in the nm-applet?

---

### Post by wildmanne39 on 2011-09-27
Hi, welcome to the forum! Here is how to make that load at start up.
```
sudo su 
echo drxvi314 >> /etc/modules 
exit
```
For the 2nd question go to startup applications and you can add it there, you will need to find the path to the program you want to have start at startup, then add it, here is a screenshot to give you an idea of what it will look like.

Just replace the path with the name of your program.
Thank you

---

### Post by AEiMBAK on 2011-09-27
Thank you for your help.

I found somerwhere else that I can use
```
sudo update-rc.d wimaxd defaults
```is that correct aslo I need to start the daemon with
```
wimaxd -c /etc/wimaxd.conf
```

---

### Post by wildmanne39 on 2011-09-27
Hi, I am not sure, I only know the way I mentioned should work.

What are you wanting to use this command for exactly.
```
sudo update-rc.d wimaxd defaults
```
Thank you

---

### Post by AEiMBAK on 2011-09-27
I've already used your way and it's working.
I just wanted to know if that works too, just for knowledge.

thanks again. and any thoughts about why the network manager and the nm-applet doesn't show the new device although it's working and I'm connected to the internet.

---

### Post by wildmanne39 on 2011-09-27
Hi, I did a search but I did not find an answer to why it is not showing in network manager.

Did you use network manager to setup the connection or did you do it manually?
Thank you

---

### Post by AEiMBAK on 2011-09-27
After I plug the usb modem it get recognized as eth1 and that what happens in Windows too (LAN Adapter)

I then start the wimaxd daemon (that's before I knew how to add it to start up). then I use the wimaxc client to make the connection.

but the network manager nor the applet shows that I'm connected or even shows eth1.

---

### Post by wildmanne39 on 2011-09-27
Hi, I am not sure but it maybe because you used the the wimaxc client to make the connection instead of setting it up through network manager, if it was me since it is working I think I would leave it as it is.
Thank you

---

### Post by Israeru on 2011-10-21
> **AEiMBAK said:**
> Hi, I'm new here. I've just managed to get the ZTE AX225 modem working in ubuntu 10.10 using Sprint4G Developer Pack driver (drxvi314).
The modem get recognized after I load the module drxvi314 manually, I get new adapter eth1, I start connection manager (wimaxd - wimaxc) establish connection and I have internet access.

My questions are:
How can I make the module drxvi314 load automaticly durring boot or after I insert the usb modem?
How can I start the wimaxd daemon at start up?

After I get connected, the network manager doesn't show eth1 - How can I make eth1 shows there and be able to see its status in the nm-applet?

Hello friend

I have some questions>

How do you do that? 
I tried to compile the driver and generate the drxvi314 in Ubuntus 10.04 and the driver compiles but dont create the ethernet interface when i tried to charge the module.

Can you post a tutorial?

How are you making to connect to the internet?

Do you edit your wimax.conf? 

The data for user and password in wimax.conf is the same in wendos? 

Greetings

---

### Post by Israeru on 2011-10-21
You have to compile network manager with wimax support, i see an article about this issue in google but i dont have the link now.

Greeting

---

### Post by anas on 2012-01-19
can you please tell us how you did it ... i`v been waiting for a long long time for this ...:D:popcorn::popcorn::popcorn::D

---

