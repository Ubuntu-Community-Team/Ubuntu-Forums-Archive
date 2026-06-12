---
title: "trying to get eee PC to connect to wifi router"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by ray field on 2009-01-04
I recently bought an Asus eee PC 1000, and installed Adam M's Intrepid kernel -- things were working pretty nicely, until I tried adding some third-party scripts, which busted my wifi, and also apparently screwed up my networking -- Samba, which had been working just fine, no longer displays remote computers on the eee box (though the other boxes on my home network are able to transfer files to the eee).

in an effort to get the wifi running again, I ditched Network Manager in favor of wicd, which seems to offer a chance of working.  after some tweaking, I finally can work things so that the eee sees the router.  however, it cannot connect -- though I've selected the correct passkey, when I try to connect, the progress bar gets to "Validatiing authentication" -- then the progress bar stops, with the message "Not connected." 

Advanced Settings for the router connection has only "Use Encryption" selected, and WPA 1/2 (Passphrase) in the selection bar (in the router I have WPA selected for the authentication type), and the correct passphrase in the key.

two additional notes:

* the eee pc successfully connects to the router under the default Xandros installation;

* when I toggle the wifi (sudo /etc/acpi/eeepc/eeepc-wifi-toggle.sh) before it toggles off, I get

ra0: ERROR while getting interface flags: No such device

fwiw, I'm not a complete newbie, having delved somewhat into Suse over the last few years.

---

### Post by ray field on 2009-01-05
maybe some sort of encryption protocol issue?

---

### Post by superprash2003 on 2009-01-05
have you tried with WEP ?

---

### Post by ray field on 2009-01-05
hmm -- I went to try, but when I couldn't get WEP to work, had another look at the settings in the router.  With "Use encryption" and "WPA 1/2 Passphrase" selected in wicd's Advanced Settings page, I changed "Cipher Type" to "Auto" in the Trendnet Tew-432BRP's WPA pag, and I'm now connected just fine.

thanks for the hint!

---

### Post by superprash2003 on 2009-01-06
nice.. please mark thread as SOLVED under thread tools

---

