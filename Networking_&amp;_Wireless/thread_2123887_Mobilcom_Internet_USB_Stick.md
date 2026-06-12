---
title: "Mobilcom Internet USB Stick"
date: 2013-03-09
forum: Networking &amp; Wireless
---

### Post by Boguz on 2013-03-09
I have bought an Internet USB Stick from Mobilcom/Debitel (XS Stick W21) a couple of weeks ago when i moved to Germany.

The stick works fine on my mac, but i can't get it to work on my girlfriend's laptop (running Ubuntu 12.04 LTS on a Toshiba Satellite laptop).
i have looked on the internet and i can see other people have had the same problem as we are having, but i can seem to find a solution.
i have tried several things but i can't do it! =(

Any ideas on what i should do to get it working?

i don't know if this helps, but...

when i run *lsusb*
```
BUS 002 Device 004: ID 1c9e:9801 OMEGA TECHNOLOGY
```

I really appreciate your help!
**Thanks**!

---

### Post by westie457 on 2013-03-09
This link might be useful for you. [http://forum.ubuntuusers.de/topic/umts-stick-xsstick-w21-von-mobilcom-debitel-4g/#post-4333882](http://forum.ubuntuusers.de/topic/umts-stick-xsstick-w21-von-mobilcom-debitel-4g/#post-4333882)

It appears to have a solution or at least it will point you in the right direction.

---

### Post by varunendra on 2013-03-09
On my 12.04, it looks like the driver 'option' doesn't know this device yet. But I haven't updated for months.

Please post outputs of -
```
modinfo option | grep -i 1c9e
usb-devices | grep -A10 -B2 9801
dmesg | tail -20
```
..after plugging-in the modem.

---

### Post by Boguz on 2013-03-09
> **westie457 said:**
> This link might be useful for you. [http://forum.ubuntuusers.de/topic/umts-stick-xsstick-w21-von-mobilcom-debitel-4g/#post-4333882](http://forum.ubuntuusers.de/topic/umts-stick-xsstick-w21-von-mobilcom-debitel-4g/#post-4333882)

It appears to have a solution or at least it will point you in the right direction.

Thanks. i have seen that page, and i actually tried to follow it. But my german isn't so good...
i think i have made all the things they say in that page, but it still doesn't work.

---

### Post by Boguz on 2013-03-09
> **varunendra said:**
> On my 12.04, it looks like the driver 'option' doesn't know this device yet. But I haven't updated for months.

Please post outputs of -
```
modinfo option | grep -i 1c9e
usb-devices | grep -A10 -B2 9801
dmesg | tail -20
```
..after plugging-in the modem.

 So here are the infors you asked me...

modinfo option | grep -i 1c9e
```

alias:          usb:v1C9Ep9607d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1C9Ep9603d*dc*dsc*dp*ic*isc*ip*

```

usb-devices | grep -A10 -B2 9801
```

T:  Bus=02 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1c9e ProdID=9801 Rev=00.00
S:  Manufacturer=USB Modem
S:  Product=USB Modem
S:  SerialNumber=1234567890ABCDEF
C:  #Ifs= 5 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

```

dmesg | tail -20
```

[ 3967.751734] init: modemmanager main process ended, respawning
[ 3967.762102] init: modemmanager main process (8128) terminated with status 255
[ 3967.762144] init: modemmanager main process ended, respawning
[ 3967.775582] init: modemmanager main process (8130) terminated with status 255
[ 3967.775612] init: modemmanager respawning too fast, stopped
[ 4580.792510] usb 2-4: USB disconnect, device number 2
[ 4618.916064] usb 2-4: new high-speed USB device number 3 using ehci_hcd
[ 4619.072868] scsi8 : usb-storage 2-4:1.0
[ 4619.073310] scsi9 : usb-storage 2-4:1.1
[ 4619.371458] usb 2-4: usbfs: process 8315 (usb_modeswitch) did not claim interface 0 before use
[ 4619.581328] usb 2-4: usbfs: process 8316 (usb_modeswitch) did not claim interface 0 before use
[ 4619.583695] usb 2-4: usbfs: process 8317 (usb_modeswitch) did not claim interface 0 before use
[ 4619.773241] usb 2-4: USB disconnect, device number 3
[ 4620.140070] usb 2-4: new high-speed USB device number 4 using ehci_hcd
[ 4620.273442] usb 2-4: config 1 has an invalid interface number: 5 but max is 4
[ 4620.273451] usb 2-4: config 1 has no interface number 4
[ 4620.295575] scsi10 : usb-storage 2-4:1.5
[ 4621.293503] scsi 10:0:0:0: Direct-Access     USBModem Disk             2.31 PQ: 0 ANSI: 2
[ 4621.295182] sd 10:0:0:0: Attached scsi generic sg2 type 0
[ 4621.299230] sd 10:0:0:0: [sdb] Attached SCSI removable disk

```

---

### Post by varunendra on 2013-03-09
> **Boguz said:**
> 
```

I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

```


So far what we suspected (+ some more). Let's try an old fix. Follow what is suggested in post #62 here : [http://ubuntuforums.org/showthread.php?t=1969322&p=12132847#post12132847](http://ubuntuforums.org/showthread.php?t=1969322&p=12132847#post12132847)

---

### Post by Boguz on 2013-03-09
hi

i think that helped, but when i restart then i have to go again into terminal again.
is this normal?

---

### Post by varunendra on 2013-03-10
> **Boguz said:**
> hi

i think that helped, but when i restart then i have to go again into terminal again.
is this normal?

No it's not normal. What do you need to do in terminal ?

---

### Post by alexfish on 2013-03-11
Hi folks

Can have a look at this thread

[h=1][SIZE=4]Thread: [modem-manager not working]("http://ubuntuforums.org/showthread.php?t=1969322")[/SIZE][/h]
BR

Alex

---

### Post by varunendra on 2013-03-12
> **alexfish said:**
> Can have a look at this thread
[h=1][SIZE=4]Thread: [modem-manager not working]("http://ubuntuforums.org/showthread.php?t=1969322")[/SIZE][/h]


Actually, alexfish, if you follow the link I pointed the OP to, it takes to the same thread you linked to, pointing to the same 'generic' form of the solution by yourself :P

But I'm happy that you yourself are here now :)

---

### Post by bmork on 2013-03-20
> **alexfish said:**
> Hi folks

Can have a look at this thread

**[SIZE=4]Thread: [modem-manager not working]("http://ubuntuforums.org/showthread.php?t=1969322")[/SIZE]**



Whenever you do that, and it works, it would be very nice if you could forward all details to the [linux-usb]("http://vger.kernel.org/vger-lists.html#linux-usb") mailing list so that we can make this work out-of-the-box for the next user with the same modem.  There is really nothing to it.  Send the commands you used to make it work, lsusb and/or usb-devices output, dmesg messages etc and someone will either figure out the rest or ask you for any missing info.

The reward is the warm fuzzy feeling of having helped the community to get even better USB modem support. And if you want, a credit line in the commit message.  That's pretty close to fame :)

---

