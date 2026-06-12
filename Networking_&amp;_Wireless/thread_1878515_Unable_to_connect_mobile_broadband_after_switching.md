---
title: "Unable to connect mobile broadband after switching from Ubuntu 11.10 to Xubuntu 11.10"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by ask_ on 2011-11-09
Hello.

I have a Reliance Netconnect internet card , the data card is manufactured by Huawei technologies.

I have a relatively old PC. I had installed Ubuntu 11.10 on it. I could successfully connect to the internet via the above connection. I had created the connection from the edit connections bar.

But since my PC was reacting slowly in general to Ubuntu I switched to Xubuntu 11.10 . I deleted Ubuntu install and re-installed Xubuntu. I created a connection in Xubuntu using same method as above , but the OS is not detecting the data card. In Ubuntu when creating new connection , it detected the data card What to do so that the connection works in Xubuntu as well ?

---

### Post by RedSingularity on 2011-11-09
Is it a USB device or a PCMCIA device?  Also, If you boot the xubuntu live CD, does it detect the device properly?

---

### Post by ask_ on 2011-11-09
It's a USB device. I have installed Xubuntu now on the PC.Forgot to check from Live CD . Note , USB device is detected as seen by lsusb command. But while creating network connection it wasn't detected.

In Ubuntu , it detects the USB device while creating network connection , & it skips the step where bill plan is asked. Xubuntu is not detecting the USB device and is asking bill plan. In Xubuntu , the option it shows is create this connection for any device. While in Ubuntu it showed the name of the particular device.

result of lsusb command :-
```
Bus 004 Device 007: ID 12d1:1412 Huawei Technologies Co., Ltd. 
```

---

### Post by RedSingularity on 2011-11-10
Can you boot into the live CD with the adapter plugged in?  No need to reinstall, just run a live session with the adapter plugged in and see if the machine recognizes it.

It has been built into the linux kernel since 2.6.20 so it should be working.  If you turn off the computer with the device plugged in and then boot into a live CD session, it may be recognized correctly.  I am assuming it was not plugged in when you installed xubuntu.

---

### Post by ask_ on 2011-11-10
I was hoping that Xubuntu would give better speeds than Ubuntu on my old PC. But it seems even Xubuntu was too much for it. So installed Lubuntu on my old PC.

> **RedSingularity said:**
> Can you boot into the live CD with the adapter plugged in?  No need to reinstall, just run a live session with the adapter plugged in and see if the machine recognizes it.

It has been built into the linux kernel since 2.6.20 so it should be working.  If you turn off the computer with the device plugged in and then boot into a live CD session, it may be recognized correctly.  I am assuming it was not plugged in when you installed xubuntu.

This time around I did check whether Live CD (of Lubuntu) detects the device. And it did. So went ahead with the install of Lubuntu.Does Live CD detection help to detect device after install as well ? I thought Live CD trial doesn't have any effect on later install.

Anyways . Thanks, internet is working fine now. :):) .

---

### Post by RedSingularity on 2011-11-10
When the device is plugged in during install, Ubuntu can see it and install the proper kernel modules that operate it.  Its always a good way to test hardware.  Boot into a live cd with it :)

---

### Post by ask_ on 2011-11-10
Nice , will keep it in mind , the next time when I have to do an install. New to Linux/Ubuntu/UNIX , but this forum has great learning environment .

Thanks for helping in this thread.

---

### Post by abhishekchakraborty on 2011-11-15
Respected Sir

I'd Ubuntu 10.04 in my PC and suddenly I've found the latest one 11.10 and I downloaded and test it through using CD before I install. now the problem is when I'm trying to connect with my USB data card it creates and establish connection both , but during page loading it fails..

In Mozila browser it's showing "Server not found"..

I'm using ZTE-3570Z USB data Card and Using AIRCEL 2G connection on that regard.. But all seems null to me

Abhishek Chakraborty

---

### Post by ask_ on 2011-11-15
> **abhishekchakraborty said:**
> Respected Sir

I'd Ubuntu 10.04 in my PC and suddenly I've found the latest one 11.10 and I downloaded and test it through using CD before I install. now the problem is when I'm trying to connect with my USB data card it creates and establish connection both , but during page loading it fails..

In Mozila browser it's showing "Server not found"..

I'm using ZTE-3570Z USB data Card and Using AIRCEL 2G connection on that regard.. But all seems null to me

Abhishek Chakraborty

I think you should better open a new thread for your problem. You will more likely be able to get help faster.

The problem in this thread was concerned with inability to detect data card , which was pretty much solved.So this thread has been marked as solved , hence people won't respond to it,mostly.

Your PC is detecting the card and establishing the connection. So your problem is a bit different.

I would have helped you ,but I am a beginner just as you.

If someone else solves your problem in this thread , it is well and good. But it is my strong recommendation that you create a new thread.

---

