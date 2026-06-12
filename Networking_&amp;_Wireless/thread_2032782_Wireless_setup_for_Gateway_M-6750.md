---
title: "Wireless setup for Gateway M-6750"
date: 2012-07-24
forum: Networking &amp; Wireless
---

### Post by nickelbox on 2012-07-24
I understand that Gateway does not have any native drivers to install for my wireless card on my M-6750. I am looking for step by step instructions on how to get my wireless card to work (since I am fairly new to Ubuntu). 

From Terminal:
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88W8362e [TopDog] 802.11a/b/g/n Wireless [11ab:2a08] (rev 03)
    Subsystem: Marvell Technology Group Ltd. 88W8362e [TopDog] 802.11a/b/g/n Wireless [11ab:2a08]
06:00.0  Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev  01)
    Subsystem: Gateway 2000 Device [107b:0380]
    Kernel driver in use: r8169

Can anyone assist?
Thanks in advance!

---

### Post by bakegoodz on 2012-07-31
[https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k](https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k)

---

### Post by nickelbox on 2012-08-03
So I followed the commands and it now says "command not found"

Here's my progress

blacklist mrv8k
kerry@kerry-M-6750:~$ mkdir mrv
kerry@kerry-M-6750:~$ cd mrv
kerry@kerry-M-6750:~/mrv$ wget -c [http://www.cafuego.net/stuff/mrv.zip](http://www.cafuego.net/stuff/mrv.zip)
--2012-08-03 18:47:32--  [http://www.cafuego.net/stuff/mrv.zip](http://www.cafuego.net/stuff/mrv.zip)
Resolving [www.cafuego.net](www.cafuego.net) ([www.cafuego.net](www.cafuego.net))... 106.187.43.105, 2400:8900::f03c:91ff:fedf:8b07
Connecting to [www.cafuego.net](www.cafuego.net) ([www.cafuego.net)|106.187.43.105|:80](www.cafuego.net)|106.187.43.105|:80)... connected.
HTTP request sent, awaiting response... 301 [http://archive.cafuego.net/stuff/mrv.zip](http://archive.cafuego.net/stuff/mrv.zip)
Location: [http://archive.cafuego.net/stuff/mrv.zip](http://archive.cafuego.net/stuff/mrv.zip) [following]
--2012-08-03 18:47:54--  [http://archive.cafuego.net/stuff/mrv.zip](http://archive.cafuego.net/stuff/mrv.zip)
Resolving archive.cafuego.net (archive.cafuego.net)... 117.20.11.221
Connecting to archive.cafuego.net (archive.cafuego.net)|117.20.11.221|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 227937 (223K) [application/zip]
Saving to: `mrv.zip'

100%[=========================>] 227,937      131K/s   in 1.7s    

2012-08-03 18:47:57 (131 KB/s) - `mrv.zip' saved [227937/227937]

kerry@kerry-M-6750:~/mrv$ unzip mrv.zip
Archive:  mrv.zip
  inflating: mrv8335.inf             
  inflating: MRV8335NT.sys           
  inflating: MRV8335XP.sys           
kerry@kerry-M-6750:~/mrv$ sudo ndiswrapper -i mrv8335.inf
sudo: ndiswrapper: command not found

---

### Post by bakegoodz on 2012-08-04
```
sudo apt-get install ndiswrapper-utils-1.9
```

---

### Post by nickelbox on 2012-08-04
Once I do that, do I complete the rest of the commands?

sudo ndiswrapper -i mrv8335.inf 
sudo ndiswrapper -m 
cd .. 
rm -rf ./mrv

---

### Post by bakegoodz on 2012-08-04
Yes, after you install ndiswrapper you can run it.

---

### Post by nickelbox on 2012-08-04
Interesting how the instructions didn't mention anything about installing ndiswrapper.

---

### Post by nickelbox on 2012-08-06
Ok, installed nidswrapper but then I get this

couldn't open mrv8335.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219

---

### Post by nickelbox on 2012-08-07
Any ideas on this?

---

### Post by nickelbox on 2012-08-09
I am hoping someone can help me with this problem  :(

---

### Post by nickelbox on 2012-08-13
Anyone who can help with this issue?

---

### Post by SupermanNC21 on 2012-08-15
I have same problem i have Gateway M675PRR i think ur wireless card is newer than mine can't read N network but i have yet to be able to install ndiswrapper an ethernet's doesn't work either.

---

