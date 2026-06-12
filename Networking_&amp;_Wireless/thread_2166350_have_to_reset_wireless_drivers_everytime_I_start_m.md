---
title: "have to reset wireless drivers everytime I start my computer (12.10 &amp; 13.04)"
date: 2013-08-08
forum: Networking &amp; Wireless
---

### Post by joefunsch on 2013-08-08
I have a broadcom b43 type modem (HP dv5 laptop) and recently upgraded from 12.10 to 13.04.  Everytime I start my computer now I have to open the terminal and run the following commands:

sudo modprobe -r b43
sudo modprobe b43

As soon as I do, the wireless comes on and I have no further issues.

How do I get this driver installed to stay permanently?  back on 12.10, I had to update a driver for this and it installed just fine and never had issues again.  I forgot what what I did.....:confused:

Please help,

Regards, 
JoeF

---

### Post by chili555 on 2013-08-09
Please try this:```
sudo su
echo b43 >> /etc/modules
exit
```Reboot and tell us if it's working. If not, please post:```
ls /etc/modprobe.d
```Thanks.

---

### Post by joefunsch on 2013-08-10
chili555; you da man!

That worked perfectly.

I want to say that in 12.04 my wireless worked "out of the box".  That carried up to 12.10 when I "updated" from 12.04 but a few weeks ago I did a fresh install of 13.04 and not only did the wireless stop working but it would also lock my computer up so I went back to 12.10 by doing a "fresh install".  There, the system worked fine but the wireless always had to be reset.

then a week ago I "Updated" to 13.04 over the net and the computer didn't lock up anymore but the wireless issue stayed.  Your idea of:

sudo su
echo b43 >> /etc/modules
exit & reboot

now the wireless self-starts.  Thank you.  i can live with this.  Now maybe you have an Idea for this; the wireless comes up "not connected" nor does it find any access points until 20-30 seconds after the desktop is up.  Livable? yes but in past versions, it seems like the wireless networks were loaded earlier in the boot sequence than what is happening now.  Is this the case or might I still have something slightly messed up?

Thanks for your assistance.
JoeF

---

### Post by chili555 on 2013-08-10
Glad it's almost working! Let's have a look at:```
cat /etc/network/interfaces
```

---

