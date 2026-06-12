---
title: "Upload failure"
date: 2013-05-10
forum: Networking &amp; Wireless
---

### Post by dank245 on 2013-05-10
Hi all,

I have two different devices that I use in my home and work environment (two different places, two routers). Here are some key infos about the devices:

- Toshiba Laptop, Lubuntu 13.04 (32 bit), Thunderbird as email client (incoming server is POP), Wuala as sync client (cloud storage)
- Asus Netbook, Ubuntu 13.04 (64 bit),  Thunderbird as email client (incoming server is IMAP), Wuala as sync client

At my home router I have no problem in sending and receiving emails and the Wuala sync works perfectly (down- and upload) for both devices (Laptop and Netbook). The connection is wireless.

At work the situation is another one. I perfectly receive emails and the Wuala download works properly for both devices. BUT I cannot send emails on Lubuntu (the POP account) and the Wuala upload does not work for both devices. The only upload that works is sending emails from the IMAP account. My first idea was that there might be some firewall issues, so I disabled it (sudo ufw disable) but nothing changed. 

In the very same environment is a Windows 7 PC connected by wire to the router. On this one the above mentioned email-POP-account is configured on Thunderbird and it works properly (incoming and outgoing). On this device the Wuala client is not installed. 

On my Android smartphone I have configured both email accounts (POP and IMAP) as well as Wuala syncing service. Using it wireless at the work router down- and uploads work smoothly. 

Even worse (or not), former Ubuntu versions (up from 11.04) have always worked without any complaints in the work environment. 

For me it looks like a Ubuntu problem for outgoing data, because other devices (Win 7 and Android) have not encountered this issue. 

Thanks very much in advance for your kind help.

---

