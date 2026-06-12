---
title: "20' sec Lag for opening any web sites in PPPOE mode [ADSL] !!!"
date: 2011-02-27
forum: Networking &amp; Wireless
---

### Post by Vahids on 2011-02-27
Hi,

ubuntu: 10.10 Updated
Modem:  Dlink DSL2740U
Internet: ADSL
Phone: Galaxy S I9000 (WiFi)

I set username/password in modem (PPPOE mode) and when modem is Turn On, I connected to Internet.
but in opening site or download file (any send packet) I have to wait ~20 sec to replay server.
but if I use Bridge mode in modem I connect to Internet by ubuntu pppoe connection everything is fine and speedy.

I need to set username/password in PPPOE mode cuse my phone is thirsty of Internet.

I don't have this issue in Phone or Windows.:confused:

[COLOR="Red"]Edit[/COLOR] ----------------------------------
I can't send this thread, after ~20 sec waiting, Firefox wants to download a "*newthread*.PHP" file !!! :confused:
I have to Exchange to bridge mode!

---

### Post by Vahids on 2011-02-27
at less tell me what's going on when i press Return key to open a website?

what's ubuntu do ?

---

### Post by Vahids on 2011-02-27
> **vahids said:**
> hi,

ubuntu: 10.10 updated
modem:  Dlink dsl2740u
internet: Adsl
phone: Galaxy s i9000 (wifi)

i set username/password in modem (pppoe mode) and when modem is turn on, i connected to internet.
But in opening site or download file (any send packet) i have to wait ~20 sec to replay server.
But if i use bridge mode in modem i connect to internet by ubuntu pppoe connection everything is fine and speedy.

I need to set username/password in pppoe mode cuse my phone is thirsty of internet.

I don't have this issue in phone or windows.:confused:

[color="red"]edit[/color] ----------------------------------
i can't send this thread, after ~20 sec waiting, firefox wants to download a "*newthread*.php" file !!! :confused:
I have to exchange to bridge mode!

help me..........

---

### Post by dineshs on 2011-03-01
May be a problem with MTU.Set MTU to 1482 via network manager(Hope you are using network manager for configuring devices)
Rightclick NM icon-edit connections-under wired tab select ethernet-edit-change MTU-apply and restart

---

