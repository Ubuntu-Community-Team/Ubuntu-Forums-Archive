---
title: "My Wi-Fi Network Doesn't Appear But Others Do"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by DarkRage4 on 2010-06-07
My home wi-fi network doesn't appear on my wireless list but other networks like my neighbors for example do. My network did appear on Windows. The thing I don't understand is if my Wi-Fi adapter didn't work on linux, then why does my neighbors come up? 

Is there a way to get my network?

I'm using TRENDnet TEW-624UB

---

### Post by 5BallJuggler on 2010-06-07
I had the same problem on a new lucid install.

The problem was down to the channel number. the area in which I live is quite congested with Wi-Fi traffic, as a result I was using channel 13 on my router as it was clear and unlikely to be used.

the upshot was that lucid did not detect it, I had to lower the channel number to less than 10 for my system to be able to see it.

Hope this helps

Phil

---

### Post by DarkRage4 on 2010-06-07
How would you change the router channel? I checked my router settings, and theres 2 for channel (wide channel and standard channel) but both of them only have one option which is auto

---

### Post by DarkRage4 on 2010-06-08
Any ideas?

---

### Post by jnorthr on 2010-06-08
what is the make and model of your router ? did it ever work before ? you may be seeing ur neighbors system cos it has a stronger signal. Is your router close to the actual wifi adapter or in another room ? sometimes if ur router is working on a small power output it's signal may not reach ur kit especially if there are walls, iron bars, electric cables, etc in the way.

Do you have security wep/wap enabled on ur router ? the standard suggestion is to turn off security initially until you can gain a connection.

which ubuntu version r u using ? older versions may not act the same way as newer versions.

if you can get to a terminal command panel, you can try the '[COLOR="purple"]ifconfig[/COLOR]' command to identify known comms adapters on ur system. Mine shows 'eth0' 'lo' and 'wlan0' as the available adapters. ur's might or not have the same. The wlan0 or similar adapter is for wireless activity.

The [COLOR="Purple"]iwlist[/COLOR] command can give u details of whats currently working/or not.
[COLOR="purple"]iwlist wlan0 channel [/COLOR] would show ur current channel and freq.
[COLOR="purple"]iwlist wlan0 scanning [/COLOR]    will show a bunch of stuff.
8-[

---

### Post by DarkRage4 on 2010-06-08
> **jnorthr said:**
> what is the make and model of your router ? did it ever work before ? you may be seeing ur neighbors system cos it has a stronger signal. Is your router close to the actual wifi adapter or in another room ? sometimes if ur router is working on a small power output it's signal may not reach ur kit especially if there are walls, iron bars, electric cables, etc in the way.

Do you have security wep/wap enabled on ur router ? the standard suggestion is to turn off security initially until you can gain a connection.

which ubuntu version r u using ? older versions may not act the same way as newer versions.

if you can get to a terminal command panel, you can try the '[COLOR=purple]ifconfig[/COLOR]' command to identify known comms adapters on ur system. Mine shows 'eth0' 'lo' and 'wlan0' as the available adapters. ur's might or not have the same. The wlan0 or similar adapter is for wireless activity.

The [COLOR=Purple]iwlist[/COLOR] command can give u details of whats currently working/or not.
[COLOR=purple]iwlist wlan0 channel [/COLOR] would show ur current channel and freq.
[COLOR=purple]iwlist wlan0 scanning [/COLOR]    will show a bunch of stuff.
8-[

My router make is linksys and the model is WRT300N with firmware version 1.1. Yes my router has WPA security but for both the interferences and security shouldn't be part in this since it works without a problem on windows and my wi-fi is upstairs, not very far.

I'm using Ubuntu 10.04 (as it says in my user stat post profile - box to the left).

When I type 'ifconfig' I see 'eth0', 'lo', and 'wlan0' just like you.

When I type 'iwlist' I see about approx. 15 lines come up displaying the devices but it doesn't say what is and what is not working, it just says [interface] in front of all of them

When I type 'iwlist wlan0 channel' 14 channels come up with freqs all in 2.4x GHz

And when I type 'iwlist wlan0 scanning' it says 'No scan results'

---

### Post by DarkRage4 on 2010-06-08
bump

---

### Post by DarkRage4 on 2010-06-09
Still nothing has worked :( Any more suggestions

---

