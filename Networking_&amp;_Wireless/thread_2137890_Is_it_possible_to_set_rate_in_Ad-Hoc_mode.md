---
title: "Is it possible to set rate in Ad-Hoc mode?"
date: 2013-04-22
forum: Networking &amp; Wireless
---

### Post by GarEngLLC on 2013-04-22
I am trying to run a test and I want to set the data-rate on my laptop that is setup for Ad-Hoc mode.  If I run ```
iwlist wlan0 bitrate
``` I get a > wlan0    unknown bit-rate information.  response.  

Undeterred, I then ran ```
sudo iwconfig wlan0 rate 11M
``` to attempt to lock the data rate to 11Mbps, but it doesn't not respond (just returns to the command prompt, no acknowledgement, and no errors).

My question is, is it possible to do this on Lucid Lynx?

I found a post on another forum from back in 2008 that someone was having a similar problem, ion the end they said:
> [COLOR=#000000][FONT=Verdana]I got the answers on my questions on bugzilla. [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Not displayed rate is not a problem of the driver: mac80211 does not display [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]rate for ad-hoc network. Also I can't obviously increase rate with command [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]'iwconfig wlan0 rate 54M' it must increases automaticaly after applying some [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]patches that I need to find on bugzilla.[/FONT][/COLOR]
But they didn't post any links or followups, so I have no idea if they got it to work.

Anyone know what I need to do to set/lock the rate?  TIA!

---

