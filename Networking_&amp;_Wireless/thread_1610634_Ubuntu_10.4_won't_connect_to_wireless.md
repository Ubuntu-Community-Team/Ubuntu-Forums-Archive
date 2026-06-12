---
title: "Ubuntu 10.4 won't connect to wireless"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by doggygirl_10 on 2010-10-31
Hi...I'm running Ubuntu 10.4 Netbook Remix on a Dell Mini Netbook 9 (I think that's what it is.) I used to be able to connect to my wireless internet fine, but then my brother put a password on it. So there's a little box that comes up and tells me to enter a password now. I do, and it tries to load for a minute and then wants me to enter my password again. It just keeps going like this...

I've searched around, but I could never find anything that helps...Sorry if this has been asked before.

Thanks for your help. :)

---

### Post by MooPi on 2010-10-31
Is the interface asking for the wireless pass phrase or your password ?

---

### Post by doggygirl_10 on 2010-11-01
Oh, sorry, it's asking for the wireless pass phrase. Sorry I wasn't clear on that...

---

### Post by doggygirl_10 on 2010-11-01
Oh, now that I've looked around some more I should mention that it's a wpa connection (I think) and the little box is combined "wpa &wpa2". Also, every time I boot up it says I have an outdated or missing driver, whatever that means. 

I don't know how to go into/post codes or anything else that the other threads have. And their solutions are quite confusing, it all goes waaaay above my head....

---

### Post by doggygirl_10 on 2010-11-03
Well, I just installed 10.10 for netbooks, or Unity, or  whatever it's called.

I'm still having the exact same problem.

---

### Post by mutex023 on 2010-11-03
Get the correct pass phrase from ur bro :). Also check with him whether he set up the security as WPA2 or something else.

---

### Post by doggygirl_10 on 2010-11-03
> **mutex023 said:**
> Get the correct pass phrase from ur bro :). Also check with him whether he set up the security as WPA2 or something else.

I have, the pass phrase and everything should be correct. (It's a WPA) I double-checked and even tried some different security settings, like WEP, but they didn't work either.

---

### Post by mutex023 on 2010-11-03
Does System > Administration > Hardware Drivers, suggest any wireless drivers to install ?

---

### Post by doggygirl_10 on 2010-11-03
> **mutex023 said:**
> Does System > Administration > Hardware Drivers, suggest any wireless drivers to install ?

I can't find "system"...sorry for the trouble...

---

### Post by mutex023 on 2010-11-03
Oh sorry, you are using the Netbook remix edition, I don't know exactly where the Restricted Hardware Drivers Menu is available on this version of ubuntu. But search around and you might find it. Can some one here who has used the netbook edition please help ?

---

### Post by archithcr on 2010-11-03
Do you know which Wireless chipset your netbook has? That can help us guide you. 
 If you want to get to the System menu, i suggest that you logout and come to the login screen, and right before you type in your user password, take a look at the options below.  
One of them will say something like Desktop session to load. right next to it, you will have a drop down menu. the menu will currently read "Ubuntu Netbook Remix" or "Unity". if you take a look at the menu options, one of them will be "Ubuntu Desktop" and another will be "Ubuntu Desktop (Safe)".  
 Select the "Ubuntu Desktop Session", and type in your password and log in. you should be logged into the desktop environment. if you notice the menubar at the top, there is a "System" option. if you click on it, there's a subsection called "Administration". Under the administration, you have a sub option called "Additional Drivers".  Hope this helps.

---

### Post by doggygirl_10 on 2010-11-03
> **archithcr said:**
> Do you know which Wireless chipset your netbook has? That can help us guide you. 
 If you want to get to the System menu, i suggest that you logout and come to the login screen, and right before you type in your user password, take a look at the options below.  
One of them will say something like Desktop session to load. right next to it, you will have a drop down menu. the menu will currently read "Ubuntu Netbook Remix" or "Unity". if you take a look at the menu options, one of them will be "Ubuntu Desktop" and another will be "Ubuntu Desktop (Safe)".  
 Select the "Ubuntu Desktop Session", and type in your password and log in. you should be logged into the desktop environment. if you notice the menubar at the top, there is a "System" option. if you click on it, there's a subsection called "Administration". Under the administration, you have a sub option called "Additional Drivers".  Hope this helps.
 
I got it! Thank you! And no, I don't know which chipset I have. All I know is that it's a Dell Insperon 910 Netbook...


> **mutex023 said:**
> Does System > Administration > Hardware  Drivers, suggest any wireless drivers to install ?

Yes, it does. It has a gray circle and is called "Broadcom B43 wireless driver". The other one has a green circle, so it's already on.

---

### Post by mutex023 on 2010-11-03
> **doggygirl_10 said:**
> 
Yes, it does. It has a gray circle and is called "Broadcom B43 wireless driver". The other one has a green circle, so it's already on.

So you have a Broadcom wireless chipset. The one which has the green circle, is it called something like Broadcom STA...?

---

### Post by doggygirl_10 on 2010-11-04
> **mutex023 said:**
> So you have a Broadcom wireless chipset. The one which has the green circle, is it called something like Broadcom STA...?

Yup, "Broadcom STA wireless driver." What is with me and not mentioning things? Sorry.

So for good measure, here's what the STA says:

"These package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4321-, and BCM 4322-based hardware."

B43:
"This package installs the firmware needed for usage of the B433 kerneldriver.
Supported chipsets: BCM4306/3- BCM4311- BCM 4312- BCM4312"

---

### Post by mutex023 on 2010-11-04
Go to System>Administration>Synaptic Package Manager and install the 
'bcmwl-kernel-source' and 'bcmwl-modaliases' packages. I am assuming you can access the internet through a wired ethernet cable. Then restart and check if wifi works and let me know.

---

### Post by doggygirl_10 on 2010-11-04
> **mutex023 said:**
> Go to System>Administration>Synaptic Package Manager and install the 
'bcmwl-kernel-source' and 'bcmwl-modaliases' packages. I am assuming you can access the internet through a wired ethernet cable. Then restart and check if wifi works and let me know.

I installed them and restarted...it still doesn't work. Yes, I have an ether net cable.

---

### Post by mutex023 on 2010-11-05
Bump. You need some real linux cmd line and wifi experts to help you from here on. Sorry :(

---

### Post by mutex023 on 2010-11-05
Ok, after searching this forum i found something from here - [http://ubuntuforums.org/showthread.php?t=1604868&highlight=wifi+broadcom](http://ubuntuforums.org/showthread.php?t=1604868&highlight=wifi+broadcom)

Install the 'firmware-b43-lpphy-installer' package. If that doesn't work go through these forums, search for 'broadcom wifi'. You might find a solution.

---

### Post by doggygirl_10 on 2011-02-04
Okay, I got it to work!! :D This may be cheating, but how I did it:

I called the internet company and got the security taken off the Wifi. (The dude helping me was super nice. Just like you guys are. :D )After that, I turned on the driver called Broadcom STA wireless driver. It worked after that, I guess it just hates passwords.

On another note, how do I switch the title of the thread to "Solved"?

---

