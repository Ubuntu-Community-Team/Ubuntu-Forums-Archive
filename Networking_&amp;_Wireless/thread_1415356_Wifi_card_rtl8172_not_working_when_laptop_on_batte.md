---
title: "Wifi card rtl8172 not working when laptop on battery"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by marstrand68 on 2010-02-24
Hi there!
I have a small problem with my wireless connection.
I am using a Fujitsu Amilo pi3560 with a Realtek rtl8172 wireless card, and running the latest driver (rtl8192se_linux_2.6.0014.0115.2010). The OS is Ubuntu 9.10.
Everything runs perfectly - when my laptop is connected with the power cord. But when I go battery the wireless disconnects after a few minutes. It then asks for the wpa password, searches for the router, asks again, and so on indefinitely, until I reboot and it all replays once more.
I am guessing this is a driver problem, and I have googled it from every possible angle, but so far no luck.
Can anyone help? It kinda takes the fun out of a laptop when it is not all that mobile...
If ndiswrapper can be avoided, it would be much preferred.
By the way, I am a total newbie.
marstrand68

---

### Post by moaoci on 2010-03-05
A new version of the driver is fixing the battery problem.  I know it works on 64bit  9.10 Ubuntu but I don't know if it is a 64bit driver or if it is a 32bit driver fully compatible with 64bit system.

The driver file is rtl8192se_linux_2.6.0015.0127.2010.tar.gz and is 1905119 bytes long.  Another version of the same file is 1860920 bytes long but it is not working on battery.  Last night I checked the realtek download site but it is an old rtl8192se driver.  You should get it from realtek by emailing to realtek support at [EMAIL="wlanfae@realtek.com"]wlanfae@realtek.com[/EMAIL] or to [EMAIL="roger_liang@realtek.com"]roger_liang@realtek.com[/EMAIL].  I prefer you get it from realtek but I will sent it when you request it by private message.


**Driver file now available from Realtek download site **
[http://www.realtek.com.tw/downloads/...Downloads=true]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true")


The driver works with a simple make + make install + reboot ,  BUT remember, it has to be recompiled each time the linux kernel changes number.

---

### Post by c.pfarher on 2010-03-11
I posted a solution here:
[http://kikipblog.blogspot.com/2010/03/realtek-8172-de-toshiba-a505-s69803-en.html]("http://kikipblog.blogspot.com/2010/03/realtek-8172-de-toshiba-a505-s69803-en.html")
good luck!

---

