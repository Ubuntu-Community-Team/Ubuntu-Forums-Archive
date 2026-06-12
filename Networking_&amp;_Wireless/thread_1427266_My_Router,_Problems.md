---
title: "My Router, Problems"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by Psumi on 2010-03-11
Okay, so I just moved into my apartment in the first two weeks of february. After a few weeks of having Internet actually work; the router or my IBM's wireless card started having issues.

1. The IBM would not detect the wireless network. This would go on and off throughout the day on random days.

2. The router would periodically not connect with the modem (or the modem refused to broadcast to the router.

3. I found out that my wireless card was dying on my IBM because of these things.

4. Could my router, which I bought last year, be dying already? (It's a Linksys WRT320N.)

My cable modem is a Scientific Atlanta. However, as I have said, both the router, IBM, and modem have been working since I got them last year until I moved that is.

Should I worry about possible attackers too?

---

### Post by juancarlospaco on 2010-03-11
Wifi overlapping with other *(maybe non-visible)* Wifi networks.

Solution, you need to move away to other channel on your router, is common on apartments.
:)

---

### Post by Kevbert on 2010-03-11
when you connect via wireless please try the following in terminal
```
iwconfig
iwlist scanning

```
Please post back the response. It may be that either the signal quality is poor or that other networks are using the same wifi channels.

---

### Post by swoll1980 on 2010-03-11
I would say connect directly to the modem to rule that out, but that's probably not a good idea.

---

### Post by juancarlospaco on 2010-03-11
Your router is 802.11**N**, your IBM is...?

or buy a long wire :)

---

### Post by CharlesA on 2010-03-11
Doesn't matter what the wireless card is, since a wireless-N router will accept Wireless b, g and n, unless configured otherwise.

I am thinking that it is probably wireless interference. Have you tried scanning to see what channels are being used and if there is a lot of overlap?

---

### Post by Psumi on 2010-03-11
> **Kevbert said:**
> when you connect via wireless please try the following in terminal
```
iwconfig
iwlist scanning

```
Please post back the response. It may be that either the signal quality is poor or that other networks are using the same wifi channels.

I get these outputs...

iwconfig...

```
lo        no wireless extensions.

eth1      no wireless extensions.

irda0     no wireless extensions.

eth0      IEEE 802.11b  ESSID:"FurniVilet"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:23:69:85:3B:AE   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:FF40-D36B-C142-A116-6243-557C-4141-A960   Security mode:open
          Power Management:off
          Link Quality=99/100  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:4   Missed beacon:2
```

iwlist scanning:

```
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth0      Scan completed :
          Cell 01 - Address: 00:22:3F:9B:48:4D
                    ESSID:"Jaxson"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:31  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 216ms ago
          Cell 02 - Address: 00:1C:DF:F8:5D:D4
                    ESSID:"triathlete"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:39  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 92ms ago
          Cell 03 - Address: 00:13:10:7F:C8:1E
                    ESSID:"linksys wireless router"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:44  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 84ms ago
          Cell 04 - Address: 00:24:56:A5:68:59
                    ESSID:"2WIRE725"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:27  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 132ms ago
          Cell 05 - Address: 00:18:39:60:A3:21
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:35  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 68ms ago
          Cell 06 - Address: 00:25:56:1B:97:74
                    ESSID:"5070 Wireless"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:37  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 132ms ago
          Cell 07 - Address: 00:24:56:C6:3A:99
                    ESSID:"abc123"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality:29  Signal level:0  Noise level:0
                    Extra: Last beacon: 256ms ago
          Cell 08 - Address: 00:23:69:85:3B:AE
                    ESSID:"FurniVilet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:90  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 72ms ago
          Cell 09 - Address: 00:1F:B3:C1:32:49
                    ESSID:"Nomad"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:39  Signal level:0  Noise level:0
                    Extra: Last beacon: 232ms ago
```

Turning off TKIP on my router doesn't do anything.

Yes, there is A LOT of overlap on every channel. However, the router (when set to auto channel) sets it to 11, which is the worse channel.

---

### Post by CharlesA on 2010-03-11
When you say that channel 11 is worse, what do you mean? That it has more interference then the others?

---

### Post by Psumi on 2010-03-11
> **CharlesA said:**
> When you say that channel 11 is worse, what do you mean? That it has more interference then the others?

Channel 11 causes my IBM laptop to not detect the router at all, similarly, the PS3 has very bad connections to the router when in 11.

---

### Post by CharlesA on 2010-03-11
> **Psumi said:**
> Channel 11 causes my IBM laptop to not detect the router at all, similarly, the PS3 has very bad connections to the router when in 11.

Have you tried manually setting to a different channel: like channel 9 or 10?

---

### Post by Psumi on 2010-03-11
> **CharlesA said:**
> Have you tried manually setting to a different channel: like channel 9 or 10?

Right now I have it on 6, because it seems pretty stable.

---

### Post by KiwiNZ on 2010-03-11
This is a known issue with linksys wireless routers. I recently fixed this issue for a friend who was going nuts with his home network dropping out at random times during the day.

I turned wireless off on his router , went down to to the stores and purchased one of these [http://www.apple.com/airportexpress/](http://www.apple.com/airportexpress/)

Connected this to his router and all is well. If you know someone with one or say a D-link Access  point or similar you could try the same .

---

### Post by Kevbert on 2010-03-11
Signal quality and signal level seem fine. It doesn't look like changing channels will make all that much difference as [802.11b/g channels overlap]("http://en.wikipedia.org/wiki/IEEE_802.11") and your seeing quite a few other wifi networks.
Do you get any error messages in the dmesg log regarding your ipw2100 driver ?

---

### Post by juancarlospaco on 2010-03-11
[I]A lot of interference on Channel 6, and theres no 802.11N link being used,
check interference, microwave, wireless phone, inverters, and such.[/I]

One thing i dont understand is why are you using 802.11**B**, is better to use **G**,
since your AP support these, try to move to **G**, go from 10Mb/s to 54Mb/s,
maybe your IBM is too old and dont support **G**, 
get an USB WIFI G with SMA connector in that case.

Signal is almost perfect **99/100** at the moment of these iwconfig.
:)

---

### Post by Psumi on 2010-03-11
> **juancarlospaco said:**
> [I]A lot of interference on Channel 6, and theres no 802.11N link being used,
check interference, microwave, wireless phone, inverters, and such.[/I]

One thing i dont understand is why are you using 802.11**B**, is better to use **G**,
since your AP support these, try to move to **G**, go from 10Mb/s to 54Mb/s,
maybe your IBM is too old and dont support **G**, 
get an USB WIFI G with SMA connector in that case.

Signal is almost perfect **99/100** at the moment of these iwconfig.
:)

I'm saving up for a new computer in a couple years anyway, don't need one.

> **KiwiNZ said:**
> This is a known issue with linksys wireless routers. I recently fixed this issue for a friend who was going nuts with his home network dropping out at random times during the day.

I turned wireless off on his router , went down to to the stores and purchased one of these [http://www.apple.com/airportexpress/](http://www.apple.com/airportexpress/)

Connected this to his router and all is well. If you know someone with one or say a D-link Access  point or similar you could try the same .

I'm assuming that has linux drivers readily available, and doesn't require to be plugged in via USB ever? Even to setup?

I need G compatibility, which it has, for my PS3.

---

### Post by KiwiNZ on 2010-03-11
> **Psumi said:**
> I'm saving up for a new computer in a couple years anyway, don't need one.



I'm assuming that has linux drivers readily available, and doesn't require to be plugged in via USB ever? Even to setup?

I need G compatibility, which it has, for my PS3.

Its an Access point that connects to your Router via Lan Cable and you plug it into a power outlet near by .

Or use say a D- Link or similar access point  [http://www.dlink.com/products/?pid=326](http://www.dlink.com/products/?pid=326)

---

### Post by LowSky on 2010-03-11
your wasting money buying the apple thing. Your problem is your router's channel. Switch to any number of channels or have it set to scan. 

Also make sure your signal is password protected. If others are using your connection it could be knocking you off.

---

### Post by KiwiNZ on 2010-03-11
> **LowSky said:**
> your wasting money buying the apple thing. Your problem is your router's channel. Switch to any number of channels or have it set to scan. 

Also make sure your signal is password protected. If others are using your connection it could be knocking you off.

Its a known issue with Linksys Wireless Routers as I said earlier

---

### Post by Psumi on 2010-03-11
> **KiwiNZ said:**
> Its a known issue with Linksys Wireless Routers as I said earlier

But it only happened when I moved to a high-traffic wireless area? Seems like a channel problem.

---

### Post by LowSky on 2010-03-11
> **KiwiNZ said:**
> Its a known issue with Linksys Wireless Routers as I said earlier

Most likely solved with a firmware update. I just googled: "linksys dropping wireless connection" and all the links that appear first are from years ago, most say solved with channel change or firmware update

> **Psumi said:**
> But it only happened when I moved to a high-traffic wireless area? Seems like a channel problem.

Exactly why I think its a channel problem.

---

### Post by Psumi on 2010-03-11
> **LowSky said:**
> Most likely solved with a firmware update. I just googled: "linksys dropping wireless connection" and all the links that appear first are from years ago, most say solved with channel change or firmware update



Exactly why I think its a channel problem.

And I already have the latest firmware for my router: 1.0.03 (Build 010.)

---

### Post by overdrank on 2010-03-11
Moved to Networking & Wireless

---

### Post by pricetech on 2010-03-11
> **overdrank said:**
> Moved to Networking & Wireless

I should hope so.

OP:  Trying another channel won't cost you a dime, and yes, make sure you use security on your wireless.

If that doesn't work, then give the other ideas a try.

---

### Post by katie-xx on 2010-03-11
> **CharlesA said:**
> Doesn't matter what the wireless card is, since a wireless-N router will accept Wireless b, g and n, unless configured otherwise.
I am thinking that it is probably wireless interference. Have you tried scanning to see what channels are being used and if there is a lot of overlap?

My Thomson router wouldnt with 9.10.
I had to set the router to 802.11g ..or 802.11b ..one or the other ..not mix.

Kate

---

### Post by isee on 2010-03-11
> **swoll1980 said:**
> I would say connect directly to the modem to rule that out, but that's probably not a good idea.

Excuse me but I was reading this thread and would like to know why this is "probably not a good idea" as I have just unplugged my DLink and now have a direct DSL connection to my ISP's modem.

My concern is that I've lost my DLink firewall with this configuration.

---

### Post by Psumi on 2010-03-11
> **isee said:**
> Excuse me but I was reading this thread and would like to know why this is "probably not a good idea" as I have just unplugged my DLink and now have a direct DSL connection to my ISP's modem.

My concern is that I've lost my DLink firewall with this configuration.

Wouldn't be a good idea for me due to where my PS3 is.

Besides, my modem only has ONE ethernet port, so my laptop would have to be on ALL THE TIME to share its Internet (if I can broadcast my Internet like a mac on Linux.)

However, the wireless card on the laptop is dying anyway.

---

### Post by Psumi on 2010-03-11
Also, setting it to the least used channels (9 or 10) still drops it from my laptop.

---

