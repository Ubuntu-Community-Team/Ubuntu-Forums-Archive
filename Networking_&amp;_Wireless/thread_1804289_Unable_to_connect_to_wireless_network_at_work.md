---
title: "Unable to connect to wireless network at work"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by StealthMode on 2011-07-14
Hello, I'm fairly new to Ubuntu, and loving the learning curve. Currently I'm having trouble connecting to the guest wireless network at my work. I've read through a couple threads that seem similar to my problem. I tried going through the terminal window and following the instructions that was offered to others. I'm just wondering if my hardware is different, if I need drivers, if my permissions aren't correct. 
 
1. I recently received a Sony Vaio laptop model # VGN-FE770G from a friend, and I'm enjoying running Ubuntu. 
2. I followed another thread that suggested to change some lines in /etc/network/interfaces, but I don't have permission to edit this file. I don't really have the need to set up multiple users on my laptop, so how can I change my permissions to root? (Or is it a good idea even?) Should I log in as root?
3. How can I set my laptop up to be flexible with network selections, using hardware: (built-in camera and microphone for example), and useful applications? 
 
THANKS!
I ran "ifconfig -a" and this is what I got. 
>  
[SIZE=3][FONT=Times New Roman]eth0      Link encap:Ethernet  HWaddr 00:13:a9:48:c3:00  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:1000[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]lo        Link encap:Local Loopback  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX packets:20 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX bytes:1272 (1.2 KB)  TX bytes:1272 (1.2 KB)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]wlan0     Link encap:Ethernet  HWaddr 00:18:de:62:86:9d  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:1000[/FONT][/SIZE]
[FONT=Liberation Serif]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT]

---

### Post by chili555 on 2011-07-14
You shouldn't have to set up /etc/network/interfaces at all. Your version of Ubuntu uses Network Manager. You should be able to click the icon, see your work network and connect. Here is a sample from my machine; you see my network GBR1.

You have a wireless interface, wlan0 which suggests that the driver is in order. Let's save permissions and root privileges for a later time. We probably don't even need it!

---

### Post by StealthMode on 2011-07-14
Thanks for the reply! I have used the network manager, and have come up with nothing. It sees the network, attempts to join, but it will not lock on. Is it possible that this is a windows only or encrypted network? A co-worker JUST bought a brand spankin new windows 7 machine, and it connected to the network just fine.

---

### Post by chili555 on 2011-07-14
> Is it possible that this is a windows onlyI suppose anything is possible, but in this day of smart-phones, iPads, etc., it seems highly unlikely that any enterprise would do such a thing. I have never found a network that I couldn't connect to using Linux if I had permission and the encryption key.> or encrypted network? Very likely, however, you should be challenged for the encryption key, if so. Let's see what's going on under the hood. Please open a terminal and do:```
sudo iwlist wlan0 scan
```When challenged, enter your user password; the same one you use when you log on to the computer. It won't show up but that's OK, just key it in and press Enter. Post the result. If more than one access point is shown, just post the work guest details.

Let's look into the wireless driver details, too:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by StealthMode on 2011-07-14
sudo iwlist wlan0 scan
> 
**[FONT=Times New Roman][SIZE=3]Cell 19 - Address: 00:22:90:93:3F:31[/SIZE][/FONT]**
**[SIZE=3][FONT=Times New Roman]Channel:1[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Frequency:2.412 GHz (Channel 1)[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Quality=39/70 Signal level=-71 dBm [/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Encryption key:off[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]ESSID:"tsgt_wlan_guest"[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]11 Mb/s; 12 Mb/s; 18 Mb/s[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Mode:Master[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Extra:tsf=0000093945b16178[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Extra: Last beacon: 1488ms ago[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 000F747367745F776C616E5F6775657374[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 010882848B0C12161824[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 030101[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 050700010000000000[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 0706555320010B1E[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 0B050500640000[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 2A0104[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 2D1A6E181BFFFF000000000000000000000000000000000000000000[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 32043048606C[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 3D1601000700000000000000000000000000000000000000[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 851E0E008F000F00FF0359004851322D53456173742D41340000000005000036[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 9606004096000B00[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: DD180050F2020101800003000000270000004200000062000000[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: DD06004096010104[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: DD050040960305[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: DD050040960B09[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: DD050040961400[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Cell 20 - Address: 00:22:90:95:EC:91[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Channel:6[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Frequency:2.437 GHz (Channel 6)[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Quality=51/70 Signal level=-59 dBm [/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Encryption key:off[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]ESSID:"tsgt_wlan_guest"[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]11 Mb/s; 12 Mb/s; 18 Mb/s[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Mode:Master[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Extra:tsf=00000afedd856178[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Extra: Last beacon: 1348ms ago[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 000F747367745F776C616E5F6775657374[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 010882848B0C12161824[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 030106[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 050400010000[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 0706555320010B1E[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 0B0500004B0000[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 2A0106[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 2D1A6E181BFFFF000000000000000000000000000000000000000000[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 32043048606C[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 3D1606000500000000000000000000000000000000000000[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 851E0B008F000F00FF0359004851534C2D4C6962726172792D41340000000036[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 9606004096000800[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: DD180050F2020101800003000000270000004200000062000000[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: DD06004096010104[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: DD050040960305[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: DD050040960B09[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: DD050040961400[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Cell 21 - Address: 00:22:90:96:0F:61[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Channel:11[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Frequency:2.462 GHz (Channel 11)[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Quality=32/70 Signal level=-78 dBm [/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Encryption key:off[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]ESSID:"tsgt_wlan_guest"[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]11 Mb/s; 12 Mb/s; 18 Mb/s[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Mode:Master[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Extra:tsf=000004190b5c5131[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Extra: Last beacon: 1320ms ago[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 000F747367745F776C616E5F6775657374[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 010882848B0C12161824[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 03010B[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 050400010000[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 0706555320010B1E[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 0B050000830000[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 2A0104[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 2D1A6E181BFFFF000000000000000000000000000000000000000000[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 32043048606C[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 3D160B000500000000000000000000000000000000000000[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 851E0D008F000F00FF0359004851312D43523130312D41313000000000000036[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 9606004096000800[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: DD180050F2020101800003000000270000004200000062000000[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: DD06004096010104[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: DD050040960305[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: DD050040960B09[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: DD050040961400[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Cell 22 - Address: 00:22:90:96:20:D1[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Channel:11[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Frequency:2.462 GHz (Channel 11)[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Quality=29/70 Signal level=-81 dBm [/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Encryption key:off[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]ESSID:"tsgt_wlan_guest"[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]11 Mb/s; 12 Mb/s; 18 Mb/s[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Mode:Master[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Extra:tsf=00000613f5bd062d[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]Extra: Last beacon: 1312ms ago[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 000F747367745F776C616E5F6775657374[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 010882848B0C12161824[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 03010B[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 050400010000[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 0706555320010B1E[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 0B0502006D0000[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 2A0104[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 2D1A6E181BFFFF000000000000000000000000000000000000000000[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 32043048606C[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 3D160B000700000000000000000000000000000000000000[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 851E0E008F000F00FF0359004851534C2D504348616C6C2D4135000002000036[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: 9606004096000B00[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: DD180050F2020101800003000000270000004200000062000000[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: DD06004096010104[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: DD050040960305[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: DD050040960B09[/FONT][/SIZE]**
**[SIZE=3][FONT=Times New Roman]IE: Unknown: DD050040961400[/FONT][/SIZE]**

 
lspci -nn | grep 0280
 
>  [FONT=Liberation Serif]06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02) [/FONT]
 
EDIT: not sure why the smiley's ended up in there! Probably just auto-input for the emoticons.

---

### Post by chili555 on 2011-07-14
Wow! Every driver genie's worst nightmare: three networks all with the same name and none is overwhelmingly stronger than the others. I expect that Network Manager roams between the three endlessly and never really connects with any. Sounds like certain clubs on Saturday night at about 2:00 am.

Let's concentrate on this one:> Cell 20 - Address: [COLOR="Red"]00:22:90:95:EC:91[/COLOR]
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=51/70 Signal level=-59 dBm
Encryption key: off
ESSID:"tsgt_wlan_guest"Please click on Network Manager, click Edit Connections. Select Wireless. Add the MAC address, highlighted above, to BSSID. Save and close. Now see if it will connect to the strong network and not roam to the others.

At the bottom of the reply box, you can check off "Disable Smileys."

---

### Post by StealthMode on 2011-07-15
Ok I'm hoping I understood correctly and that I did this right. Here was my process. 
System>Preferences>Network Connections>Wireless (tab)>Choose wlan_guest>Edit.
 
Then I typed the address into BSSID. The part that confuses me is that there is a line for "MAC address" right below the line for BSSID. Should I type it into both? Or just BSSID?

---

### Post by chili555 on 2011-07-15
In BSSID *only*, type:> 00:22:90:93:3F:31If you try it a few times and it doesn't work, try lower-case:> 00:22:90:93:3f:31Fingers crossed!

This is a well known problem in large offices, factories, hospitals, etc. where you may be between access points and roaming causes Network Manager to wander and never solidly connect. There are two ways to differentiate in your setting, the MAC address and the channel. Network Manager can't yet do all things for all people all of the time.

---

### Post by StealthMode on 2011-07-15
Ok I tried it. I typed that address into BSSID and applied the changes. Then, I would have to manually go back and click on the wireless network to join again. It would work for a while and do nothing. I went back into Network Connections and found that it had opened a NEW connection with the same name "tsgt_wlan_guest". So I deleted the first one I had established and tried the address under BSSID in the new connection that it had made. This time it automatically started trying to connect. It still turned up nothing, but it seemed to work a little better. I'm trying that one a few times, and I'll try typing the lower case "f" in there instead of upper case.
 
EDIT: Ok, every time I try to connect, it opens a NEW connection and ignores the one I edited with the address under BSSID.

---

### Post by StealthMode on 2011-07-18
I still haven't gotten wireless to connect, but I was able to plug into an ethernet connection at my desk.
 
But I'd still like to get this solved! Thanks for your help and your patience with me!

---

### Post by chili555 on 2011-07-18
I am not sure I have any better answer. NM is problematic in that particular instance; i.e. multiple access points with the same ESSID and roaming (read: disconnecting, reconnecting, etc.) Here is a whole discussion about the subject and I'm sure a quick search could find more: [http://osdir.com/ml/networkmanager-list/2011-02/msg00040.html](http://osdir.com/ml/networkmanager-list/2011-02/msg00040.html)

Just follow Next by Thread > Network Manager reason codes. What we do not see is a foolproof way to set some flag or modifier that causes a reply that it's fixed.

In a more perfect NM world, setting the BSSID would lock connection to the selected access point. I am fairly sure it could be done manually. I haven't tried Wicd in some time and you might look into it. 

Here is an interesting thread: [http://www.linuxquestions.org/questions/linux-wireless-networking-41/wicd-and-other-network-managers-roam-uncontrollably-any-ideas-789269/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/wicd-and-other-network-managers-roam-uncontrollably-any-ideas-789269/)

I wish I could be more helpful.

---

### Post by StealthMode on 2011-08-01
Hey Chili, I have installed Ubuntu on a friend's daughter's brand new HP laptop, and I'm having similar issues. Unable to connect to a wireless network. This time, however, it won't even detect a wireless network. Has the wireless somehow been turned off? (PS, I never got mine to connect here at work, but I settled for an ethernet connection at my desk. It does just fine with other wireless networks outside of my work.)

---

### Post by chili555 on 2011-08-01
> This time, however, it won't even detect a wireless network. Has the wireless somehow been turned off? It could be, or it could be that a proper driver is not installed.

Do you want to troubleshoot your wireless connection at work? What does this tell us?```
sudo iwlist wlan0 scan
```

---

### Post by StealthMode on 2011-08-01
wlan0      Interface doesn't support scanning.

---

### Post by chili555 on 2011-08-01
Is your wireless interface indeed wlan0?```
iwconfig
```

---

### Post by StealthMode on 2011-08-01
> lo    no wireless extensions.
eth0     no wireless extensions. 
 
I connected it to an ethernet connection, which worked just fine. This is a dual-boot machine, and worked just fine connecting wireless before I installed Ubuntu. Seems like something got lost in the shuffle.

---

### Post by chili555 on 2011-08-01
> (PS, I never got mine to connect here at work, but I settled for an ethernet connection at my desk. [COLOR="Red"]It does just fine with other wireless networks outside of my work.)[/COLOR]I guess I'm confused. Does the Ubuntu machine you are using now connect to wireless networks in Ubuntu ever or anywhere??

---

### Post by StealthMode on 2011-08-01
Sorry to confuse you. I am trying to help a friend get his computer's wireless working. Originally, I started this thread because I needed help with my own Sony Vaio laptop that wasn't connecting to wireless here at work. I gave up and just settled for a wired connection. 
 
My friend bought a laptop for his daughter's birthday. I installed Ubuntu 10.04 on it with a dual partition for Windows Vista. I'm pretty sure I got it to work properly. This HP machine is not recognizing ANY wireless networks currently. Not even picking them up. I figured this was a similar problem, although on my laptop, it would recognize the network, just wouldn't connect. This one can't even see the network. 
 
Should I have started a new thread? Sorry again for the confusion, I didn't want to clutter up the forum with multiple threads.

---

### Post by chili555 on 2011-08-01
You needn't start a new thread. I just want to make sure if we're troubleshooting your friend's laptop or yours. It will be difficult to diagnose your friend's if we don't have physical access.

I will be happy to help you get your current laptop's wireless going. It sounds to me like it has no installed wireless driver and, if you wish, I'd be happy to help.

---

### Post by StealthMode on 2011-08-01
Absolutely, I'd love the help. The one I'm working on right now is his laptop. I have it right here next to me and I have his passwords and permission to get it working. Let's do this!

---

### Post by chili555 on 2011-08-01
Does it have a working wireless driver? If so, it will show a wireless interface such as wlan0 or eth1 here:```
iwconfig
```If so, does it scan?```
sudo iwlist wlan0 scan
```Of course, substitute the actual interface if it's not wlan0. If there is no wireless interface, let's see what kind of card it has:```
lspci -nn | grep 0280
```

---

### Post by StealthMode on 2011-08-01
Ok, those are the same commands you had me run earlier. I ran those on this HP machine. No scan and no interface. I'll do the last one and then edit this post with the results.
 
Results: 
> 02:00.0 Network controller [[COLOR=red]0280[/COLOR][COLOR=black]]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01) [/COLOR]

---

### Post by chili555 on 2011-08-01
This device works with the driver rtl8192ce which is on the latest version of Ubuntu, Natty 11.04 but must be compiled from source code in earlier versions. Is it present there? ```
modinfo rtl8192ce | grep 8176
```If not, you could install the latest Ubuntu version or we could get our geek on and compile some source code.

There is sometimes a problem with firmware.

---

### Post by StealthMode on 2011-08-01
Result:
> ERROR: modinfo: could not find module rtl8192ce 

---

### Post by StealthMode on 2011-08-01
I have the .iso file for the latest version saved here at work, so I could try to re-burn a live disc and try to do an install there. I was having a bit of trouble doing the dual partition when I was trying to install 11.04. But someone linked me to a good, helpful page that might be able to help me get through it again.

---

### Post by chili555 on 2011-08-01
Compiling is not terribly hard but a newer version cures a lot of ills, including wireless. If it doesn't work perfectly, post back and we'll look into the firmware.

---

### Post by StealthMode on 2011-08-01
I will burn a new disc and get back to you tomorrow morning. I won't be able to start the install and re-partition the drive till the morning.

---

### Post by chili555 on 2011-08-01
I will look for you then.

---

### Post by StealthMode on 2011-08-01
Thanks for all your help. Sooner or later I might understand how to make a computer do what I tell it to do!

---

### Post by StealthMode on 2011-08-02
Ok, Ubuntu 11.04 installed, I am pretty sure I partitioned the drive correctly. There was some kind of error that said "apt-clone" failed or something, but it went ahead with the install. I unplugged the ethernet connection, and when I click on the Wireless icon in the tray, it says "wireless is disabled by hardware switch."
 
I checked the Update Manager for available updates, installed them, and WHAT DO YOU KNOW? The thing works now! Wireless detects and connects! Interesting! Now I'm thinking I need to bring my Sony in and try the upgrade! Chili, can you recommend any help with harware issues? I haven't gotten any responses. [http://ubuntuforums.org/showthread.php?t=1807137](http://ubuntuforums.org/showthread.php?t=1807137) 
 
Again, thanks for all your insight.

---

### Post by chili555 on 2011-08-02
Glad it's working! Have fun.

---

