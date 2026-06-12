---
title: "Wirelles RTL 8185 drivers"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by bovcan on 2010-05-12
Hi!
I have Wirelles card with RTL8185 chip.
When I install Ubuntu 10.04 system install me driver for RTL8180.
Problem is, I have very low signal strenght (15%) and connection dies sometimes. I have a server running and if I try to access my web site from other PC sometimes get an errror Page not found.
If I go to server and go to any url than it work again.

I tried to DL drivers from RealTek [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L)
but after install id worse. Signal strenght is better , almost full.
But connection dies but truly dies, I must to reconnect than is OK for a wile.

What cause this problem and how to solve this.

Thx

---

### Post by bovcan on 2010-05-12
bump

---

### Post by bovcan on 2010-05-13
bump

---

### Post by bovcan on 2010-05-13
Great, now it is happening the same with default drivers.
WTF is this?

---

### Post by Crio on 2010-05-13
See if it helps: [http://ubuntuforums.org/showthread.php?t=1478782](http://ubuntuforums.org/showthread.php?t=1478782)

---

### Post by bovcan on 2010-05-14
Tried, but then I lost wirelles in Network manager. Mybe I do something wrong.
I am running server. After some time, if I try to access my website from other computer page do not load(connection couldn'd be esta...)
Then I open FF in server PC and try to access exp. google.com than it works.
After that, if I try to access my web site again(from other PC) it is working.

It is looks like wirelles card is shut down or something.

---

### Post by bovcan on 2010-05-14
Probalby it will work now. Before I use Win7 and something went wrong.
Now I try again with ndiswrapper, DL windows XP driver and it looks it work.
Signal strenght is Full or almost full.

---

### Post by bovcan on 2010-05-15
Ok, Wireless id now working normaly without any downtime.
[SOLVED]

---

### Post by madnux on 2010-06-04
I have the same problem. Windows XP SP3 ok but in Kubuntu 10.04 with the last updates mi WiFi lost connection.

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

---

