---
title: "Weird wireless router problem"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by afeasfaerw23231233 on 2009-10-31
While my bittorrent server is working, my notebook cannot connect to the wireless router. The message from the router says it is because of wrong WPA key. Once I switch of deluge the notebook can connect immediately. However the traffic of bittorent is not hight at all -- there are only under 10 downloadings and uploadings altogether. The speed is limited to 50Kb/s and the total number of connections is under 50. 

Does anybody have a similar problem?

EDIT: Once the wireless has been established successfully, deluge can be switched on again and the wireless connection never drops even the traffic reaches 10mbps (which is the maximum bandwidth provided by the ISP).

---

### Post by dearingj on 2009-10-31
Strange indeed. What brand & model number is your router?

---

### Post by afeasfaerw23231233 on 2009-10-31
D-link DI-524
It has the latest firmware flashed.

---

### Post by afeasfaerw23231233 on 2009-11-03
Perhaps the cpu of the router was too busy that it mistaked the WPA key as invalid?

---

### Post by afeasfaerw23231233 on 2009-11-07
Here's the extract of dmesg ```

[   92.740014] wlan0: associate with AP 00:19:5b:df:63:da
[   92.742405] wlan0: RX ReassocResp from 00:19:5b:df:63:da (capab=0x431 status=17 aid=1)
[   92.742407] wlan0: AP denied association (code=17)
[   92.940013] wlan0: associate with AP 00:19:5b:df:63:da
[   92.942415] wlan0: RX AssocResp from 00:19:5b:df:63:da (capab=0x431 status=17 aid=1073)
[   92.942418] wlan0: AP denied association (code=17)
[   93.140015] wlan0: associate with AP 00:19:5b:df:63:da
[   93.142426] wlan0: RX AssocResp from 00:19:5b:df:63:da (capab=0x431 status=17 aid=1073)
[   93.142429] wlan0: AP denied association (code=17)

```

And from the internet I found the definition of the status codes

```

   Status code    Meaning
> > >                 0       Successful
> > >                 1       Unspeci&#64257;ed failure
> > >               2&#8211;9       Reserved
> > >                10       Cannot support all requested capabilities in the Capability Information &#64257;eld
> > >                11       Reassociation denied due to inability to con&#64257;rm that association exists
> > >                12       Association denied due to reason outside the scope of this standard
> > >                13       Responding station does not support the speci&#64257;ed authentication algorithm
> > >                14       Received an Authentication frame with authentication transaction sequence number
> > >                         out of expected sequence
> > >                15       Authentication rejected because of challenge failure
> > >                16       Authentication rejected due to timeout waiting for next frame in sequence
> > >                17       Association denied because AP is unable to handle additional associated stations
> > >                18       Association denied due to requesting station not supporting all of the data rates in the
> > >                         BSSBasicRateSet parameter
> > >           19&#8211;65 535     Reserved

```

code 17 = Association denied because AP is unable to handle additional associated stations?
That means the router is too busy (because of bittorrenting?) to handle the wireless association?

I tried flash DD-WRT on it but the router only has 4MB of memory so it is not possible.
What a crappy router!

Any idea?

---

