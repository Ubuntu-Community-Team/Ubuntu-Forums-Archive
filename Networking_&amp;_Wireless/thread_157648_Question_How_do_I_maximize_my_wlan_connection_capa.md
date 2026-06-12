---
title: "Question: How do I maximize my wlan connection capability?"
date: 2006-04-09
forum: Networking &amp; Wireless
---

### Post by Bjoern E Braathen Haaland on 2006-04-09
I have seen this elsewhere:

[LEFT]```
$ sudo ethtool -s eth0 speed 10 duplex full autoneg off port mii
```[/LEFT]
  
 followed by
     [LEFT]```
$ sudo dhclient
```
Now obviously this person is attempting to enhance his ethernet connection. His problem was that he's using an ethernet connection, but not at maximum capability.

I'm using a wireless connection. The maximum capability where I live is 10 Mpbs, that's the main connection capability, but I'm only getting around .700-1.0 Mbps. There may be many reasons why, I realize that. My question is:

Is the Wireless connection capability automatically limited, and is there any way to maximize this capability using a command in shell?

Thanks for reading.
[/LEFT]

---

### Post by jml on 2006-04-09
If you are successfully connecting to the wireless connection, you should be able to connect at a significant percentage of the theoretical maximum speed.  The reality is that it is virtually impossible to actually reach the theoretical maximum.  Many things will slow down the connection.  A cordless phone or base station could introduce radio frequency interference.  Even a microwave oven radiates at a frequency that could interfere with your connection.  Also, the actual signal strength between the two points makes a big difference.  It not just the actual distance, but also the nature of the intervening walls and obstructions between the tow points.  

Hope this helps a bit.

Joe

---

### Post by Bjoern E Braathen Haaland on 2006-04-10
That helps, I've learned something. I'm going to switch to ethernet as soon as possible anyway.

---

### Post by spd106 on 2006-04-11
Sometimes switching to a different channel can improve the connection. With 802.11b/g there are three non-overlapping channels: 1, 6 and 11. 

Here in the UK most wifi products default to channel 11. So this gets quite busy in a densely populated area. Switching your AP to another channel should improve things. The client cards will automatically follow the ssid. This isn't a magic wand though as there may be other devices on that channel already. I also found that one of my wifi cards wouldn't work on channel 1. Have a play around and see if you can find any improvements.

I must mention as a last thought that channel usage is restricted some countries.

---

