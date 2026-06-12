---
title: "3G USB dongle with PIN-enabled SIM"
date: 2010-08-09
forum: Networking &amp; Wireless
---

### Post by dangerjunkie2002 on 2010-08-09
Hi,

I've just unlocked my 3G mobile broadband dongle so it can be used with SIM cards from multiple providers. (It's a ZTE MF627 that the unlocking process appears to have turned into an MF626)

Networkmanager works fine with it when I've got the original Three.co.uk SIM inserted and I can join the network. When I insert my Vodafone SIM (which works in the area I'm going to - The Three one doesn't due to poor network coverage) the dongle lights up green and the device appears as a virtual CD. If I eject the virtual CD it disappears and reappears as a modem. 

When I ask NM to connect the NM icon zaps up and down like it's doing something but the modem stays lit up green (rather than changing to blue == 3G mode, which it does with the Three SIM). NM sits there spinning its wheels and never connects.

I decided to try it in Windows to see if I had a dongle problem or a Linux problem. In Windows the dongle lights green then when I press connect a dialogue pops up that tells me the Vodafone SIM has PIN security enabled and asks me for the PIN. When I enter the PIN the dongle changes from green to blue and connects.

My conclusion is that NM isn't connecting because the SIM isn't becoming ready as it's sitting there waiting to validate the PIN which doesn't arrive. I can work around this by disabling PIN security on the card but I would rather not. What do I need to do to make NM demand and validate the SIM PIN if there is one please?

Thanks,
Paul.

---

### Post by alexfish on 2010-08-09
your post is a little confusing

does the connection work when the pin code is disabled

have you entered the pincode in NM and then fails to connect

---

### Post by dangerjunkie2002 on 2010-08-09
Hi,

I will clarify...

On Windows both of my SIMs work:

Three (No PIN) card turns blue and connects as soon as the connect button is pressed.
Vodafone (PIN) card stays green, when the connect button is pressed the modem manager demands the PIN. When the PIN is input the card turns blue and connects.

On Ubuntu:

Three (No PIN) card turns blue and connects as soon as I select the network in NM.
Vodafone (PIN) card stays green when I click NM, the PIN is never requested and NM sits there with its icon "pinging" up and down.

I haven't tried disabling the PIN on the Vodafone SIM card and seeing what happens with NM but I can do that when I get home if it helps.

Thanks,
Paul.

---

### Post by alexfish on 2010-08-09
have you entered the pin code details in the Network Manager vodafone connection

---

### Post by dangerjunkie2002 on 2010-08-09
Doh! First time I've used NM with a PIN-enabled SIM and I missed that. Thank you. Sorry I wasted everyone's time and bandwidth.

Cheers,
Paul.

---

### Post by alexfish on 2010-08-09
Hi

you ain't wasted any ones  time

this what forums are for

Enjoy

regards

alexfish

---

