---
title: "Having some Wireless Troubles."
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by Kyomaru on 2010-07-21
Hello, i am new to ubuntu, and so i dont know much. I want to switch my laptop from XP to Ubuntu, but right now, i cant risk installing it. i dont want to have it partitioned so i can dual boot, so for now i only run the try-it-out mode. 

Before i consider installing though, i want to see if i can get everything to work ahead of time, that way im not regreting instalation. I have a Compaq Presario V2000 laptop, with 55GB hard drive and 516MB ram. So far, the trial mode is working great, but the wireless will not work. Ive tried to install the driver, but i am unable to do so. I have looked this up, and i have tried many things, and so far, none have worked. 

I was wondering if it was just part of the trial thing or not, but it is a Broadcom Wireless BCM4318 driver. if someone could please help me to understand this, i would appreciate it.

---

### Post by corrytonapple on 2010-07-21
What do you mean by "unable to do so"?

---

### Post by Kyomaru on 2010-07-21
> **corrytonapple said:**
> What do you mean by "unable to do so"?

well, when i try to install it, it says that it could not be installed. is it cause im not on the internet perhaps?

---

### Post by corrytonapple on 2010-07-21
Get a wired connection to the internet and then try again.

---

### Post by Kyomaru on 2010-07-22
> **corrytonapple said:**
> Get a wired connection to the internet and then try again.

alright, now it installed, but it says the device is not ready. what now? i think if i can get this working, i will be closer to installing this.

---

### Post by cariboo on 2010-07-22
If you are running from a Live CD, installing the driver isn't going to work, if you reboot. You may be able to get it working if you just restart networking. Open an Applications->Accessories->Terminal and type:

```
sudo service networking restart
```

---

### Post by Kyomaru on 2010-07-22
> **cariboo907 said:**
> If you are running from a Live CD, installing the driver isn't going to work, if you reboot. You may be able to get it working if you just restart networking. Open an Applications->Accessories->Terminal and type:

```
sudo service networking restart
```

well, i tried the code, but it wasnt working. it said:
restart: Unknown instance:

---

### Post by corncob on 2010-07-22
More work, but, if you have room on your HD, you could at first install Ubuntu to dual boot with XP and see if everything is working that way.  If so, you could either delete the XP partition with gparted and expand the Ubuntu partition into the unallocated space, or reinstall Ubuntu selecting the "use entire disk option".

---

### Post by Kyomaru on 2010-07-22
> **corncob said:**
> More work, but, if you have room on your HD, you could at first install Ubuntu to dual boot with XP and see if everything is working that way.  If so, you could either delete the XP partition with gparted and expand the Ubuntu partition into the unallocated space, or reinstall Ubuntu selecting the "use entire disk option".

well, that HD is pretty filled up, cause its been through its share of hardships, so i dont think it has enough space....:(

---

### Post by corrytonapple on 2010-07-22
Well hard drives are cheap now days. Try [newegg]("http://ubuntuforums.org/www.newegg.com") for one.

---

### Post by d3vi1dog562 on 2010-07-22
```

sudo etc/init.d/network-manager start
or
sudo etc/init.d/networking start

then

sudo NetworkManager


```

---

### Post by Kyomaru on 2010-07-22
> **corncob said:**
> More work, but, if you have room on your HD, you could at first install Ubuntu to dual boot with XP and see if everything is working that way.  If so, you could either delete the XP partition with gparted and expand the Ubuntu partition into the unallocated space, or reinstall Ubuntu selecting the "use entire disk option".

well, i've tried to partition it, but only with Disk Mngmt on XP, and i dont see any unallocated space on it. its all a single color bar, and nothing else. do you know any free windows programs that could help? emphasis on FREE

---

### Post by grahammechanical on 2010-07-22
Is there a network manager icon the top of the screen on the right? I recently tried a live CD on my sister's Vista laptop. I was able to connect to the internet. I did not need to install Ubuntu to use the internet.

I just needed (1) to make sure that wireless was switched on in hardware. There was a button which turned the wireless part of the laptop on and off. Saves battery power I think. (2) that Network manager was recognising the wireless electronics in the laptop.  A left click on the network manager icon should show a list of nearby wireless networks. If it does then wireless should be working in Ubuntu. (3) select the correct wireless network (in my case it was my sister's Sky network). (4) The Network manager should then try to access the router. (4) put in the WPA-PSK key when asked to do so. There should be a label on the router giving this. It might have another name, such as wireless key.

It worked for me  - Regards.

---

### Post by corncob on 2010-07-22
My wife had a 300 GB external USB HD hooked up to her Toshiba notebook when I came along and merrily installed Ubuntu on it.  I didn't mean to do it but it installed on the external drive rather than the internal one.  Everything seems okay though -- maybe a little slower but okay.  Maybe an eSATA drive would be better than a USB if your computer has the port and you want to go that route.  I don't know.

---

### Post by Kyomaru on 2010-07-22
> **grahammechanical said:**
> Is there a network manager icon the top of the screen on the right? I recently tried a live CD on my sister's Vista laptop. I was able to connect to the internet. I did not need to install Ubuntu to use the internet.

I just needed (1) to make sure that wireless was switched on in hardware. There was a button which turned the wireless part of the laptop on and off. Saves battery power I think. (2) that Network manager was recognising the wireless electronics in the laptop.  A left click on the network manager icon should show a list of nearby wireless networks. If it does then wireless should be working in Ubuntu. (3) select the correct wireless network (in my case it was my sister's Sky network). (4) The Network manager should then try to access the router. (4) put in the WPA-PSK key when asked to do so. There should be a label on the router giving this. It might have another name, such as wireless key.

It worked for me  - Regards.

well, see, i also run the live CD as well, and have XP as the original OS. when i run XP, the wlan is lit up, but if i run Ubuntu, the light turns off, and i cant turn it back on. Then i install the driver, but i am still unable to connect; in the wireless section of the connections, it says "Device Not Ready"

---

### Post by corncob on 2010-07-22
> **Kyomaru said:**
> well, i've tried to partition it, but only with Disk Mngmt on XP, and i dont see any unallocated space on it. its all a single color bar, and nothing else. do you know any free windows programs that could help? emphasis on FREE

When I had XP I remember opening "My Computer", left clicking on drive C, then properties, and getting a pie chart showing used and free space.

---

### Post by corncob on 2010-07-22
> **Kyomaru said:**
> well, see, i also run the live CD as well, and have XP as the original OS. when i run XP, the wlan is lit up, but if i run Ubuntu, the light turns off, and i cant turn it back on. Then i install the driver, but i am still unable to connect; in the wireless section of the connections, it says "Device Not Ready"

Try entering in the (Ubuntu) Terminal
```
rfkill list all
```
If something is blocked type
```
sudo rfkill unblock all
```

---

### Post by Kyomaru on 2010-07-22
> **corncob said:**
> Try entering in the (Ubuntu) Terminal
```
rfkill list all
```
If something is blocked type
```
sudo rfkill unblock all
```

well, i typed it in, and it says:
Soft Blocked: no
Hard Blocked: no

...... @_@

---

### Post by corncob on 2010-07-23
> **Kyomaru said:**
> well, i typed it in, and it says:
Soft Blocked: no
Hard Blocked: no

...... @_@

It was just a thought I had.

---

### Post by Kyomaru on 2010-07-23
> **corncob said:**
> It was just a thought I had.

well, every thought helps. really, just so long as i can get it running, i know ill be able to get it working if i install ubuntu. i know its difficult to give these instructions to someone who;s only running the liveCD right now, but i appreciate all the help.

---

### Post by Kyomaru on 2010-07-24
Well, so, i just decided to switch to Ubuntu, wireless or not, cause my parents moved our desktop and ran a new ethernet cable to it in its new room, leaving an open one for this laptop. It was just so much easier to do than all of the trouble i was going through.

---

### Post by Kyomaru on 2010-07-24
alright, so today i tried my wireless and its working now. i thank all of you for trying to help me out (even if all i had to do was take the plunge). really, i appreciate it so much. thank you *bows*

---

