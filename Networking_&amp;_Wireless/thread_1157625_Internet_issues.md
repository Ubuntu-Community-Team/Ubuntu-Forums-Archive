---
title: "Internet issues"
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by Cyberhog on 2009-05-12
I really have 2 problems. 

I really have no idea what version of ubuntu I'm using the only thing that I read was it being something like Hardy Heron. (sorry if the Prefix is wrong for the title of the thread)

It shows that I am connected to the local network, but I still can't browse any websites. It was working a while back. I have not made any changes to my network settings either. Here is my second problem. I thought I did something that messed up the whole Operating System so I decided to re download it. Now whenever I restart my computer the DSL settings that I put in previously are gone. 

Any help?

---

### Post by dbuttera187 on 2009-05-12
are you trying to use wireless or ethernet? do you have your dhcp client enabled? when you say redownloaded it do you mean that you reinstalled it onto your PC?

---

### Post by Cyberhog on 2009-05-12
I'm using ethernet. Yeah, I'm pretty sure I have the dhcp client enabled. Yes, that it was I meant. I re installed it onto my PC.

---

### Post by dbuttera187 on 2009-05-13
my buddy had a problem with his dhcp client where he had to go into the connection settings and enter in the dhcp client ID, which for him was dhcp3 and he runs ubuntu jaunty. it was the default client. You might want to see if that needs to be changed or anything. have you thought of upgrading to jaunty or any of the newer versions? i have only been using since intrepid but the experience has been relatively smooth for me, always a couple bumps along the road but pretty smooth. usually the auto eth0 works without any configuring which is why i think it might be the dhcp client id.

---

### Post by Cyberhog on 2009-05-13
Alright, so I'll upgrade to jaunty. I've never really heard up the dhcp client ID though. I'll look into it and post back the results.

---

### Post by dbuttera187 on 2009-05-14
prob a good choice to get jaunty. let me know how that goes for ya.

---

### Post by Cyberhog on 2009-05-16
Alright, so I installed jaunty. I'm using the auto eth0 and it says I'm connected, but I still can't browse and websites. Any other suggestions?

---

### Post by Beanmonster on 2009-05-16
Dan you ping the DSL router?

---

### Post by Cyberhog on 2009-05-16
If I'm doing it right, then yes I can ping the DSL router.

---

### Post by Beanmonster on 2009-05-17
Any success cyberhog?

If you open up a terminal box and type:
```
$ ping {IP Address of DSL router} 
```

Mine is 192.168.0.254

You should get:
```
bean@bean-desktop:~$ ping 192.168.0.254
PING 192.168.0.254 (192.168.0.254) 56(84) bytes of data.
64 bytes from 192.168.0.254: icmp_seq=1 ttl=255 time=6.29 ms
64 bytes from 192.168.0.254: icmp_seq=2 ttl=255 time=0.578 ms
64 bytes from 192.168.0.254: icmp_seq=3 ttl=255 time=0.608 ms
64 bytes from 192.168.0.254: icmp_seq=4 ttl=255 time=0.578 ms
64 bytes from 192.168.0.254: icmp_seq=5 ttl=255 time=0.582 ms

```

If you get a request timed out or other error, then we need to look at your IP.

If you are getting the above then check:

1) Your settings on the actual router i.e. account and password
2) The physical line
3) That your DNS settings in the network manager and on your router correspond with those used by your ISP.

keep us updated :)

---

### Post by Cyberhog on 2009-05-18
When I ping the IP address of the DSL router I get:

```
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=3.68 ms
```

I'm pretty sure that's fine.


Since I'm using the auto eth0 don't the settings just come up automatically in the network manager? (sorry if that's a stupid question, I'm quite new to Ubuntu)

Physical line?

---

### Post by Beanmonster on 2009-05-19
That shows you're connected successfully to your router. :)

by physical line I mean, is the actual dsl line working and connected?

If you're not able to browse, then it is probably DNS settings that need looking at.

DNS (Domain Name System) is located through your ISP and tells your browser where to find the URL/domain you are wanting to lookup. (to put it simple)

Right click on the network manager and select Connection Info. Under auto eth0 you should see all the details and addresses. Write down the 2 DNS addresses.

In firefox, browse to your router ([http://192.168.0.1](http://192.168.0.1)) and find more about your connection status. Usually along with your public IP and gateway you'll find DNS adresses, see if they match the addresses you wrote down (they are supposed to through DHCP) 

Try ping the public gateway that your router is connected to and then the DNS's. 

It could be an account issue so you might want to double check.

To recap: 

[LIST=1]
[*]Your computer is successfully connected to the router
[*]You have been assigned the right DNS's (if you are unsure, ask your ISP for them)
[*]Your router is connected to the internet. (you can tell by the status)
[/LIST]
There is no problem on your side then.

Keep us updated on your progress, would love to see you connected and happy :)

---

### Post by Cyberhog on 2009-05-19
Completely unexpected, but I just came home from school and it's working. I'm seriously confused now.

---

### Post by Beanmonster on 2009-05-20
Thats good to hear, it was most probably an issue with your line or your isp. 

I'm glad you got it working :)

---

### Post by Cyberhog on 2009-05-20
Eh, never mind it stopped working. At least, now I can contact my isp to fix the problem.

---

