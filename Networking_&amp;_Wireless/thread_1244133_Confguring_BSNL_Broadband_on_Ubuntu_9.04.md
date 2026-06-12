---
title: "Confguring BSNL Broadband on Ubuntu 9.04"
date: 2009-08-19
forum: Networking &amp; Wireless
---

### Post by aditya.gnu on 2009-08-19
:PHi All Ubuntu Geeks,
Ive recently installed the latest distribution of Ubuntu 9.04 and I am trying to configure the BSNL Broadband Internet connection onto it, But I am unable to do so. 
Some of my attempts were by installing using **rp-pppoe.tar.gz** package, but it was of no use.
And when I executed the command** "mii-tool"** its result is failing by displaying my ethernet card is not been detected.
And for your information my PC is MSI Motherboard 754 Socket and AMD Athlon 64" Processor with 1.2GB of RAM and it's 3 yrs old one.
Is it because my PC is outdated or if there is some thing else, Kindly let me know.**ASAP**.
[B]And also the steps for configuring BSNL Broadband on Ubuntu 9.04.(Screen shots if possible).
[/B]
Thanks in Advance.
Regards,
Aditya.:KS

---

### Post by nagub on 2009-08-19
Is it that you are referring to BSNL Evdo , by any chance ?

---

### Post by aditya.gnu on 2009-08-19
No not bsnl evdo, its Normal Internal through a ADSL Modem ie Dataone with its variety of Internet Subscription Plans. I hope u got it na..

Regards,
Aditya.

---

### Post by superprash2003 on 2009-08-19
hope this guide helps [http://www.prash-babu.com/2009/08/configure-bsnl-airtel-mtnl-in-ubuntu.html](http://www.prash-babu.com/2009/08/configure-bsnl-airtel-mtnl-in-ubuntu.html)

---

### Post by aditya.gnu on 2009-08-20
Well thanks Prashant for providing the link , I'll surely try it and let u know the status.

Aditya.

---

### Post by varunmagical on 2009-08-20
Hi,
I am a BSNL broadband user.
there are two simple ways ( each of 8 steps):

WAY 1:

1.launch terminal
2.Keep your modem on
3.type this:  sudo pppoeconf
4.enter your password(Ubuntu password)
5.select next or yes to everything ( just enter your bsnl username & password when prompted)
6. You are done!
7. Internet will be connected automatically when your modem is on!
8. ENjoy & welcome to ubuntu!

Way 2:

1.click on the two monitors(networking) icon in right top corner of screen ( near calender)
2.vpn connection->configure vpn
3.dsl tab
4.enter bsnl username & password
5.click apply
6. You are done!
7. Internet will be connected automatically when your modem is on!
8. ENjoy & welcome to ubuntu!

---

### Post by aditya.gnu on 2009-08-21
Thanks for the suggestions Varun, but what if I wanted to connect manually like in Windows , rather an automatic connection.
Kindly send some hints on this issue, to be frank is it possible in this way or will it rise to installation in some other dependency package.

Aditya.

---

### Post by neophyte_7 on 2009-08-21
You can switch on/off the modem..I guess......

:popcorn::KS

---

### Post by 10Digits on 2009-09-02
One way of configuring the modem manually...is to enter the following commmands at the terminal...

pon-dslprovider...to turn on
poff-dslprovider...to turn off
ipconfig-ppp0...don't know what it does ....most probably tells the status of the connection.

---

### Post by editdigital on 2009-09-10
Your Second method does not work out here, because when you click on the top right corner you get option of the ethernet card and also the DSL connection. Only either on of them gets selected at a given point of time.
When the DSL is selected, the LAN connection gets unchecked and network connection with the router breaks but it tries to connect the router to DSL which is not possible now as the LAN connection is lost.

---

