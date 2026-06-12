---
title: "Wireless works / doesn't work"
date: 2006-02-21
forum: Networking &amp; Wireless
---

### Post by irw on 2006-02-21
I have spent hours on the fora, fiddling with my laptop, and still cannot solve this problem:

I have an old Gateway Solo 2500 with a fresh install of Breezy on it. I can connect to the wireless network at work with no problems at all via a netgear USB WG111v2 thingy.

At home, I have a Netgear DG834G wireless router.  With a friends laptop (running windows) I can connect wirelessly easily. With my laptop, I can not connect at all. It makes no difference whether I am in the same room or not.

GTKWifi and wifi-radar both can detect the home wireless signal, but when I try to connect, I often get the first saying there is 0% signal and the second a good signal.  However, it does not matter what I do, I cannot connect to the router/internet.

Trying to ping the router gets a network unreachable error.

Help!  Does anyone have any ideas what may be going on here?

Ian.

---

### Post by Lambert on 2006-02-21
Post the out put of these commands

sudo iwlist wlan0 scan

sudo iwconfig wlan0


replace wlan0 with the devices interface if different.

Also what kind of network settings are you using? open or encrypted? If encrypted wep or wpa? if wep open or shared key? hex or ascii key format?

---

### Post by irw on 2006-02-21
I have just re-installed breezy, so the following is done from home without having accessed the work network - I tried to use Automatix today (at work) and it wrecked my installation!

sudo iwlist wlan0 scan:
```
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:B5:C1:6C:4E
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-50 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:22 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
```

sudo iwconfig wlan0:
```
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:2346 B   Fragment thr:2400 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-50 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

There is an ESSID set for the connection. It has detected the correct channel (6) - although changing this has had no effect. The router and reciever are about two feet apart with nothing in between to weaken the signal. At work there are 4 walls and several feet of paper filing between the router and laptop with 100% signal strength!

> Also what kind of network settings are you using? 
 - open at home for now - I decided to try to limit the number of problems for now; once up & running I plan to use WEP/WPA.  At work, I am encrypted with WEP - a hex key.  What is an open or shared WEP key?

---

### Post by Lambert on 2006-02-21
Try running this command and then see if you can at least associate with the router. Instead of all zeros for access point you should see the mac of the router.

```
sudo iwconfig wlan0 rts off frag off freq 2.437G ap 00:0F:B5:C1:6C:43 commit
```

You can also add a section to the command including the essid

essid ________

---

### Post by irw on 2006-02-22
Thanks Lambert.

I tried ```
sudo iwconfig wlan0 rts off frag off freq 2.437G ap 00:0F:B5:C1:6C:4D commit
```

Unfortunately I get an error with this:
```
Error for wireless request "Set RTS Threshold" (8B22) :
     SET failed on device wlan0 ; no such device
```

If I remove the rts part, then I get error:
```
Error for wireless request "Set Fragmentation Threshold" (8B24) :
     SET failed on device wlan0 ; no such device
```

If I then remove the frag part as well, I get no response at all, and no change to my connection

Thank you for your help so far - any other suggestions?

---

### Post by atomicmoose on 2006-02-22
I had a similar connecttion problem with my NetGear router. It would get signal strength yet fail on DHCP. Changing to a shared WEP Key and using Hex instead of ACSII seems to have fixed the issue.

---

### Post by irw on 2006-03-06
Problem Solved!  But I have no idea how or why ...

I emailed Netgear who advised all that I had already tried (except they insisted on Windows instructions, even though I had specified Linux). The only difference was that they also suggested turning off any nearby cordless phone.

I turned off all security and turned off the phone: Windows was able to connect to the router, but not the internet, but Linux did both immediately.  I then turned on security (hide ESSID, WEP, specified MAC ony) and turned the phone back on.

It continues to work perfectly.:)  As I said, I did nothing different to before except turn the phone off. It has been back on since and has not moved, so I have no idea what was going on!

---

### Post by atomicmoose on 2006-03-15
I have 2.4GHz phones in my home and usually have no interference problems unless they are on.

I am glad you found the fix to your problem.\\:D/

---

