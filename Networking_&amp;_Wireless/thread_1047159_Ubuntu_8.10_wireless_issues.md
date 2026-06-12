---
title: "Ubuntu 8.10 wireless issues"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by Dropzone56 on 2009-01-22
Here's the scoop, I have an Toshiba TAIS Satellite L305D-S5900 with a 250gb Hard disk with an ubuntu and vista partion. It has the AMD Athalon 64x2 Dual core moblie processor TK57. I have gotten Ubuntu 8.10 installed just fine, and when im plugged in to my router(belkin wireless g router 2.4 ghz 802.11) I can connect to the internet just fine. But if I have the Laptop unpluged from the router Ubuntu does not dectect anything realted to a wireless connection. Now I know for a fact that even though the laptop is not pluged into the router it will still connect, because I went back and used vista to prove this. Plus my Ipod touch(1st gen) also has no problem finding and connecting.

So my question is this, what am I missing? The help section in Ubuntu was not exactly helful in this situation, and I was unable to find any realted threads that were useful. Now that doesn't mean they don't exist, I must have missed them.

Thanks in advance to anyone that resoponds.

---

### Post by Dropzone56 on 2009-01-22
So I went back though the help section in Ubuntu, and found that my wireless device is diconnected because I dont have any drivers for it. Apperntly I need to find some windows drivers for it. So where would I find those?

---

### Post by Sportingfan on 2009-01-22
In order to get an answer to your question, please provide more information about your wireless card.

In terminal do:

```
iwconfig
```

There you'll probably see that your wireless is on wlan0;
Then perform

```
iwlist wlan0 scan
```

Then copy the output to this thread.

I had a similar problem, and solved it. See my thread: [http://ubuntuforums.org/showthread.php?t=1045143](http://ubuntuforums.org/showthread.php?t=1045143)

The solution provided in my thread works for intel wireless cards.

---

### Post by Dropzone56 on 2009-01-22
trent@trent-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

trent@trent-laptop:~$ 


trent@trent-laptop:~$ iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

trent@trent-laptop:~$ 

I's thinking Ubuntu doesn't even know my wireless card exists. I have found the windows drivers for my card. But I don't know what to do with them, I got them from the Toshiba website but there is a couple of other drivers as well, I hope i got the right ones.

---

### Post by Dropzone56 on 2009-01-22
this is the card i have in my laptop &#61623;
&#61623;
&#61623;
&#61623;
  Atheros 802.11 b/g wireless-LAN

---

### Post by Frenkenstain on 2009-01-22
I have the same card, and ubuntu tells me that the restricted drivers are active, but I still only have wired network(eth0) and the loopback (lo), any help appriciated.

---

### Post by SpenceMakesSense on 2009-01-22
try googling around for the drivers. to install them youll need ndisgtk but youll need the laptop to be connected to the internet some other way(wired probably the obvious way here) and run ```
 sudo apt-get install ndisgtk
``` in some cases they may give you an exe that has to be run and that will exctract the files to a specific location. Youll need wine to extract the files or extract them on a windows machine and put them on a flash drive. ndisgtk will ask you to find a .sys file I believe. just find the .sys file and it will tell you if it detects the proper hardware or not. if not then you chose the wrong file.

---

### Post by Dropzone56 on 2009-01-23
Ok, that makes sense. Thanks

---

