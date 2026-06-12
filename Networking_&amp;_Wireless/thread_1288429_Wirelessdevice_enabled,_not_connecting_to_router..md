---
title: "Wirelessdevice enabled, not connecting to router."
date: 2009-10-11
forum: Networking &amp; Wireless
---

### Post by jeantea on 2009-10-11
Hello. I just decided to install Ubuntu on my laptop, since I've been ashamed to use Windows for so long. 
I keep hearing that if you are into computing you should use some linux OS, and since I'm a Windows W***e, Ubuntu seems like the way to go.
I installed Ubuntu yesterday, and still havn't  got my wireless to work. Atm i'm using my wired connection, but i want to use the wlan.

I have had some development.
At first my wlan "light" didn't ligth up, and wouldn't light up. I ran some sort of update, when trying to install Flash10, and now the light is indicating that my Wireless is activated. it ran quite many updates.
It also finds my wlan, but it wont connect.
Its secured with WPA & WPA2 Personal (shows when i connect) and double checked with the router. i enter my password, but it won't connect.
I am not using the "Windows Wireless Drivers" app.

My laptop is a Hp dv8354ea runing Ubuntu 9.04, and i think that the wlan card is some broadcom card. My router is a Belkin N Wireless Router.

I really hope someone could help me. I don't want to go back to Windows.

---

### Post by Bucky Ball on 2009-10-11
Plug in an ethernet cable. A lot of Broadcom products now work 'out of the box' but you need to download the restricted drivers. The 'catch 22'. It can save a lot of time trying this first.

You can find the exact card by by opening a terminal:

Applications->Accessories->Terminal

typing this:

```
lspci
```In the list will be the exact name of your Broadcom card, but plug that cable in and your problems should be solved. I have a DV6305us and am using 8.04 and that was my experience. It has worked for a lot of others. There has been a driver developed for Broadcom cards (B43 and b43-fwcutter) and you should be able to follow your nose.

DON'T try ndiswrapper until you try my suggestions (if you read that you should). :)

Good luck and welcome.

---

### Post by jeantea on 2009-10-11
Thank you for a very quick reply!
What i found was:
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
My wired network works just fine. but i would like the wireless to work just as fine ;)

I think i maybe alreaddy have installed ndiswrapper. What problems could that cause?

---

### Post by jeantea on 2009-10-11
> **Bucky Ball said:**
> Plug in an ethernet cable. A lot of Broadcom products now work 'out of the box' but you need to download the restricted drivers. The 'catch 22'. It can save a lot of time trying this first.

You can find the exact card by by opening a terminal:

Applications->Accessories->Terminal

typing this:

```
lspci
```In the list will be the exact name of your Broadcom card, but plug that cable in and your problems should be solved. I have a DV6305us and am using 8.04 and that was my experience. It has worked for a lot of others. There has been a driver developed for Broadcom cards (B43 and b43-fwcutter) and you should be able to follow your nose.

DON'T try ndiswrapper until you try my suggestions (if you read that you should). :)

Good luck and welcome.

Uhm. I've installed (or something) b43-fwcutter, and uninstalled the ndiswrapper. This dind't really work. Now I cant find my wlan at all. 
How does this b43-fwcutter work anyway?
Any suggestions?

[quote=http://linuxwireless.org/en/users/Drivers/b43#device_firmware]
in latest versions of Ubuntu (all flavors) and Debian just need to install the b43-fwcutter package: **sudo apt-get install b43-fwcutter** 
when you are asked "Fetch and install firmware?" answer "Yes" (just press "Enter) 
[/quote]
I did not get the "fetch and install firmware" message. Am I doing this wrong?

---

### Post by houstonbofh on 2009-10-11
> **jeantea said:**
> I think i maybe alreaddy have installed ndiswrapper. What problems could that cause?
It makes it very hard to help you, when you don't even know what you did... :)  If you change ANYTHING from stock, you absolutely have to keep track, and if it doesn't work, you have to change it back.  Anything changed from stock can be an issue later (especially around upgrade time) and so you need to know.

Now if you have ndiswrapper installed, and you fix the firmware, you will be loading a driver twice, and they will fight.  So open synaptic and search for 'ndiswrapper' and see if it is installed.  If so, yank the two or three packages, and lets try the "official" method first.  Close synaptic, and open System -> Administration -> Hardware Drivers.  If it has an option for wireless, install it.  In most cases, you will now have a working WiFi card.

---

### Post by jeantea on 2009-10-11
I think i've updatet alot in synaptic.
And i did install the ndiswrapper, together with a ndisgtk.
I have now removed them.
and installed the b43-wfcutter.
With the ndiswrapper at least i could see that my wlan-card found signals.
Now with the b43-wfcutter i cant even find the signals. (the wlan led is lighted).

Tried the Harware Drivers, but it could only find Software Modem (and it is enabled).
Did this help any at all?

Currently running b43-wfcutter. But still cant connect (or find) wlan. :P
When I press the network button (left to the sound icon) it will not say I got a wireless connection at all.
Any idea of how i can get a list over what i AM running? and post it here, so maybe someone could push me in the right direction.

---

### Post by houstonbofh on 2009-10-11
> **jeantea said:**
> I think i've updatet alot in synaptic.

This is what I was afraid of.  You may have changed some things, and forgot them.  Boot off the LiveCd, and try the Hardware Drivers applet again.  If it finds your nic, you may want to just reinstall, so you know that you have a clean install running.

---

### Post by jeantea on 2009-10-11
Well. I tried to run it Live from the CD. And guess what was in the Hardware Drivers?
My wlan card. 
I installed a clean copy of Ubuntu and I am now ready for action!
Now i have activated Broadcom B43 wireless driver. But now i cant enable my wlan card. Any Ideas? Remember. Fresh copy now ;)

---

### Post by houstonbofh on 2009-10-11
> **jeantea said:**
> Well. I tried to run it Live from the CD. And guess what was in the Hardware Drivers?
My wlan card. 
I installed a clean copy of Ubuntu and I am now ready for action!
Now i have activated Broadcom B43 wireless driver. But now i cant enable my wlan card. Any Ideas? Remember. Fresh copy now ;)
Lots!  And now that we are working from a clean slate, we can dig right in! :)

1) Right click on the Network Manager Applet.  Is 'wireless' enabled?  Also look at your laptop, is the a switch for your wireless card, and is it on?  (It may be a function switch, or a soft switch)

2) When you left click the network manager icon, do you see any access points to connect to?

3) Once we are sure it is on, open a terminal.  We want 'lspci' 'ifconfig' 'iwconfig' and 'iwlist scanning' outputs.

That should get us started.

---

### Post by jeantea on 2009-10-11
> **houstonbofh said:**
> Lots!  And now that we are working from a clean slate, we can dig right in! :)

1) Right click on the Network Manager Applet.  Is 'wireless' enabled?  Also look at your laptop, is the a switch for your wireless card, and is it on?  (It may be a function switch, or a soft switch)

2) When you left click the network manager icon, do you see any access points to connect to?

3) Once we are sure it is on, open a terminal.  We want 'lspci' 'ifconfig' 'iwconfig' and 'iwlist scanning' outputs.

That should get us started.

1)
Yes, wireless is enabled. But my "hardware" switch isnt on. (checked the bios, it's not disabled). But my wlan led wont light up :(

2)
No, i do not find any access points. (Maybe because my wlan led isn't lit?)

3)
lspci 
```

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```ipconfig
```
eth0      Link encap:Ethernet  HWaddr 00:1b:38:bc:79:f1  
          inet addr:95.34.240.103  Bcast:95.34.240.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:febc:79f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8380 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12720670 (12.7 MB)  TX bytes:1339572 (1.3 MB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```iwconfig 
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```iwlist not actually giving much info..

Now, what do we know now?! :P

---

### Post by houstonbofh on 2009-10-11
Look for a function key combination...  On many Dell systems, it is 'Fn + F2' to toggle the WiFi.  Also, try enabling and disabling in network manager.

Also, did you reboot after enabling the hardware drivers?  That can reset the card as well.

---

### Post by jeantea on 2009-10-11
> **houstonbofh said:**
> Look for a function key combination...  On many Dell systems, it is 'Fn + F2' to toggle the WiFi.  Also, try enabling and disabling in network manager.

Also, did you reboot after enabling the hardware drivers?  That can reset the card as well.

Running a HP machine. ;) So Fn + F2 gives me. Print xD
Well. Now i disabled the Wireless, and enabled it againt, now the led is lit :)
But still not getting signals. What to do? :P

---

### Post by jeantea on 2009-10-11
Hah! Messing around in the user and groups settings. There was a little thing called "connect to wireless and ethernet networks" setting that wasn't activated.
Looks like my user isn't an administrator?
You know anything about this. 

Anyways! at the moment, i'm hooked up on my wlan! Thanks for all help! ^^

:guitar:

---

### Post by houstonbofh on 2009-10-11
Ha!  Too odd.  Hope you had fun tho...  The interesting problems are always the best at the end.

---

### Post by jeantea on 2009-10-11
Haha. Yeah. Had fun. And now it works so I am happy as well. Thank you for your patience. I think i like Ubuntu. And now i am installing some security updates. (those were the updates I installed before), but then my wlan didnt work. So I'm a little excited! Hehe. Wish me luck, and be prepared to hear more from me ;)

---

### Post by Bucky Ball on 2009-10-11
In System->Admin->Network click unlock and check the wireless properties. Are the settings in there the same as in your router (ESSID and security key, wep or wpa)?

Is the router serving an IP (DHCP server) or have you a static one setup? If you are getting served an IP the Configuration setting in there should be set to 'Auto-Configuration (DHCP)' and enable roaming off.

---

### Post by jeantea on 2009-10-12
> **Bucky Ball said:**
> In System->Admin->Network click unlock and check the wireless properties. Are the settings in there the same as in your router (ESSID and security key, wep or wpa)?

Is the router serving an IP (DHCP server) or have you a static one setup? If you are getting served an IP the Configuration setting in there should be set to 'Auto-Configuration (DHCP)' and enable roaming off.
I get served an ip automatic, for all my devices except one i think :)
Its been working like a charm for some hours now. I can even communicate with my win2003server. :) Ubuntu FTW! ^^

---

### Post by houstonbofh on 2009-10-12
Looks like we got another one hooked. :D

---

### Post by jeantea on 2009-10-12
> **houstonbofh said:**
> Looks like we got another one hooked. :D

hehe. guess so. Tried to get dual screen with Ubuntu. And it of course failed!
Loginscreen glitched, and nothing worked.
Fixed it with the revocery "terminal" (if you know what i'm talking about) and found the proper code to uninstall it :) Will probably, look for some more detailed info, or even post one more thread for research :)

---

### Post by Bucky Ball on 2009-10-12
Dual screen is definitely do-able but needs a bit of tweaking. You learn as you go. 

Welcome, good news about the wireless and good luck with it all. If you post about something else remember to create a new thread; you will have better chance of help with the correct title for your problem. You can always post a link to the new one here. :)

---

### Post by jeantea on 2009-10-13
> **Bucky Ball said:**
> Dual screen is definitely do-able but needs a bit of tweaking. You learn as you go. 

Welcome, good news about the wireless and good luck with it all. If you post about something else remember to create a new thread; you will have better chance of help with the correct title for your problem. You can always post a link to the new one here. :)

Hehe. Thx for all help, and thx for Welcome.  I posted a new one. I want to know what i got to do to run wow. I think maybe my wine is broken.

Follow @ [http://ubuntuforums.org/showthread.php?t=1289422](http://ubuntuforums.org/showthread.php?t=1289422)

When we talk about broken. I think my printer is messed up. Nothing works. Not Ubuntu, Windows 2003 server 64bit or windows xp 32bit. -_- *cry*

---

### Post by Bucky Ball on 2009-10-13
What are you using wine for?

---

### Post by jeantea on 2009-10-14
I was thinking about playing WoW.
But i think i need a "backup" os, so i'll install win7 on my other harddrive. ^ ^

---

