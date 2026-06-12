---
title: "Huawei E5830 with Ubuntu"
date: 2010-02-20
forum: Networking &amp; Wireless
---

### Post by Sven6210 on 2010-02-20
I have the Huawei E5830 (similar to the Huawei E5) UMTS modem incuding a WiFi router. It is a very convenient device and allows several computers to share one UMTS connection by WiFi. It works without problems with Windows. Unfortunately I can not access it through USB from Ubuntu. And in order to change the APN/profile I need to access it via USB as the web interface doesn't allo to change the APN/profile name.

Does anybody has experience with this device under Ubuntu? Any help would be welcome.

---

### Post by pdc on 2010-02-21
how about this? 

[http://ubuntuforums.org/showthread.php?t=1409916](http://ubuntuforums.org/showthread.php?t=1409916)

---

### Post by Sven6210 on 2010-02-22
That threat is not answering my question.

I can connect to the internet. However, when changing the SIM (changing the country) I still need a Windows machine in order to change the profile (APN, user nam etc.) for the new SIM. And I can not send SMS through the device even though I connected it via USB to my Ubuntu.

It is a great device but I can't fully use it under Ubuntu yet :(

---

### Post by Sven6210 on 2010-04-22
Today I installed the new firmware of the Huawei E5830 and now I am able to change the APN profile through the web interface.

Now the only issue I still have: I can not send or receive SMS with the E5830 and I can not send USSD messages in order to recharge my account or inquire my accounts balance.

---

### Post by haswig on 2010-04-22
Hi,

which firmware did you use?

is it possible to turn off the firewall with this one?

greeting

---

### Post by Sven6210 on 2010-04-22
I use the latest version as published on:

[http://blog.brightpointuk.co.uk/huawei-e5-e5830-e5832-imo-firmware-update-available](http://blog.brightpointuk.co.uk/huawei-e5-e5830-e5832-imo-firmware-update-available) 

with the file name 'WLCGCPU11020_UPDATE_ALL_NO_QCSBL_V100R001C00B112SP05_USB.exe'

FTP address:

[ftp://ftpaccess:Brightpoint1@ftp.brightpointuk.co.uk/Technical%20Support/Huawei/e5832/WLCGCPU11020_UPDATE_ALL_NO_QCSBL_V100R001C00B112SP05_USB.exe](ftp://ftpaccess:Brightpoint1@ftp.brightpointuk.co.uk/Technical%20Support/Huawei/e5832/WLCGCPU11020_UPDATE_ALL_NO_QCSBL_V100R001C00B112SP05_USB.exe)

Yes, you can turn the firewall off - at least you have a setting in the web interface to do so. But I did not try nor verify the function. I am just glad that I can change the APN profile through the web interface now.

The only outstanding issue:
I have not been able to send or receive SMS messages or USSD code (e.g. for charging the prepaid account or inquiring the account balance) through Ubuntu. If you connect the device through USB with a Ubuntu machine it is not recognised as modem with AT command set, probably because the firmware of the device itself manages the modem within the device (otherwise it would probably not be possible for the device to connect itself).

I will keep on looking for a solution. At least sending and receiving SMS would be great as one of my prepaid operators requires that I send an SMS to book a daily or monthly package.

---

### Post by haswig on 2010-04-23
Thanks for the quick reply

> **Sven6210 said:**
> I use the latest version as published on:

[http://blog.brightpointuk.co.uk/huawei-e5-e5830-e5832-imo-firmware-update-available](http://blog.brightpointuk.co.uk/huawei-e5-e5830-e5832-imo-firmware-update-available) 

with the file name 'WLCGCPU11020_UPDATE_ALL_NO_QCSBL_V100R001C00B112SP05_USB.exe'

FTP address:

[ftp://ftpaccess:Brightpoint1@ftp.brightpointuk.co.uk/Technical%20Support/Huawei/e5832/WLCGCPU11020_UPDATE_ALL_NO_QCSBL_V100R001C00B112SP05_USB.exe](ftp://ftpaccess:Brightpoint1@ftp.brightpointuk.co.uk/Technical%20Support/Huawei/e5832/WLCGCPU11020_UPDATE_ALL_NO_QCSBL_V100R001C00B112SP05_USB.exe)


ok, flashed it and worked fine (on the 2nd run)

> 
Yes, you can turn the firewall off - at least you have a setting in the web interface to do so. But I did not try nor verify the function. I am just glad that I can change the APN profile through the web interface now.

The only outstanding issue:
I have not been able to send or receive SMS messages or USSD code (e.g. for charging the prepaid account or inquiring the account balance) through Ubuntu. If you connect the device through USB with a Ubuntu machine it is not recognised as modem with AT command set, probably because the firmware of the device itself manages the modem within the device (otherwise it would probably not be possible for the device to connect itself).

I will keep on looking for a solution. At least sending and receiving SMS would be great as one of my prepaid operators requires that I send an SMS to book a daily or monthly package.

I found a setting to activate UPNP. Maybe there is a program which handles SMS over upnp?

Edit: Strange thing is that i get a other ID when i connect to Linux(openwrt) over USB. With the org. firmeware i got 1446 for storage and when i turn on umts i got 1401. Now i stays by 1446 and the modem is not recognized.

---

### Post by haswig on 2010-04-26
> **Sven6210 said:**
> 
I will keep on looking for a solution. At least sending and receiving SMS would be great as one of my prepaid operators requires that I send an SMS to book a daily or monthly package.

I have look into www-folder on the e5830. and there should be some sites to send and receive sms. I tested it and could send and receive SMS. The link is //routerip/en/sms.asp.

hth

---

### Post by Sven6210 on 2010-04-26
That's it for sending an receiving SMS. I just tried it and it works great.

The normal web interface I access through:

   [http://192.168.1.1/](http://192.168.1.1/)

After login I am on:

   [http://192.168.1.1/en/content.asp](http://192.168.1.1/en/content.asp)

And with manually entering the following address I can send and receive SMS:

   [http://192.168.1.1/en/sms.asp](http://192.168.1.1/en/sms.asp)

Works great. It looks like the SMS menu is existing but not integrated into the main content page.

Now I'm only lacking the possibility to send and receive USSD messages in order to recharge my prepaid account or inquire the accounts balance. Does anybody have an idea for that? How can I find out what other 'webpages/services' might be hidden on my E5830?

Best regards

Sven

---

### Post by haswig on 2010-04-27
> **Sven6210 said:**
>  How can I find out what other 'webpages/services' might be hidden on my E5830?


I did it by telneting to the e5 and browsing through the www folder. I took a screenshot from it. [http://bilderhost.com/show.php/861_www-en.jpg.html](http://bilderhost.com/show.php/861_www-en.jpg.html)

[IMG]http://bilderhost.com/show.php/861_www-en.jpg.html[/IMG]

There is also a ussd_sim_card_handle.asp, but it didn't work with my simcard.

---

