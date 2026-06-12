---
title: "SMTP authentication type"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by The4thFloor on 2009-12-03
I'm not sure if this is the correct forum for this, but I hope it's close enough.

I recently set up my Hotmail account for use in Evolution, and everything works fine, but I was wondering if someone could explain the differences between SMTP server authentication types, and which of them would be the most secure one? At the moment, it's set to PLAIN, which was the default, I think. 

Did a quick Google search, but couldn't find a simple, clear explanation. 

Thanks in advance.

---

### Post by puppywhacker on 2009-12-03
SMTP is an ancient protocol for sending email. In it's original form no authentication was needed whatsoever. Since spam is becoming a huge issue, some smtp servers start to require that you authenticate before sending email. Since SMTP is a readable text-based protocol you can sniff usernames and passwords from the wire, so plain-text passwords are not well-protected. 

That is why it is advisable to use an encrypted link with SSL/TLS (same thing, different version).

The other authentication types do not involve sending the password over the link, but use digest challenges to check if both sides know the password. If you use SSL or TLS it doesn't matter, but otherwise click "check for supported types" and see if your smtp server supports NTLM/SPA or GSSAPI or DIGEST MD5 or CRAM MD5. It will strike-through the unavailable options

---

### Post by The4thFloor on 2009-12-05
Alright, thanks for clearing that up.

---

