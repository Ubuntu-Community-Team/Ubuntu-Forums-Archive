---
title: "How to send sms via ZTE MF100 modem"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by sovichet on 2010-12-14
Hello! I'm a beginner in Ubuntu. I'm from Cambodia. I've purchased a modem (model ZTE MF100). It work very well on ubuntu. But i want to know, which application that allow to send sms via this modem model?

Thank you,
Sovichet Tep.

---

### Post by alexfish on 2010-12-15
hi

try wammu

---

### Post by sovichet on 2010-12-15
Oh! Thank you very much! Now i can send the sms from my modem to my friend. By the way, do you know other app that allow us to use USSD to check balance or refill balance? coz Wammu allow ZTE MF100 modem to send sms, check contact only :)

I hope you know about this.

Thank you :) ;)

---

### Post by alexfish on 2010-12-15
> **sovichet said:**
> Oh! Thank you very much! Now i can send the sms from my modem to my friend. By the way, do you know other app that allow us to use USSD to check balance or refill balance? coz Wammu allow ZTE MF100 modem to send sms, check contact only :)

I hope you know about this.

Thank you :) ;)

each service provider may have different dial codes and procedures + different encoding and decoding
 on of the easiest ways ,
find out if your service provider has " web page account" most do have this , google search "your provider accounts"  or ask your provider for a how to access . 

back to the software , only advice is to search the web , try them :

only thing to watch out for and possibly avoid  , are software packages which want to change system settings , or remove vital dependencies of existing connection managers. Treat with caution , 
if they can't provide answers to these two basics,. Best advice : **if in doubt. Don't install**

one of the safest way to experiment with is , use a serial terminal , armed with the necessary AT commands . :p

Have fun

Added a useful Link

[http://www.developershome.com/sms/GSMModemIntro.asp](http://www.developershome.com/sms/GSMModemIntro.asp)

alexfish

---

### Post by kasun.gamlath on 2011-01-18
but how to configure wammu to recognice ZTE MF100??

---

### Post by alexfish on 2011-01-18
Hi

there should be a wizard in the menus

if met with failure can try gammu-config from the terminal

Code:

gammu-config


it should produce a  " .gammurc" file in the home directory

something like :

[gammu]

port=/dev/ttyUSB1
model=auto
connection = at115200
synchronizetime = yes
logfile = 
logformat = nothing
use_locking = 
gammuloc = 
name=myisp

---

### Post by MarkoCro on 2011-07-24
Here's how I do it using gammu for CLI and you also have GUI wammu:

[http://www.techytalk.info/send-receive-sms-using-gsm-modem-phone-ubuntu/]("http://www.techytalk.info/send-receive-sms-using-gsm-modem-phone-ubuntu/")

Man I love Linux :)

---

