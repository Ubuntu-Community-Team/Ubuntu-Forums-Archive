---
title: "Im connected but not connected ?!?"
date: 2011-08-14
forum: Networking &amp; Wireless
---

### Post by Rythemz on 2011-08-14
I'm 1000% new to Ubuntu but i configured my wired connection and i have the two arrows at the top right. It says im connected but when i try to acess anything it says im not. 
Please help me its fairly Urgent.

---

### Post by Actonix on 2011-08-14
You need to provide more info. 

How did you configure your connection ?

Are you using DHCP or is it manually configured ?

---

### Post by Rythemz on 2011-08-14
Manually what else do you need?

---

### Post by varunendra on 2011-08-15
If you configured it manually, can we have a look at the configuration details? Like IP address, subnet, gateway and dns.

These commands will provide us all of these:
```
ifconfig
route -n
cat /etc/resolv.conf
```

Just open a terminal, enter these commands one-by-one and paste their outputs in your new post. For better readability, select the pasted text and click on the # symbol at the top of the edit box where you create/edit your post. Doing this will automatically create [ code] and.. [ /code] tags around the selected text (you can also type them manually if you wish).
Keep each output in a different 'code' tag set.

These may help determining some external factors also:
```
sudo dhclient
```
(whether a dhcp server available or not on your network)
```
nslookup google.com
```

---

### Post by Actonix on 2011-08-15
> **Rythemz said:**
> Manually what else do you need?


Provide further details as adviced above - more might be required, really all depends on your setup and how things progress, one needs to check on how you have installed things and take it from there

It could simply be down to wether your Wireless connection is password based or using WEP or the mode in use "Infrastructure Mode" or "Ad Hoc", possibly even down to how your router is setup if you have one, might be setup up as a Gateway or is just a Router, does it provide DNS or are you setup to use another DNS server (your ISP's or a free one), there are quite a few things that can get in the way of your connecting to the internet  - but let's just take things step by step and not look to deeply into possible causes - might also help to know if you have successfully connected this way before or if this is a first attempt

---

### Post by Rythemz on 2011-08-16
**When i type ifconfig a couple ip's come up**

---

### Post by Rythemz on 2011-08-16
Can somebody please help me thank you.

---

### Post by varunendra on 2011-08-16
In order to help you, we need the outputs I asked for in my previous post. Please read it thoroughly and post accordingly.

---

### Post by Furball588 on 2011-08-16
Since you configured manually what did you enter for an IP, a subnet mask, a DNS server and a default gateway?

---

### Post by Rythemz on 2011-08-16
For the first one nothing comes up at all.

the seccond
;; connection timed out; no servers could be reached

---

### Post by Rythemz on 2011-08-16
THere can you help me now please

---

### Post by AlexDudko on 2011-08-16
You definitely do something wrong. Output of the first command should have at least information about lo interface even if there's no network connection at all.

---

