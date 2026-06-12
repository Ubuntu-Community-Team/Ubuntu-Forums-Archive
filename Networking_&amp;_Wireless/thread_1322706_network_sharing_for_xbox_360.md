---
title: "network sharing for xbox 360"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by doesburg on 2009-11-11
Sunday i switched from Vista to Ubuntu, it feels great it works fine blabla.

But, there is only one thing missing: my connection to Xbox Live.
With Vista on it i could you my notebook to connect my xbox to xbox live.
In Ubuntu it still doesn't work.
I have used this toturial: [http://www.dhnet.ufl.edu/getconnected/tutorials/wired/ics/xbox_linuxnat/text.php](http://www.dhnet.ufl.edu/getconnected/tutorials/wired/ics/xbox_linuxnat/text.php)

And evry thing went fine but when i do ifconfig in terminal it gives this on the connection to the xbox:
eth0      Link encap:Ethernet  HWaddr 00:14:0b:45:f1:08  
          inet6 addr: fe80::214:bff:fe45:f108/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7920 (7.9 KB)  TX bytes:7553 (7.5 KB)
          Interrupt:17 Base address:0x6000 

In the toturial i replaced eth0 with wlan0 en eth1 with eth0, because i taught that that was my situation.

Fine; i followed the toturial but my xbox can't connect. I think i found the reason why:
the network manager in the gnome taskbar says that wireless is connected but that wired is disconnected.

My situation just to make clear -> Wlan -> Laptop running Ubuntu 9.10 -> switch/hub with nothing else than the laptop and xbox connected -> Xbox 360(which i want to connect with the internet.) 

Can anyone help me out?

---

### Post by Iowan on 2009-11-11
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a help page for connection sharing.

---

