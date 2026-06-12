---
title: "stupid internets - Cannot view any web pages on the Internet"
date: 2013-05-06
forum: Networking &amp; Wireless
---

### Post by Lukey Cat on 2013-05-06
I have an internet connection, It won't go to any site (like turntable.fm for example), and doesn't even light up.
[IMG]http://farm8.staticflickr.com/7295/8714862875_a8a489cb1b.jpg[/IMG]Quick! before I pour water on it!

---

### Post by matt_symes on 2013-05-06
Thread moved to **Networking and Wireless** sub forum.

I have edited the title for you as well to be more descriptive.

---

### Post by Lukey Cat on 2013-05-06
> **matt_symes said:**
> Thread moved to **Networking and Wireless** sub forum.

I have edited the title for you as well to be more descriptive.
wow that was fast
[IMG]http://farm8.staticflickr.com/7459/8715973440_924323445c.jpg[/IMG]

---

### Post by papibe on 2013-05-06
Hi Lukey Cat.

Could you open a terminal and post the results of these commands?
```
sudo lshw -C network

lspci -nnk | grep -iA2 eth

ifconfig

route -n

nslookup ubuntu.com
```
Regards.

---

### Post by pfeiffep on 2013-05-06
Ignore the c:\Users\pfeiffep - I'm using a Windows machine to answer this. Access a terminal window Ctrl-Alt-t and type ping google.com you shoud see similar results as I've posted

> C:\Users\pfeiffep>ping google.com


Pinging google.com [74.125.228.100] with 32 bytes of data:
Reply from 74.125.228.100: bytes=32 time=10ms TTL=252
Reply from 74.125.228.100: bytes=32 time=8ms TTL=252
Reply from 74.125.228.100: bytes=32 time=8ms TTL=252
Reply from 74.125.228.100: bytes=32 time=9ms TTL=252


Ping statistics for 74.125.228.100:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 8ms, Maximum = 10ms, Average = 8ms

If you don't see something similar than you don't have internet connectivity.

Post back with your results - and give us some specifics about your computer

---

### Post by Lukey Cat on 2013-05-06
are you sure it says ping google and not ping the dreaded website?

---

### Post by Lukey Cat on 2013-05-06
wait a minute, unknown host...

---

### Post by Lukey Cat on 2013-05-06
Seems like you're using the same version as me, must work...

---

### Post by matt_symes on 2013-05-06
Hi

@Luckey Cat. 

After you have run a command copy and paste the output from the terminal into your posts. That way those helping you can see exactly what the output is and they will not have to try and second guess what you mean.

You copy and paste from the terminal by highlighting the text -> right click -> copy and paste into your next post.

When posting text from the terminal into your posts, please use code tags. You do this by highlighting the text in your post and hitting the # button above where you type your text.

This will make it much easier to help you. 

Please run the commands that papibe posted as they will give an idea of you current setup; what's working and what's not.

[B]EDIT:
[/B]
And welcome to the forums :D

Kind regards

---

### Post by Lukey Cat on 2013-05-06
didn't nslookup. Imapatient connection

---

### Post by Lukey Cat on 2013-05-06
Specs:
-Dimension 2400
-1 gig of RAM
-those good viewsonic monitors from the 90s
-a random paper jamz amp (couldn't find anything else :???:)
-Lucid Lynx (10.04)

---

### Post by matt_symes on 2013-05-06
Hi

@Luckey Cat.

Please read post #9.

Kind regards

---

### Post by Lukey Cat on 2013-05-06
how do I do that without internet =|

---

### Post by papibe on 2013-05-06
> **Lukey Cat said:**
> how do I do that without internet =|
Press Ctrl+Alt+T to open a terminal. Then, copy each command separately from post #4 into the terminal and press enter.

Regards.

---

### Post by Lukey Cat on 2013-05-06
I doubt it copies into the windows puter =P

---

### Post by matt_symes on 2013-05-06
Hi

> **Lukey Cat said:**
> how do I do that without internet =|

Do you have an Ethernet port ?

Is your Ethernet port working ?

Can you plug directly into the router using an Ethernet cable ?

To help diagnose your problem we will need this information.

Kind regards

---

### Post by Lukey Cat on 2013-05-06
My ethernet is being used already, by the PC, and they're in completely different rooms...

---

### Post by matt_symes on 2013-05-06
Hi

Can you move the PC that is having Internet connection problems into the other room and pulg the cable into it ?

If not then you will have to type the output of those commands manually. 

Without that output we will have no idea what is wrong with your computer.

Kind regards

---

### Post by Lukey Cat on 2013-05-06
Is it possible to have two computer inputs on the same monitor? =P

---

