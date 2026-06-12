---
title: "Slow internet after a while"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by Jellevdwerff on 2009-05-17
Hi there!

Well, first of all, I'd like to say I'm very happy with my new Ubuntu installation. It's just fabulous.

I have a problem, though. My internet connection becomes really slow, after using the internet for about 10 minutes. I have successfully disabled ipv6, but it didn't matter much. Normally, my overall speed is 10mbit (a little more than 1MB/s, in fact). But, after a while, my speed becomes a tenth of my normal speed. That's 1mbit, a bit more than 100 kb/s. It's very frustrating, since I have to reconnect all the time if I want to download files at speed, or internet for a bit. I'm using a wireless connection by the way. With Ubuntu Jaunty and a Linksys WMP54g PCI card. It's not just firefox or something, but the problem accures with every application that uses the internet.

Is there anybody out there with a solution?

Thanks in advance. You people are great, doing all the work for nothing!


Greetings from the Netherlands.

---

### Post by Jellevdwerff on 2009-05-18
I think I have solved it now. My ipv6 wasn't actually disabled. I recompiled the kernel, using this [tutorial]("http://ubuntuforums.org/showpost.php?p=7033690&postcount=9"). And now I've got it up and running again!

Greetings, 

Jelle

---

### Post by Jellevdwerff on 2009-05-18
It's not solved. It took about half an hour now, before it got to 100 kb/s, I reconnected, and now it's up and running again, but of course I don't want to have to do that twice an hour. I'm absolutely sure I disabled ipv6.

Thanks in advance.

---

### Post by binbash on 2009-05-19
I re-wrote my ipv6 blog post, you can find how to disable ipv6 very easily from there : 

[http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html)

---

### Post by alstarno on 2010-06-29
Did you solve your problem Jellevdwerff?
I have the exact same problem. I have a 10mbit line and have always got 800kb/s everywhere. When I upgraded to ubuntu 10.04 I discovered that my internet was way slower than it used to be, and not only on my ubuntu laptop, but on my whole network. It's like my internet is limited to 100kb/s. When I turn of my ubuntu computer, the network is fine for the other computers and I get 8mbit at the speedtest.net.

It helps to reboot my computer. For example I rebooted and installed some ubuntu updates, and download started at 700kb/s, but after a while went down to aprox 100kb/s. And if I reboot and run the speedtest.net I get 8mbit, but if I try 10 minutes later its like 0,8mbit.

I tried the IPv6 fix in firefox, but it didnt work, so I dont think that's the problem.

---

