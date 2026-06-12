---
title: "ZTE ZXDSL on Jaunty/9.04"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by ThePhoenixPrince on 2009-04-28
Hello all,

This is an  old and troubling topic.

Making ZTE ZXDSL 852 work on Ubuntu. How do I do that?

I did my homework and here are my results.

1)UbuDSL
I installed this software. Installation went fine. After installation, I ran the settings demon. The first two steps go well. On 3rd step, I'm being asked to plugin my modem. Once I plugin, it recognizes my model. Then, it goes on to compilation the driver and there I get trouble, it says compilation failed. And, it goes on but it's of no use because it doesn't even power on the modem.

2)Unicorn Drivers.
I found my modem uses unicorn chips. I extracted the unicorn driverarchive from the UbuDSL package and compiled it. Compilation went on with a few errors. I got a ko file and I hit loaded the module using insmod. After that my modem powers on.(Lights lit). lsusb returns my modem's chipset info on bus 2 device 2.

3)Now, I launched pppconfig and then I created the connection  to number P8,35,3 (which is my dialup number in Windows) with username and password. When I launch this connection, I get an iocntrl error.

4)There was another guide on Ubuntu forums but it was intended for the same modem with a different chipset.


Now, I want to get internet on Ubuntu. Can anybody help me out?  I'm a Linux newbie. Although I'd prefer explanation, I don't need them. Just tell me what to enter on terminal or what to download and run. I'd be glad if anyone could checkout why UbuDSL cannot compile the drivers. I'm more used to GUI and most Linux newbies are. Therefore, UbuDSL will be of great use to many.

This is a wubi dual boot system with Windows XP SP3. Hit back if you need further information. I need internet on Ubuntu very badly. I'm planning to swicth to Ubuntu full time. I'm still using a dual boot because of internet problems.

Please help ASAP.

Thanks in Advance.

---

### Post by gkyasitha on 2009-05-25
a newer version is released and it'e working!
thanks ubudsl!

---

### Post by ThePhoenixPrince on 2009-05-27
> **gkyasitha said:**
> a newer version is released and it'e working!
thanks ubudsl!

negative.
the ubudsl loads and the compilation also succeeds but the configuration fails when in the driver installation stage. tried separately compiling and modprobing the driver. compilation succeeds but modprobe won't recognize the module.

---

### Post by gkyasitha on 2009-05-28
> **ThePhoenixPrince said:**
> negative.
the ubudsl loads and the compilation also succeeds but the configuration fails when in the driver installation stage. tried separately compiling and modprobing the driver. compilation succeeds but modprobe won't recognize the module.

yes yes I have the same problem! :(
I think ubudsl team manage to solve it and they post a newer version in there web site.
It doesn't say a single word that this is a newer version or something but I think it is a new one. Compiling error is fixed:D

But before that I had used this method by chaturaaz.

[http://groups.google.com/group/techkatha/browse_thread/thread/933a93b1c9e60218?hl=en](http://groups.google.com/group/techkatha/browse_thread/thread/933a93b1c9e60218?hl=en)

I don't know whether something have do with above method!
It work perfectly for me.

And instead of ubudsl there is also another application called Easy_connect.I have the software but I don't know how to use it.(even how to install it!):(

[http://bee.ineodev.org/forum/viewtopic.php?t=111](http://bee.ineodev.org/forum/viewtopic.php?t=111)

I think you have more brain than mine so give it a try!;)
Use Google translator to translate from French to English.
If you find that it works please let me know with step by step procedure.:p

sorry for my English hope this will help you:)

---

### Post by gkyasitha on 2009-05-28
P8,35,3 :D
are you from sri Lanka?

---

### Post by ThePhoenixPrince on 2009-05-28
ahh yes am from sri lanka...eh, btw, these are English forums and other languages should be avoided. Who else would be using zxdsl852 modems?

eh btw, SLT may not be the only ISP using that vcli. (that 35 thing)

 Only SLT and another weird ISP in Polland and another in Algeria uses ZXDSL852 modems. Conversely, the Polland ISP uses the Conexant chip set but SLT's modem uses Unicorn chip set. The unicorn chipset has no main stream driver with good quality as I said before as I found out from some Debian and mandriva sites. 

well, i have no idea how could chandra's method work... :S confusing.
what does modprobe has to do with splash screen?

you can look at easyConnect guide now [http://translate.google.lk/translate?hl=en&ie=UTF-8&oe=utf-8&u=http://bee.ineodev.org/forum/viewtopic.php%3Ft%3D111&client=firefox-a]("http://translate.google.lk/translate?hl=en&ie=UTF-8&oe=utf-8&u=http://bee.ineodev.org/forum/viewtopic.php%3Ft%3D111&client=firefox-a")

I'm going out now. I will try EasyConnect and get back with more info tomorrow or later tonight. The EasyConnect download link in that forum at the beginning isn't working. 

goto [http://forum.ouedkniss.com/upload/index.php?PHPSESSID=146eaaf7bfaeb40c8b51715cc3d0b40e&direction=0&order=&directory=Logiciels](http://forum.ouedkniss.com/upload/index.php?PHPSESSID=146eaaf7bfaeb40c8b51715cc3d0b40e&direction=0&order=&directory=Logiciels)

and download the Project_EasyConnect.zip 

Hmm, if all fails, am gonna screw up my modem and ask for a router. :D

---

### Post by gkyasitha on 2009-05-28
[quote=/]
Hmm, if all fails, am gonna screw up my modem and ask for a router. :D[/quote]

yes you better should because this modem is cursed!:(including the people who used it.I had suffered a lot because of this modem.

Every time ubuntu log-on its says "connection terminated" Do you know how to fixed it.It is the only headache I have with this modem.

---

### Post by ThePhoenixPrince on 2009-05-28
> **gkyasitha said:**
> yes you better should because this modem is cursed!:(including the people who used it.I had suffered a lot because of this modem.

Every time ubuntu log-on its says "connection terminated" Do you know how to fixed it.It is the only headache I have with this modem.


eh well connection terminated said by ubudsl demon? ehm i guess u hav nothing to do bat it excpt delaying the startup of ubudsl daemon... eaither way, when it starts up, it would show that message i'm guessing...

so, for u it wrked only aftr chatura's method? i will look a lil detailed into it... btw hmm am sittin for local ALz thz August..... pretty busy with studies...

---

### Post by gkyasitha on 2009-05-28
How to delay the ubudsl daemon startup?

---

### Post by ThePhoenixPrince on 2009-05-28
> **gkyasitha said:**
> How to delay the ubudsl daemon startup?


actually there are many ways but hmm i guess the ubudsl setup has an option in which you are allowed to enter a delay

---

### Post by gg_cOR on 2009-06-01
Hello,

I am the developper of the EasyConnect program ^^
i just want to precise that the program is adapted for "Easy Algeria Telecom", so the VPI.VCI is configured to 0.35

if you can get me the VPI.VCI and the authentification file (pap/chap-secrests ...) of your provider i can adapt the program.


regards,
++++

---

