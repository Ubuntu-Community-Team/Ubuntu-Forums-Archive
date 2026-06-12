---
title: "Wireless Usb adapter problem"
date: 2010-02-20
forum: Networking &amp; Wireless
---

### Post by KapowLiam on 2010-02-20
Hey guys i bought a wireless usb adapter from amazon it came today but before i purchased i asked the owner will it work on linux ubuntu. They said yes i got the package today and a cd with EXE in now i have used wine to open the exe  to install the drivers (not sure if correctly installed)


Anyhow im on the internet with the Ubuntu machine but its very slow browsing for some odd reason :S. Now im about a meter away from my router and i put the wireless adapter in my Vista machine and it works fast.. But the thing is its working fast on ubuntu then it starts 2 become slow.. Example


Google Search Facebook  On vista = Loads within a second
Google Search Facebook  On Ubuntu= Loads Within a second.. But after that it takes ages 2 loads.. Now Heres the settings 


802.11 WiFi (wlan1)
Hardware address 00:60:B3:56:2C:EA
Driver ZD1211RW
Speed 1MB/S

Ip : 192.168.1.3
Broadcast 192.168.1.255
subnet mask 255.255.255.0
default route 192.168.1.1
primary dns 192.168.1.1 

Now its only giving me a  signal of 34%
But when i put it in my vista i think it gives me the same or a bit less... But it works fast on vista and sometimes fast on ubuntu machine i mean if i google many things it searches fast... then say a minute later it searches slow .  so i dont know the problem anyone can help it will be fab

---

### Post by cchhrriiss121212 on 2010-02-20
If you look at the settings you posted it has Speed 1Mb/s which is why it is going slowly. When wireless devices are claimed to be supported in linux you should not need to install a windows driver in wine.

I would ask the person you bought it from for support advice. You may just need to add an extra line in /etc... or something. I have a wireless usb adapter that works automatically in 9.04 but not in 9.10.

---

### Post by KapowLiam on 2010-02-20
Thanks for the reply i found out how to make it 54mbs

But its only for now because everytime you restart it will go back to 1/mb but there is a code and somebody said to put it in interfaces so i edited the file and put the code in but it says i do not have premission or something.

---

### Post by cchhrriiss121212 on 2010-02-20
To edit important files you need to open a terminal and type:
sudo gedit /your file

Then you will be able to save the changes.

---

