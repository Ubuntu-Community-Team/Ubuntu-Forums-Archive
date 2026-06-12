---
title: "Wireless Network Not Working after Installation"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by BushidoBrown on 2010-12-14
Hey all,

After running into some initial partitioning problems with the installation of Ubuntu 10.04 LTS on my HP Laptop (Windows Vista 64-bit), I am now experiencing connection problems.

Basically, I cannot connect to the internet. It works when I boot back into Vista, but not in Ubuntu. I should probably note that it did not work during the trials I ran of Ubuntu (I ran both Ubuntu 10.04 and 10.10 trials on my USB and both had the same problem). I thought that maybe a full installation would fix it, but nope.

The wireless repeatedly tries to connect to my home network, asking for the WEP password each time but then failing to connect. On occasion, the symbol for connection looks like it is working but there is still no connection.

I have tried every solution in the troubleshooting section for wireless problems on Ubuntu. However, I noted that most of these solutions were either poorly written or are not working on my laptop for some reason.

For instance, the first one says to enter something in the terminal and you should get either ENABLED, DISABLED, etc back but I get a long message without any of the words asked for.

Another issue is that when it gets to the step about finding the Windows drivers and using some program to 'wrap' them, I click on the program and an error pops up saying it could not be found.

The many problems I am encountering just trying to get Ubuntu to work (I've spent about 10 hours on various problems including this networking problem) are disillusioning -- perhaps my laptop is too screwed up to run two operating systems.
/rant

Anyways, any help would be appreciated before I throw in the towel.

Thanks

EDIT: Please no reinstall Ubuntu solutions -- believe me I have tried redownloading and reinstalling both versions a few times each.

---

### Post by agarzon on 2010-12-14
> **BushidoBrown said:**
> Hey all,

Another issue is that when it gets to the step about finding the Windows drivers and using some program to 'wrap' them, I click on the program and an error pops up saying it could not be found.


If you want to get ndiswrapper working you need to install it first.  I was under the impression that Networkmanager took care of having to use ndiswrapper.

Anyway, if you are using some old network troubleshooting that suggests using the ndiswrapper program (check the date on the thread you are looking at)

Problem is.... you need an Internet connection for this or you will not be able to access the repositories. See if you can connect a cable directly to your router while you work this out...

There are some instructions on how to download and install ndiswrapper using another computer....

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by BushidoBrown on 2010-12-14
Thanks for the quick reply,

I followed all of the directions on the link you gave me. It installed ndiswrapper and installed the .inf file I got from a website for my Realtek Wireless Adapter (PC ID: 10ec:8168 ). However, it did not work and I fear the instructions on that link are not up-to-date.

---

### Post by BushidoBrown on 2010-12-14
Well, after spending 7 straight hours going through every single forum thread related to wireless issues in Ubuntu as well as every document in help, I'm throwing in the towel.

How can a modern OS have such huge holes when it comes to the most important thing operating systems should do--connect to the internet?

Whatever, thanks for the help agarzon -- I appreciate the attempt.

---

### Post by agarzon on 2010-12-16
Sorry I was of little help, and that you got frustrated with trying to get Ubuntu running. I know It can be frustrating sometimes, specially when it comes to networking.

My experience with Ubuntu on laptops is that sometimes it works great, and sometimes it doesn't. 

I have installed different versions of Ubuntu (and OpenSUSE) on 4 different laptops: IBM, Dell, HP and Compaq. My personal experience says that if the wireless card (adapter) was not working while using the live CD, chances are you will have some (or a lot of) trouble getting it working once is installed (not impossible though). If it worked with the life CD, there is not guarantee it will work once is installed!!!

I am currently going through some intermittency issues with the wireless card on my Desktop. If it looses connection it will not come back until I reboot.

ON my work machine I had to remove the wireless adapter because it was causing conflict with the OS. To the point that I tried 6 different flavours/version of Linux and neither one of them solved the problem. ONly removing the hardware itself. This one was a broadcom chip branded Dell,and of the ubuntu wiki pages warned against using this card...

---

### Post by agarzon on 2010-12-16
One thing to consider is that sometimes you have to blacklist a default driver before you try to run a driver through ndiswrapper. This is mentioned on the same web page I mentioned earlier.

Did you blacklist any generic drivers first?

---

