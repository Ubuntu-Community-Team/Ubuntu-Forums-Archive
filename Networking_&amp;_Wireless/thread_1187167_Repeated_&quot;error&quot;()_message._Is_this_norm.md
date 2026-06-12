---
title: "Repeated &quot;error&quot;(?) message. Is this normal?"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by IainPurdie on 2009-06-14
I'm running 9.04 on an Acer TravelMate 2410 with the Broadcom wireless adapter. To a certain extent things are fine (mainly VGA problems, not relevant to this issue), but I have an intermittent problem where my hard drive goes beserk and effectively locks my system up.

The only way out is a hard reset, which is not ideal with files open, etc. I've lost count of the number of hard drive scans I've had to run on the shared FAT32 partition. I digress.

On checking my /var/log/syslog I am seeing a very large number of appearances for the following lines:

```
Jun 14 14:03:15 iain-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake 
Jun 14 14:03:15 iain-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Jun 14 14:03:46 iain-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake 
Jun 14 14:03:46 iain-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Jun 14 14:04:17 iain-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake 
Jun 14 14:04:17 iain-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Jun 14 14:04:48 iain-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake
```

Yes, that's two every thirty seconds or so: one "completed -> group handshake" and one "group handshake -> completed".

Wireless performance seems fine, I disconnect rarely (and when I do, my other laptop does as well which points to router issues and not PC ones). The only other time it drops is when the hard drive goes into overdrive, but only after a few minutes. I assume more to do with the system going doo-lally than anything else.

Is there a reason for the messages listed? Is it possible that it's somehow causing the problems I'm experiencing? Any help hugely appreciated as I'm getting sick of hard rebooting several times a day - and then having to run disc scans.

---

### Post by Kevbert on 2009-06-14
What sort of signal strength/quality are you getting on wireless ?
Please post back the terminal output of
```
iwconfig
```

---

### Post by irv on 2009-06-14
> I've lost count of the number of hard drive scans I've had to run on the shared FAT32 partition. I digress.
Can you clarify what you mean? It sounds like you don't have a very clean install. Why are you sharing a Fat32 partition. Any time I install Ubuntu I use ext3 or with 9.04 I use ext4 partition, it boots and run much faster. How big a HD do you have? If you answer these questions maybe someone can help with the errors you are getting.

---

### Post by IainPurdie on 2009-06-14
Signal strength is 2-3 bars where I am now, 4 bars (I'm 2m away from the router) at my girlfriend's flat. Both routers are different makes/models and the problem occurs no matter whether I'm here or there so it's definitely not router-related.

iwconfig output:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"BobWiFi"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1D:0F:EE:8B:3E   
          Bit Rate=54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:42/100  Signal level:-69 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by IainPurdie on 2009-06-14
> **irv said:**
> Can you clarify what you mean? It sounds like you don't have a very clean install. Why are you sharing a Fat32 partition. Any time I install Ubuntu I use ext3 or with 9.04 I use ext4 partition, it boots and run much faster. How big a HD do you have? If you answer these questions maybe someone can help with the errors you are getting.

Hey, Irv - sorry, as I said I was digressing. The FAT32 thing is a side-issue. I have XP, Windows7 and Ubuntu on my laptop so I use a shared FAT32 partition that all OS's can access. If I'm working on a file on there, or downloading a torrent to it when I have to hard reboot it causes obvious issues :(

My Ubuntu install is on EXT3 which generally doesn't even hiccup, but as EXT3 isn't accessible by Windows it's no use for file storage.

---

### Post by Kevbert on 2009-06-15
The signal quality that you posted seems a little low. Are you seeing many other wireless network at both locations ? It may be that you need to change the wireless channel of the router in both cases as it may be interference from other networks on the same channel as most people just use the default which the router is set to.

---

### Post by IainPurdie on 2009-06-15
I'll give it a try, but I honestly doubt that's the issue. At my parents' (the one with the lower signal), there are one or two other networks that occassionally appear - usually with a strength of barely one bar. At my girlfriend's (where I am now), there is just the one and I'm on it now - connection 4 bars and details below:

```
wlan0     IEEE 802.11g  ESSID:"Leah"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:65:D4:4A   
          Bit Rate=54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:79/100  Signal level:-45 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I'm sat close enough to the router I can touch it!

Also, do note that I'm having no perceived issues performancewise. Everything's fast, my connection's not going up and down. Nothing on the screen is telling me there's an issue. It's purely my syslog becoming bogged down in these "errors" or "notifications".

---

### Post by Kevbert on 2009-06-15
I've just checked my Jaunty logs and only get the messages you've reported a couple of times in a single session. It may just be that this message is a red herring...
What's the model of Broadcom card ? You can get this via
```
lspci | grep Network
```
I've just found [this]("https://bugzilla.redhat.com/show_bug.cgi?id=481033") which may give some clues.

---

### Post by IainPurdie on 2009-06-15
The card is a "06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)" which I believe was never a "favourite" of Ubuntu until recently. Performance, however, is fine.

You're right, it may be a red herring. While unconnected to a network last night, the hard drive dump/spin/mentality/whatever occurred again - and that is my main issue. It would be nice to find out why I'm getting loads of these "errors", but it seems they're really of no consequence other than filling up my log.

Hey ho. Thank you for your help, though! I'll keep poking around to try and resolve my main issue.

---

