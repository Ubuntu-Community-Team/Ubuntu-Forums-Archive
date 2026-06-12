---
title: "[SOLVED] Can see networks but cannot connect"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by Azabith on 2008-12-07
I have just installed Ubuntu on my laptop - **Acer Aspire 5570z**. Everything worked fine except for the wireless network. I followed a few threads and installed the right driver using **ndiswrapper** and got the atheros driver for my laptop. I then installed **WICD** and finally got to see my router. The bad news was that i couldnt connect to the router. I am sure the user name and password are correct.

---

### Post by abhilashkumar on 2008-12-08
Try using the gnome network manager. If that doesnt work you should try using madwifi.

I have an Acer 4520 and with every break of the Wifi I have to try either madwifi or ndiswrapper. 

But... since your networks are showing up in wicd then maybe you shoud try resetting your router password.

---

### Post by bryonak on 2008-12-08
MadWifi has been declared legacy by it's developers.
You should use ath5k or ath9k (depends on your network card, but this should be done automatically) and set the wireless extension in WICD to "wext".

For example, just try loading ath9k with modprobe and unload the wlan, ndiswrapper, ath_pci and other wireless modules you may have loaded.

---

### Post by carml on 2008-12-08
Did you try manually setting up the configuration via System->Administration->network?

---

### Post by Azabith on 2008-12-08
I tried manually as well it didnt work 
I am running out of options at the moment I will remove ndiswrapper and install madwifi and try that with the network manager. I'll keep you posted

---

### Post by bryonak on 2008-12-08
Again: madwifi is deprecated.. or maybe you already tried the newer Atheros drivers and it didn't work?

WICD should be fine, since it has a more advanced network encryption support than the Gnome Network Manager (which in turn has nice functions like turning the card off completely, and integrated VPN, though the usage is more cumbersome than with a direct script in WICD).

Also note that you shouldn't have any entries in /etc/network/interfaces other than the one for the loopback adapter.

---

### Post by markg48 on 2008-12-08
madwifi should work fine i have atheros card and it works fine if u want an easy isntall i have the deb package if u need it

---

### Post by bryonak on 2008-12-08
Yep, of course it should work fine right now... the development has been stopped just this year, so most of the cards are still supported.
Besides, both MadWifi and the ath5k/ath9k are for Atheros cards only.

There is no need for installing debs, the new modules are included in Intrepid by default.

---

### Post by Azabith on 2008-12-08
I tried madwifi and it didnt work at all. So that brings me back to the starting point. ndiswrapper and wicd are back since they have brought me the closest to solving this issue. 

I did reset the password on my router and still nothing. 

I am still able to see routers but am not able to connect. 

```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
this is what i get when i run iwconfig 

when i try connecting with wicd the status it says 
"Putting interface down..." then gives tells me not connected almost immediately 

WPA supplicant driver is set at ndiswrapper

---

### Post by bryonak on 2008-12-08
@Azabith: Did you, for some reason, put me on ignore?
You don't have to use neither MadWifi nor ndiswrapper, but the new Atheros drivers: ath5k or ath9k

---

### Post by Azabith on 2008-12-08
Thanks all 
Everything is working perfectly now
I added the ath5 driver and got it running 
:)

---

