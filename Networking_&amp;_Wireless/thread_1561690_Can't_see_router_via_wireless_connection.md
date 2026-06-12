---
title: "Can't see router via wireless connection"
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by GaryReggae on 2010-08-26
I am having problems connecting to my new router. It just does not appear in the list of connections under Network Manager. It is not a problem with my laptop's wireless adapter as I can connect to another wireless router. It is also not a problem with the router itself - my Nintendo Wii can pick it up over Wi-Fi and use it and that is further away from the router. It also works if I ethernet it straight into the laptop.

The router was provided by Sky Broadband and is a D-Link, pretty standard type of ADSL router with four ethernet ports, wireless and telephone cable socket. I am using the default settings for the SSID and network key, as well as the encryption type (WPA).

I have tried using 'Add hidden wireless network' but that doesn't work and the router is not hidden anyway.

If I do iwconfig I get:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"GAZ"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ppp0      no wireless extensions.

Any ideas? Ubuntu version = 10.04. The wireless adapter is a very standard issue onboard Intel device but as I say, I can connect to my old Belkin wireless router no problem.

Thanks,

Gary

---

### Post by Lucretius on 2010-08-26
try changing your router channel

---

