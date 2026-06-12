---
title: "GSM Modem - Password required"
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by FokkerCharlie on 2010-07-10
Hello!

I think that I'm being stupid and must have missed something, but...

I have a USB GSM modem that was supplied when I started using a KCELL (Kazakhstan) payg mobile deal.  Connecting to KCELL works just fine, Network Manager took care of everything.

Unfortunately, I am very disappointed with the speed of the service I am seeing.  (If anyone has any tweaks that they'd like to share about the speed of these setups, I'd be delighted to hear them!) and want to try with a different sim card.

When I put the new sim in, I can create a new connection, no problem... but when I try to connect, I see the following dialog:

Mobile broadband network password
A password is required to connect to 'Beeline'
ZTE Incorporated ZTE CDMA Technologies MSM

The dongle is listed by lsusb as:
ONDA Communication S.p.A. ZTE MF636

I use this sim for data with my mobile, no problem, but the password field is blank.

I have re-flashed the dongle to a non-KCELL branded firmware, to no particular effect.

Am I missing something?

All input appreciated.

Charlie

---

### Post by simo on 2010-07-10
Disable SIM PIN and try recreating connection in NetworkManager. If still ask you for password enter password which provider gave you.

cheers!

---

### Post by FokkerCharlie on 2010-07-10
Hi Simo

Thanks for your response.

I disabled the sim-pin, and tried re-connecting... it still asks me for a password.  The thing is, that there is no password supplied.  I don't think that one is required.  The same is true for both the beeline and KCELL sims that I am playing with.

However, I tried typing 'blank' in the password field.  I failed.  I typed 'blan' instead, and then network manager reported that the network was connected.  However, I don't seem to be able to transmit any data!

The 'blan' thing is curious.  'blank' doesn't work.  Nor does 'password' 'user' 'pass' or a whole bunch of other things I have tried.

Any more suggestions?

Charlie

---

### Post by FokkerCharlie on 2010-07-10
Ah!

OK.  It suddenly flashed into life.  Many thanks!

Charlie

---

