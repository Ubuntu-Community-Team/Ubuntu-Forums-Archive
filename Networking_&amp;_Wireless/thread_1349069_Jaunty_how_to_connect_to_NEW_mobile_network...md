---
title: "Jaunty: how to connect to NEW mobile network..?"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by Thanh-BKK on 2009-12-07
Hi.

Since a couple of days i have a SIM card for Thailand's brand new 3G network and a matching phone, a Samsung L700 (had the phone before but now it finally "can" 3G, too).

Now i try to connect my Jaunty laptop to that network and it won't work!

The reason being that when i connect the phone via USB cable and create a new "Mobile Broadband" connection via network manager it only gives me "pre-set" choices, such as the usual three GSM providers in my country - them being AIS, D-TAC and True. The 3G network (TOT Mobile) has only been launched last week so i would not expect Ubuntu to "know" it already, however.......

On Windows (Samsung PC Studio) i have an option to create a brand new connection WITHOUT any pre-set country or ISP settings. On Ubuntu i don't seem to have such option.

What i need is the "dial-up number" which is *99***1# and the APN name which is "internet", NOTHING ELSE. 

I have tried modifying any of the three available pre-set configurations but none will work, in fact trying to connect will cause the phone to reset/reboot itself. The same phone with a D-TAC SIM card, using the D-TAC pre-set, works fine. And that same phone with the 3G SIM on Windows works fine, too.

Oh, and another phone (Samsung U800) won't work either, it does not reset/restart but does not go online either. Needless to say that that phone, too, works fine on Windows and, with D-TAC, also on Ubuntu.

So how can i create a new "Mobile Broadband" connection from scratch, please? 

Many thanks in advance......

Thanh

---

### Post by Nittalope on 2009-12-08
Well, on the network icon that is on the top bar, next to the date and time, just right click, choose Edit Connections, then go to the Mobile Broadband tab, clic Add and follow the steps. When you are up to Choose Your Provider check I can't find my provider, then insert your APN name and that's it. Now you have to edit your connection to add the "Dial-up number" and you're done.

Hope it works for you as it worked for me.

---

### Post by Thanh-BKK on 2009-12-08
Hi.

Yeah i have been there - but i do not have an option "can't find my provider". All there is are the three GSM providers for Thailand, AIS, D-TAC and True. No other option.

And in selecting the country itself there is also no option "other" or "Custom" or something like that.

If there was i would not have to ask the question in first place.......

Best regards......

Thanh

PS i am running Jaunty if that helps?

---

### Post by pdc on 2009-12-09
I think your are being told: it is the APN settings that determine what your simcard reaches out to;

the name of the network is to help you, NOT the simcard;

so you can rename a network name to "FISH & CHIPS" and if you have the correct APN you should be fine

---

### Post by Thanh-BKK on 2009-12-09
Hi.

If that would be the case it would be working, no? There are some settings behind the operator pre-sets which are not accessible through the GUI on Ubuntu... and those settings make it not work. 

For instance, i use D-TAC GSM. The APN is "internet", the dial-up number is *99#. With the D-TAC SIM in my phone, this connection fires up just fine.

Now i change the settings in Ubuntu, i.e. network name to "3G", APN is the same ("internet"), and the dialup number to *99***1#. Then i put the 3G SIM into my phone and - nothing, respectively the phone crashes/resets upon trying to connect.

Same on Windows when trying to use a modified D-TAC connection, however one created from scratch (country = other, provider = other) works just fine with the same phone. And on Windows, respectively the Samsung PC Suite thing, i could see that there were a bunch of settings such as network country code(520-something), ports and IP addresses in those pre-set operators that were greyed out and not modifyable, i guess the same on Ubuntu but there they are not even visible. 

And it is this "other - other" possibility that i am missing on Ubuntu and which, in my opinion, has to be there. 

Kind regards.....

Thanh

---

