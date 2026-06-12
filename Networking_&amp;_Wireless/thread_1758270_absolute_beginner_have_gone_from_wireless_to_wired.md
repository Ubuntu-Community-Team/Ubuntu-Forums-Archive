---
title: "absolute beginner have gone from wireless to wired"
date: 2011-05-14
forum: Networking &amp; Wireless
---

### Post by caroleann on 2011-05-14
i have been using ubuntu well for many months without any trouble. after rebooting my computer i found that it is showing that my network is wired instead of wirless. this happenned once before and i rebooted and it seemed to fix itself. this time i haven't been so lucky . please cananyone help ? not too compicated answers pleas as i am a granny nearly 70!!!!
thanks
caroleann:(

---

### Post by cprofitt on 2011-05-14
Carolanne:

I need to ask some questions to get a good idea of what is happening.

What makes you think that it is showing that your connection is wired vs. wireless?

Can you run the following commands (I have quoted what the output should be similar too):

iwconfig
> 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


> 
eth0      Link encap:Ethernet  HWaddr 00:1c:25:9a:76:5e  
          inet addr:192.168.1.198  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:fe9a:765e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11017 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10786174 (10.7 MB)  TX bytes:2376539 (2.3 MB)
          Interrupt:20 Memory:fc000000-fc020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:6a:0e:08:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lspci | grep Network
> 
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
03:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300


Those should help us get a little bit farther

---

### Post by caroleann on 2011-05-14
i know that it has changed from wireless to wired because when i click on the triangle type sign it says wired connection . i have tried to use the network manager to change it back to wireless with no success. i will try and do what you suggest . i am using my husbands laptop at the moment to access help. thanks  i have entered the command and the quote it lo no wireless connection and eth0 no wirless connection and that is all.  with the ispci command not found. when i change the network command the wirless sign comes up on the screen saying the network is disconnected you are now offline.

---

### Post by irv on 2011-05-14
> **caroleann said:**
> i have been using ubuntu well for many months without any trouble. after rebooting my computer i found that it is showing that my network is wired instead of wirless. this happenned once before and i rebooted and it seemed to fix itself. this time i haven't been so lucky . please cananyone help ? not too compicated answers pleas as i am a granny nearly 70!!!!
thanks
caroleann:(
First: I am gramps of 72, and I would like to ask a stupid question: Are you using a laptop? and is there a switch somewhere on the the laptop to turn the wireless on and off? I have one on my laptop, that is why I am asking.

---

### Post by caroleann on 2011-05-14
> **irv said:**
> First: I am gramps of 72, and I would like to ask a stupid question: Are you using a laptop? and is there a switch somewhere on the the laptop to turn the wireless on and off? I have one on my laptop, that is why I am asking.No i am using my husbands lap top at the moment the problem is on my desktop computer , thanks for your interest though.):P

---

### Post by irv on 2011-05-14
> **caroleann said:**
> No i am using my husbands lap top at the moment the problem is on my desktop computer , thanks for your interest though.):P

What is confusing to me is you said:
> my network is wired instead of wirless.
This to me means you have a wireless and a wire network card in you desktop. If this be the case if you unplug the wire it should just find the wireless.

---

### Post by caroleann on 2011-05-14
i know it sounds stupid but i do not have a wired system on my computer only wirless using a wireless card and router.  But when i boot up the computer it keeps showing the wired symbol and i am unable to diable it.  i have tried all the things in help section butit still doesn't work. :confused:

---

### Post by cprofitt on 2011-05-14
caroleann:

Were you able to run those commands on your desktop?

---

### Post by Nyrobie on 2011-05-14
Caroleann I know you posted the answers to the commands but could you copy and paste them here for us to see.

So we can see what your computer is saying to better help you. 

Regards,

---

### Post by caroleann on 2011-05-14
Iwill have to set up an ethernet system to my computer so that I can get on line ,and then i will be able to do as you ask.  i will do it tomorrow. thanks

---

### Post by irv on 2011-05-15
> **caroleann said:**
> Iwill have to set up an ethernet system to my computer so that I can get on line ,and then i will be able to do as you ask.  i will do it tomorrow. thanks

This will not work. if you setup an ethernet system then type the commands you will then show what you just setup.

What you need to do is run the two commands
```
iwconfig
```
and 
```
lspci | grep Network
```
Then copy the out put to a text file save it to a USB memory stick to transfer it to your husbands laptop and then copy and paste it to a post in this thread. That way we will see exactly what your network setting are before you make any changes to it.

---

### Post by caroleann on 2011-05-16
Thanks Kev I understand what you are saying , I will have to get myself a new memory stick as my grandson borrowed mine and it seems to have gone missing.  I tried to get on line with the ethernet without any joy either!!
Thanks again Carole

---

