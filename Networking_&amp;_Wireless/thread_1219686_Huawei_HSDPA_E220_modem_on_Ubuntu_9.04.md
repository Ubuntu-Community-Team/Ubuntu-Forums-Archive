---
title: "Huawei HSDPA E220 modem on Ubuntu 9.04"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by vbrocz on 2009-07-22
I've installed ubuntu 9.04 and when i connect my Huawei HSDPA E220 modem it installed perfectly. But when i try to connect to the internet with the task bar icon, it always ends up with the message saying nework has been disconnected. So i cant go online.

Can anyone help me with this issue?????

---

### Post by Aragwain on 2009-07-22
I had similar problem. When I was installing Ubuntu 9.04 from LiveCD, modem worked perfectly. But after installing, my modem wasn't on the list in nm-applet.

But I found how to make modem work. You have just to connect modem before startup of the system. Then, Ubuntu will load all the drivers and modules to run GSM connection. I did so, and now I send this message with the GSM connection. :D

---

### Post by Aragwain on 2009-07-22
One minute ago I installed wvdial and wicd. To try using modem without nm-applet, use first:
```

sudo wvdialconf

```That should configure wvdial to use our modem. I don't know, but you may be pressed to open /etc/wvdial.conf and change "Phone", "Username" and "Password". It's typical to a mobile network you're using. When everything is ok, you use:
```

sudo wvdial

```It'll be long time to wait, because wvdial in one moment doesn't know what to do and:
```
--> Don't know what to do!  Starting pppd and hoping for the best.
```

---

### Post by NoReflex on 2009-07-22
Hello!

I have the exact same modem and it has worked for me flawlessly since Jaunty Alpha 2.
Now I'm using Jaunty (9.0.4) and it works very well.
I plug the modem in and then I can connect to my Mobile Broadband Connection (Vodafone).
I remember that when using Hardy I had to add and remove some modules to get it to work.
I think the best way to resolve your issue is by plugging in the modem and then check the output of **tail /var/log/messages**
It should tell you the modem was connected and more important it will tell you which driver it chose for the device.
Get back to us with the output of that command and I'm sure we'll be able to help you.

Good luck!

Best wishes,
NoReflex

---

### Post by NoReflex on 2009-07-22
Aragwain,

I think it will be easier to use gnome-ppp to configure the modem without nm-applet.
The "long time it waits" can be bypassed by enabling "Stupid mode" in gnome-ppp when configuring the connection.

NoReflex

---

### Post by Aragwain on 2009-07-22
Thanks NoReflex. I've just downloaded gnome-ppp. It works perfectly and it uses wvdial. So everything works well. But I had to change default entry in gnome-menu, because to connect via wvdial, you need to use pppd, which requires root. But everything works fine. Thanks NoReflex.

And in /var/log/messages it stays, that to use this modem is used driver "option". I tried to load this module after startup by modprobe, but it didn't worked. I will try to add "option" to /etc/modules, and then we'll see.

I just added "option" to /etc/modules. Modem works now even when not plugged in before startup. I don't know how, but first I tried to connect with sudo gnome-ppp with "Stupid Mode = on", it didn't connect (I don't know why, output is clear), then with wvdial (didn't connect too: )
```

--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Jul 22 14:27:12 2009
--> Pid of pppd: 3933
--> Using interface ppp0
--> pppd: &#65533;GV[08]HEV[08]
--> pppd: &#65533;GV[08]HEV[08]
--> pppd: &#65533;GV[08]HEV[08]
--> pppd: &#65533;GV[08]HEV[08]
--> pppd: &#65533;GV[08]HEV[08]
--> pppd: &#65533;GV[08]HEV[08]
--> local  IP address 95.40.82.134
--> pppd: &#65533;GV[08]HEV[08]
--> remote IP address 10.64.64.64
--> pppd: &#65533;GV[08]HEV[08]

```I waited 1 minute more or less. Then I hit Ctrl+C. I tried again with gnome-ppp, and now it works!

Thanks NoReflex for gnome-ppp ;)

sudo wvdial works now too. I changed a little /etc/wvdial.conf. Now it is:
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
ISDN = 0
Phone = *99#
Modem = /dev/ttyUSB0
Username = internet
Password = internet
Stupid Mode = on
Baud = 9600
Idle Seconds = 0

```

---

### Post by NoReflex on 2009-07-22
I believe you must allow some time for the modem to register to the GPRS / 3G network after plugging in the modem (about 20-30 seconds in my case). That could be the reason it didn't work the first time you tried.

NoReflex

---

### Post by Aragwain on 2009-07-22
Of course. Now when I plugged it in and waited a little time it works perfectly.

How is your modem, vbrocz?

---

