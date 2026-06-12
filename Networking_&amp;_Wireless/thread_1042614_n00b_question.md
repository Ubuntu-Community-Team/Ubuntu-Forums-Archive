---
title: "n00b question"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by FiskFisk33 on 2009-01-17
On ubuntu server, how do i connect to a wireless network?

---

### Post by Mehall on 2009-01-17
type iwconfig to find out what the interface name is for your wireless card: probably wlan0 or ath0 (those are zeroes)

then, to scan for networks: (in all steps, replace wlan0 with the interfacce name you got from iwconfig)
```
iwlist wlan0 scan
```

then, to connect to a network:

```
sudo iwconfig wlan0 essid "Network-Name"
```

if it's WEP secured, then:

```
sudo iwconfig wlan0 essid "Network-Name" key HEXKEY
```

I can;t remember how to for WPA off the top of my head so if it's WPA secured, go google, or wait for someoen who DOES remember.

Oh, and once you've told it to connect:

```
sudo dhclient wlan0
```

---

### Post by Amanpreet on 2009-01-17
you should try right clicking on the area in the top right of your screen and click add to panel, then click network monitor, once it is there click on it and type in your network name

was this helpful, if not I have another way:)

---

### Post by Mehall on 2009-01-17
> **Amanpreet said:**
> you should try right clicking on the area in the top right of your screen and click add to panel, then click network monitor, once it is there click on it and type in your network name

was this helpful, if not I have another way:)



he said it was server, so no GUI

Oh, and the last step was wrong in my previous post here's what it should be:

```
sudo dhclient wlan0
```

*goes and edits original too*

---

### Post by FiskFisk33 on 2009-01-17
[QUOTE=Mehall;6568135

```
iwlist wlan0 scan
```

[/QUOTE]

it just says no scan results :(

i know for a fact theres several networks nearby, including the one i want to connect to, which is wep secured.
i am running 8.10 btw.


And it did work without problems on desktop version

---

### Post by Mehall on 2009-01-17
> **FiskFisk33 said:**
> it just says no scan results :(

i know for a fact theres several networks nearby, including the one i want to connect to, which is wep secured.
i am running 8.10 btw.

Are you sure your wireless card is working?

also:

```
sudo ifdown wlan0
sudo ifup wlan0
```

then try again.

or:

```
sudo /etc/init.d/networking restart
``` (might be "network" not "networking" i can't remember off the top of my head)

---

### Post by FiskFisk33 on 2009-01-17
it still just says

wlan0 No scan results

And it says it instantly when i press enter.


now i put sudo infront of the iwlist wlan0 scan and now it said "interface doesnt support scanning : network is dowm"

---

### Post by Mehall on 2009-01-17
> **FiskFisk33 said:**
> it still just says

wlan0 No scan results

And it says it instantly when i press enter.

give us a copy of what ifconfig and iwconfig say?

---

### Post by FiskFisk33 on 2009-01-17
> **Mehall said:**
> give us a copy of what ifconfig and iwconfig say?

```
ifconfig

lo	Link encap:Local Loopback
	inet addr:127.0.0.1 Mask:255.0.0.0
	UP LOOPBACK RUNNING MTU:16436 Metric:1
	RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:0
	RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)


iwconfig

lo	no wireless extensions.

eth0	no wireless extensions.

wmaster0	no wireless extensions.

wlan0	IEEE 802.11abg ESSID:""
	Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
	Tx-Power=0 dBm
	Retry min limit:7 RTS thr:off Fragment thr=2352 B
	Power Management:off
	Link Quality:0 Signal level:0 Noise level:0
	Rx nwid:0 Rx invalid crypt:0 Rx invalid frag:0
	Tx excessive retries:0 Invalid misc:0 Missed beacon:0

```

and as i edited in before, when i put sudo infront of the iwlist wlan0 scan it said "interface doesnt support scanning : network is dowm"

---

### Post by ugm6hr on 2009-01-17
Give the output from:
```
lshw -class network
```

---

### Post by albinootje on 2009-01-17
> **FiskFisk33 said:**
> 
and as i edited in before, when i put sudo infront of the iwlist wlan0 scan it said "interface doesnt support scanning : network is dowm"

Does 
```

sudo iwconfig wlan0 essid "any"
sudo iwlist scan

```
give the same result ?

---

### Post by FiskFisk33 on 2009-01-17
> **albinootje said:**
> Does 
```

sudo iwconfig wlan0 essid "any"
sudo iwlist scan

```
give the same result ?

yes

---

### Post by albinootje on 2009-01-17
> **FiskFisk33 said:**
> yes

Can you give the wifi card temporarily an ip address, and then try the scanning again ?
Some years ago I came across a wifi card which only wanted to "wake" up like that. A friend of mine found out.

---

### Post by FiskFisk33 on 2009-01-17
if i knew how to


... :P

---

### Post by albinootje on 2009-01-17
> **FiskFisk33 said:**
> if i knew how to


... :P

I'm not sure whether to apply this to wmaster0 or wlan0 ..
But try the following :
```

sudo ifconfig wmaster0 10.1.1.1 up
ifconfig -a
sudo iwlist scan

```
And :
```

sudo ifconfig wlan0 10.2.2.2 up
ifconfig -a
sudo iwlist scan

```

---

### Post by Mehall on 2009-01-17
> **FiskFisk33 said:**
> if i knew how to


... :P

If I'm right:

```
sudo iwconfig wlan0 192.168.0.82
```

(Picked because that was the last IP I got from a DHCP server =P)

---

### Post by FiskFisk33 on 2009-01-17
Awesome, now it scans, and finds the router.

Now it says the key is an invalid argument.

The router is set to 128 bit encryption in ASCII mode.
13 numbers and letters.

---

### Post by albinootje on 2009-01-17
> **Mehall said:**
> If I'm right:

```
sudo iwconfig wlan0 192.168.0.82
```

(Picked because that was the last IP I got from a DHCP server =P)

For your wired connection ?
Well, go ahead :)

The ip-address doesn't matter, it's only needed to "wake" up the wifi-card, if at all applicable to this situation..

---

### Post by FiskFisk33 on 2009-01-17
well it did wake it,

;)

---

### Post by albinootje on 2009-01-17
By the way, WEP is insecure, you should use WPA2 if you can.
I've also read that some people had problems connecting to WEP, whereas WPA or WPA2 worked fine.

One other option is to edit /etc/network/interfaces since you don't need scanning anyway.

See here :
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by Mehall on 2009-01-17
> **albinootje said:**
> By the way, WEP is insecure, you should use WPA2 if you can.
I've also read that some people had problems connecting to WEP, whereas WPA or WPA2 worked fine.

One other option is to edit /etc/network/interfaces since you don't need scanning anyway.

See here :
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

thats a good point. does anyone remember what the flag is for using a typed key, rather than a hex one?

---

### Post by FiskFisk33 on 2009-01-17
YES! it works!
THANKYOU!
i love this foruM!

i changed the key in the router, i wasnt at the mood to "wrestle another one" ;)

---

### Post by albinootje on 2009-01-17
> **FiskFisk33 said:**
> YES! it works!


Glad to see you have it working now! :)

---

