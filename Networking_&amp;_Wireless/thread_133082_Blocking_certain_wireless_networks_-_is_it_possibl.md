---
title: "Blocking certain wireless networks - is it possible?"
date: 2006-02-19
forum: Networking &amp; Wireless
---

### Post by NeoChaosX on 2006-02-19
Okay, I just recently set up a new wireless network for my home, and I've got a problem. While I can find and connect to my wireless network, there's a second network somewhere in my neighborhood that's also avalible to my computer. Said second network has a poor signal from where I am, and I can't surf the net if I'm connected to it. 

What I've noticed is that if the computer is idle for too long while on the family network, it will for some reason or another, automatically connect to this second network. What I want to do is block the second network so that Kubuntu never ever, tries to connect to it, even if it sees it. Is there a way to do this? Right now, I use the wireless-tools and wpa_supplicant pacakges to connect (the latter because I secured the family network with WPA).

---

### Post by NeoChaosX on 2006-02-20
*bump*

I could use some advice here. The wireless network switching is getting annoying. :(

---

### Post by mpvano on 2006-02-21
Make sure:

1. Your wireless configuration tool has specified the ESSID of your network, not just "any" or blank or whatever wild card your network driver uses.

2. You are using some form of encryption on your access point, even 40 bit WEP encryption with a key you tell everyone, the mere fact that you are using it, helps your driver figure out it's connected to the right AP.

3. Find out what channel you are on and what channel the other network is on. If they're the same (yes, they can be!), change your network to another channel, preferably one that's scanned for earlier by your driver.

Most routers come preconfigured for channel 6. What most people don't understand is that the channels are each about 6 channels wide (+-3channels from center). This means that there are only 3 primary channels available if strong signals are involved - 1, 6 and 11. The idea is that nearby routers shoud use these, and then those further out use 3 and 9, and still further out ones use 2, and 8, and then back to 1,6 and 11.

Since almost all routers come set for channel 6, try channel 1 first, then 11. Also make SURE your ESSID is specified and that you are using encryption. Even weak encryption will help your driver decide that another network is not the right one.

If your driver supports scanning (with "sudo iwlist wlan0 scan" (use the correct name for your adpater here) it helps to collect ALL the details about all the networks in range and save the information. If it doesn't support scanning, it may be worth temporarily booting up windows or asking a friend to bring over a machine that does support scanning and survey the situation.

I discovered the situation here and had a terrible time with it until I understood what was going on. I have set up a testbed with three networks here on channels 1, 6, and 11 and find it works quite well, but ONLY if all the measures I have suggested are employed.

hope these suggestions help,

Mario

---

### Post by NeoChaosX on 2006-02-21
1) I really don't use any tools, save for wpa_supplicant. In the /etc/wpa_supplicant.conf file, I have my home network specified as the highest priority to connect to, along with just it's WPA key. WPA_supplicant runs during boot up, and it instructs the system to automatically connect to a network.

Here's the output of iwlist:
```
nael@fina:~$ sudo iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:14:95:79:F3:C9
                    ESSID:XXXXXXXXXX
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/94  Signal level=-54 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:wpa_ie=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
          Cell 02 - Address: 00:0D:88:94:0C:4F
                    ESSID:"default"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=5/94  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5 Mb/s
                    Bit Rate:11 Mb/s
                    Extra:bcn_int=100
```
...and both networks are on the same channel. You say change it to channel 1? Will that get scanned first? I'll give it a try.

---

### Post by adamonduty on 2006-02-21
You could write a script that connect to your wireless network, then set that script as a cronjob to run every 10 minutes or something. This might be as simple as:

```
iwconfig ath0 essid homenetwork
dhclient ath0

```

although I'm not sure if using WPA suppliant would change that, as I've never used it.

---

### Post by NeoChaosX on 2006-02-21
mpvano: Argh, it didn't do anything. The network switched anyway even though I changed my network's channel from 6 to 1.

---

### Post by mpvano on 2006-02-22
Switching your own network's channel helps, but you STILL need to have some other criteria for selection.

The rest of the advice I gave you was to make sure that you configure your client to require a MATCH on ESSID or MAC address in your case. By the way, you should STILL be able to require a match on ESSID even if it's hidden.

Both networks are apparently candidates. If one's momentarily weak (think multipath reception on an FM radio or TV when someone walks across the room- it happens all the time with wireless as well) then you'll get the wrong one.

Can't you tell WPA supplicant NOT to connect to open networks? That's basically going to always be a problem if one's available and the other one's temporarily weak. The automatic selection process you describe is inherently flawed if you ever allow open networks as a choice.

There's not much point in locking down your network and using elaborate security like WPA if you tell your computer to automatically switch to an open network if it sees one!

Sometimes, you have to give up convenience in the interest of making things work.

I'll have to bow out of this discussion because I don't use WPA supplicant - perhaps someone who is familiar with it can help you make sure it doesn't make promiscuous connections like this.

I suspect thta the way most wireless drivers work will always make this difficult to achieve in practice, that's why I manually switch connections by specifying all the details to the driver here - It's the only thing I've found so far that works.

sorry,

Mario

---

