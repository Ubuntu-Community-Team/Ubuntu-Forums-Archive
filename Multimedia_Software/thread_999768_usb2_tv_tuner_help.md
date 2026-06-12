---
title: "usb2 tv tuner help"
date: 2008-12-02
forum: Multimedia Software
---

### Post by joni8.10 on 2008-12-02
Hi I'm new to Linux and have just installed ubuntu 8.10. I can't get my Sabrent usb2 tv tuner to work on this system and I can't find any support either. I've found webpages that talk about building a driver, but I am a beginner and do not understand what they're talking about. Is there anyone out there who can help?

---

### Post by joni8.10 on 2008-12-25
ker..plunk!!

---

### Post by xc3RnbFO8P on 2008-12-25
In **Terminal** show the output of **dmesg**

---

### Post by joni8.10 on 2008-12-25
> **Ringi said:**
> In **Terminal** show the output of **dmesg**

I can't copy and paste it into here for some reason.

---

### Post by wolfen69 on 2008-12-25
> **joni8.10 said:**
> Hi I'm new to Linux and have just installed ubuntu 8.10. I can't get my Sabrent usb2 tv tuner to work on this system and I can't find any support either. I've found webpages that talk about building a driver, but I am a beginner and do not understand what they're talking about. Is there anyone out there who can help?

give us the link where it talks about building a driver.

---

### Post by wolfen69 on 2008-12-25
go to system>administration>software sources and make sure all repos are checked off. close and reload.
do in terminal:
```
sudo apt-get install mercurial tvtime xawtv module-assistant
```
then
```
sudo m-a a-i v4l2
``` let it do its thing then reboot then try tvtime and xawtv.

---

### Post by joni8.10 on 2008-12-27
> **wolfen69 said:**
> give us the link where it talks about building a driver.

Here it is:

[http://ubuntuforums.org/showthread.php?t=927234&highlight=sabrent](http://ubuntuforums.org/showthread.php?t=927234&highlight=sabrent)

---

### Post by joni8.10 on 2008-12-27
> **wolfen69 said:**
> go to system>administration>software sources and make sure all repos are checked off. close and reload.
do in terminal:
```
sudo apt-get install mercurial tvtime xawtv module-assistant
```
then
```
sudo m-a a-i v4l2
``` let it do its thing then reboot then try tvtime and xawtv.

Thanks for this! However the second code won't work...it asks me what is v4l2...should I tell it something else?

---

### Post by joni8.10 on 2008-12-29
bump!

When I try the code sudo m-a a-i v4l2, the terminal asks me: what is v4l2?

what should I do now?

Please and thanks.

---

