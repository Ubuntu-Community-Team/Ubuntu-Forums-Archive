---
title: "Mobile Broadband: How can I get it to remember the PIN?"
date: 2011-08-05
forum: Networking &amp; Wireless
---

### Post by JaegerSifu on 2011-08-05
I have a Vodafone Mobile Internet stick set up as my main Internet access, the thing is it asks me for the PIN every time I log in/start up. Is there some way to get Ubuntu to remember the pin and connect automatically on startup? I only got Ubuntu yesterday so its all new to me. Thanks

---

### Post by JaegerSifu on 2011-08-05
Also is it possible to monitor how much bandwidth is used? I have a 5GB limit and it would be good to know how much I have left.

---

### Post by JaegerSifu on 2011-08-06
It would be great if someone could help me out here, really. :)

---

### Post by alexfish on 2011-08-06
If your using network manager then  in connection details the should be a  text box labelled " PIN" 

has the pin code been entered 

can have a look at this site for data flow  etc

[http://www.pcurtis.com/ubuntu-mobile.htm](http://www.pcurtis.com/ubuntu-mobile.htm)

alexfish

---

### Post by scorp123 on 2011-08-06
I removed the PIN on my Novatel 3G modem. I simply stuck the SIM card into an old SonyEricsson mobile phone and then went into the settings there and removed the PIN. But I did write down a few other details such as the theoretic phone number of the SIM (even though I can't use my 3G SIM for phone calls it still has a mobile phone number!) + subscriber ID + contract ID + IMEI code of the modem ... so if ever my 3G modem and/or the SIM card in there get stolen I just need to call my provider's helpdesk and the SIM card and the modem get remotely deactivated.

So that's the easy route I chose. As I always keep my 3G modem in my laptop bag together with my laptop I don't find that too problematic. The only way for my 3G modem and SIM card to disappear is when and if the whole laptop bag including my laptop would get stolen ... and _that_ would by far be the bigger problem.

Automatic entry of the PIN code can be scripted if you really insist on that. I had to do it for a different 3G stick one of my customers gave me (they are a mobile phone provider!). I was supposed to use the stick whenever I wanted to establish a VPN connection into their networks. They'd check the MAC address so it really needed to be that particular stick. And I was strictly forbidden from removing the PIN code on that one.

So here is what I did:

In the repos there is a tool called **wvdial** ... you need to install it: ```
sudo apt-get update && sudo apt-get install wvdial
```

Then you need to edit the config file. On GNOME:
```
gksudo gedit /etc/wvdial.conf
```
On KDE:
```
kdesu kate /etc/wvdial.conf
```
Plain old terminal using "vi":
```
sudo vi /etc/wvdial.conf
```

My file looks like this ("Sunrise" is my provider here in CH):
```
[Dialer Sunrise]
Modem = /dev/ttyUSB0
Baud = 460800
Init1 = AT+CPIN="1234"
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0&C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = USB Modem
Phone = *99#
Username = ''
Password = ''
Carrier Check = no
Stupid Mode = yes
``` The "Init1" command up there will send the PIN code "1234" to the modem and thus unlock it! The rest of the lines initiate a 3G connection. Obviously you will need to adjust those settings for your 3G provider. Some providers use the dial-up number ***99#** to trigger a 3G connection (e.g. Sunrise in Switzerland uses this one) ... others use this: ***99***1#** (e.g. Swisscom uses this one) ... Usually your provider's web site should tell you which one it is. That's how I know the settings for my providers here in Switzerland -- it's all on their web pages if you look closely enough. So please check the web pages of your provider and adjust the settings in my example above as needed.

And then to get a nice desktop icon on GNOME I created a launcher:
```
gedit ~/Desktop/3G-Connection.desktop
``` ... with this content (needs to be adjusted):
```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Sunrise 3G Connection
Type=Application
Terminal=false
Icon=internet.png
Name=Sunrise 3G Connecion
Exec=gksudo 'gnome-terminal -x wvdial Sunrise'

```

So when I click on this launcher it will trigger a 3G dial-up connection with automatic PIN entry .... 

It's not elegant ... but at least it works.

---

