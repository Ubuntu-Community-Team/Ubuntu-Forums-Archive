---
title: "Periodic Network Stalls"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by divot_powell on 2010-04-05
Hi,

I have ubuntu karmic installed on my Toshiba A300 laptop which is having some issues. Ever since I upgraded to karmic my networking periodically stalls for 15-30 seconds. It happens around once every 1 to 5 minutes and is causing me a large amount of frustration for example when playing videos off of a networked drive.

At first I thought this was due to a bug in my wireless card but the same thing is happening when I use a cabled connection or going through my phone using usb.

I don't know where to begin with this one, does anyone have any advice that might help me track this down? I can upload any information you need..

Cheers,

Dan

---

### Post by jaakan on 2010-04-05
What is your wireless router?
Did you have any issues with older versions of Ubuntu?
Does your wireless work on installed or do you have to get the driver and which driver and model of your wireless in your laptop?

---

### Post by divot_powell on 2010-04-06
> What is your wireless router?

Netgear WRT624v3 at home. But I don't think it's a problem with that as I'm connecting into other routers around the place (uni, coffee shops etc) and it happens there too. I also use my HTC Dream (T-Mobile G1) to tether which also has the same issues.

> Did you have any issues with older versions of Ubuntu?

Nope, I've used every version of ubuntu since Hardy on this laptop and never had this problem.

> Does your wireless work on installed or do you have to get the driver and 
> which driver and model of your wireless in your laptop?

It works from installed. lspci tells me it's a: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61). Pretty certain it's the first.

---

### Post by mbehamin on 2010-04-06
hi 
im not sure what exactly your problem but try to adjust your MTU into 1460 bytes. 
it may helps you im not sure (it happens under heavy load connection traffic!!!)

regards

---

