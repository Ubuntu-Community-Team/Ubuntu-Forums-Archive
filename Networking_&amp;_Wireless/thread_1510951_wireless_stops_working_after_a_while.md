---
title: "wireless stops working after a while"
date: 2010-06-16
forum: Networking &amp; Wireless
---

### Post by XVampireX on 2010-06-16
I'm having some problems with wireless, it works fine on boot but after a while pretty much randomly, it can be a few days or it can be a few hours, it stops working. I'm not sure which command would tell you what and it would take a little while to debug it because like I said it's random, but if anyone knows what to do please tell me! I'm on Lucid Lynx 10.04.

Another something that's really bothering me (But not related to wireless) is that for some reason when I restart my computer, the top panel keeps changing the applets locations.

Anyone can help me? Will really appreciate it!

---

### Post by LadZh on 2010-06-18
I have the same problem.
By me it's a matter of minutes that connection to the internet drops. 
In the panel wireless remains connected however there connection clearly stops working. 
I'm using Ndiswrapper in Lucid (Ubuntu 10.4)
If I consult /var/log/messages it doesn't say anything suspicious. 
Where can I look for the source of the problem and how can the problem be fixed?
If I have wired connection to the same router everything works just fine. 
Wireless connection on the same laptop in Windows connected to the same router works fine as well.
There is clearly a problem with the wireless in Lucid.
Anyone care to help?

P.S. I'm not a newbie... years back I used to be a Linux system administrator.

---

### Post by LadZh on 2010-06-18
Another data point, I rarely get more than 2 out of 4 bars of wireless strength even if I'm sitting right next to the router. So, it's usually around 20-60% strength.

I have the following wireless pci controller

02:04.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 43)

---

### Post by Bucky Ball on 2010-06-18
Next time it drops off, before doing ANYTHING else, put this in a terminal:

```
dmesg
```

Post the result. Do you know what wireless card you are using? Please try to include all relevant hardware details when posting. If you don't know:

```
lspci
```

... and post that. Your card will be near the bottom somewhere. If you are using Network Manager, try Wicd or for Atheros cards MadWifi. Wicd worked a treat for me with Intel card. Another possible cause: have you got static IP set up on your LOCAL machine? If so, check the router is not set up as a DHCP server as this will definately cause drop outs. They are sending each other an IP so while you might connect initially, when the router or machine tries to resend the IP, crash, the other device is already sending one!

---

### Post by LadZh on 2010-06-18
The router serves dhcp addresses nicely.
I use dynamic address on my laptop.

---

### Post by Bucky Ball on 2010-06-18
LadZH, you have a separate issue from the poster and should post a thread explaining exactly your problem, hardware, all details you can think of. You will get more specific help.

---

### Post by LadZh on 2010-06-18
Actually as it seems I've solved my issue. 

I downloaded the latest Ndiswrapper from their site on sourceforge 

[http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/)

Compiled the module ndiswrapper.ko (I just run command "make" without running make install)

went 

cd /lib/modules/2.6.32-23-generic/kernel/ubuntu/ndiswrapper/

renamed the existing module into ndiswrapper.ko_old

sudo mv ndiswrapper.ko ndiswrapper.ko_old

Put newly compiled module into the directory /lib/modules/2.6.32-23-generic/kernel/ubuntu/ndiswrapper/

sudo cp ./ndiswrapper.ko /lib/modules/2.6.32-23-generic/kernel/ubuntu/ndiswrapper/

removed old module from the memory 

modprobe -r ndiswrapper

and 

loaded the new module 

modprobe ndiswrapper 

Ensured that the new module was loaded 

lsmod | grep ndiswrapper 

Ensured that the module is running in the new version

ndiswrapper -v 

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.32-23-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
**version:        1.56**
vermagic:       2.6.32-23-generic SMP mod_unload modversions 586

I'll report later, once I have rebooted my laptop, whether the issue was really solved. 

If I don't report back here - you can assume the issue was solved, otherwise I'll be back here.

---

### Post by Bucky Ball on 2010-06-18
Ndiswrapper? Not the go for Broadcom anymore but if it works ...

---

### Post by LadZh on 2010-06-19
Unfortunately the problem is back i.e. it is still there :(

The wireless connection to the internet drops after a while... 
Wireless connection icons in the status bar remains/shows connected however the connection to the internet drops... 

ping doesn't get any responses...

---

### Post by Sean Hayes on 2010-06-19
I've got the same problem. Thread here: [http://ubuntuforums.org/showthread.php?t=1477539](http://ubuntuforums.org/showthread.php?t=1477539)

---

