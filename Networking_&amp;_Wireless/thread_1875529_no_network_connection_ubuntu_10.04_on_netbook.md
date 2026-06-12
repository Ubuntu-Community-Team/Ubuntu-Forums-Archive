---
title: "no network connection ubuntu 10.04 on netbook"
date: 2011-11-04
forum: Networking &amp; Wireless
---

### Post by optima4 on 2011-11-04
I can't find help. I hope you guys will. I didn't realize I would not be able to connect to the internet once I erased my windows 7 starter OS and installed unbuntu 10.04 lts 32 bit. I called my internet co (chater) and my computer co. Neither were helpful.

I have a notebook. LT27 gateway

Our internet is a wireless connection. 

When I go to the network icon @ top right taskbar I have "no network devices available" only "vpn connections" is highlight. If I go to system>admin>network tools, I am at a window with several tabs: devices, ping, traceroute, port scan, lookup, finger, whois.

All I have been able to try and input is my router address but no luck. The other thing I found online was a generic code for address: 127.0.0.1 and netmask: 225.225.225.0- this didn't work. I do not know what DNS Server is or IPv4 or IPv6.

Please help

---

### Post by dcstar on 2011-11-04
> **optima4 said:**
> I can't find help. I hope you guys will. I didn't realize I would not be able to connect to the internet once I erased my windows 7 starter OS and installed unbuntu 10.04 lts 32 bit. I called my internet co (chater) and my computer co. Neither were helpful.

I have a notebook. LT27 gateway


Try a later Ubuntu release like 11.04, it may be too new for 10.04.

This question should be in the Hardware & Laptops forum.

---

### Post by pqwoerituytrueiwoq on 2011-11-04
if you want to stick with 10.04
post the output of lspci we *may* be able to find the driver you need
i assume you are using wireless have you tried a hardware conection (will be easer to post output)

---

### Post by optima4 on 2011-11-05
Thanks. I'm on my android can't navigate very well to find the forums.

Where can I find output lspci? Do mean mean hardware like connecting with an ethernet cable to my modem?

Sry to be so new. Thanks for a quick response.

---

### Post by optima4 on 2011-11-05
I googled what lspci is. I think I can find it in the command prompt? I will have to in the morning been texting on my phone hours on end trying to figure this out and its very later here now.

---

### Post by optima4 on 2011-11-05
I attached my lspci photos from my phone. I hope you guys can help. Post from my phone so my best chance is your forum.

---

### Post by pqwoerituytrueiwoq on 2011-11-05
[http://ubuntuforums.org/showpost.php?p=9446984&postcount=6](http://ubuntuforums.org/showpost.php?p=9446984&postcount=6)
that is relevant to your hardwired network card
on the second picture what is the last line
namely the numbers near the end

---

### Post by optima4 on 2011-11-06
I can't believe I left that part out. 

Also I'm confused am I supposed to open every one of these links and save them?

[COLOR=Blue][http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/)[/COLOR]

The computer I'm on says I cannot open some of these downloads without searching online for how to. Usually that means I can't open them.

Thanks you sooo much for getting back to me!

---

### Post by optima4 on 2011-11-06
I'm sorry I see it now...> download the file named "compat-wireless-2.6.tar.bz2"
(Using my mothers computer for internet where it gets busy and hectic here.) :guitar:


*I do not have a disc drive on my laptop. Making sure to note it. I have 4GB and 8GB USB flash drives.

---

### Post by optima4 on 2011-11-06
OK, well I am just completely stumped guys :confused:  I followed most of these commands in the link you posted me. I enabled  my cd drive and downloaded the driver to my USB. I do not have internet  connection so I am having more trouble. I also do not have a cd drive on  this computer. So I downloaded the driver to the USB and connected it  to my computer. I followed the code, which I had to write in OpenOffice  Writer, then paste it in the Terminal.

I was asked to continue, y/n? I chose yes. It then said Abort. 
Upon restarting I had a black screen asking me "what I wanted to  'boot'". Not knowing why it was I tried several codes for a kernel and  configs. I disconnected the USB and everything came back on. 

I then realized the first post in the link was for an Ethernet  connection. I actually hooked up an Ethernet cable to our wireless modem  here yet still have zero results. 

I then followed the next code by pasting the code for 'wireless' into  Terminal. I have had the same results as since I begin, "command not  found".

I'm getting really frustrated. I do not think I can do this with out  someone who has more knowledge. I really want to learn this stuff, but I  do not have access to the internet anymore of my own other than my  Android. Can anyone give me advice? I read once there were Linux support  groups at times. Where can I find one in my local area?

thanks

---

### Post by optima4 on 2011-11-06
[SIZE=3][B]I am so stoked right now!! I installed 11.10 AND IT WORKED

wooot

[/B][SIZE=2]Dont wana speak too soon because the ehternet chord is still plugged in but I got it, thank the Heavens.[/SIZE]
[/SIZE]

---

