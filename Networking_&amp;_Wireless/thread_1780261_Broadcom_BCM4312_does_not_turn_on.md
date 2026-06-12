---
title: "Broadcom BCM4312 does not turn on"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by saidhabla on 2011-06-11
Hi,

Last night I turned off my Wireless Card Broadcom BCM4312 via button. Today I can't turn it on... any help?

More Info:
System: Ubuntu 11.04 (same thing happened in 10.11 so I upgraded and it fixed itself)
Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

Thanks!

---

### Post by josephmills on 2011-06-11
could we please see a ```
rfkill list all 
``` thanks

---

### Post by saidhabla on 2011-06-12
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

Thanks!

---

### Post by josephmills on 2011-06-12
ok so the hard blocked means that the wireless switch is turned off so you need to turn it on. What kind of computer is this ?

&#1048;&#1058;&#1040;&#1050;, &#1078;&#1077;&#1089;&#1090;&#1082;&#1080;&#1081; &#1079;&#1072;&#1073;&#1083;&#1086;&#1082;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085; &#1086;&#1079;&#1085;&#1072;&#1095;&#1072;&#1077;&#1090;, &#1095;&#1090;&#1086; &#1073;&#1077;&#1089;&#1087;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1081; &#1082;&#1086;&#1084;&#1084;&#1091;&#1090;&#1072;&#1090;&#1086;&#1088; &#1086;&#1090;&#1082;&#1083;&#1102;&#1095;&#1077;&#1085; &#1090;&#1072;&#1082; &#1095;&#1090;&#1086; &#1074;&#1072;&#1084; &#1085;&#1091;&#1078;&#1085;&#1086;, &#1095;&#1090;&#1086;&#1073;&#1099; &#1074;&#1082;&#1083;&#1102;&#1095;&#1080;&#1090;&#1100; &#1077;&#1075;&#1086;. &#1050;&#1072;&#1082;&#1086;&#1081; &#1101;&#1090;&#1086; &#1082;&#1086;&#1084;&#1087;&#1100;&#1102;&#1090;&#1077;&#1088;?

---

### Post by saidhabla on 2011-06-12
Sorry my English is not good enough... I think I don't really understand what you mean with "what kind of computer is this". So here I go...

Laptop Compac-HP CQ-50 102LA

In this video [http://www.youtube.com/watch?v=GFCnYe1vAZY](http://www.youtube.com/watch?v=GFCnYe1vAZY) (in Russian) u can see in the 00:54sec the Wireless button. It's red, it has to be blue, so I press it and nothing happens... also I've tried on my Windows 7 partition and it works good in there...

Thanks again.

---

### Post by josephmills on 2011-06-12
press the wireless power button next to the power button then let us see a ```
rfkill list all 
``` thanks  

&#1055;&#1088;&#1077;&#1089;&#1089; &#1073;&#1077;&#1089;&#1087;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1081; &#1082;&#1085;&#1086;&#1087;&#1082;&#1080; &#1087;&#1080;&#1090;&#1072;&#1085;&#1080;&#1103; &#1088;&#1103;&#1076;&#1086;&#1084; &#1089; &#1082;&#1085;&#1086;&#1087;&#1082;&#1080; &#1087;&#1080;&#1090;&#1072;&#1085;&#1080;&#1103;, &#1090;&#1086; &#1076;&#1072;&#1074;&#1072;&#1081;&#1090;&#1077; &#1087;&#1086;&#1089;&#1084;&#1086;&#1090;&#1088;&#1080;&#1084; ```
rfkill list all 
``` &#1089;&#1087;&#1072;&#1089;&#1080;&#1073;&#1086;

---

### Post by saidhabla on 2011-06-12
I press it once and it's still red (off)... then:

0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

I press it again and sitll red (off):

0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

---

### Post by josephmills on 2011-06-12
try ```
rfkill unblock  all 
``` then hold down the wireless button for 10 seconds then try  ```
rfkill list all 
``` we want it to say hard block and softblock no  

&#1087;&#1086;&#1087;&#1088;&#1086;&#1073;&#1091;&#1081;&#1090;&#1077; ```
rfkill unblock all 
``` &#1079;&#1072;&#1090;&#1077;&#1084;, &#1091;&#1076;&#1077;&#1088;&#1078;&#1080;&#1074;&#1072;&#1103; &#1085;&#1072;&#1078;&#1072;&#1090;&#1086;&#1081; &#1082;&#1085;&#1086;&#1087;&#1082;&#1091; &#1073;&#1077;&#1089;&#1087;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1099;&#1093; &#1074; &#1090;&#1077;&#1095;&#1077;&#1085;&#1080;&#1077; 10 &#1089;&#1077;&#1082;&#1091;&#1085;&#1076;, &#1072; &#1079;&#1072;&#1090;&#1077;&#1084; &#1087;&#1086;&#1087;&#1099;&#1090;&#1072;&#1090;&#1100;&#1089;&#1103; ```
rfkill list all 
``` &#1052;&#1099; &#1093;&#1086;&#1090;&#1080;&#1084; &#1089;&#1082;&#1072;&#1079;&#1072;&#1090;&#1100;, &#1078;&#1077;&#1089;&#1090;&#1082;&#1080;&#1081; &#1073;&#1083;&#1086;&#1082; &#1080; &#1085;&#1077; softblock 

&#1050;&#1072;&#1082; Google &#1055;&#1077;&#1088;&#1077;&#1074;&#1086;&#1076;&#1095;&#1080;&#1082; &#1088;&#1072;&#1073;&#1086;&#1090;&#1072;&#1077;&#1090;?

---

### Post by saidhabla on 2011-06-12
Still off 

0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

I pressed the button but it's still red...

(Im not russian btw :) )

---

### Post by saidhabla on 2011-06-12
Done!

It has to be 'sudo rfkill unblock all'.

Thank you so much!

---

### Post by josephmills on 2011-06-12
> **saidhabla said:**
> 

(Im not russian btw :) )
 
ROTFLMAO 


hmm.... could we see a ```
lsmod
```
nevermind glad to see that it works might have to put it in the .rc file If it wont work after reboot

---

