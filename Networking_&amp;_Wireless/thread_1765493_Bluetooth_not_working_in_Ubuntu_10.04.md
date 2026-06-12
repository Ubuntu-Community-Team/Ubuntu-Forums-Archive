---
title: "Bluetooth not working in Ubuntu 10.04"
date: 2011-05-23
forum: Networking &amp; Wireless
---

### Post by Jyothisankar on 2011-05-23
HI,
I was using single boot Ubuntu 9.10 on a Compaq Core2Duo laptop with 2.2GHz Processor and 3GB RAM. Bluetooth was working fine with 9.10. After my upgrade to 10.04, I was no longer able to connect to any bluetooth device and the bluetooth daemon kept telling me that I have no blue tooth adapters plugged in. 
Tried $lsusb and following was the result.

```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 1004:6000 LG Electronics, Inc. VX4400/VX6000 Cellphone
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04f2:b098 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
Bus 5 was connecting to my Mobile and 2 was showing the Wifi Adapter
Though previously bluetooth and Wifi both were started using the same hardswitch, Bluetooth nowhere to be seen.
I tried reinstalling the all the bluetooth packages including
Bluez and bluez-gnome. Still got the same error.
I fed up and reached a conclusion that my bluetooth adapter must be broken or something.
I had almost closed the chapter.
Last month I tested Ubuntu 11.04 using a live USB and when I switched my wifi on to connect to internet, bluetooth icon popped up in the notification area. I first though it was an error because of the beta version I tested. But the bluetooth was actually working and I transferred some files to my phone successfully.
Now a question came up why is bluetooth not working in 10.04?
I again reinstalled everything related to bluetooth but result is still the same, no bluetooth.
Can anyone help me to get my bluetooth back?
Note 1: Please don't suggest an upgrade as none of the upgrades are stable enough for me to use as a primary OS. 
Note 2:I never tried a dongle to surely know about a software problem

---

