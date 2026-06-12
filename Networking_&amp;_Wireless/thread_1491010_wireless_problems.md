---
title: "wireless problems"
date: 2010-05-23
forum: Networking &amp; Wireless
---

### Post by lanching123 on 2010-05-23
hello everyone, im totally new to linux and to this forum.  someone had just given my a pc with no OS so i installed ubuntu 10.04.  the pc has a wireless card but i can not seem to get the OS to recognize it.  my wired connect is fine but wireless is non existent.  i do not know a lot about linux or this computer i just got so any help you might have is greatly appreciated.

---

### Post by Megaptera on 2010-05-23
Hi,
Not sure if I can help, but those that can would want to know make/model of PC, system specs and wireless card details - could you include them please?

---

### Post by lanching123 on 2010-05-23
ok i will tell you the little i know.  the pc was put together by someone so i dont have a brand (such as dell, hp, etc).  It has a pentuim 4 2.4ghz processor, half gig of ram, 40 gig IDE hard drive, and thats about all i know.  The wireless card is a netgear 54 mbps wireless PCI adapter WG311v3.  Thats all i can figure out about this computer and wireless card.  Any help or suggestions for getting this running are greatly appreciated.  Thank You

---

### Post by lanching123 on 2010-05-23
ok i was able to hook it up to my wired connect and that seems to work.  I cheched to see if there was a driver to download for the wireless card but there wasnt.  what should my next step be?

---

### Post by theteapatriot on 2010-05-23
try system/admin/driver. if it is listed enable it. no? then google ( card# chipset.) then google ( chipset# Linux ). No results then no support. If you find it, try to find apt-get chipset# or wiget-get chipset#. ( terminal commands to download and install ). If no results, then download package start looking for install info, Deb or Ubuntu pac preferd. You will need to use terminal to do most installs. Rpms will sometimes install by double clicking. Most times you will need to open terminal ( cd ) (change directory to where you stored package) do( make ) and ( make install ). Hope that helps some. You can also try system/admin/package manager. Hit refresh to update list click on drivers or hardware not sure which there is a win wireless driver pac. Also chipset# will be needed for help from someone smarter than I.

---

### Post by lanching123 on 2010-05-23
ok i read through your suggestions and some parts i understand.  for example, the chipset is Marvell 88w8335.  unfortunately other than that im still a little confused.  what should i do know that i know the chipset number

---

### Post by lanching123 on 2010-05-24
ok after some searching around on here and elsewhere online i am at a total loss.  i tried all sort of things i have come across with no success.  I guess i need some very specific step by step instructions.  any help is appreciated!

---

### Post by lanching123 on 2010-05-26
through much trial and error and searching around online i finally came across this link
[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)
i followed it and i finally got my wireless card to work.  so anyone with this same issue using this same wireless card the link above is your answer.  figured i would share so hopefully it will be easy for others to find since it took me days to find it and before i did it was at a total loss.

---

