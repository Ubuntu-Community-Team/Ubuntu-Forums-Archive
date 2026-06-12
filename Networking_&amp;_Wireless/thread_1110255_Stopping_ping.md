---
title: "Stopping ping"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by Robbyx on 2009-03-29
I have just run the shieldsUP! all service ports test scan and whilst all my ports are stealthed I am advised that I should stop my computer responding to ping. Is there an easy way to do this?

Robin

8.10

---

### Post by PhrankDaChickenGeek on 2009-03-29
You can add following line to /etc/sysctl.conf file:

```
gksudo gedit /etc/sysctl.conf
```


Append following line to:
```
net.ipv4.icmp_echo_ignore_all = 1
```

You'll need to reboot for it to take effect, or run the following:
```
sudo su
echo "1" > /proc/sys/net/ipv4/icmp_echo_ignore_all
exit

```

---

### Post by Robbyx on 2009-03-29
Thank you for your helpful reply. I have followed your advice and also adjusted my firestarter settings to stop a response to pinging but it seems that something is still responding. Here is the error message:

> 
Ping Reply: RECEIVED (FAILED) &#8212; Your system REPLIED to our Ping (ICMP Echo) requests, making it visible on the Internet. Most personal firewalls can be configured to block, drop, and ignore such ping requests in order to better hide systems from hackers. This is highly recommended since "Ping" is among the oldest and most common methods used to locate systems prior to further exploitation.

I have looked in the web address of my router and it does not seem to be telling me that it is set to auto respond to pings, but then I do not know where to look specifically for that setting. I just went through them all looking for likely candidates.

Can you please give me some further suggestions to  how I can stop the ping response?

Robin

PS I have rebotted and it made no difference to the scan results.

---

### Post by cariboo on 2009-03-29
If you are using a router the ping response that Shieldsup is refering to is from your router. Shieldsup only checks your router, it does not have the ability to check anything behind the router. 

I have a Linksys wrt54gs and it has the ability to disable ping response in the router management console.

Jim

---

### Post by Robbyx on 2009-03-30
Thank you for your response re the router. I can not find an appropriate setting to turn off the ping response so  I have just sent a message to my ISP for guidance.

R

---

### Post by coutts99 on 2009-03-30
> **Robbyx said:**
> Thank you for your response re the router. I can not find an appropriate setting to turn off the ping response so  I have just sent a message to my ISP for guidance.

R

What kind of router do you have?

---

### Post by Robbyx on 2009-03-30
> **coutts99 said:**
> What kind of router do you have?

Its a Thompson  780WL also known as a Speedtouch.

Robin

---

### Post by zaphodbblx on 2009-03-30
one downside is some of the speed tests wont work without responding to ping...

---

