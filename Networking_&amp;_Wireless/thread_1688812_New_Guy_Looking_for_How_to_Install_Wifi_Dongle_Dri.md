---
title: "New Guy Looking for How to Install Wifi Dongle Drivers"
date: 2011-02-15
forum: Networking &amp; Wireless
---

### Post by monkeychef on 2011-02-15
Hi All,

So I have just started using Linux, and so far I really like it. I put it on my grandpa's old laptop (Acer Aspire 5570z) and I found out that his wireless card absolutely sucks(excuse the language if you find it to be offensive). Anyway, I went and bought him a nice Edimax EW-7811Un dongle, and on Newegg reviewers say it works on linux. I am currently on Ubuntu 10.04 LTS, and some easy to follow instructions would be greatly appreciated. I already downloaded the file from the Edimax website for Linux, I just don't know how to install it. ([http://www.edimax.com/en/support_detail.php?pl1_idSelect=support.php%3Fpl1_id%3D1%26mwsp%3D1&pl1_id=1&pd_id=347&button=Go#01](http://www.edimax.com/en/support_detail.php?pl1_idSelect=support.php%3Fpl1_id%3D1%26mwsp%3D1&pl1_id=1&pd_id=347&button=Go#01))

Thanks!

---

### Post by Slave2Metal on 2011-02-15
Extract the zip that you downloaded and open it, then open document and click on the ppt file. It's labeled quick installation guide.

---

### Post by monkeychef on 2011-02-15
First of all, thanks for the quick reply.

Second, step 4 wants me to use the file insmod 8192cu.ko, but I don't have that.

---

### Post by Slave2Metal on 2011-02-15
You're doing this in terminal, correct?

---

### Post by Slave2Metal on 2011-02-15
................

---

### Post by monkeychef on 2011-02-15
Hehe...I was actually clicking some links in the driver folder that looked correct and ran them in terminal...guess that didn't work.

Although now when I type tar zxvf rtl8192CU_linux_v2.0.939.20100726.tar.gz into terminal it says no such file or directory

I am such a noob.

---

### Post by Slave2Metal on 2011-02-15
Try copy/paste straight from the guide.

---

### Post by monkeychef on 2011-02-15
Nope, same thing...this is very odd.

Does it help if I tell you I have the driver files on a usb stick and not the hd?

---

### Post by Slave2Metal on 2011-02-15
This may be a case of the blind leading the blind...hold on, give me a minute.

---

### Post by monkeychef on 2011-02-15
Btw, I found this link on a Newegg site ([http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU)) and there is an install.sh shell

I ran it, but at the end I get Authentication failure
Compile make driver error: 1, Please check error Mesg

I can't find the error message. 

Other than that, take your time. I really appreciate your help.

---

### Post by Slave2Metal on 2011-02-15
> **monkeychef said:**
> Btw, I found this link on a Newegg site ([http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU)) and there is an install.sh shell

I ran it, but at the end I get Authentication failure
Compile make driver error: 1, Please check error Mesg

I can't find the error message. 

Other than that, take your time. I really appreciate your help.



Check this, I'm still too much of a noob to help, lol    This appears to be the thread you need.  
[http://ubuntuforums.org/showthread.php?t=1590873](http://ubuntuforums.org/showthread.php?t=1590873)

---

### Post by monkeychef on 2011-02-15
I'm still getting no directory found. I'm done for the night. I'll come back tomorrow and hopefully we/I/others can help to solve this annoying problem.

---

### Post by Slave2Metal on 2011-02-15
> **monkeychef said:**
> I'm still getting no directory found. I'm done for the night. I'll come back tomorrow and hopefully we/I/others can help to solve this annoying problem.
Everything you need is in that thread I posted.  Just move the folder from the usb to the desktop and give it a whirl.

---

### Post by monkeychef on 2011-02-18
So it turns out that there is a difference between 1 and lowercase L. I am such and idiot. Anyway, its working great now. Thanks for all of your help man.

---

### Post by Slave2Metal on 2011-02-19
> **monkeychef said:**
> So it turns out that there is a difference between 1 and lowercase L. I am such and idiot. Anyway, its working great now. Thanks for all of your help man.

Glad you got it working.  Looks like Chili got you all squared away.  He's a big help and has helped me in the past.

---

### Post by hisham1969 on 2011-03-07
Hi,

Sorry to revive an old thread. I got an Edimax EW-7811Un today and i just cannot get it to work. I followed the advice in this thread, but it still won't work.

I am very new to ubuntu, I'm running Ubuntu 10.10 on a very old Dell Inspiron 8200.

Thanks.

---

### Post by monkeychef on 2011-03-07
> **hisham1969 said:**
> Hi,

Sorry to revive an old thread. I got an Edimax EW-7811Un today and i just cannot get it to work. I followed the advice in this thread, but it still won't work.

I am very new to ubuntu, I'm running Ubuntu 10.10 on a very old Dell Inspiron 8200.

Thanks.
Well you definitely came to the right place. These guys are really great. Before anyone else gives you advice, have you made sure you are spelling everything correctly? Sometimes the font makes it hard to differentiate between 1 and l (see).

---

