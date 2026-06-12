---
title: "Wiresless Network Setup Issue"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by Rog3236 on 2009-04-15
I posted this inappropriately I'm afraid in another category. After which I discovered this one. For that I apologize.

I have Ubuntu 8.10 installed on my Dell Desktop and I also installed it on my Dell notebook computer. I used the dual boot installation procedure and it went great on my desktop but took some effort on my laptop. I am at this point quite satisfied and impressed with Ubuntu.

However, I am unable to get my wireless connection working. I have a DI-524 router and a TEW-424UB Trendnet network adapter for my laptop. Communication is fine when booted into Windows. The network adapter is "dead" when booted into Ubuntu i.e. no steady green LED light or blinking green indicating scanning. I suspect I need an appropriate driver.

In reading posts related to the problem I really don't see a step by step guide for getting it up and running. Being a "newbie" can't understand some of the programs referenced in these threads. I know there has to be some sort of coherent guide indicating the steps e.g. Do this.If it doesn't work do this and you should see this. etc. etc.

Would appreciate some suggestions and links that would point me in the right direction.

Thanks,
Roger

---

### Post by superprash2003 on 2009-04-16
first we need to see which card you have exactly.. post output of the following from the ubuntu terminal
1)lshw -C network
2)iwconfig
3)iwlist scanning

---

### Post by Rog3236 on 2009-04-16
Guess what? I don't exactly know how to do that; i.e. do a copy from the terminal screen to some program/format you would be able to read. What are the steps?

---

### Post by Rog3236 on 2009-04-16
Wow! I got the thing working. I was browsing around and found information about ndiswrapper and the graphic interface (can't remember the program name) and after rebooting the notebook it indicated network was available.

Still don't know how to do a copy and paste of a terminal screen though.

Roger

---

### Post by superprash2003 on 2009-04-17
its just like copy pasting text from one window to another.. highight the text.. right click , click on copy and paste..

---

