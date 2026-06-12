---
title: "Share a wireless connection"
date: 2006-06-20
forum: Networking &amp; Wireless
---

### Post by GuitarHero on 2006-06-20
I have a network card in my windows PC which sits next to my ubuntu computer and I want to use the internet connection from windows for the ubuntu computer with ethernet.  What programs do I need to do this, and how do I install them because it wasnt in the synaptic thing and i have no idea what the hell im doing in ubuntu.

---

### Post by x64Jimbo on 2006-06-20
Not sure I understand your question. Let's see if I got it straight...
Windows machine has a wifi card in it that connects to the internet and you want to share its connection with the Linux machine? You need to set up a network bridge. You have a crossover cable that runs between the two machines' ethernet cards and you set up a "network bridge" on the windows machine that bridges the ethernet and wifi connections. Please reply if that solution doesn't help of if I misunderstood your setup.

---

### Post by GuitarHero on 2006-06-20
Yep that sounds about right.  I have a connection on the windows machine and i want the ubuntu machine to use it also.

---

### Post by GuitarHero on 2006-06-22
So how do I do it?  I bridged the connection on the windows computer but simply enabling ethernet connection on ubuntu doesn't do it..... help

---

### Post by GuitarHero on 2006-06-22
Please help me

---

### Post by fragos on 2006-06-22
System-> Administration-> Networking-> Connections tab-> Activate eth0
-> Hosts tab-> +Add (give it what it wants, an IP and an alias name).

You may need to do something similar on the Windows side.

---

### Post by GuitarHero on 2006-06-22
Ok now I have my wireless and 1934 connection brideged, incoming connections enabled, and an ethernet cable plugged into my windows machine, and eth0 as default, etho0 enabled with DHCP, and a host with the IP of my windows machine and alias as ubuntu on the ubuntu machine.  Its not working so im guessing im missing something.  I added ubuntu to the allowed names on the windows machine also.  This is frustrating.

---

### Post by Dcoyaz on 2006-06-23
This is probably not the best way to do this. The windows internet sharing is sort of a proxy and is quite a pain to setup, unless you are using all windows computers. How is your windows computer connected to the internet? If it's usb, that'll present even more problems. The best way to do this is to pick up a cable/dsl router, assuming you are using one of the 2 and let it be the gateway for both computers. In any event if you did this back to back method it would be much easier to make your ubuntu box the one connected and have windows route throught it.

---

### Post by Slim Odds on 2006-06-23
[quote=Dcoyaz]This is probably not the best way to do this. The windows internet sharing is sort of a proxy and is quite a pain to setup, unless you are using all windows computers. How is your windows computer connected to the internet? If it's usb, that'll present even more problems. The best way to do this is to pick up a cable/dsl router, assuming you are using one of the 2 and let it be the gateway for both computers. In any event if you did this back to back method it would be much easier to make your ubuntu box the one connected and have windows route throught it.[/quote] 
Wrong and wrong.

I have lots of Ubuntu and Windows machines and I have to just say that you are wrong on many things. The disinformation in your comments needs to be addressed. 

1) Using Windows ICS (Internet Connection Sharing) is not hard, it is easy (at least for Windows 2000 or XP).
 
2) Whether the upstream Internet connection is USB or not is completely irrelevant.
 
If you have a working Internet connection with Windows and you have a second network port, you just enable ICS for the Internet connected interface. The other network will automatically be setup with a DHCP server and proper routing. It's just that easy.
 
 I'm no fan of Microsoft, but ICS on Windows XP (or 2000) is easy and works just fine. If you really want to turn the table, using Ubuntu to share the connection is also not too hard once you have the upstream Internet connection working.

---

### Post by GuitarHero on 2006-06-23
So I dont need to bridge any connections?

---

### Post by Slim Odds on 2006-06-23
[quote=GuitarHero]So I dont need to bridge any connections?[/quote]

When you enable ICS on Windows, it will automatically enable IP forwarding. It also provides NAT.

---

### Post by GuitarHero on 2006-06-23
My networking panel wont open now.... i click on it and it says opening but then it just stops....

also should i set ubuntu to DHCP or what?

---

### Post by Slim Odds on 2006-06-23
[quote=GuitarHero]My networking panel wont open now.... i click on it and it says opening but then it just stops....

also should i set ubuntu to DHCP or what?[/quote] 
It's easiest to use DHCP to get you address. But you can do it static if you want, but then you have to setup the gateway and DNS address too.

---

### Post by GuitarHero on 2006-06-24
my network panel still wont open

---

### Post by GuitarHero on 2006-06-24
bump

---

### Post by GuitarHero on 2006-06-26
ok now i have my network panel open( i reinstalled).  Ive tried dhcp but it wont work.  Ive enabled sharing.  Here is a pic of the output cmd in windows gives me with ipconfig /all:
[http://img144.imageshack.us/img144/9852/info2dg.png](http://img144.imageshack.us/img144/9852/info2dg.png)

Tell me what to fill in where for static ip, because ive tried seemingly everything i can think of and it wont work.

---

### Post by GuitarHero on 2006-06-26
WHY DOESNT NETWOKING WORK WITH UBUNTU

sorry.... just fed up

---

### Post by Dcoyaz on 2006-06-26
Ok, i thought maybe i wouldn't post again. God Syndrom folks just rub me the wrong way... But if it was "just that easy" ;)

GH, the screenshot only shows one interface. The command ipconfig /all should show all intefaces assuming they are active/enabled and have a link. For starters make sure the ethernet interface on your windows box is enabled. Use a crossover cable between the windows box and the ubunto box. Both systems link lights should be on. Also make sure the wireless interface is using windows wireless management and not the one provided by linksys if at all possible. If you have ICS configured on the wireless interface than windows should configure the ethernet interface properly. The problem here being that windows configures the  network(ethernet) side of the interface with a 192.168.0.x ip address and DHCP pool. It looks like you wireless card is getting the same ip range and this will cause problems. You may need to tweak that a bit. Your ubunto box should be configured for DHCP you can check this by going into a shell and do the following:

cat /etc/network/interfaces

You should see something along the lines of:

auto eth0
iface eth0 inet dhcp

This means it's setup for dhcp, if not make it so.

also in the shell do an ifconfig to see what is going on with eth0. If it's setup for dhcp and your link lights are good on both computers connected with the crossover cable then it should have an ip address of 192.168.0.x. As i said above the routing here is going to be a problem. Both sides wireless and ethernet can't be matching or it won't route properly. If the ip range does not match your wireless side you should be able to ping what ever gateway the command "route" (also in the shell) shows. If it does match the wireless side then you know you are at least getting configured with dhcp and just need to tweak on the network configuration on the wireless side as XP won't let you modify the ethernet side.

Hope this will get you going.

---

### Post by GuitarHero on 2006-06-26
ah connected at last!  turns out it was a driver issue with the windows box, and here i was blaming ubuntu.  Well thanks, i feel stupid.

---

