---
title: "Router as a repeater"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by dchey on 2010-03-22
I want to know if it is possible and how to setup a higain wifi antenna from a dd-wrt flashed linksys wrt54g router and use the router as a repeater and pick up the signal on my Ubunutu 8.10 with a bcm4318 54g card. The total distance is crowding 100 feet and coax does not seem to be an option.

---

### Post by 2hot6ft2 on 2010-03-22
> **dchey said:**
> I want to know if it is possible and how to setup a higain wifi antenna from a dd-wrt flashed linksys wrt54g router and use the router as a repeater and pick up the signal on my Ubunutu 8.10 with a bcm4318 54g card. The total distance is crowding 100 feet and coax does not seem to be an option.
I think you already know that router with dd-wrt will work as a repeater so I take it the question is how to get the bcm4318 54g card working.

I don't see it listed in [The Definitive 9.10 Broadcom Solution Guide]("http://ubuntuforums.org/showthread.php?t=1368699")

You may have to use the Windows Wireless Driver for 8.10
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get install ndiswrapper ndisgtk
```
Then it will be in
System > Administration > Windows Wireless Drivers

You'll need the drivers .inf file from windows to install it.
There's a how to here for setting it up:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
And a troubleshooting guide here
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

DD-WRT Repeater Bridge instructions are here:
[http://www.dd-wrt.com/wiki/index.php/Repeater_Bridge](http://www.dd-wrt.com/wiki/index.php/Repeater_Bridge)

---

### Post by 2hot6ft2 on 2010-03-22
Also see this thread for your card so you get the right driver for your card.
[BCM4318 Driver = BCMWL5 or BCMWL6?]("http://ubuntuforums.org/showthread.php?t=467129")
And
[[SOLVED] Driver BCM4318 wireless internet]("http://ubuntuforums.org/showthread.php?t=902534")

---

### Post by dchey on 2010-03-22
Thanks for you quick responce, Both the router and my bcm4318 work. The original antenna on the 4318 will pick up 4 private networks. When i hook the higain antenna to the 4318 I can pickup 12. The hot spot locations require me to move the antenna to a line of sight location and I am unable to get any network signal (when set to repeater mode) broadcast from the router to the 4318. I have never hooked up a network and am at a complete loss as to how to make this work.

---

