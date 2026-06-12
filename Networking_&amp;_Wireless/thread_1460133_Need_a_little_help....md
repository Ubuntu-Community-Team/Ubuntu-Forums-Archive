---
title: "Need a little help..."
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by Edge-1337 on 2010-04-22
I'm COMPLETELY new to Linux, and just upgraded from Windows Vista Home Premium 32Bit.

When I was on Vista my Atheros AR5001 worked just fine, and the WiFi Button (physically built on the Compaq Presario C700) worked just fine. When I upgraded to Ubuntu 9.10 both stopped working.

I've tried searching but to no avail. I was able to find through the terminal (through a command I cannot remember) that my card is hard blocked. I've tried the switch and the LED will not turn blue (blue means on, amber means off).

Linux can detect that my WiFi card is there and that it's working properly, it just says it's turned off. SO how do I fix this?

---

### Post by bkratz on 2010-04-22
> **Edge-1337 said:**
> I'm COMPLETELY new to Linux, and just upgraded from Windows Vista Home Premium 32Bit.

When I was on Vista my Atheros AR5001 worked just fine, and the WiFi Button (physically built on the Compaq Presario C700) worked just fine. When I upgraded to Ubuntu 9.10 both stopped working.

I've tried searching but to no avail. I was able to find through the terminal (through a command I cannot remember) that my card is hard blocked. I've tried the switch and the LED will not turn blue (blue means on, amber means off).

Linux can detect that my WiFi card is there and that it's working properly, it just says it's turned off. SO how do I fix this?

The command you are talking about is

rfkill list

It may not help, but worth trying 


sudo rfkill unblock all
rfkill list

The sudo command will require your password which will not be echoed to you, just press enter when done

---

