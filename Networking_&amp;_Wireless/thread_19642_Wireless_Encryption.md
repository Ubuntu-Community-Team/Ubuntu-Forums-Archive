---
title: "Wireless Encryption"
date: 2005-03-12
forum: Networking &amp; Wireless
---

### Post by Ryan450 on 2005-03-12
hey gang,

I've gotten my atheros based card to work fully without encryption at 36 mb/s.. Now that I know the card officially works under this distro, I want to enable the encryption, but when I do that my wireless card can not connect to the router. therefore, no wireless internet for linux.. 

I use a 64-bit encryption WEP.. I used the networking menu from the system configuration to configure my wireless card (loved the configurater, straight and to the point) when I type in my 5 digit encryption (which is 64-bit wep) it cannot connect to the router.. any ideas on what I can do?

---

### Post by flyfishin on 2005-03-12
5 digits?  Is that the passphrase that you used to generate the key or the actual key?  Every 64 bit key I generate is 10 characters long.  To get wireless encryption working you need to enter the actual key generated and not the passphrase.

---

### Post by Ryan450 on 2005-03-12
[QUOTE=flyfishin]5 digits?  Is that the passphrase that you used to generate the key or the actual key?  Every 64 bit key I generate is 10 characters long.  To get wireless encryption working you need to enter the actual key generated and not the passphrase.[/QUOTE]
 ok, in my router website it asks me for a 5 digit number to act as my WEP (I'm guessing that would be the passphrase)  I have no idea how to see the 10 character long key that your seeing :S...

---

### Post by flyfishin on 2005-03-13
I have a Linksys router.  I type in a passphrase and click on a key that generates the key. The router then shows me the key generated on the screen.  Are you setting up WEP or WPA on your router?

---

