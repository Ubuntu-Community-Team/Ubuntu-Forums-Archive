---
title: "Huawei E169 doesn't connect."
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by Ifaistos on 2009-05-15
I have a huawei E169, on Jaunty on aa Asus 1000.
It does recognize it, but can't coonectr although it seems that it is trying.

I live in Hellas (Greece) and am connected with Wind Broadband.  Anybody had the same problem and solved it somehow?

Thank you :-)

---

### Post by panmoto on 2009-05-15
i have a similar experience but with a happy ending.

i use sierra 881u on my kubuntu/ubuntu laptop (not dual-booting but dual desktop environment). i tried first on kubuntu, it was recognized but after several attempts it can not connected, log off and switch to ubuntu it connected successfully, back to kubuntu and voila it works.

maybe log off and re-login would help?

btw : are you sure you configure the connection right?

fyi : 
i've tried huawei e220 and e156g, and they both works in 9.04.

---

### Post by GeorgeVita on 2009-05-15
Hi **Ifaistos**,

I have exact the same configuration and works with no modification!
I have 9.04 single boot from HD but I have also tried successfully live USB stick, UNR 9.04 installation and live.

In all situations I had the SIM PIN check removed.

To check try the following:
- remove SIM PIN check using Wind's application s/w
- boot Ubuntu without the modem
- disable wireless from network manager icon (no WiFi)
- right click network manager icon to **Edit connections > Broadband**
- delete any connection already exist and close window
- plug in modem and wait for the "assistant" to begin (if not try to ADD manually a Broadband Connection)
- follow instructions and choose **TIM** as the provider
- leave all fields to defaults (*99#, web, web, gint.b-online.gr)
- if asked for more passwords leave them blank and click "use unsafe area ..."
- Connect by clicking Network Manager icon and then TIM
- "allow this connection to use keyring" every time

Regards,
George

---

### Post by Ifaistos on 2009-06-15
It worked like a charm!!!
Thank you :-)

---

