---
title: "aireplay-ng help (sucessful test)"
date: 2009-10-22
forum: Networking &amp; Wireless
---

### Post by MFontana on 2009-10-22
When I type

 "root@null:~# aireplay-ng -1 0 -e Kee Network -b 00:23:69:96:4B:CD -h 00:C0:A8:B5:0F:AB mon0
"aireplay-ng --help" for help.
root@null:~# "

It says ask for help. Why?? 


root@null:~# airmon-ng start wlan0


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!
-e 
PID    Name
2535    NetworkManager
2539    wpa_supplicant
2579    avahi-daemon
2580    avahi-daemon
5765    dhclient
Process with PID 5765 (dhclient) is running on interface wlan0


Interface    Chipset        Driver

wlan0        RTL8180/RTL8185    rtl8180 - [phy0]
                (monitor mode enabled on mon0)

root@null:~# aireplay-ng --test mon0
15:54:40  Trying broadcast probe requests...
15:54:40  Injection is working!
15:54:42  Found 1 AP 

15:54:42  Trying directed probe requests...
15:54:42  00:23:69:96:4B:CD - channel: 6 - 'Kee Network'
15:54:46  Ping (min/avg/max): 1.446ms/128.377ms/166.860ms Power: 0.00
15:54:46  30/30: 100%

root@null:~# aireplay-ng -1 0 -e Kee Network -b 00:23:69:96:4B:CD -h 00:C0:A8:B5:0F:AB mon0
"aireplay-ng --help" for help.
root@null:~#

---

### Post by MFontana on 2009-10-22
Bump

---

### Post by MFontana on 2009-10-22
bump

---

### Post by Kraust on 2009-10-22
For one, I'd suggest using BackTrack, because I have only ever had any success with Aircrack when it's with BackTrack. It's a Live CD, so you don't need to install / partition anything.

Also, you're using both wlan0 and mon0, I've only ever had to use wlan0 (or in BackTrack's case I'd use eth0)

Also you don't beed to use -e if you use -b (As -e is the ESSID and -b is the BSSID and only one is needed)

I'm thinknig the problem is that your ESSID has a space in it, so just omit the ESSID.

Just to give a few pointers:

First you want to do "airmon-ng start wlan0" to enter monitor mode and then you want to use airodump-ng to start collecting packets. I use something like "airodump-ng -c 6 -w wep --bssid (bssid here) wlan0" to collect the packets.

While you're doing that you want to Get Auth from the AP. I can't remember what aireplay that is exactly. I think it's the one you've mentioned. Once that's done you want to -3 or maybe -2 (honestly can't remember) to start getting IVs if that's what you want.

Basically that's it.

EDIT: As for your program suddenly not working, it's happened to me rarely. I'd guess that it would be because your Wireless Adapter is having issues with the driver. There might not be anything you can do to solve that.

---

### Post by MFontana on 2009-10-22
thats what i was thinkin, lemme try that

Edit: about the space

---

### Post by MFontana on 2009-10-22
root@null:~# aireplay-ng -1 0 -b 00:23:69:96:4B:CD -h 00:C0:A8:B5:0F:AB mon016:33:22
 Please specify at least a BSSID (-a) or an ESSID (-e)
root@null:~#

---

### Post by Kraust on 2009-10-22
Oh okay, I always mix -b and -a up.

Assuming that the -b given is the target bssid just enter:

"aireplay-ng -1 0 -a 00:23:69:96:4B:CD mon016:33:22"

If your interface is right that should work.

Some of the aireplay commands need a -a and some of them need a -b for the target. If you get that error just swap -a with -b.

---

### Post by MFontana on 2009-10-22
whats 16:33:22, accident??

---

### Post by Kraust on 2009-10-22
Just whatever your interface is, that's what your post reads to me?

---

### Post by MFontana on 2009-10-22
ah. you're a gentleman and a scholar. thankyou very much

root@null:~# aireplay-ng -1 0 -a 00:23:69:96:4B:CD mon0
No source MAC (-h) specified. Using the device MAC (00:C0:A8:B5:0F:AB)
16:43:54  Waiting for beacon frame (BSSID: 00:23:69:96:4B:CD) on channel 6

16:43:54  Sending Authentication Request (Open System) [ACK]
16:43:54  Authentication successful
16:43:54  Sending Association Request [ACK]
16:43:54  Association successful :-) (AID: 1)

---

### Post by calrogman on 2009-10-22
The only thing I can see wrong with your original command is that you need to place quotes around - or escape the space in - "Kee Network".

---

### Post by MFontana on 2009-10-22
correct about the quotes. tried it and original command worked. simple a55 sh1t always throwin a monkey wrench in it, if that makes any sense.

---

