---
title: "Help a n00b"
date: 2006-06-18
forum: Networking &amp; Wireless
---

### Post by cesugden on 2006-06-18
Hello,

I'm new to linux, loving it more every day, however am really struggling trying to get my wireless adapter to work. I think am nearly there just with a couple of settings missing, I'd appreciate any help.
I have a WUSB54G wireless linksys usb adapter. Am using ubuntu Dapper Drake and ndiswrapper. The hardware seems to be installed...
"ndiswrapper -l"
Installed ndis drivers:
rt2500usb               driver present, hardware present

"iwconfig"
wlan0     IEEE 802.11g  ESSID:"SpeedTouch1C8236"
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and in system -> admin I have activated the wlan0 and it becomes active, I have also set up the correct settings for it here (the router, the wep key, DHCP assigning) yet I'm still not getting a connection to the router. The internet doesn't work and niether does my wireless routers homepage. Do I need to edit a file somewhere to input the correct settings for my adapter to connect?

Thank You
Chris

---

### Post by ????? on 2006-06-18
Have you tried modprobing ndiswrapper? ( sudo modprobe ndiswrapper )

---

### Post by cesugden on 2006-06-18
yep tried that, didn't work. #-o

---

### Post by flintflake on 2006-06-18
I'm right there with ya.   I have the same problem.   So close.... but not surfing.

---

### Post by stupidkid on 2006-06-18
Some times the wireless seems to be working but it's actually not (mine was like that). Run
```
iwlist wlan0 scan
```
and see if you pick up your network.

---

### Post by flintflake on 2006-06-19
I ran that and it said:

wlan0    no results

---

### Post by cesugden on 2006-06-19
I ran that command and it seems ok, the output was:

wlan0     Scan completed :
          Cell 01 - Address: 00:11:F5:A5:EF:D4
                    ESSID:"SpeedTouch1C8236"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-61 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

---

### Post by stults on 2006-06-20
TIP: you can check to see if you are connected to your network by using ping
     In the command line type 'ping 192.168.1.1' (replace 192.168.1.1 with your router address).  You can stop the ping with ctrl+c.  If you receive times in ms, then you are connected.  If you recieve 'Host unreachable', you are not connected

First try to disable your WEP encryption on the router and see if you can connect.  I can't get on my router with Dapper if WEP is enabled (i'm still working on that).  If WEP is your problem, you could try to go back to the earlier version of Ubuntu called Breezy Badger (5.10) as my wireless worked perfect with it.  Or you could keep trying and post how you figured it out (I could use the help). :-)

---

### Post by goodmaj on 2006-06-20
Does the pull down Administration --> Networking show your wireless card as wlan0?  If it does not (that is, it shows up as eth0 or eth1 etc.) then edit 
/etc/modeprobe.d/ndiswrapper/ so that the line 
alias wlan0 ndiswrapper matches what you saw above instead of wlan0.

---

### Post by stupidkid on 2006-06-20
[QUOTE=flintflake]I ran that and it said:

wlan0    no results[/QUOTE]
That means your card isn't working. Might be some driver problem.

@ cesugden.
Your card is installed fine, it might be the router's problem. e.g. not strong enough signal? I'm not really sure, I also use ndiswrapper in Ubuntu and it works perfectly. Try messing around with some config files. Actually post your /etc/network/interfaces (I believe that's the correct file name).

---

### Post by noname101 on 2006-06-20
What does lsmod say?

---

