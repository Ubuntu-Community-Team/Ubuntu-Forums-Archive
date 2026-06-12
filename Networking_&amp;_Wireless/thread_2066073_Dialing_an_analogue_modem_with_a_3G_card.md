---
title: "Dialing an analogue modem with a 3G card"
date: 2012-10-03
forum: Networking &amp; Wireless
---

### Post by marcovanbeek on 2012-10-03
I have a fairly standard Ubuntu 12.04 / Unity set-up on an HP laptop, with a Gobi un2400 3G modem, which all works fine, and connects to the 3G network without a problem. I can send and receive text messages via Wammu, and apart from the well-documented issues I have no real issues.

So, here is my question: I have a client with a temperamental broadband connection. Every so often I need to dial in on their analogue line, get a PPP session going, and then connection to the web interface on the router and reboot it. Obviously no other way in as the broadband is down.

I can't see any way in the Network Manager set-up to configure a simple dial-up networking connection to a phone number using that modem, so that I could dial it without needing access to an analogue line. The 3G modem seems to support AT commands, so maybe I am just looking in the wrong direction. Any suggestions anyone?

---

### Post by jonobr on 2012-10-03
Hello


I dont think its possible,

The 3G card is an air interface technology connecting to a base station which uses a different modulation scheme.

Telephone modems use things like V90 V34 etc where as 3G uses QAM, BPSK and so on.

You can indeed use AT commands and dial strings with the card, but its not traditional mod/demod stuff on a regular analogue line.

---

### Post by marcovanbeek on 2012-10-04
I have done it before with a normal mobile phone using a USB connection, and I can tell Minicom to tell the modem to dial a number. My current data SIM doesn't have a call plan, so the call doesn't come through. I don't really want to enable a call plan, and get looked into a 12 or 24 month contract unless it is going to work, so I might try sticking my phone SIM into it and seeing if it works, but as I mentioned, I have had it working before with a USB cable and my old Ericsson phone that had a built-in AT compatible modem.

---

