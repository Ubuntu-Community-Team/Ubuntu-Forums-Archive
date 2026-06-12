---
title: "Aircrack problem"
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by Mariogeo on 2009-06-19
When i type airodump-ng wifi0 it shows the networks i'm in range but when i type
other commands with airdump-ng does not show any networks. I probably need special commands to work with my hardware at this case but i'm not an expert so
i'm asking for help. But my chipset is atheros.
 
I tried to write: airodump-ng wifi0 --ivs --w data --channel 11 and the screen is without networks. No it isn't the channel command is responsible. I tried various numbers. When i just type airodump-ng wifi0 it says the first network is channel 1
and the other is channel 11. I also didn't specify any channel but still the same.

---

### Post by carcar1 on 2009-06-20
I assume your using this for educational purposes?  Is your card in monitor mode?

```
 sudo ifconfig devid down
```

then 

```
sudo iwconfig devid mode monitor 
```

Or

```
airmon-ng start devid (next part is optional) the channel you want it to be set on (1-11)
```

And the -ivs does not capture full packets so don't use it.  For me crackign wep I use this airodump.

```
airodump-ng -w capture ath0
```

that sets your .cap for further use on cracking to "capture"

then I'll go in and set it to the specific channel with

```
airodump-ng -c 11 (normally) -w capture5 ath0
```

Hope that helps! :)

---

