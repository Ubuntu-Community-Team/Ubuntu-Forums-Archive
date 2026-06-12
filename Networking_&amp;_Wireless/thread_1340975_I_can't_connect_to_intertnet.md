---
title: "I can't connect to intertnet"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by kaleem on 2009-11-29
hello 

I am a new user of Ubuntu 9.10

I previously have a ( adsl connection ) it work correctly with windows XP

my modem is TP-link External modem 

the model no : td-8610


please help me

---

### Post by kaleem on 2009-11-29
help help !!

---

### Post by pdc124 on 2009-11-29
we need a bit more information . What you have posted so far is like saying "my car doesnt go . Help . Help .Help "

what have you tried ?
what is your connection  setup ( router? wireless?  ?network)

spend a few minutes looking at some of the other posts and you can dda bit of information as well 
eg
sudo ifconfig 
sudo iwconfig 
route -n

---

### Post by kaleem on 2009-11-29
thank you very much 

my connection is called 

adsl 

it require a username and password to connect

it is wired of course 

its speed is 128

the modem is called 

tp-link external adsl2+ modem 

model no : td-8610 

[http://www.tp-link.com/products/product_spe.asp?id=40](http://www.tp-link.com/products/product_spe.asp?id=40) 

this is a link of my modem you can see what is the type 

i live in Yemen our internet service provider is Yemennet

I will try your advice and reply 

please help me

---

### Post by pdc124 on 2009-11-29
so you need to read the instructions that came with your router ( or look at the online version) 

you need to log into your router with a browser ( usually [http://192.168.0.1](http://192.168.0.1) or 192.168.1.1 or 192.168.1.2 ) 
and then enter  the password and username that your internet supplier gave you

---

### Post by kaleem on 2009-11-29
I thank you again my friend 

but could you tell me where I should insert these digits in linux 

in windows I was insert similar values in area called internet protocol

could you support with images 


thank you very:o very much

---

### Post by kaleem on 2009-11-29
more help please

---

### Post by linuxonbute on 2009-11-29
> **kaleem said:**
> I thank you again my friend 

but could you tell me where I should insert these digits in linux 

in windows I was insert similar values in area called internet protocol

could you support with images 


thank you very:o very much


If you already have everything connected and it is already working under 

windows then you need to configure the network under linux.

Please let us know if this is the case. Have you been using the same PC 

and modem with windows?

If not then did you have the same modem and a different PC?

---

### Post by kaleem on 2009-11-29
thank you very muck

yes I use the same pc and the same modem

---

### Post by kaleem on 2009-11-30
now I have established a connection between pc and the modem tp-link 

but I still not able to access to the internet 

what is the solution for this bad problem

---

### Post by intspeed on 2009-11-30
After an upgrade from 9.04 to 9.10 I was unable to connect to Internet and I could not get it fixed. I have done a fresh installation of 9.10 over the old upgraded and problem solved. If you are using dual boot than take care about the partitions you choose.

---

### Post by kaleem on 2009-11-30
thank you ,, but may partitions are OK and booting is OK

but please tell me how I can make a connection 

where ? what I must write in terminal 

any information may be benefit

---

### Post by Borg6of9 on 2009-11-30
Well first you need to configure your network connection.  You see that bar upthere ?   Go in system > Preferences.  Click on Network connections.  You will get a tab called Wired and a connection called Auto eth0, that's your wired connection.  
 
Go on your windows machine and get the IP details of your connection.  You need to know your IP, subnet mask, IP gateway and DNS server.   Note them and enter them on your linux box in that "auto eth0" by clicking edit.  
 
first thing you should do to test your connection is to ping your gateway.  after, ping your DNS server and after ping [www.google.com]("http://www.google.com"), they are not blocking ICMP.
 
Have fun !

---

### Post by kaleem on 2009-12-01
thank you very much 

but my connect in windows give no DNS it is set up to automatic .

and my connect require a username and password in windows to access or to make a connection 

in ubuntu where should I write username and password ??

thanks for you again 

I am waiting

---

