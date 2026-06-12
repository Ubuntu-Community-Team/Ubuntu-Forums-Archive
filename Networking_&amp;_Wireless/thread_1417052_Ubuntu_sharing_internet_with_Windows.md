---
title: "Ubuntu sharing internet with Windows"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by DBQ on 2010-02-26
Hi everybody. I have an Ethernet hub, and want two computers (both notebooks) to share my internet connection. One is running Ubuntu 9.10 and the other is running Windows Vista. I want both computers to be able to connect to the internet (I use a cable modem).

However, when I plug both computers in, I am able to get only one of them working at one time. When Ubuntu works with the internet, Windows does not work (although it sees the internet connection). When Windows works, Ubuntu sees the connection, but cannot connect.  Any help would be nice.

---

### Post by Iowan on 2010-02-26
Hmmm... I remember a similar thread some time ago (I don't think it got solved...). Do both machines get (different) IP addresses?

---

### Post by Whisp3r on 2010-02-26
It sounds like your router has one of the following problems:

DHCP isn't working. 
It's settings only allow one host to be connected. 

When you have both plugged in (I'm assuming ethernet), does one stop working if you plug the other one in? Or as long as one is connected the other doesn't?

---

### Post by captain_171 on 2010-02-26
The ISP only allows one MAC (one computer) per cable modem or DSL device this is why you need a NAT (router linksys, dlink, netgear). You can use Windows to share the connect (very bad idea) or you can use ubuntu to share the connection but you will need 2 network cards in one of them 2 computers. If you need help doing that just ask

---

### Post by DBQ on 2010-02-26
Sorry for double posting please see what I wrote in the next post.

---

### Post by DBQ on 2010-02-26
> 
When you have both plugged in (I'm assuming ethernet), does one stop working if you plug the other one in? Or as long as one is connected the other doesn't?


The latter.

> 
Do both machines get (different) IP addresses? 


Yes

---

### Post by DBQ on 2010-02-26
I also noticed that the same thing happens when both machines are booted into Ubuntu (one using liveCD 7.04).

---

### Post by DBQ on 2010-02-26
> **captain_171 said:**
> The ISP only allows one MAC (one computer) per cable modem or DSL device this is why you need a NAT (router linksys, dlink, netgear). You can use Windows to share the connect (very bad idea) or you can use ubuntu to share the connection but you will need 2 network cards in one of them 2 computers. If you need help doing that just ask

I see, but will I still at least be able to use the hub to network two machines together for say file and printer sharing?

---

### Post by MS-Hater on 2010-02-27
captain_171 is pretty much correct.

---

### Post by Iowan on 2010-02-27
My DSL modem acts like a router - it has firewall and DHCP server. Some modems don't work that way - they "lock onto" A MAC address and must be reset to work with a different address. If yours is one of those, you will need a different way to share the connection. [ICS]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is one option, a router would be another.
For ICS, you will need either a hub, switch, or crossover cable to connect the two machines. That connection *should* allow file/printer sharing... but there will be more setup required.

---

### Post by DBQ on 2010-02-27
[qoute]
That connection should allow file/printer sharing... but there will be more setup required. 
[\quote]

I assume you mean my current connection. Any pointers on how to get the file and printer sharing working?

---

### Post by MS-Hater on 2010-02-27
for windows, run the "network setup wizard" and near the end tell it to "turn on file and printer sharing". I'd suggest that you tell the windows box that it's connecting to the internet through a hub\router, else you may find that the windows box can't connect tot he 'net.after sharing files and folders is enabled, you'l have to look online to find the MS tutorial on how to share a folder. (note: LINUX will only be able to access shared folders if they're on the same "workgroup" as the LINUX box; for example, if my windows box sharing the sprint wireless broadband were on the workgroup "MSHOME", I'd have to change a specific line in the smb.conf file before the linux box could access the windows shares.) Also, when you connect to the cable modem directly, do you have to do anything, or does it automatically connect when you plug the cable in?

---

### Post by DBQ on 2010-02-27
> 
Also, when you connect to the cable modem directly, do you have to do anything, or does it automatically connect when you plug the cable in?


Both computers see the connection to the network.

---

### Post by MS-Hater on 2010-02-27
OK, just checking... from what I gather, you've got a few choices:

1.) Get a Wi-Fi router and disable the wireless aspect of it, using that as your gateway between the cable modem and the computers (only draw-backs that I can see are that it adds hardware to the setup, and if you don't chage the Wi-Fi router's default administration login info, can be potentially hijacked);
2.) See if you can hack the cable modem and override the setting that limits the connection availability to just one MAC address (theoretically possible, but, admittedly, potentially risky and very difficult for all but the most elite hackers out there);
3.) Take the advice given earlier about using one computer to share the internet connection with the other through ICS (easiest fail-safe method possible);

---

### Post by DBQ on 2010-02-27
I think for now I will give up on trying to get the ICS working, as I do not have much time.

However, I still want to be able to share files and printers.

---

### Post by Iowan on 2010-02-28
On which machine(s) are the files/printers that need to be shared? Samba is the standard for sharing between Linux and Windows - the client is already installed (you should be able to access Windows shares *from* your Ubuntu box).

---

### Post by captain_171 on 2010-03-04
Did you get this working?
Where you can be online with both PC's and share files?

---

### Post by ndefontenay on 2010-03-04
What about those usb modems working only with windows. Is there a way to achieve that so an ubuntu machine could also enjoy internet access?

This thread really interest me because my dad lives in a place where only those modems are available so he can't switch to linux :(

---

### Post by captain_171 on 2010-03-04
For a client that need dial up service with ubuntu I use.
[http://reviews.cnet.com/routers/actiontec-dual-pc-modem/4505-3319_7-30539108.html](http://reviews.cnet.com/routers/actiontec-dual-pc-modem/4505-3319_7-30539108.html)

This is a dial up router and this WILL work with any thing that works with tcp/ip.

Or find a serial modem that works with a serial port they are just more harder to install in linux let alone ubuntu

USB thoughts my thoughts on USB is that it should never be used for any communications such as ethernet, internet, wireless, phone, even printers.
its to unreliable (for a end user) I only recommend using usb if its the only choice.

Thoughts?

---

