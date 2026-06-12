---
title: "dell mini 9 won't discover networks?"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by platinumlolita on 2009-06-26
I have a dell mini 9. Every time I want to connect to a Wi-fi network, I need to borrow mum's iPod Touch or somebody's laptop to get the SSID of the current network and type it into my mini 9. This is because I can't get my mini 9 to look for all of the networks it can connect to.

It won't discover ANY network. Once I get the SSID, it works just fine, but obtaining it can be annoying.

Is there a utility that works with hardy (gnome or kde, it doesn't matter) to scan and discover networks?

If there is no utility and my laptop simply lacks a wireless card that can scan, is there a cheap USB tool that will do that? I don't mind if the USB tool is a/b/g, I just need it to get the SSIDs of networks. And when I say cheap, I mean up to fifteen dollars. Something flash drive shaped, like a linksys adapter or something off of ebay or amazon.

Thanks in advance, Ubuntu nerds!

---

### Post by platinumlolita on 2009-06-26
did I offend people or something? Just a simple question...

---

### Post by superprash2003 on 2009-06-27
post output of **sudo iwlist scanning**

---

### Post by platinumlolita on 2009-06-27
> **superprash2003 said:**
> post output of **sudo iwlist scanning**

here's my results:
chris@chris-laptop:~$ sudo iwlist scanning
[sudo] password for chris: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1F:F3:C2:45:25
                    ESSID:"HOME"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-52 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

pan0      Interface doesn't support scanning.

chris@chris-laptop:~$ 

so how does that look?
I suppose I need a USB thingamabob that supports scanning... Any suggestions for a cheap one? A/B/G/N it doesn't matter.

---

### Post by platinumlolita on 2009-06-27
or umm... Did that output just list them all or did it list the one I'm connected to?

---

### Post by snowpine on 2009-06-27
Maybe give wicd a try? I find it to be a little more full-featured than network manager. [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

The mini 9's wireless card is capable of scanning. You shouldn't need a new card.

---

### Post by philcamlin on 2009-06-27
your outputshows that it can scan but when you go to the network tab it doesnt show any networks?

---

### Post by superprash2003 on 2009-06-30
that command lists the output of all wifi networks around

---

### Post by platinumlolita on 2009-07-01
Awesome. I'll use that command next time at starbucks. Anyone recommend a good GUI for it or something? I can't seem to find a decent one... GTK would be nice, but I can suffer with KDE.

I mean, what's the best, fastest, simplest utility? I hate extra steps.

I will try the ones recommended here.

---

### Post by platinumlolita on 2009-07-01
Ok I have wicd installed via Synaptic pkg mgr (it had to ditch the default manager).
It's nice. Just one problem, though. There's no system tray icon. I'd like a tray icon. Is there another application that does that? Or should I just put a launcher for wicd next to my notification area? I have that done now. It sits between Exaile control and system volume...

If no, then thank you all so much for your help. This solves my tedious borrowing mess.

YAY!

---

