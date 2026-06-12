---
title: "Ubutnu 10.04 on Compaq Mini CQ10-405DX"
date: 2010-11-26
forum: Networking &amp; Wireless
---

### Post by Yezman on 2010-11-26
[http://www.bestbuy.com/site/Compaq+-+Compaq+Mini+Netbook+/+Intel%26%23174%3B+Atom%26%23153%3B+Processor+/+10.1%22+Display+/+1GB+Memory+/+160GB+Hard+Drive+-+Black/1347086.p?childSku=null&skuId=1347086&count=null&id=1218267360010](http://www.bestbuy.com/site/Compaq+-+Compaq+Mini+Netbook+/+Intel%26%23174%3B+Atom%26%23153%3B+Processor+/+10.1%22+Display+/+1GB+Memory+/+160GB+Hard+Drive+-+Black/1347086.p?childSku=null&skuId=1347086&count=null&id=1218267360010)

(FYI- I am a high school senior and Ubuntu nub, most of what i know is stuff i've looked up and read about then fixed/tried to fix)

So I finally got Ubuntu 10.04, after 10.10 not installing (HP told me their motherboard doesn't support it). I tried Mint but that didn't work, so i went to 10.04. I got it all install and everything, but my wireless card isn't working. It at first was telling me 

eth0 could not load (when i did dmesg | grep eth)

And i looked at some other things but don't remember :(, i didn't change anything.

I restarted and now regardless of wither or not my wifi key is on/off, when i click on the wifi button in the top right, it says disconnected, under the wireless networks. I've tried creating a new network with the same pass, security and name as the one in my house (my iTouch has the wifi and its right next to my netbook), and i tried connecting to a hidden network, using the same info. Nothing for either. 

I just typed "dmesg | grep eth0" and i got 2 lines, one saying "r8169: eth0: link down" and the other saying "link is not ready". Regardless if the wireless led is on/off.

What should i do from here? Anyone have any suggestions, or need more info to start helping?

Thanks.

---

### Post by grahammechanical on 2010-11-26
Have you looked through the wireless trouble shooting guide?

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

When you left clicked the WiFi icon did you see a list of available wireless networks? Did you right click to see if networking is enabled and also wireless is enabled? If there is a list of wireless networks then it proves that your wireless card/device is recognized and functioning. So, why can you not connect? Is your network (the router/modem) in that list?

What was the problem installing 10.10? Computer manufacturers test out their products to make sure that they work with Microsoft operating systems. They do not test out any form of Linux. This is the sense in which a motherboard is said to not support Linux. The motherboard is just a machine. Any operating system programmed to communicate in the computer language that the electronics on the board understand can be installed provided it can communicate with all the electronic components being used.

Have you tried connecting with an ethernet cable?

Regards.

---

### Post by Yezman on 2010-11-26
I will look at the guide.
 
 
When i left clicked, i didn't see any available networks, just said disconnected. If by seeing if the network is enabled, you mean the boxes that i can check, yes. But, it still says disconnected.
 
Ubuntu 10.10 and Mint both told me something like rt_2800 (not sure about number), then something about "MCU request failed, no response from hardware". But 10.04 worked fine.
 
I just went downstairs and used my Ethernet to install some updates (just the ones from the software center). It worked fine. (the internet through Ethernet)
 
I will take a look at the guide then update what has happened.
 
----
 
Device: wlan0
Driver: rt3090
State: Disconnected
Default: No
HW Address: 00.00.00.00.00.00
 
---
lshw -C Network
(Below this line is the wireless interface)
*-network Disabled
---
sudo iwlist scan
wlan0 "No Scan Results"
---
Idk if putting this random info here helps at all, i've looked through the guide and haven't really gotten anywhere. If you have any ideas and need to know set info, let me know what to do and i will post it.

---

### Post by Yezman on 2010-11-26
Well i searched "3090" on the forums and found tons of similar posts.... They all had the same simple solution, enter what is below and it works.

sudo mkdir -p /etc/Wireless/RT2860STA/
sudo touch /etc/Wireless/RT2860STA/RT2860STA.dat
sudo service network-manager restart

Worked perfectly fine for me!

---

### Post by WrightPC on 2010-12-04
10.10 works on my CQ10-405DX just fine after a little tweak.

I found my answer [here]("https://answers.launchpad.net/ubuntu/+question/132350").
Add "blacklist rt2800pci" to "/etc/modprobe.d/blacklist-wlan.conf" with the following command:
```
sudo echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist-wlan.conf
```then reboot. 

Suspend to Ram works reliably.
Hibernate to disk works reliably.
Random boot failures have disappeared.

All is well.

---

