---
title: "Can't connect to the internet with ppp0 while eth0 is active"
date: 2010-07-02
forum: Networking &amp; Wireless
---

### Post by Alan502 on 2010-07-02
HI, please help me this can't be too difficult :P

My machine has Ubuntu 10.4, installed a week ago. I'm connecting to the Internet with a Wireless 3G modem, the interface is named ppp0. Additionally, I have a network card that is connected to a home router, that's eth0. Everything works fine with eth0 disabled, all my apps can access the internet correctly. But, my issue is that when i enable eth0, i can't access the internet with any app.

So why do i need eth0 anyway? The thing is that i must share my internet connection with my sister, who is also connected to our home router. I planned to give her access by installing squid on this machine and configuring her browser to connect to squid. However, since none of my apps can connect to the internet while eth0 is active (whereas squid and all other apps work fine with eth0 disabled) I can't let her connect to squid while squid is working correctly.

Please help! It will be very appreciated :D Ask if i didn't leave anything clear!!


BTW selecting "use this connection only for resources on its network" under "routes..." of the ipv4 tab of "Auto Ethernet" made it a little better. Firefox and Xchat started to work with eth0 active. Squid still doesn't work though (althought it works just fine with eth0 disabled)

---

### Post by Iowan on 2010-07-02
Have you seen [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") ICS help page?  I suspect that when eth0 is active, **route -n** will show it as the default gateway. You might be able to change that in Network Manager.

---

### Post by dvn3ch on 2010-07-02
@Alan502

I am not positive but this link may help you...[https://help.ubuntu.com/community/SharingMobileBroadband](https://help.ubuntu.com/community/SharingMobileBroadband)

I believe that you are trying to use your computer as the connection to the Internet and route it through a router that your sibling is using to gain access to the Internet as well.  Is that right?  If so, I believe the link above will help you through your ordeal.

---

### Post by dvn3ch on 2010-07-02
@Iowan

That is a good reference page but he did say that he was using a _3G modem_ (mobile broadband) which has its own set of rules from wired and WiFi cards.

I believe that [this]("https://help.ubuntu.com/community/SharingMobileBroadband") is a better source for what he is trying to do, it even mentions squid, too.

---

### Post by Alan502 on 2010-07-02
Thanks for your replies :D

Yeah, I have already checked the ICS ubuntu help page and it is not too useful. 

That link is excellent, although it mentions wvdial. I had already heard of wvdial and tried it some time ago but i couldn't get it to work with my modem. The article mentions ubuntu 8.10 too, where NetworkManager did not support mobile broadband. What would change if instead of wvdial i'm just using NetworkManager?

---

