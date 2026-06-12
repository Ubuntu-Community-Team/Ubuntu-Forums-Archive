---
title: "Asus eepc 1008ha problem with ethernet connection"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by dpellon on 2009-08-02
Hi I had an old pc with ubuntu, I only stayed with ubuntu like a month beause i decided to buy a gaming pc, so I was forced to come back to windows, now i buyed a Asus EeePc 1008ha (seashell) and decided to install ubuntu, the problem is that neither the ethernet nor the wifi works.

I have searched in the web for answers, this is the best info <i have found:

> 1- After installing Jaunty, download (from some other machine, of course), the AR813X-linux-v1.0.0.9.tar.gz package from [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)

2 - Install the driver, ignoring some errors that may appear. Just follow this steps:

Code:
[QUOTE]tar -xzvf AR813X-linux-v1.0.0.9.tar.gz
cd src
make
sudo make install
sudo insmod atl1e.ko
(the last two steps must be redone if you do a kernel upgrade)

Done, you should get wired network now.

Note: People using 2.6.30+ kernels (which is not the default in Jaunty): 
These steps must be followed: Post by BandedHawk. It works.[/QUOTE]

In my previous pc i installed a program to open the terminal where i want (so i didnt had to specify a directory), but now i have no conectivity.

Ok i downloaded the driver (in another pc), i put the driver in the desktop, i opened the terminal and copy pasted the code (obiously it failed without a specified directory).

So considering that my pc username is daniel and the driver is located in the desktop, which will be the exact code i will have to write?

Thanks for your time and sorry for my bad english.:)

---

### Post by Crafty Kisses on 2009-08-03
I'm not sure what you're asking, but if you're asking how to navigate to the driver on your desktop and if your user name is "daniel" the command would be:
```
cd /home/daniel/Desktop/AR813X-linux-v1.0.0.9.tar.gz
```
Now what you can do when your navigating with directories is press "tab" and it will autofill the most relevant option. You can also put *, which stands for a kind of wild card. For example, if the driver file was called AsusDriver.tar.gz you could run:
```
cd /home/daniel/Desktop/Asus*
```
Remember when working the Terminal everything is case sensitive, your English is fine by the way. ;-)

---

### Post by dpellon on 2009-08-03
thanks for your reply
when I put this directory: 
> cd /home/daniel/Desktop/AR813X-linux-v1.0.0.9.tar.gz
it tells me that its not found, i im sure thats the directory and the filename is correct, also im not sure to write cd source or cd only.

Also should i let tar and make like that or should i change it?

I realy apreciate your time :)

---

### Post by Crafty Kisses on 2009-08-03
Remember it's case sensitive.

---

### Post by dpellon on 2009-08-03
Ok i realized that my desktop its called escritorio (spanish version), so now i think the file got decompressed so what should i do know:confused:

---

### Post by dpellon on 2009-08-03
Now its already working :) thank very much you codename.

---

