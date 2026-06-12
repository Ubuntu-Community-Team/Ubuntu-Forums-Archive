---
title: "Poor wireless stability vs Windows"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by gamphd on 2009-12-28
I'm using WEP 104/128 (which for some reason is called WEP 40/128 on Ubuntu but accepts a 26-digit hex password instead of an insecure 10 nevertheless) with authentication set to Shared Key instead of the default Open System, whatever that is.  To the extent that there is any correspondence in the interfaces, Vista uses the same settings but maintains a stable connection, although if it's any consolation, Windows 7 isn't backward-compatible with my router or its setup at all and requires a wired connection.

---

### Post by shairozan on 2009-12-28
Hey there, 

I think what you're looking at is an encryption issue. WEP 40 and WEP 64 are the same key size, the only difference is the number of bits used in the encryption. Thus 40 and 64 bit WEP, while similar, are incompatible. 

The same is said for 104 and 128 bit. They're similar, but different encryptions. If your router supports only WEP 104, you may want to look at moving to 64 bit or 128 bit that you can get to work with Ubuntu. 40 and 104 are odd encryptions, and are significantly easier to crack. I would actually recommend moving to WPA with a pre-shared key if possible.

---

