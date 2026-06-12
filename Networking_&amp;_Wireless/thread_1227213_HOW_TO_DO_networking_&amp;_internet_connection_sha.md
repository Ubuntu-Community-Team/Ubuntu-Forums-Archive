---
title: "HOW TO DO networking &amp; internet connection sharing ICS in XUBUNTU-WINDOWS Network"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by Neill_R on 2009-07-30
[SIZE=2][FONT=Courier New]

closed








Hello [/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New]I am requesting **_HOW TO DO_** information in regards to networking and internet connection sharing ICS in a mixed XUBUNTU - Windows computer network.[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New]Rightly or wrongly I, for the moment at least, believe that a XUBUNTU gateway will afford more security than a Windows based gateway.[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New]Although I have worked in the past on UNIX boxes, I am new to Linux and I am not a networking guru. So please if you can help, do explain in simple clear steps how I should or could set up my system to provide the access and functionality I need.[/FONT][/SIZE]
 
**_[SIZE=2][FONT=Courier New]My Hardware [/FONT][/SIZE]_**
 
[FONT=Courier New][FONT=Courier New][SIZE=2]1.[/SIZE][/FONT] [/FONT][SIZE=2][FONT=Courier New]A HP Pavilion n5271 Pentium III 700 MHz, 256Mb RAM with DLINK 660 PCMCIA network card connected to Hub (see below), which is running XUBUNTU 9.04 alternative-CD version. Connection to the Internet is via an Option-ICON 225 USB mobile broadband modem connecting to Orange UK. [/FONT][/SIZE]
 
[FONT=Courier New][FONT=Courier New][SIZE=2]2.[/SIZE][/FONT] [/FONT][SIZE=2][FONT=Courier New]A NETGEAR DS104 4 port dual speed hub [/FONT][/SIZE]
 
[FONT=Courier New][FONT=Courier New][SIZE=2]3.[/SIZE][/FONT] [/FONT][SIZE=2][FONT=Courier New]Three Windows based PC (Connected to the hub)[/FONT][/SIZE]
[FONT=Symbol][SIZE=2]·[/SIZE] [/FONT][SIZE=2][FONT=Courier New]Windows 2000 Advanced server [/FONT][/SIZE]
[FONT=Symbol][SIZE=2]·[/SIZE] [/FONT][SIZE=2][FONT=Courier New]Windows XP PRO SP3 (currently client PC but required to be middle tier server (IIS and or Apache Oracle application server)[/FONT][/SIZE]
[FONT=Symbol][SIZE=2]·[/SIZE] [/FONT][SIZE=2][FONT=Courier New]Windows XP Pro SP2 running Oracle 11g[/FONT][/SIZE]
 
[FONT=Courier New][FONT=Courier New][SIZE=2]4.[/SIZE][/FONT] [/FONT][SIZE=2][FONT=Courier New]I also have but not currently deployed [/FONT][/SIZE]
[FONT=Symbol][SIZE=2]·[/SIZE] [/FONT][SIZE=2][FONT=Courier New]A LINKSYS WRK54G wireless router[/FONT][/SIZE]
[FONT=Symbol][SIZE=2]·[/SIZE] [/FONT][SIZE=2][FONT=Courier New]A LINKSYS WCPC54G ver4 Notebook adapter [/FONT][/SIZE]
[FONT=Symbol][SIZE=2]·[/SIZE] [/FONT][SIZE=2][FONT=Courier New]A WUSB54GS USB Network adapter[/FONT][/SIZE]
[FONT=Symbol][SIZE=2]·[/SIZE] [/FONT][SIZE=2][FONT=Courier New]A windows 2000 Pro Client PC with Network PCI card (But no place to connect to)[/FONT][/SIZE]
 
**_[SIZE=2][FONT=Courier New]My Purpose[/FONT][/SIZE]_**
 
[SIZE=2][FONT=Courier New]The purpose of this network is to educate myself on various computer systems and technologies and to replicate in some way a computing environment that has been in place at places where I have worked in the past and hopefully will again in the future. In the meantime, my work-styled, home-based network will provide the opportunity to refresh, update and extend my computing skills. [/FONT][/SIZE]
 
 
**_[SIZE=2][FONT=Courier New]My Requirements[/FONT][/SIZE]_**
 
[SIZE=2][FONT=Courier New]In order to demonstrate my competency with new technologies it is important to be able to show off those technologies functioning to remote sites. Therefore, not only will I need to have ICS access to the WWW from all the Windows PCs but I will need the networking system to forward requests from the internet to internally provided services and to send back responses to those remote requestors (Port Forwarding?)[/FONT][/SIZE]
 
 
**_[SIZE=2][FONT=Courier New]WWW [/FONT][/SIZE]_**
[COLOR=black][SIZE=2][FONT=Courier New]On the WWW there is a page where I will manually assign my current external IP-ADDRESS into hyperlinks that will then point to my services. This is perfectly adequate for my purposes. I realise that I will have to have a regime of port numbering so that services say like http (80) can be run on two different internal servers (IIS or apache)[/FONT][/SIZE][/COLOR]
 
**_[COLOR=black][SIZE=2][FONT=Courier New]LINUX [/FONT][/SIZE][/COLOR]_**
[COLOR=black][SIZE=2][FONT=Courier New]While there are a few things I dislike about UNIX (for example case sensitivity) &#8220;I am Spartacus!&#8221; &#8220;No I am sPartacus&#8221; &#8230; [/FONT][/SIZE][/COLOR]
[COLOR=black][SIZE=2][FONT=Courier New]I a very pleased with XUBUNTU 9.04 and look forward to get to understand it in more detail.[/FONT][/SIZE][/COLOR]

---

### Post by superprash2003 on 2009-07-30
you could check out firestarter , it would solve your ICS as well as port forward issue

---

### Post by Neill_R on 2009-07-30
Yes I have tried firestarter but am unclear how to set up the ethernat connection.Does one need dhcp-server to configure the network(internal) cards address? If yes what is the DHCP server in my win2K server doing? at the moment i can connect to the internet but can't start firestarter if ICS is selected.

---

### Post by superprash2003 on 2009-07-31
dhcp is not compulsory , static ip would work.. what error do you get when you try to start firestarter?

---

