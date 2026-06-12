---
title: "Network connection Reset Issues:"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by klepto on 2010-03-20
In any application that uses a good amount of bandwidth like Transmission
or Sabnzbdplus I see the speed go to normal, shoot through the roof and then reset to 0/kb and repeat. In transmission the connection reset is every 6 seconds or so. Is this a known problem with 9.10?

Thanks for your help.

---

### Post by 2hot6ft2 on 2010-03-20
> **klepto said:**
> In any application that uses a good amount of bandwidth like Transmission
or Sabnzbdplus I see the speed go to normal, shoot through the roof and then reset to 0/kb and repeat. In transmission the connection reset is every 6 seconds or so. Is this a known problem with 9.10?

Thanks for your help.
That's the first I've read about it so I would say it's not normal. Perhaps a driver issue.

---

### Post by klepto on 2010-03-20
Ahh I think this is the culprit:

[31375.008107] wlan0: no probe response from AP 00:1e:2a:5f:60:8c - disassociating
[31376.387792] wlan0: authenticate with AP 00:1e:2a:5f:60:8c
[31376.411316] wlan0: authenticated
[31376.411335] wlan0: associate with AP 00:1e:2a:5f:60:8c
[31376.415335] wlan0: RX ReassocResp from 00:1e:2a:5f:60:8c (capab=0x411 status=0 aid=1)
[31376.415351] wlan0: associated
[31385.009093] wlan0: no probe response from AP 00:1e:2a:5f:60:8c - disassociating
[31385.226616] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[31385.298672] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[31386.413840] wlan0: authenticate with AP 00:1e:2a:5f:60:8c
[31386.430266] wlan0: authenticated
[31386.430288] wlan0: associate with AP 00:1e:2a:5f:60:8c
[31386.437784] wlan0: RX ReassocResp from 00:1e:2a:5f:60:8c (capab=0x411 status=0 aid=1)
[31386.437803] wlan0: associated


Either my ath0 drivers are messed up or my wireless router is giving up the ghost

---

