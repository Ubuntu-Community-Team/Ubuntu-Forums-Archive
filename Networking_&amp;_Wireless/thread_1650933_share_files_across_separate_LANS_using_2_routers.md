---
title: "share files across separate LANS using 2 routers"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2010-12-22
I have 2 routers, each are assigning IP with DHCP on.
One router is plugged into cable modem
second router is downstairs plugged into first router. Wire runs in WAN of second router.
Each router has its own IP subset. 
First router assigns IP's to 192.168.1.xxx
second router IP's to 10.0.0.xxx

I know I can use the second router as an AP with DHCP OFF.
BIG BUT though is my wifi verizon phone got no IP assigned when running like that and wirelessly connecting to the second router. Laptops were just fine.
SO, I reconfigured second router with its own subset IP being handed out. Now verizon phone is perfect.

How can I share files between connected PC's using it this way?
Makes no sense on the phone issue, but it is what it is and I would like it to work like I think it should work, is that too much to ask from these software engineers?

---

### Post by Grenage on 2010-12-22
Can you configure the two routers to use DHCP while on the SAME subnet, but using different scopes?

Example:

Router A: 192.168.1.1, DHCP scope 192.168.1.2-49
router B: 192.168.1.50 DHCP scope 192.168.1.51-99

Can you specify a gateway on the router B's DHCP config, or does it default to itself?

> Makes no sense on the phone issue, but it is what it is and I would like it to work like I think it should work, is that too much to ask from these software engineers?

Alas, most of these units are for home gateway use; they have only one purpose in mind.  The more advanced configs are 'normally' limited to business models, but you can often hack your way around stuff.

---

### Post by CharlesA on 2010-12-22
Moved to *Networking & Wireless.*

It gets complicated when things are on different subnets.

If I hook up a router to my working network using one of the LAN ports, and turn DHCP off on that router, it will act as an access point.

In short, hook up router #2 to router #1 using a LAN port on router #2. Try that and see if it works.

---

### Post by sdowney717 on 2010-12-22
> If I hook up a router to my working network using one of the LAN ports, and turn DHCP off on that router, it will act as an access point.

That is how it was for a few years. BUT, the new wifi phone I got, a kin2m, was having troubles. It would connect but never get an IP number assigned.
Upstairs gateway router was ok, it worked, but it needs to work downstairs and the netgear router has a better signal everywhere.

So I would like to possibly share files and apparently I cant have it all work, even though I should be able to have it all work.

If anyone knows how to share files or folders across different LAN's please let me know.

One of the issues used to be watching video shared on the LAN, I dont do it now, but might like to again.

---

### Post by Grenage on 2010-12-22
Use a static IP on the phone, or look at what I posted earlier.  Subnets aren't usually a problem, you just need to ensure that routes are correctly configured.

---

### Post by CharlesA on 2010-12-22
Have you tried using another wireless device to connect to the netgear?

Does the same thing happen if you use a wired connection on the netgear?

I doubt it's the phone that's the problem. It should "just work."

---

### Post by sdowney717 on 2010-12-22
[https://secure.logmein.com/products/hamachi2/](https://secure.logmein.com/products/hamachi2/)
found this free windows software.

It mentions setting up a VPN, so does linux setup VPN's?

any useful links?

---

### Post by sdowney717 on 2010-12-22
> Have you tried using another wireless device to connect to the netgear?

yes, my daughters XP laptop always connected without any problems as I was trying different things with the routers.

Weirdly, when using the Gateway upstairs router as the DHCP on, it would assign IP to the laptop thru the netgear router ok, but the phone would connect and never get an IP, just 0.0.0.0 or if left sitting a long time, a totally erroneous useless unrelated IP would be listed in the phone.

---

### Post by CharlesA on 2010-12-22
0.0.0.0 is listed when the device has no ip address.

Would it get something like 169.254.x.y ?

---

### Post by sdowney717 on 2010-12-22
yes, I think so.
the router was supposed to give out 192.168.001.xxx

---

### Post by CharlesA on 2010-12-22
Yep, the 169.254.x.x address is an APIPA - the device gets that if it cannot contact a DHCP server. You can try giving the device a static IP and seeing if it can connect to the internet and go from there.

That would be a whole lot easier then doing the whole "two seperate networks" thing.

---

### Post by sdowney717 on 2010-12-22
interesting idea. I dont think it can be done but I will check.

kin2m manual is here
[http://pcdphones-client.s3.amazonaws.com/files/667/English_Manual.pdf](http://pcdphones-client.s3.amazonaws.com/files/667/English_Manual.pdf)

---

