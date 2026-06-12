---
title: "How can my monitor's HDMI-DVI cable interfere with the wireless network??"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by parsim on 2008-12-28
This sounds crazy, but my monitor cable is causing my wireless network card to crap out.

I had no network problems, until I bought a new HDMI cable plus HDMI-DVI adapter for my monitor. Immediately my wireless card began dropping out, running very slow, and throwing error messages into the log. I have finally figured out that it's the monitor cable: if I switch back to a regular DVI cable, everything works fine again. I don't even need to reboot. 

I have a Netgear wireless card which lspci reports as "Texas Instruments ACX 111 54Mbps Wireless Interface". It uses the 'acx' module. My video card is an nVidia GeForce 8600GT and I use the 'nvidia' driver.

Here's my ping with the DVI cable connected:

```
$ ping router
PING router (192.168.0.1) 56(84) bytes of data.
64 bytes from router (192.168.0.1): icmp_seq=1 ttl=64 time=1.48 ms
64 bytes from router (192.168.0.1): icmp_seq=3 ttl=64 time=1.85 ms
64 bytes from router (192.168.0.1): icmp_seq=4 ttl=64 time=1.61 ms
```

Then I switch to the HDMI cable + HDMI-DVI adapter, being very careful not to touch or jolt anything else:
```
$ ping router
PING router (192.168.0.1) 56(84) bytes of data.
64 bytes from router (192.168.0.1): icmp_seq=1 ttl=64 time=777 ms
64 bytes from router (192.168.0.1): icmp_seq=2 ttl=64 time=23.3 ms
64 bytes from router (192.168.0.1): icmp_seq=4 ttl=64 time=4.76 ms
...
64 bytes from router (192.168.0.1): icmp_seq=21 ttl=64 time=9670 ms
64 bytes from router (192.168.0.1): icmp_seq=22 ttl=64 time=13892 ms
64 bytes from router (192.168.0.1): icmp_seq=23 ttl=64 time=13246 ms
--- router ping statistics ---
282 packets transmitted, 50 received, +113 errors, 82% packet loss, time 289517ms
```

I also see lots of errors in the system log like:
```
[ 1475.702045] wlan0: tx error 0x20, buf 05! (excessive Tx retries due to either distance too high or unable to Tx or Tx frame error - try changing 'iwconfig txpower XXX' or 'sens'itivity or 'retry')
[ 1475.702053] wlan0: several excessive Tx retry errors occurred, attempting to recalibrate radio. Radio drift might be caused by increasing card temperature, please check the card before it's too late!
[ 1475.702056] disabling above message
[ 1475.702060] wlan0: tx error 0x20, buf 06! (excessive Tx retries due to either distance too high or unable to Tx or Tx frame error - try changing 'iwconfig txpower XXX' or 'sens'itivity or 'retry')
[ 1475.702309] wlan0: less than 5 minutes since last radio recalibration, not recalibrating (maybe card is too hot?)
[ 1478.923515] wlan0: tx error 0x20, buf 07!
[ 1478.923526] wlan0: tx error 0x20, buf 08!
[ 1478.923533] wlan0: tx error 0x20, buf 09!
[ 1478.923542] wlan0: tx error 0x20, buf 10!
[ 1478.923809] wlan0: less than 5 minutes since last radio recalibration, not recalibrating (maybe card is too hot?)
[ 1478.923814] disabling above message until next recalib
[ 1482.695648] wlan0: tx error 0x20, buf 11!
[ 1482.695658] wlan0: tx error 0x20, buf 12!
[ 1482.695666] wlan0: tx error 0x20, buf 13!
```
It seems extraordinary that a monitor cable (or adapter) could throw out my wireless, but I'm sure it's doing it. Has anybody heard of anything like this?

---

### Post by laceration on 2008-12-29
That is weird.  I am no expert the system messages and wireless, but as I understand it the video connections from hdmi to dvi are the exact same.  It is just different plugs on each end.  This makes me think that perhaps you either have a defective cable that is shorting out and somehow doing this strange stuff or the HDMI jack was not hooked up right.  Unless someone with more authoritative knowledge shows up here to answer you, I would try returning that cable and trying another...and I would go with another brand!  If its the jack you'd have to swap out the card.

---

### Post by parsim on 2008-12-31
Well, this is my oddest computer fix yet... I wrapped the HDMI cable and adapter in aluminum foil.

I tested it carefully, watching my System Monitor -> Network History as I unwrapped and rewrapped the al foil. It was clear cause and effect: network performance fell away to nothing as I unwrapped the al foil, and returned as I re-wrapped it.

I will see what my cable store has to say about this. :)

---

### Post by Magellan on 2009-01-02
> **parsim said:**
> Well, this is my oddest computer fix yet... I wrapped the HDMI cable and adapter in aluminum foil.

I tested it carefully, watching my System Monitor -> Network History as I unwrapped and rewrapped the al foil. It was clear cause and effect: network performance fell away to nothing as I unwrapped the al foil, and returned as I re-wrapped it.

I will see what my cable store has to say about this. :)

Sounds like a low quality cable to me.  Not enough shielding.
I would guess that the cable runs pretty close to your wireless antennae and the signal bleeding out of the cable is causing noise in the wireless network.

---

