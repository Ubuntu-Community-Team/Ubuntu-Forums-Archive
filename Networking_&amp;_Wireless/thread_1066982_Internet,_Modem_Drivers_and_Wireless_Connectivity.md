---
title: "Internet, Modem Drivers and Wireless Connectivity"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by khan.namatullah on 2009-02-11
Hellow to all

Guys! I am new to linux as well as to this forum too. I was wondering, that there is competition every where but microsoft is alone in the market and we have to take their operating systems. I read about Mac and linux in the books and on the net and then googled for both. Mac was stable as per views I read on different forums and articles but it was also costly and not easily available here in Pakistan. I searched for Linux and found that its no more the older command based OS and have developed alot and also find that for the beginners Ubuntu is the best. So, that's why i am here. 

First I read alot (It might not be too much :) as its too complicated to understand and read every thing).

Well finally i tried it on my brothers laptop Toshiba Tecra A7. Boooooooooooo It worked took sound card, VGA and every thing. 

**The Problem**

It took wireless driver also but I am unable to make connectivity between my Acer Aspire 4710G. both sides The Ubuntu and Vista were making connection even ubuntu some times get connected but Vista always gives message "Identifying Network".

Why did I needed to connect Vista and Ubuntu? the reason was I was unable to connect internet through Ubuntu. Because, Worldcall telecom the service provides through CDMA Based USB Modem from Anydata that is "510A" or perhaps. I don't know exactly. when i searched for the solution i found some detail to install anydata modem which required the gnome-ppp Application but when i tried to install the application through "sudo get-apt install gnome-ppp" it replied with no such application available.

then i tried another thing i connected my laptop through ethernet cross cable to the brother laptop and somehow created connectivity to use internet and updated data from their. 

Please let me know if i don't have such applications by default, how i will be able to install the drivers and updates as to do all this require the internet. is there any way?

Please consider that I am not a programmer nor person with too much knowledge... 

Thanks and Regards 

Khan

---

### Post by khan.namatullah on 2009-02-24
Hey all

I am still waiting for your response

I have used some stuff from different forums and came to know that my laptop is not detecting USB EVDO modem as modem but as a USB CD ROM drive. please help me out of the problem and let me know if any thing else is needed. 

I used this thread for my solution 

[http://www.linuxquestions.org/questions/linuxanswers-discussion-27/discussion-cdma-modemphone-howto-452943/](http://www.linuxquestions.org/questions/linuxanswers-discussion-27/discussion-cdma-modemphone-howto-452943/)

It clear every thing described in the thread even with more updated versions but when i run dmesg command it donot show the modem. It detects my device as USB CD ROM instead of as a modem.

Thanks and Regards

---

### Post by White Owl on 2009-02-24
What ever you do on the wireless end. Do NOT buy Quickertek products. They do not work right. I bought a Quickey Jr. and it never worked right. Dropped signals even next to the router. BOYCOTT QUICKERTEK!

---

### Post by khan.namatullah on 2009-02-26
well dear 

I am still waiting for help from all of you.

this is what i get from dmesg command

[ 1071.434954] scsi5 : SCSI emulation for USB Mass Storage devices

[ 1071.437326] usb-storage: device found at 5

[ 1071.437338] usb-storage: waiting for device to settle before scanning

[ 1071.538873] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)

[ 1071.600946] usbcore: registered new interface driver ndiswrapper

[ 1076.437888] usb-storage: device scan complete

[COLOR="Red"]**[ 1076.440849] scsi 5:0:0:0: CD-ROM            AnyDATA  CD-ROM           1.00 PQ: 0 ANSI: 2**[/COLOR]

[ 1076.449701] sr1: scsi3-mmc drive: 0x/0x caddy

[ 1076.451891] sr 5:0:0:0: Attached scsi CD-ROM sr1

[ 1076.452165] sr 5:0:0:0: Attached scsi generic sg2 type 5

[ 1076.708699] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00

[ 1076.708735] sr: Sense Key : No Sense [current] 

If needed i can post all the data what get from dmesg but here my concern was "ANY DATA" USB CDMA modem.

Please let me know how to configure it as a modem.

---

### Post by olalaaa on 2009-09-11
A cdma modem is NOT wireless connectivity device.

It is not for connecting 2 computers together. It is like a mobile phone, that call the network and connect to the internet. It is NOT for creating a LAN, but a internet connection with the provider.

So actually you need to have a different device for wireless connectivity.

If you switch the usb-storage into a usb-serial device, you gain access to a "mobile phone device", not to a "network card".

This switch is possible for the devices mentioned at the bottom of this page below

[http://www.draisberghof.de/usb_modeswitch/index.html](http://www.draisberghof.de/usb_modeswitch/index.html)

and is doable using the procedures from that page, too.

---

