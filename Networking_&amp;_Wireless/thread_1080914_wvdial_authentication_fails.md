---
title: "wvdial authentication fails"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by JulianPP on 2009-02-25
Have installed Ubuntu 8.10 to escape from Windows but can't get Dialup internet access. Settings are:

Wvdial.conf
{Dialer Defaults}
Init1 = ATZ
Init2 + ATQ0 V1 E1 S0=0 &C1 @D2 +FCLASS=0
Modem Type = Analogue Modem
ISDN = 0
New PPD = yes
Phone = 019xxxxxxx
Modem = /de/ttyS0
Username = mxxxxc
Password = nxxxxe
Baud = 115200

Modem initiates fine and dials up. Then fails Authorization:

ATDT019xxxxxxx
CONNECT 115200
User Access Verification
Username: username: login
-->Carrier detected. Waiting for prompt.
Username: username: login:
-->Looks like a login prompt.
--> Sending: mxxxxe
Password: password:
-->Looks like a password prompt
-->Sending: (password)  .....Reads like that- not my password.
% Authorization failed.
-->Connected, but carrier signal lost! Retrying...
-->Sending: ATDT019xxxxxxx
-->Waiting for carrier.
NO CARRIER

I have entered my username and password in pap-secrets and also in chap-secrets.
I've tried turning Stupid Mode on.
Still no luck.

I have googled and forummed myself crazy, but no suggestions seemed to help. I would appreciate any wisdom from anybody,
particularly re: any entries I should make in /etc/passwd or in /etc/ppp/options.
Thanks in advance, Julian

---

