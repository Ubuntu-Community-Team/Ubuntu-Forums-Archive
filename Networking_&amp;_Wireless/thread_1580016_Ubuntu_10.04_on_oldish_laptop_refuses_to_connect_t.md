---
title: "Ubuntu 10.04 on oldish laptop refuses to connect to Wi-Fi"
date: 2010-09-22
forum: Networking &amp; Wireless
---

### Post by PPM5895 on 2010-09-22
Hey, everyone. 
I installed Ubuntu 10.04 on my laptop yesterday. 
It's really great. :D

But, sadly, it won't let me connect to the internet.

I'm not sure what year the laptop is from, but I'm fairly certain it's from between 2005 and 2007. It's definitely 2005 or newer.

So here's what happens. 
I click on the little Wi-Fi bar thing in the status bar and choose hidden network. Then I choose WPA/WPA2 personal and I type in the network's name and password. After that, a black box appears and tells me that I've disconnected from Wi-Fi. :/

I checked the help file and did the terminal commands. It told me that it was disabled. I checked my "wireless device" and it was turned on. 

I have no idea what's going on but I really want it to work. I like Ubuntu so much better than Windows XP. >________>

Thanks in advance.

---

### Post by Iowan on 2010-09-22
From a terminal (Applications>Accessories>Terminal) check (post if possible) **sudo lshw -C network**

---

### Post by PPM5895 on 2010-09-22
I'll try it, thanks. ^_^

---

### Post by PPM5895 on 2010-09-22
I tried it and it didn't do anything... :/

I'm going to try a wired connection to download wireless drivers. 

On an (somewhat) unrelated note, the internet/battery icons have disappeared and I can't get them back. :'(

---

### Post by grahammechanical on 2010-09-23
Why did you choose Hidden Network? I left click the network icon and scroll down to the connection with the name of my ISP and because I have already entered the correct wireless key, the system connects. Try, removing the hidden network that you have created. Left click select edit connections. select wireless. You should see your wireless connection. Select Edit. Tick Connect Automatically. Select Wireless Security and enter the password. You can tick show password to see what you are typing. It is not the password that you use to log-on but the WPA-PSK key, also called Wireless key or may be the network security key or pass-phrase. I have seen all these terms used. You may be able to get this information off of a label stuck somewhere on the modem. Once this information is in network manager it will remember it and you should connect when ever you boot. It works for me.

Regards.

---

### Post by PPM5895 on 2010-09-23
I have to choose hidden network because it never shows any wireless connections. Not even my home network which isn't hidden.

I have the internet working with an ether net cable, but it's really annoying that I should have to do that at all. :/

Is there some way for me to check and make sure that my wireless driver is enabled, and if it isn't, enable it?

---

