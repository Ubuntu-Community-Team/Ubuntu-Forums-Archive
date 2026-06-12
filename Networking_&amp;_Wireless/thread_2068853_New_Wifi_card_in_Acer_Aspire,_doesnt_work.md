---
title: "New Wifi card in Acer Aspire, doesnt work"
date: 2012-10-10
forum: Networking &amp; Wireless
---

### Post by mark5656 on 2012-10-10
I had to buy a different motherboard for my acer aspire 3680, and it had a different wifi card in it. it has a [SIZE=1][SIZE=2]T60H938.03, instead of the previous, [/SIZE][/SIZE][SIZE=2]54.A50V7.002. They are two [SIZE=2]different[/SIZE] models completely [SIZE=2].[/SIZE] i was thinking that might be the issue it cant find any [SIZE=2]wireless[/SIZE] networks. any advice?
[/SIZE]

---

### Post by mark5656 on 2012-10-10
I want to add on; I was half asleep when i wrote that post. To be more clear, my wifi doesn't find any connections. 
Here is the additional driver info: 
[IMG]http://oi47.tinypic.com/2n1uob8.jpg[/IMG]

However, when i check the network info:
[IMG]http://oi46.tinypic.com/2qt8xzc.jpg[/IMG]

So.... it doesn't have the enable wireless option.

I then deactivate the additional driver and:
[IMG]http://oi48.tinypic.com/2a5ndzq.jpg[/IMG]

It has that option. But, no network connections appear.... 

I dont know if this helps but here are my results for iconfig with the additional driver still deactivated: 
```
~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

and lspci -vvnn | grep 14e4
```
~$ lspci -vvnn | grep 14e4
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

```

---

