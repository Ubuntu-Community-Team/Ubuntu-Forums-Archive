---
title: "Celcom Vodafone Huawei K3565-Z broadband setup"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by badaveil on 2010-02-19
[The configuration here is based on Celcom Malaysia's setting]

Download 3 debian files from [Borneoubuntu's Blog]("http://borneoubuntu.wordpress.com/")
install ozerocdoff_0.4-2_i386.deb
install usb-modeswitch_0.9.7_i386.deb (depends on Ubuntu Ver, if not necessary don't install)
install vodafone-mobile-connect_2.1.5.01-2_all.deb
select apn setting "celcom malaysia/malaysia/contract"/OK
create new profile:
<profile setting>
profile name:huaweik3565-3gpreferred
device model:huaweik3565
<connection preference>
username:blank
password:blank
preferred connection:3g only
authentication:default
apn host:celcom3g(lowercase)
<dns setting>
blank
ok

go to main menu/internet/vodafone connect/double-click/connect
when connection has been secured;
go to main menu/internet/firefox browser/double-click

---

### Post by st0nes on 2010-02-26
> **badaveil said:**
> 
create new profile:

Where do you create this profile?

---

### Post by badaveil on 2010-02-26
> **st0nes said:**
> Where do you create this profile?

I am sorry I cannot remember because I did it for a friend's laptop but it must be somewhere setting, right clicking something off the menu bar.

---

### Post by kradzcalypse on 2010-09-15
Hello,
My name is Rizal, I'm from Malaysia and new to Ubuntu.I've just installed ubuntu 9.04 Desktop edition from a cd.
 It is currently running side by side with Win XP (which i'll surely remove completely once i get fimiliar with Ubuntu :) ).
I'm having problem connecting to the internet using Celcom Blue Broadband (Mobile Broadband).In win XP i just have to browse for the Blue Cube installer and install and it detects connection automatically but in Ubuntu i must provide ;

Basic
Number : *99#
Username :
Password :

Advanced
APN :                (what's an APN and where to get it?)
Network :            (network name ?)
PIN :                 (?)
PUK :                 (?)


Where to get all the info from?


Thank you in advance.;)

---

### Post by badaveil on 2010-09-15
> **kradzcalypse said:**
> Hello,
My name is Rizal, I'm from Malaysia and new to Ubuntu.I've just installed ubuntu 9.04 Desktop edition from a cd.
 It is currently running side by side with Win XP (which i'll surely remove completely once i get fimiliar with Ubuntu :) ).
I'm having problem connecting to the internet using Celcom Blue Broadband (Mobile Broadband).In win XP i just have to browse for the Blue Cube installer and install and it detects connection automatically but in Ubuntu i must provide ;

Basic
Number : *99#
Username :
Password :

Advanced
APN :                (what's an APN and where to get it?)
Network :            (network name ?)
PIN :                 (?)
PUK :                 (?)


Where to get all the info from?


Thank you in advance.;)

A'kum

I did help a friend install the Celcom Vodafone Huawei K3565-Z on his Ubuntu 8.04 and got some help from Celcom on the configuration. You didn't clarify if yours is the same model?

---

### Post by kradzcalypse on 2010-09-15
Wassalam,

Thank you for answering, i'm not using vodafone models but BLUE CUBE Model H02.

Have you any experience connecting to internet via Celcom Blue Broadband?

Could you give celcom help center contact?

Thank you [badaveil]("http://ubuntuforums.org/member.php?u=620735")

---

### Post by badaveil on 2010-09-15
> **kradzcalypse said:**
> Wassalam,

Thank you for answering, i'm not using vodafone models but BLUE CUBE Model H02.

Have you any experience connecting to internet via Celcom Blue Broadband?

Could you give celcom help center contact?

Thank you [badaveil]("http://ubuntuforums.org/member.php?u=620735")

You have 2 options:

1. Check up topics at [http://forums.ubuntu.com.my/](http://forums.ubuntu.com.my/). If not available, ask for help.

2. Contact Celcom helpdesk at 1300 111 000 or dial 1111 if you&#8217;re calling from your mobile. Quote them every configuration properties and get them to tell you what it is, tell them you want to setup manually. You will be asked for your modem tel number coz they only entertain their clients. Since I was configuring for my friend but have a Celcom mobile phone account, they decided to help me out.

---

### Post by jimmers on 2010-09-16
Try installing usb-modeswitch 1.1.0-2 from synaptic



Luck


Jim

---

### Post by kradzcalypse on 2011-12-08
sorry for the late reply.
problem solved by using "sakis3g"
I found an article about it on other forum ;)

---

