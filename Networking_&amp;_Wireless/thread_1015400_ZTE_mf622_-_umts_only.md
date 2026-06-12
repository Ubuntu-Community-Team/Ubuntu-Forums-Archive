---
title: "ZTE mf622 - umts only?"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by aditnsr on 2008-12-18
hi,
does anyone know how to set a zte mf622 usb modem to 'umts only'?
i found on google that some operator (vodafone if i'm not mistaken) have this 'AT_OPSYS' command to set the preferred connection mode to umts or gprs only, but it doesn't work for me.
thx,
Adit

---

### Post by aditnsr on 2008-12-21
i've found a little solution (sort of)..
i can use the 'AT+COPS' command to manually select the network,
example:

AT+COPS=1,0,"your network name here",2

the first digit ('1', the one after the equal sign),
means manually select the network.
the last digit ('2', the one that came after the network name),
means UMTS.

I'm not sure if this does exactly what i wanted, which is to force
umts only mode, but i guess its worth to try.

for details, see 3GPP specs..

regards
Adit

---

### Post by mgifos on 2009-05-13
Hi,

It seems that this setting can be kept within the modem itself - I chose UMTS only option through windows modem app and applied it, after that I used the same modem under Ubuntu and "UMTS only" option worked for me.

Currently I'm using usb_modeswitch and Gnome NetworkManager in combination. My question to you aditnsr: What software do you use to setup AT commands - wvdial perhaps? Is there any possibility to use it within builtin gnome network manager, how to accomplish this?

Thx.

---

### Post by anttu on 2009-08-03
At least with ZTE MF636 the command AT+ZSNT is used.

Like this:

- AT+ZSNT? = status enquiry
- AT+ZSNT=0,0,0 = AUTOMATIC network selection, GSM+WCDMA
- AT+ZSNT=0,0,1 = AUTOMATIC network selection, GSM+WCDMA,GSM preferred
- AT+ZSNT=0,0,2 = AUTOMATIC network selection, GSM+WCDMA,WCDMA preferred
- AT+ZSNT=1,0,0 = AUTOMATIC network selection, GSM only
- AT+ZSNT=2,0,0 = AUTOMATIC network selection, WCDMA only
- AT+ZSNT=0,1,0 = MANUAL network selection, GSM+WCDMA
- AT+ZSNT=1,1,0 = MANUAL network selection, GSM only
- AT+ZSNT=2,1,0 = MANUAL network selection, WCDMA only

You can find the whole document for ZTE (Onda) AT commands in here: 
[http://www.siptune.net/siptune.net/tiki-index.php?page=ZTE+at-komennot](http://www.siptune.net/siptune.net/tiki-index.php?page=ZTE+at-komennot)
(The page is in Finnish, but just take the link named "ohje" to the pdf.)

---

