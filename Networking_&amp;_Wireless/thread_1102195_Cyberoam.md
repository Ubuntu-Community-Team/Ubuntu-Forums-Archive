---
title: "Cyberoam"
date: 2009-03-21
forum: Networking &amp; Wireless
---

### Post by Mr.Tranquil on 2009-03-21
helloo all...FIRST OF ALL MY ISP USES CYBEROAM CLIENT
my PC is connected to a LAN and my ISP uses ISDN cable line for all this things and my modem is Smart Link and i use net in ubuntu through pppoe..recenly it has caused me a lot of of problems..so i planned to use cyberoam and i got everyconfig right except the server address
actually the server address which i checked using cyberoam in windows was right and was only accessible wen internet was on
now i want internet through cyberoam client for which server address is needed so 
ny ways how to do it ????


PLZ ALSO TELL ME IN HOW MANY WAYS I CAN CONNECT TO INTERNET!!!
i repeat i am connected to lan and my modem is smart link...i hope u will help

---

### Post by rams123 on 2009-03-21
First adjust TCP/IP settings in Ubuntu (in NetManager) and [http://kb.cyberoam.com/default.asp?id=372&Lang=1&SID=](http://kb.cyberoam.com/default.asp?id=372&Lang=1&SID=)

Enjoy ;)

---

### Post by Mr.Tranquil on 2009-03-22
i have that cyberoam document plzz help me to adjust TCP/IP as u said before 
where can  find netmanager

---

### Post by rams123 on 2009-03-23
Here's a guide : [http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/]("http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/")

So first login to xp, go to tcp/ip and note down settings, use the same setting (gateway,dns,ip,subnet) in Ubuntu (in Network Manager). 

There's no need to edit mac address.

Then follow [this]("http://kb.cyberoam.com/default.asp?id=372&Lang=1&SID=") guide as I said in previous post.

---

### Post by Mr.Tranquil on 2009-03-24
hey man 
thnks for u worth response...
just not getting the TCP/IP settings in windows
i had said that my PC is connected 2 a LAN so i need TCP/IP of LAN or my dial up connection to get connected 
plzz also tell me where will i find tat in windows
is tat in ipconfig/all?????
plzzz help me

---

### Post by Mr.Tranquil on 2009-03-24
Windows IP Configuration



        Host Name . . . . . . . . . . . . : xx

        Primary Dns Suffix  . . . . . . . : 

        Node Type . . . . . . . . . . . . : Mixed

        IP Routing Enabled. . . . . . . . : No

        WINS Proxy Enabled. . . . . . . . : No



Ethernet adapter Local Area Connection:



        Connection-specific DNS Suffix  . : 

        Description . . . . . . . . . . . : Intel(R) PRO/100 VE Network Connection

        Physical Address. . . . . . . . . : xx-xx-xx-xx-xx-xx

        Dhcp Enabled. . . . . . . . . . . : No

        IP Address. . . . . . . . . . . . : xx.xx.xx.xx

        Subnet Mask . . . . . . . . . . . : xxx.xxx.xxx.xxx

        Default Gateway . . . . . . . . . : 



PPP adapter Connection to bgbpppoe at BGB:



        Connection-specific DNS Suffix  . : 

        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface

        Physical Address. . . . . . . . . : xx-xx-xx-xx-xx-

        Dhcp Enabled. . . . . . . . . . . : No

        IP Address. . . . . . . . . . . . : xxx.xxx.xxx.xxx

        Subnet Mask . . . . . . . . . . . : xxx.xxx.xxx.xxx

        Default Gateway . . . . . . . . . : xxx.xxx.xxx.xxx

        DNS Servers . . . . . . . . . . . : xxx.xxx.xxx.xxx

                                            xxx.xxx.xxx.xxx

        NetBIOS over Tcpip. . . . . . . . : Disabled






what from here????

---

### Post by rams123 on 2009-03-24
Go to "My Network Places", click on "View network connections" , Right click on "Local Area Connetion" and select Properties, Select "Internet Protocol (TCP/IP) and click Properties.

Then notedown all the settings.

[IMG]http://shup.com/Shup/134331/109224164913mydesktop.png[/IMG]

After that log in to Ubuntu, go to network manager and enter the settings that you've noted down before. (If you're confused in this step follow this [guide]("http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/").

Then download Linux Client to desktop, Right click on it and extract, Open "Terminal" from Application menu. 

Enter the following commands in Terminal:

> cd Desktop/crclient [SIZE="1"]*Press Enter and type next command.*[/SIZE]

> ./crclient -u *yourcyberoamusername*

It will ask some questions, answer them. That's it.

Got it?

---

### Post by Mr.Tranquil on 2009-03-24
actually my LAN TCP/IP properties was obtain ip address automatically!!!!!

---

### Post by Mr.Tranquil on 2009-03-24
actually dude
the ISP used to provide a specific ip address to all the ppl conencted to LAN ..its providing now too but lan ppl decided to move to a new range of ip address which took place long before in 2007 or 08.......ppl decided to keep ip address as 10.10.xxx.xxx
and subnet was 255.255.0.0 and rest were unknown so i have no idea how to configure them!!!

---

### Post by rams123 on 2009-03-24
Could you please tell me, what steps do you follow to setup connection in XP? Do you use cyberoam client in XP?  
[I]
Perhaps I may get some idea about that..[/I]

---

### Post by Mr.Tranquil on 2009-03-25
i used dial up connection in XP goto network connection then in tasks click on create a connection 
then connect to internet and set my connections automatically
then use a bradband connection which requires and username and pass
then in the properties ot tat conenction write the phone number which is BGB/bgbpppoe
 !!!!!!

ya and when i tried cyberoam client it was not working in winndows  too 
actually the server address of cyberaom was accesible throughdial up only 
so wen i conenct dial up i could acces tat site

---

### Post by rams123 on 2009-03-25
Sorry Mr.Tranquil. I think I can't help you because I'm using different kind of cyberoam connection :|

You should ask your ISP person to setup connection in Ubuntu.

---

### Post by Mr.Tranquil on 2009-03-25
okey
btw thnks a lot buddy

---

