---
title: "WPA2 Enterprise in 8.10"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by EchoP on 2009-01-30
Hey, I seem unable to connect to my schools wireless with WPA2 Enterprise, PEAP and MSCHAP v2..
I have tried almost anything, but it is unable to connect!

It connects perfectly to a public network, or my WPA2 Personal network at home.

---

### Post by cak3 on 2009-02-05
There are several threads about this. One is [http://ubuntuforums.org/showthread.php?p=6626893#post6626893](http://ubuntuforums.org/showthread.php?p=6626893#post6626893) (that links right to my post). To summarize here, I got it working by using Favux's solution ([http://ubuntuforums.org/showpost.php?p=6417688&postcount=36](http://ubuntuforums.org/showpost.php?p=6417688&postcount=36)) and then using WICD with the WPA2-TKIP profile instead of the default network manager.

You can get WICD here: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Hope this works for you, too.

---

### Post by NoobBiscUiT on 2009-04-23
just as another refrence, you can nano (or edit somehow) the peap-tkip deal located in /etc/wicd/encryption/templates/  and remove the line that says "ca_cert="$_CA_CERT" if your wpa 2 enterprise network does not use / need a certificate.

this is how i got mine working like right now :D

---

