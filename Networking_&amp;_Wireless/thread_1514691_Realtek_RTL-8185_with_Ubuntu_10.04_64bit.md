---
title: "Realtek RTL-8185 with Ubuntu 10.04 64bit"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by c.dric on 2010-06-21
Hi, 

I've been busy all day searching forums to get my RTL-8185 to work -consistently- on Ubuntu with no luck. Now most threads were quite old and were about older 32 bit versions of Ubuntu, so i'm wondering if someone found a way to get this card working properly with a fully up to date version of 10.04 64bit ? (uname & lspci output below)

The best (/least bad) result so far was to unload the rtl8180, clear the auto wlan0 setup in 'Network Connections' and reload rtl8180.

I tried the ndiswrapper way with the 32 & 64 bit XP drivers but it complained in -both cases- that the 32b driver wouldn't work with a 64b kernel and wlan0 didn't show up in iwconfig.

I hope someone can give me a clue so that i can move on and get my Elgato EyeTV hybrid to work too :D

Thx

> 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux


> 04:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
	Subsystem: Realtek Semiconductor Co., Ltd. Device 8225
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (8000ns min, 16000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 21
	Region 0: I/O ports at e800 [size=256]
	Region 1: Memory at febffc00 (32-bit, non-prefetchable) [size=512]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: rtl8180
	Kernel modules: rtl8180


---

### Post by c.dric on 2010-06-25
bump

---

### Post by Pithikos on 2010-06-28
Same problem here. Just bought 4 wireless TP-LINK cards but can't make any of them work as the only solution so far was to use some win98 drivers but I get the same complains as the drivers are x32 and my ubuntu is x64. I tryied with Vista64 but that didn't help at all. I guess I am forced to switch to Windows as it doesn't seem that there is any other solution :/

---

### Post by Pithikos on 2010-06-28
I got a workaround with it by pure experimenting. I am not quite sure what made it work but my last steps were installing everything(which i don't have any clue what they are) with
```
sudo apt-get install linux-backports-modules-wireless*
```So it installed a bunch of stuff(about 500MB). Then I used ```
sudo modprobe ndiswrapper
```Then I opened "Windows Wireless Drivers" from System>Administration and chose the drivers for Vista64x and restarted the pc. Then when I logged in Ubuntu I just ran ```
sudo modprobe rtl8180
``` and voila! Now it works though it has a speed of 2Mbps :/ Plus I have some notifications about crashes and broken packages. Oh and I run a dual system(Win7x64) and now in the menu where I have to choose OS there are too many different options for Ubuntu(server etc).
____________________________________________________________________________________________________

UPDATE:
Ok now I understood what I did. I used the rtl8180 driver from the kernel. The total speed is a bit faster than a k56 oO

---

### Post by Pithikos on 2010-06-28
Well I have some good news. After a whole day of searching and testing I finally got my network to work :D It was a very tiring day but I learnt quite a bit about linux.

So what I did is use only the rtl8180 driver that comes with the kernel. Don't use ndiswrapper at all! Just disable the network manager and load the rtl8180 and it should work as a charm. Though I haven't tried with encryption(I don't know how I can do that without the network manager).

Here are the exakt steps for someone who might be a noob like me:

1. Write in terminal lsmod. See if in the list there is anywhere written ***rtl8180*** or ***ndiswrapper***.

2. If you see ndiswrapper anywhere just write [COLOR=Red]sudo modprobe ndiswrapper[COLOR=Black]. If you see none of thoise two written there just write [/COLOR][/COLOR][COLOR=Red]sudo modprobe rtl8180[/COLOR][COLOR=Red][COLOR=Black]. If there is written only *rtl8180 *then just let it be.

3. Go to System>Administrator>System Monitor. Under processes find the ***nm-applet**.*[/COLOR][/COLOR][COLOR=Red][COLOR=Black] [/COLOR][/COLOR][COLOR=Red][COLOR=Black]Select it and click on *End Process.* Wait a little and everything should work(as I mentioned in my network I didn't use any encryptionkey to access the network so test it while having the router in "unsafe" mode).

You can also type ifconfig to see if your wifi card is there and to check its status. From my card I get the following:

wlan0     Link encap:Ethernet  HWaddr 00:27:19:c1:9d:ad  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::227:19ff:fec1:9dad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18718 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14768 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22949993 (22.9 MB)  TX bytes:4525600 (4.5 MB)
[/COLOR][/COLOR]

---

### Post by Pithikos on 2010-06-29
OK I tried my own walkthrough today but it didn't seem to do anything. Stuck with the same problems :/

---

### Post by c.dric on 2010-07-02
I'm using the rtl8180 driver that came with 10.04 and WPA keys work too.
But it's unstable. The dock applet only report 15-20% signal strength and when it disconnect, for some unknown reason, it can't reconnect by itself.

I have to 
- right-click the network manager dock applet
- uncheck the enable wireless option 
- right-click the network manager dock applet again
- click edit connections
- go into the wireless tab
- delete the auto connect that was created for my access point.
- re-enable wireless in the network manager dock applet
- then after 30s, select my access point in the network manager
- re-enter my wireless key when it prompts for it.
- then it usually reconnect after 30s

So, apart from the unstability and the signal strength, it can work and i get the same speed as my other computers. But it's a pain to connect. I can do it but if it deconnects when my girlfriend is alone, she will probably just give up ... 
and that's a shame.

I'm still hoping a better fix will come along.

---

### Post by xproject on 2010-07-12
I think I may have found the solution for 64bit users! This has not been tested with encrypted networks and only on Lucid.

[LIST=1]
[*]Get a build environment
```
sudo apt-get install build-essential
```
[*]Download the RTL8185 Linux drivers from Realtek [here]("http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false")
[*]untar drivers
[*]perform the step described [here]("http://ubuntuforums.org/showthread.php?p=9580984")
[*]Follow the ReadMe included with the Realtek driver
[/LIST]

---

### Post by c.dric on 2010-07-18
Thx xproject.

I tried it today and it seems to work fine until now.
Signal is now 80% which seems reasonable and WPA2 is working fine too.

> wlan0     802.11bg linked  ESSID:"Huisje"  
          Mode:Managed  Frequency=2.412 GHz  Access Point: 02:24:01:46:A4:D4   
          Bit Rate=54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=80/100  Signal level=-39 dBm  Noise level=-107 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I'll report in a few days if the constant deconnections i had with the rtl8180 are gone too.

Thx.

---

### Post by c.dric on 2010-07-26
One week later.

As i said earlier it looks alright now. And no more disconnects so that's great.

It does now and then drops to 50% for some unknown reason but that's not a big deal for me.

I noticed those messages in the log, any idea what they mean ? 

```
[288461.885559] CCMP: replay detected: STA=02:24:01:46:a4:d4 previous PN 00000008c4c4 received PN 00000008c4c4
[325786.698473] CCMP: replay detected: STA=02:24:01:46:a4:d4 previous PN 0000000956ac received PN 0000000956ac
[326795.175865] CCMP: replay detected: STA=02:24:01:46:a4:d4 previous PN 00000009684c received PN 00000009684c
[326958.311179] Now traffic is busy, please try later!
[326969.281365] CCMP: replay detected: STA=02:24:01:46:a4:d4 previous PN 000000099b8e received PN 000000099b8e
[326976.142543] CCMP: replay detected: STA=02:24:01:46:a4:d4 previous PN 00000009a4ba received PN 00000009a4ba
[327000.210389] CCMP: replay detected: STA=02:24:01:46:a4:d4 previous PN 00000009c43f received PN 00000009c43f
[327002.360767] CCMP: replay detected: STA=02:24:01:46:a4:d4 previous PN 00000009c71e received PN 00000009c71e
[337304.659826] CCMP: replay detected: STA=02:24:01:46:a4:d4 previous PN 00000009dfc8 received PN 00000009dfc8

```

Anyway, i consider this problem solved.

Thanks for your help xproject.

---

