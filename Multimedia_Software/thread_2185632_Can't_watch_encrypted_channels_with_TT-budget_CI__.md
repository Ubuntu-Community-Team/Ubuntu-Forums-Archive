---
title: "Can't watch encrypted channels with TT-budget CI / TT-budget C-1501"
date: 2013-11-03
forum: Multimedia Software
---

### Post by Neverlast on 2013-11-03
Hello!

I have been watching Cable-TV (Kabel Deutschland in Hamburg) under Ubuntu 12.04 with vlc-player and my DVB-C card (Technotrend TT-budget C-1501) for some weeks now. For that I generated a channels.conf that I easily imported to vlc-player. For unencrypted channels it is working properly. I didn't even had to install any drivers. I read from this forum that this is due to the kernel version I installed (3.5.0-42-generic) that already includes drivers for this card.

In order to watch encryped channels I ordered HDTV from Kabel Deutschland in Hamburg. I got a CI+Modul (manufactorer is "smardtv" from malaysia") with the according smart-card. Inserted into my Samsung TV everything works fine (after registering and so on), means I can watch encrypted HDTV channels with my Samsung TV now.

Two weeks ago I bought the add-on card (Technotrend TT-budget CI) and connected it to my DVB-C card in order to watch the encrypted HDTV-channels with my vlc-player but unfortunately it doesn't work. When I switch from an unencrypted to an encrypted channel the picture vanishes and I can only see the length and the title of the current program as if the CI-card was not working.

I searched for informations about this problem on many forums and of course I tried to get informations from the manufactorer but so far without any success. I even not know if the hardware itself is working at all as there is no LED that is indicating it is working. I reattached the card and its connector-cable to make sure it is connected properly.

I would be very happy If anyone could tell me:

1) how I can get this card working to wath the encrypted channels
2) if he has no answer for my first question - how I can find indicators that tell me the card is working at all

Maybe the following information can help with this issue:

```
$ lspci | grep SAA7146
05:01.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
```

```
$ lsmod | grep budget
budget_ci              28596  0 
budget_core            19073  1 budget_ci
dvb_core              111129  2 budget_ci,budget_core
saa7146                20336  2 budget_ci,budget_core
ttpci_eeprom           12863  1 budget_core
rc_core                26423  3 rc_tt_1500,budget_ci

```

Thanks a lot in advance!
Kay

P.S.: By the way, this is the first time I ever posted a question in a forum. Hope I did it right. If not, please don't hestitate an tell me!

---

