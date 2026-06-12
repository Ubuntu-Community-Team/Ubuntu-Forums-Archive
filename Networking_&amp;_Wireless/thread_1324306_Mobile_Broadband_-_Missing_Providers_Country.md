---
title: "Mobile Broadband - Missing Providers Country"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by kingofpc on 2009-11-12
I am trying to configure my Huawei EC226 CDMA EV-DO modem on my Ubuntu 9.10 laptop but I can't find my providers country (Sierra Leone) in the list. It will be really cool to have it there as there are three major GSM company that provides Internet services using this type of Modem. My provider is SierraTel with the number #777. Others are Zain and Tigo.

---

### Post by pdc on 2009-11-12
from their website

[http://www.sierratel.sl/products.html](http://www.sierratel.sl/products.html)

looks like they use a Huawei 220 modem; ours has configured fine on all recent versions of Ubuntu, and does fine on 9.10

so it should configure up fine for you

why not contact them directly and ask for what you need?

probably just an APN is needed;

it is not available as a google search

can you also plug your modem in; 

and type

> lsusb and copy and paste the results here

I am guessing it is

>  0x12d1 0x1003

---

### Post by kingofpc on 2009-11-12
> **pdc said:**
> from their website

[http://www.sierratel.sl/products.html](http://www.sierratel.sl/products.html)

looks like they use a Huawei 220 modem; ours has configured fine on all recent versions of Ubuntu, and does fine on 9.10

so it should configure up fine for you

why not contact them directly and ask for what you need?

probably just an APN is needed;

it is not available as a google search

can you also plug your modem in; 

and type

 and copy and paste the results here

I am guessing it is

This is the result after typing lsusb:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I can connect through the terminal command prompt after configuring and running wvdial.

---

### Post by misterfixit on 2009-12-19
> **kingofpc said:**
> I am trying to configure my Huawei EC226 CDMA EV-DO modem on my Ubuntu 9.10 laptop but I can't find my providers country (Sierra Leone) in the list. It will be really cool to have it there as there are three major GSM company that provides Internet services using this type of Modem. My provider is SierraTel with the number #777. Others are Zain and Tigo.

Don't feel left out ... the USA providers fail to list the top 5 providers, including Sprint.  I imagine that the suport crew hasn't yet been able to collect enough data from the field to set up the correct parameters.

---

### Post by GeorgeVita on 2009-12-20
Hi, from: [http://blogs.gnome.org/dcbw/2009/06/22/mobile-broadband-assistant-makes-it-easy/](http://blogs.gnome.org/dcbw/2009/06/22/mobile-broadband-assistant-makes-it-easy/)

> But if your provider isn’t listed, we need your help. [File a bug]("http://bugzilla.gnome.org/enter_bug.cgi?product=NetworkManager") in Gnome Bugzilla, tell us your provider name, your country, the common name of your plan, and the APN you use.  We’ll update the provider database with that information, and thank you profusely for making life easier for everyone else too.  We could, in the future,

Regards,
George

---

