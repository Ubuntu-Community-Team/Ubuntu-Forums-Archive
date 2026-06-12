---
title: "ubuntu hacked??"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by Hombal on 2009-08-03
Hello,

I am newbie to the ubuntu and facing a problem. I am using ubuntu for around 6 months now. Mainly for browsing..

Now I am facing a problem with my broadband data usage. my downloaded data usage shows that lot of data got downloaded even without me downloading anything significant..

I am not sure if my ubuntu is hacked or I have downloaded some malicious software which is downloading lot of data.. :confused:

Please help me... How can I check which program is downloading the data or where is the data downloaded to...

Thanks in advance
Hombal

---

### Post by SuperSonic4 on 2009-08-03
I would ask your ISP for usage logs over the time period which you suspect it to be happening in

---

### Post by sasho_zl on 2009-08-03
you can use **netstat -at **command to check your active connections.  That command will tell you  the process name - **lsof -i -n -P**
Also one good firewall won't hurt.

---

### Post by Hombal on 2009-08-05
Thanks for the hint for installing firewall..  With it i could monitor my ports..

I tried to install firewall - firestarter... it is giving following error:
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/f/firestarter/firestarter_1.0.3-6ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/f/firestarter/firestarter_1.0.3-6ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.46 80]


I have gutsy 7.10.. 

Can anyone please help me? Is it a very old version of firestrater??
When I select this package and want to force installation in the synaptic.. the force thing is disabled.. why is it so?

Which is the version of firestarter which works with gusty

Thank you!!

---

### Post by wojox on 2009-08-05
Try ufw - Uncomplicated Firewall.

```
sudo ufw enable
```

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

---

### Post by Crafty Kisses on 2009-08-05
I'd suggest you use Wireshark to see what's actually going on. If your connection is acting slow, it sounds like somebody may be ping flooding your modem.

---

### Post by suevy Suavae on 2009-08-05
Ubuntu comes with a built in fire wall. Just go into a terminal (Applications > Accessories > Terminal) and type "sudo ufw enable" (without quotes), then put in your password.

---

### Post by tomasrey88 on 2009-08-05
The downloads may just be the regular downloads that you get as updates to the operating system and installed software. Best firewall is a hardware firewall. They are impossible to hack, software firewall are hackable if you know what software is being used. 

I use a LAN router. Wireless communications are also hackable, especially smaller wep keys on older computers. 

Go through the hard drive and look through all the files or just wipe the drive clean and start over, if you are concerned.

Unless you're running stuff in root or using your computer as a server or constantly ftp ing then you should be fine. It's probably just the updates.

---

### Post by Warren Watts on 2009-08-05
Are you using a wireless network?  If you have an unsecured wireless network, someone nearby could easily be using your network to connect to the internet via your wireless network.

---

### Post by Hobgoblin on 2009-08-05
> **Hombal said:**
> 
Now I am facing a problem with my broadband data usage. my downloaded data usage shows that lot of data got downloaded even without me downloading anything significant..

What is "a lot of data", and over how long?

How do you connect to the internet?

Do you watch a lot of videos (such as Youtube) or listen to online radio? Both will count as downloading, as will every web page you visit.

---

