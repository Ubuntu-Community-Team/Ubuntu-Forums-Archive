---
title: "Strange signal strength problem with Intel 4965 WiFi"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by thefirstM on 2009-02-12
I recently upgraded the wireless card in my Dell Vostro 1500 laptop (which runs Kubuntu Jaunty x64) from the Intel 3945 to the Intel 4965. I am now having a strange problem connecting to the wireless network. At my computer's current location (around 30-35 feet from the router, through a few walls) the 3945 card would connect just fine and hold the connection. However, the new 4965 card will not connect unless the computer is within about 20ft from the router.  If I try to connect, I just get a long string of these in my dmesg:

[ 5171.880257] wlan0: disassociating by local choice (reason=3)                                       
[ 5175.396092] wlan0: authenticate with AP ffff880112a02aa0                                           
[ 5175.416564] wlan0: authenticate with AP ffff880112a02aa0                                           
[ 5175.416609] wlan0: authenticated                                                                   
[ 5175.416615] wlan0: associate with AP ffff880112a02aa0                                              
[ 5175.421295] wlan0: RX AssocResp from ffff88010031404e (capab=0x411 status=0 aid=3)                 
[ 5175.421302] wlan0: associated

 Here is where the really strange part comes in. If I take the computer back to the 30-35ft range, the wireless connection does not drop, it just keeps working fine. I have tried the default version of the iwlagn driver and the one from linux-backports-modules. I have also tried swcrypto=1 and forcing antennas. Nothing works. Does anyone else have this same problem or know of a solution?

---

