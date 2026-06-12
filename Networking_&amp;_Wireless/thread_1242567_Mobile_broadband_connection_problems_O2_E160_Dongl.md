---
title: "Mobile broadband connection problems O2 E160 Dongle"
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by Jsturdy on 2009-08-17
[FONT=Calibri][SIZE=3]Hi there,[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]I am an absolute novice when it comes to Ubuntu. My girlfriend recently purchased a Dell notebook with version 8.04 and network manager 0.7. [/SIZE][/FONT][COLOR=black][FONT=Verdana]I’m not very clued up on laptops and mobile broadband so your help is very much appreciated. [/FONT][/COLOR]
 
 
[COLOR=black][FONT=Verdana]I plug the dongle in (E160) and the system knows the dongle is present, the blue flashing light is appearing on the dongle so there is coverage but it just won’t connect.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]A wizard appears with the following [/FONT][/COLOR]
 
[FONT=Verdana][COLOR=black]New Mobile Broadband connection setup. [/COLOR][/FONT]
 
[FONT=Verdana][COLOR=black]I select UK followed by O2 (pre-pay)the summary appears and comes up with service provider and name etc.. [/COLOR][/FONT]
 
[FONT=Verdana][COLOR=black]Now the configuration is set up i click on properties and the information of the dongle comes up. [/COLOR][/FONT]
 
[FONT=Verdana][COLOR=black]Tells me the model, version, driver, data device, imsi number and IMEI number. [/COLOR][/FONT]
 
[FONT=Verdana][COLOR=black]I try to connect it just seems to be consistently trying to connect but never succeeding. [/COLOR][/FONT]
 
[FONT=Verdana][COLOR=black]Have i done something wrong?[/COLOR][/FONT]
[COLOR=black][FONT=Verdana]No error messages, basically it tries to connect and the icon does a moving symbol. If I hover over I get ALT text saying it’s dialling and names my device but never connects. I checked that I topped up successfully because the woman at O2 said £15 was put on and I have a month’s worth of net time. [/FONT][/COLOR]
[FONT=Verdana][COLOR=black]I’m getting really frustrated now. [/COLOR][/FONT]
[FONT=Calibri][SIZE=3]If you do not undserstand what I’m saying, I will try and simify as much as I can.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Do I need to put any settings in myself? [/SIZE][/FONT][COLOR=black][FONT=Verdana]Very stressed newbie:([/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Cheers everyone in advance any answers would be much appreciated..[/FONT][/COLOR]

---

### Post by Neill_R on 2009-08-17
Do you have access to a windows PC ? If so try that as an alternate test of the dongle. I am on Orange and although it connected with out extra information I chose to enter the information i gave for the windows connection.. I am also a newbee and have Xubuntu 9.04 had to run a program to turn off the CDROM drive and allow the modem to take over. But you seem to have done that already.

---

### Post by JohnFH on 2009-08-17
In 8.04 (and in later versions too I believe) the default username/password for the O2 mobile broadband is incorrect.  To fix it, edit the O2(prepay) connection in network manager and set the following details:

username: <your O2 mobile broadband number> 
password: 'password'
APN:  m-bb.o2.co.uk

Hope that works for you.

---

### Post by pi4r0n on 2009-08-17
Hello [B]Jsturdy

[/B]I have got mobile phone from O2 with _*unlimited data*_ and as far as I know they are exactly the same OK. I had this problem connecting my mob as dongle and managed to find [**this web**]("http://myhowtosandprojects.blogspot.com/2008/11/htc-diamond-as-rndis-modem.html"). I would suggested you to give a go. Its not difficult to do; so you should be OK on your own if not send me private message and will help you with this.

Cheers

pi4r0n

---

### Post by JohnFH on 2009-08-17
> **pi4r0n said:**
> Hello [B]Jsturdy

[/B]I have got mobile phone from O2 with _*unlimited data*_ and as far as I know they are exactly the same OK. I had this problem connecting my mob as dongle and managed to find [**this web**]("http://myhowtosandprojects.blogspot.com/2008/11/htc-diamond-as-rndis-modem.html"). I would suggested you to give a go. Its not difficult to do; so you should be OK on your own if not send me private message and will help you with this.


Ummm ... they are not the same.  One is a phone and the other is a broadband dongle.  Your 'fix' is completely irrelevant I'm afraid.

---

### Post by pi4r0n on 2009-08-18
Hi **JohnFH**

When I take my SIM Card out of the phone and stick it in to the dongle it works :) as I got this unlimited data plan (similar to dongle)

I could not connect before neither with my mob or dongle until I done this fix so I might be worth to try ??

Cheers

Arek

---

### Post by Jsturdy on 2009-08-20
[FONT=Calibri][SIZE=3]Thank you everyone for your replies but unfortunately still no closer to solving. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]It seems I’m inputting the wrong settings manually. Could anyone be so kind to post the settings that worked for them?[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Cheers in advance.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]BTW it does for a signal because it knows the IMEI number etc… and tells me the signal strength but does just not connect. I tried on a windows OS and it worked first time. [/SIZE][/FONT]

---

### Post by Crispian Troy on 2009-08-20
first uninstall and re install modem drivers and ur phone drivers and then connect ur phone.
it may b usefull for u


[GPS Based Wireless Solution](http://www.betaar3.com)

---

### Post by Jsturdy on 2009-08-21
Anyone know what i type in to bring up a terminal command? Apparently this might tell me what my problem is.
 
Cheers

---

### Post by vkolosowski on 2009-08-29
Hi I got here trying to solve the same problem. In the PPP settings tab on connection manager try unchecking all authentication methods except PAP. Fixed it for me with the other settings being  

Number *99#
Username o2bb
Password password
APN m-bb.o2.co.uk

Currently running 9.04 on a Samsung NC10.

Hope this helps

---

### Post by ruffmeup on 2009-09-03
hello dont no if im doin this in the rite place but here gos............i have a 3 e1550 dongle that i need to unlock the imei number is...353142039258069..if u can help in instructin me on how to do it id b verry greatfull ...u can email me [EMAIL="at...jes1863@googlemail.com.....thanks"]at...jes1863@googlemail.com.....thanks[/EMAIL]

---

### Post by Jsturdy on 2009-09-11
> **vkolosowski said:**
> Hi I got here trying to solve the same problem. In the PPP settings tab on connection manager try unchecking all authentication methods except PAP. Fixed it for me with the other settings being 
 
Number *99#
Username o2bb
Password password
APN m-bb.o2.co.uk
 
Currently running 9.04 on a Samsung NC10.
 
Hope this helps
 
[SIZE=2]Thank you and thank you eberyone.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]After a month of hardship finally sorted. [/SIZE]
[SIZE=2]An upgrade to 9.04 was the solution.[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]Thanks everyone for your responses. :D[/SIZE]

---

### Post by thoughto on 2009-11-26
vkolosowski**Re: Mobile broadband connection problems O2 E160 Dongle**
Hi I got here trying to solve the same problem. In the PPP settings tab on connection manager try unchecking all authentication methods except PAP. Fixed it for me with the other settings being

Number *99#
Username o2bb
Password password
APN m-bb.o2.co.uk

Excellent! That worked great for me. I've never managed to get the O2 dongle to work despite the fact that the 3 one worked straight away. Very grateful, Tom

---

### Post by gibbylinks on 2010-03-11
Thanks Guys. Got my dongle today and connected straight away....can't believe how easy it was. And the woman at O2 said it wouldn't work with linux...ha !! :p

Just a thought for anyone reading this. I did have to remove the dongle and put it back in to get this to work.

---

