---
title: "New to Ubuntu and need some help..."
date: 2013-02-11
forum: Networking &amp; Wireless
---

### Post by Dr AM on 2013-02-11
I have installed Ubuntu 12.10 today, but I cannot connect to the internet unless I use Vista. How can get a wireless connection? I think I am close after hours of trying. I get to Broadcom 802.11 Linux STA wireless Driver bcmwl-kernel-source (proprietary) in the software sources. It wants an authentication code to update this driver. So what do I do now?

---

### Post by chili555 on 2013-02-11
You could give it an authorization code! That is actually just your user password. If you are a nervous nellie like old Chili, you could check the device ID and be sure STA is what you *really* need. Open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by Dr AM on 2013-02-11
I will try that and see if it works. Hopefully it will.:KS

---

### Post by Dr AM on 2013-02-11
Didn't work. Huge Sigh

---

### Post by chili555 on 2013-02-11
Is it time to dig deeper? How about the data I requested?> you could check the device ID and be sure STA is what you *really* need.

---

### Post by offgridguy on 2013-02-11
If you need to install the driver, maybe this will help.
 see info at very bottom of page.

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

---

### Post by Dr AM on 2013-02-12
Thanks for the suggestions. I will make sure to try these this evening.

---

### Post by chili555 on 2013-02-12
Doctor!! Once again, please check the device ID and be sure STA is what you *really* need. Downloading and installing the direct STA driver as suggested above is simply a different way to do this:> I get to Broadcom 802.11 Linux STA wireless Driver bcmwl-kernel-source (proprietary) in the software sources. It wants an authentication code to update this driver. So what do I do now?
...and is most likely to have the same result:> Didn't work. Huge Sigh So please help me help you and run and post the requested data _before_ you do anything else. Once we know what you really have, we'll know and recommend what you really need.

---

### Post by Dr AM on 2013-02-12
What exactly am I looking for when I run and post the lspci - nn 
grep 0280 in the terminal? It did brings up some things after I entered that. I apologize for my ignorance and vagueness on this. Unfortunately I am not computer savvy.

---

### Post by chili555 on 2013-02-12
> **Dr AM said:**
> What exactly am I looking for when I run and post the lspci - nn 
grep 0280 in the terminal? It did brings up some things after I entered that. I apologize for my ignorance and vagueness on this. Unfortunately I am not computer savvy.You are looking to post it here.

---

### Post by chili555 on 2013-02-13
Perhaps I can help out here. Please open a terminal and run:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. 

Here is an example from my machine. So, in my example, I'd post:```
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:4239] (rev 35)
```If you are without an internet connection and have to copy it by hand, you could trim it down to the essentials:```
Intel Corporation Centrino Advanced-N 6200 [8086:4239]
```

---

