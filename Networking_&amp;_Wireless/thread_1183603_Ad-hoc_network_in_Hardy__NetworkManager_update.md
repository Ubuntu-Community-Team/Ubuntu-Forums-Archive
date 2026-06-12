---
title: "Ad-hoc network in Hardy / NetworkManager update?"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by Karaden on 2009-06-10
A few days ago, my mother bought a Toshiba NB100 netbook running Ubuntu Netbook remix. We've been pretty happy with it overall, apart from one minor little issue - I'd love to hear if anyone has any suggestions.

We were hoping to be able to use a Nokia N95 running JoikuSpot for internet access on the go. My laptop running Jaunty connects to and uses JoikuSpot's ad-hoc network with absolutely no problems. However, the netbook is running Hardy, and while we've managed to get it detect the network, connecting and using the internet is a different matter :(

From what I've read while researching this, it seems that Hardy has problems with ad-hoc networks in general. I had been hoping to keep the netbook on Hardy, with it being the most recent LTS release. (My mother is very new to Linux, so I'd like to keep things as simple and stable as possible.)

I was wondering if installing the most recent version of NetworkManager would add support for ad-hoc networks? Or would it make more sense to bite the bullet and install Jaunty? (If anyone has any experience with doing this on the NB100, I'd be interested to hear your experiences...)

Thanks in advance!

---

### Post by superprash2003 on 2009-06-10
yes , it does [https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

---

### Post by Karaden on 2009-06-10
Thanks for the link - however, unless I'm missing something, most of the document is regarding creating an ad-hoc network. JoikuSpot is providing the network - I am having trouble *connecting* to it. 

I updated NetworkManager to version 0.7.1 - still no dice. Have I missed something that also needs to be updated?

**Edit:** In case anyone in the future has a similar problem - I never got it working under Hardy. However, when I eventually upgraded to Jaunty, it worked out of the box. :)

---

### Post by celticbhoy on 2009-11-08
> **Karaden said:**
> Thanks for the link - however, unless I'm missing something, most of the document is regarding creating an ad-hoc network. JoikuSpot is providing the network - I am having trouble *connecting* to it. 

I updated NetworkManager to version 0.7.1 - still no dice. Have I missed something that also needs to be updated?

**Edit:** In case anyone in the future has a similar problem - I never got it working under Hardy. However, when I eventually upgraded to Jaunty, it worked out of the box. :)

Can you pass on your setup phone & ubuntu / free or premium edition

keep getting a flakky conection & have to re-connect constantlly

---

### Post by Karaden on 2009-11-08
We've been using JoikuSpot Premium edition (2.50) on a Nokia N95, with Jaunty and Karmic on both the normal release and the netbook remix.

The setup on JoikuSpot is usually set to:
Access point: always ask
Channel: 1
Encryption: none
Battery threshold: minimum
Landing page: no
GPS: no

Hope that's of some help.

---

### Post by celticbhoy on 2009-11-08
so far i have only tried the free edition - guess that night be the problem. It worked well on linpus on the AAO

---

### Post by Karaden on 2009-11-08
Well, we already had premium edition before we got the Netbook, so I never tested the free edition with Ubuntu. However, my father did use it with Windows XP, and said that there was defintely a noticeable improvement with the premium version... ymmv, of course.

---

### Post by aaronnn on 2009-11-19
hi,
I also met this problem in ubuntu 9.10.
I can not conenct to Ad-hoc network, but i can connect to AP network. it is very strange.
I also tried to instal wicd to verify and set IP by manual, it is the same.
So could anyone can help on this?
I am using Realtek 8187B wlan card.
Thanks.

---

