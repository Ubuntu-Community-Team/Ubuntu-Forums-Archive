---
title: "Ubuntu 11.04 wifi problem"
date: 2011-05-17
forum: Networking &amp; Wireless
---

### Post by jpwebber on 2011-05-17
This is a strange one, but bear with me.
 
I am a Virgin Media (UK) customer and have been using their service with no problem for some time.
I just installed 11.04 on my Lenovo N500 laptop and my router does not come up in the list of networks. I tried adding it as a new network and it connected, but I have no gateway to the internet.
I tried the route -n command and it gives a strange IP address - 10.42.43 - my router's IP address is 192.168.0.1
 
All previous versions of Ubuntu have worked fine and I can connect with a windows laptop and an Itouch.
 
Any ideas anyone?
 
Thanks, John.

---

### Post by x-master on 2011-05-17
sure your card isnt the problem ?
what wifi card you use ?

sudo lshw -C network

---

### Post by jpwebber on 2011-05-17
It's a Broadcom, but I've never had problems with it on previous versions of Ubuntu

---

### Post by x-master on 2011-05-17
i got broadcom as well, 4311 ( rev01) to be precise, and mine did not work with the integraded broadcom STA driver that comes with Ubuntu 11.04

if you have this card as well you might having the same trubble i did.
My problem is solved after removing "bcmwl-kernel-source" by using  Synaptic Package Manager, then installing "firmware-b43-installer" and  "b43-fwcutter" again by Synaptic Package Manager. After a restart, my  wireless network connection works. 

check if you have the same card, and if you use :
sudo lshw -c network

Does the card come up as "UNCLAIMED" ?

---

### Post by TBABill on 2011-05-17
Can you tell us which one? Run ```
lspci
``` in a terminal and paste the output or type back here the model number (bcmxxxx). Depending on which you have, you could either need the STA or b43 driver.

---

### Post by jpwebber on 2011-05-17
It's a BCM4312 - it doesn't come up as 'UNCLAIMED'

---

### Post by Hippytaff on 2011-05-17
The wireless script (link below) might help. It will at least return relevant information for tourbleshooting :)

---

### Post by jpwebber on 2011-05-18
Hippytaff - here are the results of running your script:

---

### Post by TBABill on 2011-05-18
Can you connect via ethernet and then go to additional drivers? The BCM4312 should use the STA (wl) driver although *some* models can use the b43 (mine cannot). Additional drivers should take care of installing the driver for you.

---

### Post by jpwebber on 2011-05-18
I don't have an ethernet connection I'm afraid - is there any way to download drivers to this windows machine?

---

### Post by jpwebber on 2011-05-19
Forget the last comment - I found an old ethernet plug which worked. I still have a problem though - email and internet is working with this, but when I try to download the additional drivers it fails and tells me to check my connection! 
 
Any more ideas please, I'm getting desperate!

---

### Post by Hippytaff on 2011-05-19
Are you running through a proxy and are you doing sudo apt-get or installing through synaptic/additional drivers?

---

### Post by jpwebber on 2011-05-19
I'm not running through a proxy and I'm using the synaptic package manager - I'll try the sudo method

---

### Post by jpwebber on 2011-05-19
tried sudo and I'm being denied permission when I try to get the update list

---

### Post by chili555 on 2011-05-19
> I tried the route -n command and it gives a strange IP address - 10.42.43 - my router's IP address is 192.168.0.1What does this tell us?```
ifconfig
```Does your wireless interface also have a 10.42.43.xx address? That is typical of computer-to-computer, or internet connection sharing arrangements. I suspect that is not what you want; I suspect you wish to connect to the router. 

Click the Network Manager icon at the top and select Edit Connections. Click the Wireless tab and highlight your network and select Edit. Make sure it is set to Mode Infrastructure, not Ad Hoc. Please see attached. Click Save and the delete your network altogether. Reboot. Let NM find your network and connect. Run:```
ifconfig
```Do you now have a 192.168.0.xx address?

---

### Post by jpwebber on 2011-05-19
Okay - I managed to install jockey-kde (additional drivers) via sudo. I then unplugged the ethernet connection and re-booted.
 
My network connection is still not found in the networks list. I added it as a new connection and nothing has changed. WIFI says it's connected, but there's no access to email or web.
 
What next, anyone?

---

### Post by chili555 on 2011-05-19
> **jpwebber said:**
> Okay - I managed to install jockey-kde (additional drivers) via sudo. I then unplugged the ethernet connection and re-booted.
 
My network connection is still not found in the networks list. I added it as a new connection and nothing has changed. WIFI says it's connected, but there's no access to email or web.
 
What next, anyone?See my post above.> I added it as a new connectionIf you mean "Create New Wireless Network" that sets up a computer-to-computer arrangement. That's exactly what you do *NOT* want.

---

### Post by jpwebber on 2011-05-20
Chilli555 - I've done as you said but the problem still is that NM is not finding my network - other nearby ones are coming up in the list, but not mine. I've never had this problem prior to 11.04. As you can see, I'm working quite happily here on my Windows laptop through my network.
 
What I need to find out is why NM can't find my network
 
Many thanks, John.

---

### Post by chili555 on 2011-05-20
Is your router set to N speeds only or mixed B, G and N? I have seen several cases where the wireless card thinks it can't do N speeds and therefor doesn't show N networks. What does this tell us?```
sudo iwlist eth1 scan
```

---

### Post by jpwebber on 2011-05-20
Chilli555 - here are the results of that:

---

### Post by chili555 on 2011-05-20
> Cell 02 - Address: 00:1B:2F:65:D7:38
                    ESSID:"[COLOR="Red"]NETGEAR[/COLOR]"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-54 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:onSo, is this your network? Does it not appear in Network Manager? Have you entered any details in NM? I hope not. I always have the best luck letting NM do all the work.

---

### Post by jpwebber on 2011-05-20
No this isn't my network. It is a NETGEAR router, but the SSID should begin 'virginmedia'. I assume that the NETGEAR mentioned here is the default SSID for someone else's network.
 
This is assuming that somehow NM hasn't 'lost' my SSID and is recognising it only by a default name.

---

### Post by chili555 on 2011-05-20
I assumed it is your network because it has a strength of 5/5. When I can scan and see my neighbor, looking right out the window at his house, I usually get 3/5 or 2/5.

Can you hook up to your router with an ethernet cable and check? Check the WPA password while you're in there.

Hey! That gives me a great idea. My neighbor's network in unencrypted, I think I'll log in to his router's administration pages and change his ESSID from 'default' to 'getsomeencryptionRyan.'

---

### Post by jpwebber on 2011-05-20
No the SSID and password are as I'd expect - I've never changed them. In any case, if they had been  changed then my other wifi devices would have stopped working.
 
Maybe I can get onto Ryan's network too - though it might be a bit of a stretch from the UK!

---

### Post by chili555 on 2011-05-20
Back in post #7, Hippytaff asked for the results of a diagnostic script. May he and I see it again? I feel like something simple is staring us in the face, but we're too blind to see. Hey, I hear a blues song coming on!

---

### Post by jpwebber on 2011-05-21
Yes - here they are again - thanks, John.

---

### Post by chili555 on 2011-05-21
Here is what I saw:> eth1      Link encap:Ethernet  HWaddr 00:24:2b:7f:73:71  
          inet addr:[COLOR="Red"]10.42.43.1[/COLOR]  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2bff:fe7f:7371/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:5335
          TX packets:8 errors:19 dropped:0 overruns:0 carrier:0> eth1      IEEE 802.11bg  ESSID:"virginmedia8037566"  
          [COLOR="Red"]Mode:Ad-Hoc[/COLOR]  Frequency:2.412 GHz  Cell: C6:5D:21:DD:F0:A4   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
Please go back to post #15. Please check and delete all entries in Network Manager. If the 10.42.x.x keeps coming back, we'll need to dig deeper.

---

### Post by jpwebber on 2011-05-21
Hi Chili - I did do the stuff in post #15 - when I reboot my network is not visible in NM, which is why I tried to set up a new connection in the first place.
 
The mystery is why my network doesn't appear in NM. Could it be that I need to change a setting on the router to cope with something new in 11.04?

---

### Post by chili555 on 2011-05-21
> my network is not visible in NM, which is why I tried to set up a new connection in the first place.I probably have not made myself clear enough. We do ***NOT*** want to Create New Wireless Network...

Why? Because that is the setup for computer-to-computer ad-hoc arrangements. I wish, with my right hand on Linus Torvald's personal C/C++ Programmer's Bible, that it was titled Set up Connection Sharing Network. That is exactly what you do ***NOT*** want! Please delete, remove and expunge all such settings and reboot. Run:```
iwconfig
```Is mode Managed? If not, please do:```
sudo iwconfig wlan0 mode managed
```Let NM look for networks and post back here to tell us the result.

Please swear that you will never touch Create New Wireless Network... again. Please.

---

### Post by jpwebber on 2011-05-21
Hi Chili,
 
I don't think I made myself clear - I haven't tried to create a new network since your post #17 - you were very clear.
 
iwconfig just returns the message 'no wireless extensions'
 
the second command you gave fails (undestandably I suspect).

---

### Post by bkratz on 2011-05-21
> **jpwebber said:**
> Hi Chili,
 
I don't think I made myself clear - I haven't tried to create a new network since your post #17 - you were very clear.
 
iwconfig just returns the message 'no wireless extensions'
 
the second command you gave fails (undestandably I suspect).



Dr Chili did you mean 

sudo iwconfig wlan0 mode managed

his/her interface is eth1

---

### Post by chili555 on 2011-05-21
Arrgh! This just gets crazier. My bad; bkratz caught me! Please do:```

sudo iwconfig eth1 mode managed
iwconfig eth1
```Now is it 'mode managed?' Now does NM see your network? I wonder if NM thinks it's not a router but an ad-hoc network and mode managed doesn't want to see any ad-hoc...?

---

### Post by jpwebber on 2011-05-21
I've got a headache!
 
Okay - iwconfig eth1 gives:
 
IEEE 801.11 Access point: not associated
Link quality:5 Signal level:0 Noise level:0
Rx invalid nwid:0 invalid crypt:0 invalid misc:0

---

### Post by chili555 on 2011-05-21
Mine is slowly progressing to a migraine. No mode shown?

---

### Post by jpwebber on 2011-05-21
I'm afraid there isn't.
 
Can I send you a virtual cold towel?

---

### Post by chili555 on 2011-05-21
Please run:```
rfkill list all
```Are we certain the wireless switch is set to 'On?' Any interesting messages in:```
dmesg | grep -e wl -e eth1
```I need a tall cool one.

---

### Post by jpwebber on 2011-05-21
The first command lists two items:
 
0 hci0 blurtooth
1 brcmwl 0: wireless LAN
 
 
The second command, among other things does say
 
eth1: no IPv6 routers present

---

### Post by chili555 on 2011-05-21
> The first command lists two items:

0 hci0 blurtooth
1 brcmwl 0: wireless LAN
And what else? Soft blocked, hard blocked, yes, no? Here is a sample from my machine:> 0: tpacpi_bluetooth_sw: Bluetooth
	[COLOR="Blue"]Soft blocked: yes[/COLOR]
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
The specific details are what bkratz and my psychiatrist need to see.

---

### Post by jpwebber on 2011-05-21
All the 'blocked' responses are 'no'
 
The dmesg command returns:
 
[25.159048] wl: module license 'MIXED/Proprietary' taints kernel
[25.415787] wl 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[25.415799) wl 0000:04:00,0: setting latency timer to 64
[25.648876] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.100.82.38
 
[71.780015] eth1: no IPv6 routers present

---

### Post by chili555 on 2011-05-21
Please do:```
ls /etc/NetworkManager/system-connections/
```Do you have a file in there called Auto virginmedia8037566? If so, delete it:```
sudo rm /etc/NetworkManager/system-connections/*
```Immediately reboot and tell us if your network shows in NM and more importantly, if you can connect.

---

### Post by jpwebber on 2011-05-22
There's nothing in the system connections folder I'm afraid.
 
I'm going to see if my local PC shop can send someone to investigate this in situ - but if they can't I'll be back here next week.
 
Thanks for all you help,
 
John.

---

