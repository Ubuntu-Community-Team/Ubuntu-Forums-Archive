---
title: "Needs Help Regarding Aircrack-ng in Ubuntu ..."
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by sandeep_talan on 2009-06-15
Hi All,

This Sandeep :( , I've encountered a problem in using Aircrack-ng on Ubuntu 9.04ver.
I'm actually using aircrack-ng for my college project on Wi-Fi Encryption...
I've started using aircrack-ng.. around a weak ago, in starting .. it was working very much fine... 
It was displaying the data packates in Airodump-ng and also it was capturing that data, I've also cracked my AP's WEP Key through it...
But now it is showing the AP in upper list of airodump.. but   not showing any client... connected to the AP...
I'm using Alfa USB card which contains rtl8187 chip, I just direct pluged the usb card and it is detected by Ubuntu and drivers are not needed to install..so it directly connects to internet by serching for Ap's.. Now when i do :::

airmon-ng start wlan0

It creates an extra interface in monitore mode.... "mon0"  ...  so I was able to connect to internet on wlan0 and and I was able to capture data through mon0 using airodump-ng.

Airodump-ng was capturing whatever I was browsing through wlan0 which was connected thrrough internet ... and It was also capturing the packates of other PC's connected to my AP. 
But now the problem is ... I'm able to use Internet correctly ..  whenever I starts airodump-ng on "mon0"  It disables my internet, and I'm not able to capture anything.....

I've also tried with two systems and two diff cards .. one for monitoring and one for browsing internet .. 
I've placed wlan0 in monitor mode by this command ... "iwconfig wlan0 mode monitor"  and then started airodump-ng on this interface ..
Then I connected to my AP through another card in another system ... but It is not showing the card in "airodump-ng" .. although it is still showing the AP ... 

Out of range cannot be the reason because both of my systems and cards are placed on the same desk...

Now I'm stuck into this because ... I'm not able to figure what to do ... 
Plz help me through this ...

Thanx.... :(

---

### Post by sandeep_talan on 2009-06-17
Ok .. I found the exact problem .....

When I start airodump-ng on "mon0" without any specified channel ... It disconnects my internet running on "wlan0" on the same machine ... 

But when I start airodump-ng on "mon0" with a specified channel like with argument "--channel 6" ...  everything works fine ...

Means  I browse internet on wlan0 and it is captured on airodump-ng .... as well as on the second machine I'm using .. It's data is also captured ..

So the reason is ... it is not supporting the channel hopping .... because ... when I ran another instance of airodump-ng on other channel ... the same problem occurs ...

Now the problem is I have three diff routers .. and I wants to capture data for all channels ..can you help me in this ..

how can I capture data from all channels... [IMG]http://forum.aircrack-ng.org/Smileys/default/smiley.gif[/IMG]

Also there is one more small problem ..when I specifies the argument "--bssid" ... It always says.. "Invalid Mac address" ...  why is It so .....

---

