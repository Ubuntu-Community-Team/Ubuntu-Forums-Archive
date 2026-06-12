---
title: "gathering wireless environment information"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by executorvs on 2009-09-09
two of my friends live in the dorms on my university's campus. I was attempting to scan for the wireless information of both APs and other wireless computers. this would allow me to show them which of the campuses APs (which operate as a WDS) are on frequencies being used less than others.
while I can get info on the APs using sudo iwlist wlan0 scan this doesn't show me the whole picture. years ago in windows I used netstumbler which was simple to use. some people have suggested I use prismstumbler, however I cannot get it to output anything.

I would appreciate any info be it program names or terminal commands which would help me detect the other laptops and any devices which may be passively broadcasting.

my dinner is riding on me getting them wireless.. so please, help a hungry student.

---

### Post by derrick1985 on 2009-09-11
> **executorvs said:**
> two of my friends live in the dorms on my university's campus. I was attempting to scan for the wireless information of both APs and other wireless computers. this would allow me to show them which of the campuses APs (which operate as a WDS) are on frequencies being used less than others.
while I can get info on the APs using sudo iwlist wlan0 scan this doesn't show me the whole picture. years ago in windows I used netstumbler which was simple to use. some people have suggested I use prismstumbler, however I cannot get it to output anything.

I would appreciate any info be it program names or terminal commands which would help me detect the other laptops and any devices which may be passively broadcasting.

my dinner is riding on me getting them wireless.. so please, help a hungry student.

I too am looking for the exact same thing. I was watching a podcast the other day, and they showed a nice windows program called inssider. Were you ever able to find a linux equivalent?

---

### Post by executorvs on 2009-09-11
no, not yet. a gui utility would be nice but I can't even find a terminal command which tells me all I need.

are you familiar with the commands:lshw -C network, dhclient, iwlist, ifconfig, and iwconfig?

they provide a great amount of info, but not everything I listed above.

---

### Post by chili555 on 2009-09-11
```
sudo apt-get install kismet
```It requires some configuration. You can search the forum and find out all about it. I have explained it a few times.

---

### Post by executorvs on 2009-09-11
I passed on kismet because when I looked on the description it said wireless b. does it also handle G networks?

---

### Post by chili555 on 2009-09-11
It says '802.11b' however, when you see max rate 54.0, you know it's also an 802.11g network. Please see attached.

---

### Post by derrick1985 on 2009-09-11
Actually,I just found one via the forums, works pretty good. 

[http://kuthulu.com/iwscanner/](http://kuthulu.com/iwscanner/)

---

### Post by executorvs on 2009-09-11
I'll take look at both a little later. I installed kismet, but it appears to need some configuration. I'm to hungry/tired for that right now.

---

### Post by executorvs on 2009-09-12
I found that iwscanner doesn't seem to detect wireless security correctly and seems to make a few other errors.. haven't tried it on a different set of hardware yet, but I will later. what was your experience?

---

### Post by derrick1985 on 2009-09-13
> **executorvs said:**
> I found that iwscanner doesn't seem to detect wireless security correctly and seems to make a few other errors.. haven't tried it on a different set of hardware yet, but I will later. what was your experience?

Haven't tested it thoroughly yet, but it picked up my local wireless network and encryption correctly, as well as found an access point that I was unaware existed in my vicinity. But, i'm not sure how well it will work with my wireless card (AR928) as I can't run my router in N mode without my connection crapping out all the time, not sure if it's the routers fault or my card. Going to have to ask around a bit. 

First impression of the program gives it some promise, further testing to see if it will stay installed, is still needed.

---

### Post by executorvs on 2009-09-13
I'm using a newer draft-N card. I've got an unsecured and a WPA connection in my house and it is telling me my wpa is wpa2 and my unsecured is wpa.. it's odd

---

