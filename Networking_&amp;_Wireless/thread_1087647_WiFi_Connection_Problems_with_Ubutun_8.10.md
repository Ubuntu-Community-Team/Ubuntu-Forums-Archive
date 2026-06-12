---
title: "WiFi Connection Problems with Ubutun 8.10"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by jesiel on 2009-03-05
Hello people.
I'm using Ubuntu 8.10.
I bought NetGear Router model WGR614 and in my desktop I have LG WiFi PCI-Card IEEE 802.11b

So, I configured a WPA secury protocol in my WiFi network.
In the Windows XP it's working perfectly.

But in the Ubuntu 8.10... in the first time that I tried to use it, the WiFi connection speed was only 10% of total... ;-(... it's so slowly...

But now... I can't logging in my WiFi NetWork... the Ubuntu does not authentic my PassWord ( WPA ).

I already tried to found one solve in the Internet...but I only found people with this problem... the solution... I could not found it...

Someone can help please?

---

### Post by nidelius on 2009-03-05
you would have to specify your hardware more exactly. Model of laptop or run some commands like

```
lspci
```

in the terminal and look for "network controller:" to show what wireless chip you are using

---

### Post by jesiel on 2009-03-05
Sure...

> lspci:
...
01:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
...


Today, I updated the system... and some news packages has been installed for NetWork.

Now... I can loggin in my Network WiFi... but the speed is only 10% or 15% ....

I tryied to found how to configure Realtek RTL8180L drivers in the web... but I could not had success...

I'm a new user in the Linux SO... so I would like to receive step by step instructions to get configure de PCI-WIFI card ... if it's possible...

Thanks.

---

### Post by nidelius on 2009-03-05
The open source driver only supports non encrypted drivers.
Install the windows driver and you'll probably get it working I found this:

[http://ubuntuforums.org/showthread.php?t=801830](http://ubuntuforums.org/showthread.php?t=801830)

And this old guide but I think it'll still be working if you follow it

[https://help.ubuntu.com/community/WifiDocs/Device/RTL8180L](https://help.ubuntu.com/community/WifiDocs/Device/RTL8180L)

---

### Post by jesiel on 2009-03-05
I see.
I had found this old guide.
I tried to follow it but... I could not have success in the configuration.

I`m begginer in the Linux SO... and some peaces of this guide, the information is not Step-by-Step... so it's a little hard for me understand all the steps ( so many... )

Any way... I'll try again follow all the guide's steps.

But if you or outher person, that using this guide... can make a easy way ( for begginer user ) showing how configure the WiFi drive, please let me know...

This problem is so common in the web... many many people that I found has the same problem about connection speed in WiFi networks.

Thanks.

---

### Post by nidelius on 2009-03-05
I understand that it's confusing. It is for everyone in the begining. And it's really annoying when it's not working as expected.

I can not tell exactly how to do in your specific case as I don't have time to investigate it deeper. But there are more general guides on how to set up ndiswrapper use google
search for your wireless network modelnumber and ndiswrapper for example

here is a more general guide on how to set up ndiswrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

