---
title: "I can not adjust connection to the Internet in Ubunta 10.4"
date: 2010-07-02
forum: Networking &amp; Wireless
---

### Post by TheIVA on 2010-07-02
Hello! (In advance I apologise for the text, wrote through the translator.)

At me terrible position. Which month I try to pass with Windows on Linux — but it is impossible.

On Ubunta 8 — there is an Internet, there is no sound.
On Ubunta 9 — there is no Internet.
On kubunta (the avenue 8-9) — is a sound and the Internet, but it has removed Windows from the loader and I by nonsense have taken down it. In results all has ended with disk formatting.
On Fedora — is not present &#1085;&#1101;&#1090;&#1072;.
**Has now established Ubunta 10.4 — the Internet is not present.**

At me:
The provider: [COMSTAR]("http://www.aaanet.ru/cts") (Taganrog)
Connection: through DOCSIS.
Router: no.
The modem: [Motorola SB5100]("http://www.motorola.com/Business/US-EN/Business+Product+and+Services/Cable+Broadband/SURFboard+Modems+and+Gateways/SB5101_US-EN") — here about 101, but they are similar.
The modem is connected through "Ethernet".
Connected so: the Network manager-DSL-create - here entered a login and the password, all.
On others Linuxs worked.

Results "ifconfig":

eth0      Link encap:Ethernet  HWaddr 00:1d:7d:90:ee:d3  
          inet6 addr: fe80::21d:7dff:fe90:eed3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27431 (27.4 KB)  TX bytes:2740 (2.7 KB)
          Interrupt:25 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:166 errors:0 dropped:0 overruns:0 frame:0
          TX packets:166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15614 (15.6 KB)  TX bytes:15614 (15.6 KB)

Thanks.

---

### Post by grahammechanical on 2010-07-02
Hello! I do not know if I can help. I am not an expert. I am not familiar with cable modems. so forgive me if I give stupid advice. I have read the Motorola instruction PDFs. They are in English. I am English and I did not find them helpful (an example of famous English understatement).

You say that you have used Network manager - DSL - create [ADD on English Ubuntu]. You have entered "a login and the password, all." Which login and password? The one that give access to your computer? Or the one that gives access to the cable modem?

The Motorola instruction PDFs do not mention the need to enter a password. This I do not understand. My broadband modem is programmed by the ISP to dial its network but the modem needs my ISP account username and password to connect. I can use a web browser to put my ISP username and password into the broadband modem. I expected a similar process for your cable modem.

I use ethernet cable to connect the modem to my computer. Just as you do. I do not use DSL. I use Auto Eth0 set to connect automatically. It does not need a login and password. This is why I think that you may have entered the wrong password. Try using Auto Eth0 to connect. Do you know of a way to access the settings stored in the cable modem? Can you confirm that the cable modem is connecting to the cable service providers network?

I am not sure if any of this will help. Regards

---

