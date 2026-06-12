---
title: "Huawei e156 support"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by daigorobr on 2009-04-24
For future and for others' reference:

Huawei e156 mobile modem (GSM/3G) works flawlessy in Ubuntu with Network Manager 0.7 once you leave only PAP as authentication method (right clicking nm-applet and editing the mobile connection).
Too bad lsusb reports it as e220 (12d1:1003), elseways it could be done automagically upon plugging it.

---

### Post by geekyhawkes on 2009-04-27
Great news thanks, im thinking of getting one of these!

---

### Post by lncoll on 2009-06-05
> **daigorobr said:**
> For future and for others' reference:

Huawei e156 mobile modem (GSM/3G) works flawlessy in Ubuntu with Network Manager 0.7 once you leave only PAP as authentication method (right clicking nm-applet and editing the mobile connection).
Too bad lsusb reports it as e220 (12d1:1003), elseways it could be done automagically upon plugging it.

Ok, mine works perfect and the provider settings where already in network-manager (9.04). But the internal card reader does not work :sad::sad:, does yours work?

---

### Post by ^_Pepe_^ on 2009-07-08
Hi!

Thank you so much for the information. I have mine on the way...

Bw the way, even I know it depends so much on the provider, coverage, and so on... what speed can you reach? 

At least 1 Mbps???

Thanks,
Pepe

---

### Post by lncoll on 2009-07-08
Speed depends on; network tipe, coverage and provider (in this order).
For GPRS networks you can expect not more than 348 Kbps. in 3G networks the most usual for me is connecting at 1.5 - 1.8 Mbps.

---

### Post by ^_Pepe_^ on 2009-07-08
ok! Thanks. Anyway, it will be so much more than my HTC S730 used as 3G modem...

Regards

---

### Post by paolini on 2009-08-25
Hi, I have bought a huawei e156b recently and I cannot configure it adequately. The connection is stablished but after some minutes I am not able to acces the net anymore, although the connection does not fall. I use the Kubuntu 8.04 and I make the connection through kppp or wvdial. I have followed some routines found in the net. 

The active commands of /etc/ppp/options are

egrep -v '#|^ *$' /etc/ppp/options
asyncmap 0
auth
crtscts
lock
show-password
modem
+pap
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In this Forum it is said to leave only the PAP as authentication method)
But how can I do that using kppp or wvdial?

Thanks

---

