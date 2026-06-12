---
title: "Needing help with a wireless problem."
date: 2011-08-12
forum: Networking &amp; Wireless
---

### Post by vampirepsycho85 on 2011-08-12
I got a laptop from a friend for 20 bucks. It's a hp pavilion zd8000. I know its a old beffy machine but thats the reason I got it . I am using it as a tinker machine so I made a small ubuntu partion(20gb) on it, because I wanted to check out the latest install of ubuntu. Well the only problem I am having if you can tell from the title is the wireless. I used the terminal and found what kinda wireless was in and it was broadcom bcm4318. Well I have tried to find out how to install but I am getting confused so I was wondering if someone could help out in steps or something. To make it simpler for me?

---

### Post by vampirepsycho85 on 2011-08-12
Is no one gonna help me  ;_;??

---

### Post by pdc on 2011-08-12
if you do this 

[http://lmgtfy.com/?q=ubuntu+wireless+broadcom+setup](http://lmgtfy.com/?q=ubuntu+wireless+broadcom+setup)

one of the answers is this

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

it says

On Ubuntu 11.04 installing the 'firmware-b43-installer' package takes care of the downloading and installation of the b43 driver. 

have a read; it's your machine you will change; seems to me you need to copy and paste this command; if you have an eth0 cable connected

> sudo apt-get install b43-fwcutter firmware-b43-installer

---

### Post by vampirepsycho85 on 2011-08-12
> **pdc said:**
> if you do this 

[http://lmgtfy.com/?q=ubuntu+wireless+broadcom+setup](http://lmgtfy.com/?q=ubuntu+wireless+broadcom+setup)

one of the answers is this

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

it says

On Ubuntu 11.04 installing the 'firmware-b43-installer' package takes care of the downloading and installation of the b43 driver. 

have a read; it's your machine you will change; seems to me you need to copy and paste this command; if you have an eth0 cable connected

I did it a bit easier way I just looked this up in synaptic pack manager 
 firmware-b43-lpphy-installer well it popped up a few options and I read the descriptions and when i found one in the description that worked with mine i marked it for installation and installed it and now it works grrrrrrrreat!!!! Now I can get to know the new ubuntu the  last one i screwed with was 10.04 and now that i have a laptop to mess with it I will dwell deep into it.

---

### Post by pdc on 2011-08-12
good work

enjoy!:D

---

