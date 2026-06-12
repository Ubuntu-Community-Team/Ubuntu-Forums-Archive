---
title: "Identify process that keeps using internet bandwidth"
date: 2012-07-18
forum: Networking &amp; Wireless
---

### Post by noravanq on 2012-07-18
Hi,

The last several days I have noticed that something is constantly using 2-7KiB downstream bandwidth. I have tried various methods to identify what the process is, but have not succeeded.

Could anyone please advise me how I can do that?

I have search the internet for tools that will monitor the bandwidth, but none have helped. For example nethogs doesn't see that bandwith is being used, unless in situations when I know I am using the internet.

bmon shows the constant usage, but doesn't have the feature to identify the process

netstat doesn't seem to produce anything that could lead me in the right direction.

---

### Post by Cheesehead on 2012-07-18
Do you mean the bandwidth usage is constant 2-7 KB/s 24/7?
Or that some application is using 2-7 KB total sometime during each day? (that doesn't seem like much)

What tool is telling you about this usage?

---

### Post by noravanq on 2012-07-18
Thanks for the reply Cheesehead.

The bandwidth usage is constant 2-4 KB/s sometimes reaching 7KB/s. And it's like this pretty much 24/7. 

System monitor sees this traffic, bmon sees it, nethogs doesn't.

---

### Post by The Linuxist on 2012-07-18
Have you tried iptraf or tcpdump? That would surely give you a better idea. At least figure out what type of traffic it is:
[LIST]
[*]TCP/UDP
[*]which port(s)
[/LIST]
things like that.

---

### Post by noravanq on 2012-07-18
Thanks for the suggestion The Linuxist. I just tried iptraf, and it shows lots of UDP traffic from various ip addresses all starting with 128.237 and various five digit ports, although port 17500 seems to come up a lot. They are 100-400 byte packets.

Any ideas what this means?

Thanks.

---

### Post by Cheesehead on 2012-07-18
Do you happen to have dropbox installed? That's characteristic of dropbox DB synchronizing....

---

### Post by The Linuxist on 2012-07-18
I agree, I see port 17500 open on mine sending UDP stuff all the time as well when dropbox is open.

---

### Post by noravanq on 2012-07-20
I do have DropBox installed, but it's not running. I have set it not to run automatically after a restart, and I hardly ever run it myself.

Today to test something I connected to the internet by tethering to my phone, and to my surprize the UDP traffic stopped. It resumed immediately after I connected back to my work network. 

Thanks for your suggestions.

---

