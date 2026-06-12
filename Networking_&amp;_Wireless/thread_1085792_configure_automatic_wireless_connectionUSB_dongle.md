---
title: "configure automatic wireless connection/USB dongle"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by raymondh on 2009-03-03
Hi.

using Linksys USB dongle to get wifi.

I am configuring my son's old desktop with 8.10 intrepid.  We can connect wirelessly using a dongle.  On boot-up, we're constantly asked to unlock keyring

"the application 'nm-applet'(usr/bin/nm-applet) wants access to the default keyring but it is locked"

How do we configure this so that it connects automatically?  I've seen a tutorial before but can't remember where.

Thanks in advance :)

---

### Post by boblemur on 2009-03-04
hopefuly im right in guessing that you have enabled automatic login?

when automatic login is enabled, the default keyring will not allow you to rember the password (which seems stupid concidering you enabled auto login so that you dont have to type passwords...) However all is not lost, you can make it unlock the keyring automaticly by changinging the password on the default keyring to nothing.

goto applications > encryption keys and something... 

then goto preferences and change the password of the default keyring to just blank.. press enter. that way it dosent need to unlock the keyring because its not encrypted.

this does bring up security issues however, your wifi password and any others in the default keyring will be stored in plain text, this means that if someone steals your computer, or has access to your files they can read those passwords.

however most of the things in the default keyring arnt particulary important to protect (as you can easily change your wep key if your computer is stolen... however unlikley it may be)

you dont have to worry any important passwords (like the ones stored by firefox when you say rember, pidgin password etc, are stored by the application which keep your data safe)

hope this helps... :)

---

