---
title: "lousy bandwidth"
date: 2012-12-03
forum: Networking &amp; Wireless
---

### Post by conradin on 2012-12-03
Hi all,
I pay for 3Mbps service at my home, but it seems I never get that, or anything close. I have DSL, that connects to a zhone modem, then to a belkin N type router. whether I am on ethernet, or on wifi, I cna expect to get 300kbps tops. This doesnt change even if I ditch the router, and connect directly to the modem. 

I have tried the speed test services, which all state that I am getting ~2.7Mbps. Although that is clearly not the case. The only thing I can think of is that the modem is giving incorrect information about the speed. 
Whats more, is I cannot access the Modem (provided by the ISP). The information in the user manual is incorrect, the manual states that the IP should be 192.168.1.1 but it is actually 10.255.252.1 even after reset. So far I am unable to login to the modem to check the settings. 

Does anyone have any input? I am thinking about buying a modem/ wireless router in one. I am very sketched out that there is hardware in my house that I cannot get into. Has anyone had similar issues with thier DSL modems, or service providers?

---

### Post by ahallubuntu on 2012-12-03
On what basis do you believe you are getting only 300 Kbps?  Do you mean 300 KBps (Bytes per second)?  Sometimes download speeds are cited in bits per second (bps) and sometime Bytes per second (Bps).  As 1 byte = 8 bits, if you were seeing 300KBYTES per second, that's 2.4MBITS per second or close to what your ISP and speed tests say.

Further, your real DSL speeds rarely get to the full maximum.  I think if you read the fine print, the DSL company doesn't promise you'll get the full 3Mbps, only UP TO that.  Of course, you shouldn't be getting 300KBITS per second but 300 KBYTES per second sounds not too far off.

No, I don't see how buying another modem will help unless there's truly something wrong with the one you have.  I assume you've contacted the DSL company to ask about that?

---

### Post by conradin on 2012-12-03
On the basis of speed checks done inside the home network. 
From outside, the modem seems responsive. Inside the network, 300kbps.
```

wget --output-document=/dev/null http://speedtest.wdc01.softlayer.com/downloads/test500.zip

```
I mean, I use it, I know its garbage. Firefox will tell me. 

form the outside, the connection looks good. Inside, its junk. see attached.
Running the same type of test, from the same website, [http://speedtest.wdc01.softlayer.com](http://speedtest.wdc01.softlayer.com)
which is the one suggested by my ISP, it states that my connection is great.

In application, i never see more than ~300Kbps. 
Im not sure whether a new modem or switching ISPs will fix the problem, but Im certainly not getting what I'm paying for as is. 

Or perhaps its a funky setting in my modem. I'm not sure. I cant get into the thing, so I have no idea.

Anyone have experience or ideas about how to get into a modem which you are connected? I cannot find a administration interface. ... How Might I find one? I mean, it must have an administrator interface right?

---

### Post by TheFu on 2012-12-03
Available bandwidth is determined by every piece in the chain between your computer and the other server.  If speedtest shows 2.7Mbps, I tend to think the issue is outside your DSL connection.

Many servers on the internet will limit download speeds from a single IP to allow multiple clients to have bandwidth.

Try downloading something from a well connected, local, University with huge pipes.  I know that my local uni - Georgia Tech - limits bandwidth to a little over 1Mbps for downloads, at least for people outside their WAN, yet it is by far the highest bandwidth that I can use for testing outside Speedtest-like locations.

As to whether you have access to the administrative part of a modem provided by your ISP - that is doubtful. ISPs have learned that giving end-users access to CPE - Customer Premise Equipment - is a bad idea.  99.999999% of customers have no interest or skill with modems, so it is best to not even all the access.  If you are certain there is an issue, call the ISP and have them run a remote test of the device.  Most ISPs have fairly thorough remote testing capabilities and can see issues that you and I cannot.

If you test with 20 different websites known to have huge bandwidth and still see the problem, complain to the ISP louder. Try to get a refund for the missing bandwidth, and strongly consider switching to an ISP that actually provides "at least" the bandwidth promised, not "up to" the amount. I did a speedtest of my ISP a few days ago and saw 25/25 - up/down.  I only pay for 16/3.

---

### Post by Cheesemill on 2012-12-03
I think you are getting confused between b (bits) and B (bytes).

ISP's usually quote speed in b/s whereas most software and OS's report speeds in B/s. As there are 8 bits in a byte then 3Mb/s is around 375kB/s.

So you can see that your speed is fine, you are getting just under the ISP's quoted speed which is normal.

---

