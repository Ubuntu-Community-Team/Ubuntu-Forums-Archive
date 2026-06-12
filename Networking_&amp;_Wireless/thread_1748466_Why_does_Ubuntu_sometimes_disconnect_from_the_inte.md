---
title: "Why does Ubuntu sometimes disconnect from the internet?"
date: 2011-05-03
forum: Networking &amp; Wireless
---

### Post by Coolcam262 on 2011-05-03
Hello,

I am quite new to ubuntu and am having some wireless internet connection problems. For some reason I get disconnected occasionally and the only way to solve this is by restarting the computer. This is not a problem I have ever had in windows and so I assume the problem is related to Ubuntu. I would try upgrading (I am using ubuntu 10.10) but every time I try I get disconnected and I have to restart :(

I have no idea what information I need to give you so please respond with what you would need to help you solve this problem.

Thanks,
Cameron

---

### Post by josephmills on 2011-05-03
Hi there here is a list of how to fill out a wireless ticket please take out all ipadress and inter address and hw address thanks 
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by Coolcam262 on 2011-05-03
**[COLOR="Orange"]Laptop Model:[/COLOR]** Advent 5431
**[COLOR="Orange"]Ubuntu Version:[/COLOR]** 10.10
**[COLOR="Orange"]Kernel Architecture:[/COLOR]** 2.6.35-28-generic i686
**[COLOR="Orange"]Wireless Brand[/COLOR]** [Realtek RTL8187SE]("http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=40&Level=5&Conn=4&ProdID=172")
**[COLOR="Orange"]Wireless type:[/COLOR]** 802.11b/g
**[COLOR="Orange"]Link Quality:[/COLOR]** 73/100
**[COLOR="Orange"]Signal level:[/COLOR]** -44 dBm
**[COLOR="Orange"]Noise level (no idea what this means, thought it might be helpful ;)):[/COLOR]** -102 dBm

I think that's all the relevant info, tell me if I've missed something out. Some of it I didn't understand and so couldn't post it, for example I couldn't find the make/model using the lspci command so instead I just googled my laptop make and model ;).

Thanks Again,
Cameron :D

---

### Post by Coolcam262 on 2011-05-04
*bump* It is a 6 hour bump limit, tell me if it's not? :)

---

### Post by Coolcam262 on 2011-05-05
Anyone? :/

---

### Post by Coolcam262 on 2011-05-11
I reinstalled ubuntu and I'm now using 10.04 LTS however now I can see all the connections but it won't connect to any of them. I have tried restarting many times and toggling the card on and off without success. I hope someone can help me,

Thanks,
Cameron

---

### Post by Coolcam262 on 2011-05-12
please??

---

### Post by josephmills on 2011-05-12
ok I am not a good guy to ask about rt cards but lets give it a shot please open your terminal and type in ```
rfkill list 
``` please paste that here this next one takes some time to load but it will ```
sudo lshw -C network
``` please paste all here

---

