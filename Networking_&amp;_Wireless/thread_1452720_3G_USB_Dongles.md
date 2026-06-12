---
title: "3G USB Dongles"
date: 2010-04-12
forum: Networking &amp; Wireless
---

### Post by yporat on 2010-04-12
Hi,
Does anyone know of an official link to Ubuntu compatible 3G USB Dongles.
I am looking for those that are "open", meaning not sold and locked by a carrier like AT&T, or T-Mobile.
I want to travel with it and use it in any country with a local SIM and data plan.
I am currently using Ubuntu 9.10 but can upgrade if need be.

Thanks in advance,
Yosef Shevah Porat
Nextel Mexico

---

### Post by pdc on 2010-04-12
various ebay sites offer such things:

here is one from australia I found:

[http://computers.shop.ebay.com.au/items/Wireless__W0QQBrandZHuaweiQQ_catrefZ1QQ_dmptZAUQ5fModemsQQ_flnZ1QQ_sacatZ162340QQ_ssovZ1QQ_trksidZp3286Q2ec0Q2em282](http://computers.shop.ebay.com.au/items/Wireless__W0QQBrandZHuaweiQQ_catrefZ1QQ_dmptZAUQ5fModemsQQ_flnZ1QQ_sacatZ162340QQ_ssovZ1QQ_trksidZp3286Q2ec0Q2em282)

some folks are very taken by the various Huawei devices eg the E5830

as it seems to pick up 3G (with appropriate simcard inserted etc!!) and then broadcasts wifi so > 1 laptop can receive;

the adverts for unlocked will say unlocked; or what worked for me is buying second-hand eg E220 Huawei; upgrade firmware (double the speed) and unlock via various sites ......

again, these ebay sites advertise folks that offer unlocking

any help?

---

### Post by Sven6210 on 2010-04-14
I can not recommend the Huawei E5830 for '[yporat]("http://ubuntuforums.org/member.php?u=1052828")' as it will not meet his requirements. I have the Huawei E5830 and it is a great device. It is a combination of a WiFi access point and a 3G modem. The device establishes a connection with the 3G provider and up to 5 users can connect to the device via WiFi.

So far so good for '[yporat]("http://ubuntuforums.org/member.php?u=1052828")', however if you change the SIM card you also need to change the APN, username and password in the E5830. The web-interface does not allow these changes through WiFi and you need to connect the device with a Windows machine in order to change the APN settings with the Huawei software.

Summary: E5830 is a great device if you do not need to change the SIM (country) or if you have access to a windows machine when changing the SIM (country).

The better solution for '[yporat]("http://ubuntuforums.org/member.php?u=1052828")' is the Huawei E160. It works out-of-the-box with Ubuntu 9.10 and 10.04 (I did not try it on earlier versions). I also have this device and I am very happy with it. Also sending and receiving SMS is no problem with the E160 (necessary for some prepaid provides), see [http://ubuntuforums.org/showthread.php?t=1407288](http://ubuntuforums.org/showthread.php?t=1407288).

I can not say which other 3G modems suits, but the E160 will definitely do it. All changes such as APN, user name, password etc. can be configured with the standard 'network-manager' of Gnome when you change the SIM (country).

---

### Post by williamroddy on 2010-04-19
Been a while since I've asked for help. In the hospital. Got an at&t GlobeTrotter USB 3g for use while in here. Works on Win 7. I've upgraded to lucid 10.04, and for a while, using usb-modeswitch made it work on Lucid. But now, nothing. It freezes everything and I have to do a hard shut-down. Please help. Can't be stuck in hospital with only food, water, and Windows. (Same results on Dell Mini-10 and Acer Aspire 5532.)

---

### Post by yporat on 2010-04-21
Thank you all for the useful tips...
I will see if I can purchase one of the recomended modems and then update you guys on the status.

Yosef Shevah Porat
Nextel Mexico

---

### Post by Sven6210 on 2010-04-22
Today I made an upgrade of the firmware of the E5830 and with this update you can change the APN profile through the web interface.  With that upgrade I can hardly recommend the E5830 for Ubuntu Users - it will work very well.

A great piece of hardware.

---

### Post by pdc on 2010-04-22
to Sven:

> Today I made an upgrade of the firmware of the E5830 and with this update you can change the APN profile through the web interface. With that upgrade I can *hardly* recommend the E5830 for Ubuntu Users - it will work very well.

You do mean that you can recommend the E5830 now?

---

### Post by Sven6210 on 2010-04-22
I can absolutely recommend the E5830 with the latest firmware.

As I use UMTS in several countries (I have three SIMs, two prepaid and one contract) I can change the SIM card when crossing the boarded and change the APN profile of the E5830 through a WLAN connection with any browser - so it works very well with any Linux as long a WiFi works. Even through an ipod touch you should be able to change the APN profile through the browse - however I did not try that.

If you want to be sure your 3G works under Ubuntu I personally can recommend:
1. Huawei E5830 - the luxury version as it offers WiFi for up to five devices
2. Huawei E160 - solid solution working out of the box

When it's getting to SMS it gets a little more tricky. So far I am not able to send and receive SMS with the E5830, however through the E160 it works.

I did not yet manage to send send and receive USSD messages (e.g. recharging prepaid accounts or inquiring account balance) with any of the obove mentioned devices yet.

---

### Post by yporat on 2010-04-28
Thanks Sven6210,
SMS is not so much critical as stability and performance,

Would you say that you get the full speed on these devices?

Thanks again,
Yosef Shevah Porat
[http://www.shimshon367.com/](http://www.shimshon367.com/)

---

### Post by Sven6210 on 2010-04-28
I have a rather good speed - but I also think that the speed depends more on the access point and the location than on the 3G hardware connected with the computer.

---

