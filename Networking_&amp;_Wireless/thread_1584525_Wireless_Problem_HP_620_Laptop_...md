---
title: "Wireless Problem HP 620 Laptop .."
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by boy90 on 2010-09-29
hi all ,

My friend facing a problem of wireless 
his laptop is HP 620 and there's no wireless connection in Ubuntu 10.04..
Although there is a connection in WIN7

result of iwconfig :


```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.427 GHz  Access Point: Not-Associated   
          Bit Rate:135 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```any Help !!!

---

### Post by FluidBlow on 2010-09-29
"Access Point: Not-Associated" This is the problem.
Try to desactivate the network manager gui, and type "sudo iwconfig wlan0 ap auto" and post the result of a "iwconfig"

---

### Post by boy90 on 2010-09-29
first, i'm sorry for being late in replay
second, thank you

and this is a result :
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.452 GHz  Access Point: Invalid   
          Bit Rate=135 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


```

---

### Post by FluidBlow on 2010-09-29
As you can see, now there is : "Access Point: Invalid" .
That means you're wireless adapter is recognized but not fully working.

What kind of wireless adapter do you have ? usb, pci ? Give me the exact entire name of the device. And did you install the drivers manually ?

---

### Post by boy90 on 2010-09-29
it's Laptop
No , i didn't install drivers manually
I'm just install Ubuntu ..

---

### Post by boy90 on 2010-09-30
OK,
after few search

is 

> [FONT=monospace]Mode: Managed[/FONT][FONT=monospace]

should be

[/FONT]> Mode: Master
[FONT=monospace]
!!!!
[/FONT]

---

### Post by FluidBlow on 2010-09-30
Humm, I don't really know the differences between Managed and Master, but I'm pretty sure that if you run through classic wifi, you have to set the mode in Managed.
I thnik the problem is the wifi driver is not recognized well.

---

### Post by boy90 on 2010-09-30
SOLVED !
as i wrote in previous post change Mode to Master
and thats works very well, here i found the solution : [https://help.ubuntu.com/community/WifiDocs/MasterMode](https://help.ubuntu.com/community/WifiDocs/MasterMode)
Big thanks Mr. FluidBlow for helping

---

### Post by FluidBlow on 2010-10-01
No problems, have a nice day (and don' t forget to use the "solved" flag on your thread)

---

