---
title: "Broadcom 5709 ethernet card not working Dell PowerEdge Server"
date: 2012-08-29
forum: Networking &amp; Wireless
---

### Post by abhinav90 on 2012-08-29
I just installed Ubuntu 12.04 Server Edition on my Dell Power Edge Server and the ethernet card is not working. I am able to see the ethernet card as Broadcom 5709 when i use lspci.

However, the ethernet card is not working and it is not connecting to the network. What should i do to diagnose and fix the same.

Would the bce driver help? if yes how do i install it on the server? I have physical access to it.

Alternately, would an ndiswrapper help in this case because ive always used it for wireless cards with no native driver, but does it also work for the ethernet card.

What should i do? Any advice is welcome. Thanks

---

### Post by josephmills on 2012-08-29
can we see 
```
lspci -nn | grep 14e4
```
or just the part that is in red ? 
thanks

---

### Post by chili555 on 2012-08-29
> I am able to see the ethernet card as Broadcom 5709 when i use lspci.Please tell us exactly what you see when you type:```
lspci -nn | grep 0200
```> Alternately, would an ndiswrapper help in this case because ive always used it for wireless cards with no native driver, but does it also work for the ethernet card.Very doubtful.

Oops, sorry. Joseph is on your case.

---

### Post by abhinav90 on 2012-08-29
I will be going to the server site tomorrow and check and let you know (since sadly i can't ssh into it as the ethernet card does not work). I need to fix it on site tomorrow so if you guys could give any advice on what plan i should go with. 

I remember running this command the last time i went and it gave me:


00:19.0 Ethernet controller: Broadcom 5709


Would it make sense to try and install the bnx2 driver for broadcom 5709 or do you think thats not the issue since it is showing the correct model number.


Any suggestion at all at this moment would be appreciated, will be going onsite in about 10 hours time.

---

### Post by chili555 on 2012-08-29
Joseph will probably assert you already have the driver but not the firmware. OK, I'm done now.

---

### Post by abhinav90 on 2012-08-29
Oh, okay, so how do i go about fixing the firmware issue? Is there anyway to make sure its firmware related and not driver related.

Its really urgent, thanks for your help.

---

### Post by abhinav90 on 2012-08-29
Oh also another thing i just remembered that might help was that the ifconfig command would give all the details of eth0 but the inet addr: IP Broadcast: and Mask line would be missing. 

It would be something like below WITHOUT the line in red:

eth0 Link encap:Ethernet HWaddr 00:0A:E6:C6:07:85
[COLOR="Red"]**inet addr:132.18.0.16 Bcast:132.18.0.255 Mask:255.255.255.0**
[/COLOR]
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:18458 errors:0 dropped:0 overruns:0 frame:0
TX packets:8982 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:4015093 (3.8 MiB) TX bytes:1449812 (1.3 MiB)
Interrupt:10 Base address:0xd400

---

### Post by abhinav90 on 2012-08-30
Is it may be just a dhcp/static ip setting issue or could it be firmware one. Pls help urgent advice needed.

---

### Post by chili555 on 2012-08-30
We really need your lspci details. Please provide.

On the chance it is a device driven by *bnx2*, let's load it and see what happens:```
sudo modprobe bnx2
dmesg | grep bnx2
sudo dhclient eth0
```

---

### Post by abhinav90 on 2012-09-01
Hey, thanks a lot chilli555, loading the bnx2 driver using your commands and restarting the server made it work!!

Really Appreciate your help !

---

### Post by chili555 on 2012-09-01
> **abhinav90 said:**
> Hey, thanks a lot chilli555, loading the bnx2 driver using your commands and restarting the server made it work!!

Really Appreciate your help !If it's not loading automagically on boot, you might add it to /etc/modules:```
sudo su
echo bnx2 >> /etc/modules
exit
```Glad it's working!

---

