---
title: "Connect to my uni network, i know this has been asked many times before but..."
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by burton247 on 2009-12-08
I've read countless posts about connecting to networks via peap but they have never been properly solved and I still cant get mine to work. 

I have a dell inspiron.

snippet of lspci is:

```
0c:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

```

ifconfig is:

```
wlan0     Link encap:Ethernet  HWaddr 00:24:d6:03:a8:7c  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:d6ff:fe03:a87c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73706 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:86622476 (86.6 MB)  TX bytes:8706156 (8.7 MB)

```

I have found these documents floating around online (I do go to Brighton btw)


hxxp://blogs.linux.ie/balor/2009/01/21/connecting-linux-to-the-university-of-brighton-wireless-network/

hxxp://blog.yeticode.co.uk/2009/02/university-of-brighton-wireless-network/

With these i would've thought it would be simple, but i cannot get it to work. I would also like to note the uni does not officially support linux and the guy who made the blog isn't replying to his emails :(


Here are the facts so far:

I have tried it with and without the CA
Today i used wicd with and without using pump
I tried it with another wireless card (zydas driver) and it connected once! and not again :(
If i dont use the certificate it just spends time verifying the connection.
Every time, every combination it always fails when it is obtaining the IP address from "University of Brighton"

Any help will be greatly appreciated. I would like to try and solve this myself opposed to getting the guy that should know how. Firstly cause he's probably rather busy, secondly cause I don't want to admit defeat.

So anyone have any suggestions as to what's going on here or what to try?

---

### Post by gordintoronto on 2009-12-08
wlan0 is your ethernet cable port, not wireless.

I think you might be making this a lot more complicated than it needs to be.  I have set up lots of wireless, but I don't recognize half the words you used: peap, CA, pump, certificate (in this context)

What version of Ubuntu are you using?  What is the make and model of your laptop?  Do you currently have Network Manager or Wicd installed?

Does the university's wireless router defintiely support DHCP?

---

### Post by burton247 on 2009-12-08
I appreciate your reply i do but...

I know it says ethernet but its lying lol 

Im really not making it more complicated, I've set up a lot too but never a peap one.

peap is the type of encryption the uses its a type of wpa2 enterprise

CA is the authentication certificate used to connect to the network

pump being an alternative dchp client that a user in the forum managed to connect using

CA is the certificate

However, i can only assume you didn't check the links because there is literally a step-by step guide of how to connect to the network...these answered your questions

Theres been a lot of bug reports posted where they cannot get this type of encryption to work on later versions of ubuntu, I'm running 9.10 2.6.31-16

There were reports from other unis that they only managed to get in working in 8.10

I am pleased you replied and I'm sorry if I come across rude or ungrateful; its not meant like that. Its just it would appear your trying to help (which is great) but without properly reading the information i have provided




My apologises for the links, put them as hxxp now

---

