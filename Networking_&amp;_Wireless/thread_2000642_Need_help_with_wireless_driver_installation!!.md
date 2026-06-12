---
title: "Need help with wireless driver installation!!"
date: 2012-06-09
forum: Networking &amp; Wireless
---

### Post by sattmullivan on 2012-06-09
Hi, this is my first post, I am new to ubuntu today and I need help.

I replaced windows with ubuntu on my computer and cannot get the wireless internet to work. I do not have access to a wire connection, so wireless is my only means of getting online.  

I think i found the solution to my problem here, [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) , but I am too stupid to understand exactly what to do.

I scrolled down to the the part labeled "b43 no internet access", but I got very confused immediately. It tells me I need to install b43-fwcutter and patch from the install media, but i have no idea what the install media is. Then tells me to go to  "../pool/main/b/b43-fwcutter/" which again i have no idea where that is...

I hope this is an easy fix, so if anyone here knows what to do  and can help me I would greatly appreciate it. I replaced my os today but now cant get on internet... please help!!

---

### Post by chili555 on 2012-06-09
Let's make sure exactly what you need. There are four or five ways to get some Broadcom drivers working. Let's double-check before you waste time. Please open a terminal and run: ```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

Please post the result and we'll proceed.

---

### Post by sattmullivan on 2012-06-09
Thank you so much for the reply, here is what happens when i type that in:

03:00.0 Network Controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

Thanks again!

---

### Post by chili555 on 2012-06-09
You're in luck, sort of. There are *two* possible ways to get this going. Let's try the quick and easy method first. Download the file I've attached and transfer it on a USB key or similar to the desktop of the Ubuntu machine. Right-click it and select *Extract Here*. Now open a terminal and do:```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
```Now we unload the driver and reload it so it sees and grabs the hopefully correct firmware:```
sudo modprobe -r b43
sudo modprobe b43
```If your wireless doesn't spring to life, please run and post:```
dmesg | grep b43
```

---

### Post by sattmullivan on 2012-06-09
Yes that worked! Thank you so much!!

My wireless sprung into life and I was successfully able to connect to the internet. So I then shut down the computer and turned it back on. When it restarted there was again no wireless connection, so I did the modprobe -r b43 then the modprobe b43 and it worked again.  

Any thoughts on this? Am I going to have to run this code every time I start the computer or is there an easier way?

---

### Post by chili555 on 2012-06-09
> Am I going to have to run this code every time I start the computer or is there an easier way?Please try this one-time fix:```
sudo su
echo b43 >> /etc/modules
exit
```Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by sattmullivan on 2012-06-09
Alright! Another fix!! I am forever in your debt chili555 ;)

Now that i have internet access I should download and install all the updates available to me? I only ask because i don't want to mess up the wireless that you just fixed for me.

---

### Post by sattmullivan on 2012-06-09
Also , do i need to keep the b43 folder in my desktop or can i delete it?

---

### Post by chili555 on 2012-06-10
> **sattmullivan said:**
> Also , do i need to keep the b43 folder in my desktop or can i delete it?You can safely delete the folder and the zip, but you might consider transferring them to a CD along with these instructions so you'll have it instantly available in case you ever need to reinstall.

---

