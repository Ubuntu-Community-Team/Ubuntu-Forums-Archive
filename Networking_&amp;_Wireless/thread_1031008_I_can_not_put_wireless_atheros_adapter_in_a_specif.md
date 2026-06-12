---
title: "I can not put wireless atheros adapter in a specific channel"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by DeepSeaNautilus on 2009-01-04
Hello I am learning to use aircrack.
I have put my card in monitor mode and used airodump-ng to capture ivs packets to a file. Now I want to use aireplay to inject packets and capture the ivs more rapidly.
The problem I have is that when I try to associate my wifi card with the ap to inject packets( but aireplay ), it shows the following error:
The ap is in channel x but ath0 is in channel y ( x and y are just invented channels )
I tried to set up ath0 channel with the following command
Code:
```

ifconfig ath0 down
iwconfig ath0 channel x
ifconfig ath0 up
```

But it didn't work. Apparently, when I type iwconfig ath0 channel x, it does not change to channel x but to a random channel. I also tried with the following commands:
Code:

```
wlanconfig destroy ath0
airmon-ng start wifi0 x
```

But it did not work, it keeps on choosing a random channel between 1 and 12.

Any help would be greatly appreciated.

---

### Post by dmizer on 2009-01-05
According to man iwconfig:
>               When using Managed mode, most often the  Access  Point  dictates
              the  channel  and  the driver may refuse the setting of the fre-
              quency.

This means your driver may not be able to do what you're tring to do. What wireless card are you using?

---

### Post by DeepSeaNautilus on 2009-01-13
> **dmizer said:**
> According to man iwconfig:


This means your driver may not be able to do what you're tring to do. What wireless card are you using?

I was not using managed mode but monitor mode. I found what my problem was: before I typed iwconfig ath0 channel c command y had opened a terminal and used airodump-ng ath0 command. Therefore the channel of ath0 changed randomly to detect networks in all the channels, and when I used aireplay to associate with a specific AP, it would not let me because the other command was dictating the channel. I solved this using first airodump-ng ath0 to detect all networks, then I chose one and then used airodump-ng again but set to a specific channel, this way aireplay-ng worked just fine.

---

### Post by dmizer on 2009-01-14
> **DeepSeaNautilus said:**
> I was not using managed mode but monitor mode. I found what my problem was: before I typed iwconfig ath0 channel c command y had opened a terminal and used airodump-ng ath0 command. Therefore the channel of ath0 changed randomly to detect networks in all the channels, and when I used aireplay to associate with a specific AP, it would not let me because the other command was dictating the channel. I solved this using first airodump-ng ath0 to detect all networks, then I chose one and then used airodump-ng again but set to a specific channel, this way aireplay-ng worked just fine.

Glad you got it figured out. Sorry I wasn't much help though ...

---

