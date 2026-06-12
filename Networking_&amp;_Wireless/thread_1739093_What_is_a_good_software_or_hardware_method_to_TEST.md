---
title: "What is a good software or hardware method to TEST WiFi strength &amp; power?"
date: 2011-04-25
forum: Networking &amp; Wireless
---

### Post by rocksockdoc on 2011-04-25
I bought a 2.4 GHz external USB WiFi 600mW radio with a 5dBi antenna for my Ubuntu 10.04 laptop but I don't seem to get any better signal strength with the external radio & antenna than with the internal - at least according to the Ubuntu default "Network Manager" signal-strength bars.

I now realize that default "Network Manager" doesn't have the signal strength reporting features that I would need, so may I ask:

[B]Q: What is a good software (or hardware) tool that will help compare how much better (or worse) any one external USB WiFi device is from another hooked to the same Ubuntu 10.04 laptop?

[/B]*Here is a Windows netstumbler result, for example - that I'm trying to get on Ubuntu 10.04 lucid:*[B]
[IMG]http://www.wi-fiplanet.com/img/2006/03/netstumbler_sm.gif[/IMG]
[/B]

---

### Post by rocksockdoc on 2011-04-27
Here is a typical view from the default Ubuntu "Network Manager" snapped today.

You need to scroll through dozens of SSIDs where you can't sort them, you can't arrange them by encryption, and most importantly, you can't sort them by quality of signal.

Certainly we can improve upon this with a recommended WiFi utility.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190172&stc=1&d=1303926559[/IMG]

---

### Post by rocksockdoc on 2011-04-27
> Certainly we can improve upon this with a recommended WiFi utility.

Doing a search, I find WiFi Radar mentioned, but, if that's the best we can do, we're in sad shape as it is not sortable, it provides lousy reception statistics, and, in the end, it's no improvement whatsoever upon that of the default Ubuntu WiFi manager.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190173&stc=1&d=1303926836[/IMG]

---

### Post by rocksockdoc on 2011-04-27
Further searching found [WireShark]("http://en.wikipedia.org/wiki/Wireshark") (and tshark) which I installed but haven't gotten to list any interfaces yet. 
- Applications -> Ubuntu Software Center -> kismet (seems to install the graphical wireshark)
- Applications -> Ubuntu Software Center -> tshark (command line tool)

EDIT: 
Debugging why WireShark won't show any interfaces, I am learning about:
- [**promiscuous mode**]("http://en.wikipedia.org/wiki/Promiscuous_mode") => forwards all traffic to the kernel but only after associating with an access point
-** [monitor mode]("http://en.wikipedia.org/wiki/Monitor_mode")** => monitors all wifi traffic w/o associating with an access point, aka rfmon
- [**pcap** ]("http://en.wikipedia.org/wiki/Pcap")(**p**acket **cap**ture) => an api for capturing network traffic

OK. I figured out why Wireshark wasn't running (I needed to start it as root):
- [Newbie question: Why won't Wireshark show any interfaces?]("http://ubuntuforums.org/showthread.php?t=1741115")

I'm looking at tutorials to see how it can show signal strength meters ... as it shows a lot ... just not what I'm looking for.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190400&stc=1&d=1304094773[/IMG]

---

### Post by josephmills on 2011-04-27
**if** your card is supported airodump-ng works all right.
to use aircrack-ng do well at least part of it 
```

airmon-ng stop wlan0

```
then 
```

airmon-ng start wlan0 

```
then 
you should be in monitor mode at this point if you do a 
```

airmon-ng 

```
Are you in monitor mode? (mon0)
if so 
```

airodump-ng mon0

```
do you see all the networks do you see the power?

---

### Post by rocksockdoc on 2011-04-27
> **josephmills said:**
> if your card is supported airodump-ng works all right.

Googling for an Airodump next-generation tutorial, I find these which I'm reading as we speak:
- [Airodumpng Basics (Part I)]("http://www.securitytube.net/video/26")
- [airodump-ng(1) - Linux man page]("http://linux.die.net/man/1/airodump-ng")

But, I couldn't find an installer or a good step-by-step tutorial for airodump (most of the beginner tutorials I found seem to be associated with something called "aircrack"). 
- [Aircrack-ng Newbie Guide for Linux]("http://www.aircrack-ng.org/doku.php?id=newbie_guide")

Is the airodump installer the same as the aircrack installer?

EDIT: Never mind. I see from further googling that to get airodump I need to install [aircrack]("http://en.wikipedia.org/wiki/Aircrack-ng"):
- [How do you install airodump on Ubuntu?]("http://ubuntuforums.org/showthread.php?t=870273")  (Answer: sudo apt-get install aircrack-ng)

And, I see the updated post which shows the multi-step command to get airodump to work:
```

$ sudo airmon-ng stop wlan0;sudo airmon-ng start wlan0;sudo airmon-ng;sudo airodump-ng mon0

```

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190401&stc=1&d=1304094912[/IMG]

---

### Post by josephmills on 2011-04-27
it is not live but ```
nm-tool
``` also works (if you have network manager )

---

### Post by rocksockdoc on 2011-04-29
> **josephmills said:**
> nm-tool

That's a great way to get a static summary of the signal strength of the access points in range!
```

$ /usr/bin/nm-tool | grep Strength
...
Linksys: Infra, 00:28:F4:B8:9A:A4, Freq 2412 MHz, Rate 54 Mb/s, **[COLOR=DarkRed]Strength 30[/COLOR]** WPA WPA2
George: Infra, 00:A0:00:55:1D:CB, Freq 2457 MHz, Rate 11 Mb/s,**[COLOR=DarkRed] Strength 78[/COLOR]**
[COLOR=DarkRed]*****[/COLOR]WISP_AP: Infra, 00:A0:00:64:7F:96, Freq 2457 MHz, Rate 11 Mb/s, [COLOR=DarkRed]**Strength 77**[/COLOR]
PublicLib: Infra, 00:A0:00:63:E8:DE, Freq 2422 MHz, Rate 11 Mb/s, **[COLOR=DarkRed]Strength 37[/COLOR]**

```I'm not sure what the numbers actually mean (presumably that's in percentages) as "nm-tool -help" doesn't do anything useful ... but this is a great start!

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190402&stc=1&d=1304094996[/IMG]

---

### Post by rocksockdoc on 2011-04-29
> **josephmills said:**
> do you see all the networks do you see the power?

I do!

```

$ sudo airmon-ng stop wlan0
$ sudo airmon-ng start wlan0 
$ sudo airmon-ng 
$ sudo airodump-ng mon0
...

```Strangely, this command also seems to 'remember' old (no longer used) SSIDs (where I know the router to be not turned on). Very interesting. There's a history embedded in the results!

But, more importantly, since there are literally scores of wlan connections reported by airmon, I'm trying to get a handle on what the strength of the signals actually indicates. Instead of a number like -1, 23, -70, etc., I would have expected a signal to noise ratio (SNR) and/or a decibel (dBM) measurement, for example. Not an absolute number. 

[B][COLOR=DarkRed] Q1: What does, for example, -1 mean as opposed to 23 or -70?
Q2: Isn't there a graphical WiFi signal strength tool extant?
[/COLOR][/B]

---

### Post by rocksockdoc on 2011-04-29
In the hope of finding a better graphical wifi signal strength tool, I installed SWScanner (/usr/bin/swscanner).

It really doesn't show much more than the graphical network manager does by way of signal strength though.

So I'd say SWScanner is yet another (graphical) bust.

While the suggested text-output tools are fantastically powerful, I'm surprised Ubuntu users don't have a need for graphical signal strength utilities.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190422&stc=1&d=1304102268[/IMG]

---

### Post by josephmills on 2011-04-29
Q1: What does, for example, -1 mean as opposed to 23 or -70?
 
ok so -23 you would be close/good signal  and -70 would be farther away so you could test new drivers and hardware buy watching the power is it better or not? also that has something to do with the isp and wifi antenna.

---

### Post by rocksockdoc on 2011-04-30
> **josephmills said:**
>  -23 you would be close/good signal  and -70 would be farther away

Is that -23 decibels? Maybe -23 dBm? Or is it a percentage of -23%? Or is it simply a range from 1 to 10 (in this case, from 1 to -100)?

If it's a range, what are the range endpoints of 1 and -100 equivalent to?

And, what's with the -1?

---

