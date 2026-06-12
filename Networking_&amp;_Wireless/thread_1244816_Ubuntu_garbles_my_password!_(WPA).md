---
title: "Ubuntu garbles my password! (WPA)"
date: 2009-08-19
forum: Networking &amp; Wireless
---

### Post by andrewcd on 2009-08-19
Hello All,

I'm relatively new to ubuntu, and I am the type of user described [here]("http://imgs.xkcd.com/comics/cautionary.png").

I just got a new router, and I set my WPA key, to my telephone number.  

When I try to connect to my wireless network however, somehow the network manager garbles my password (a 10-digit telephone number) into a 64-character hexadecimal number.  Needless to say, this doesn't work, because my network password is a 10-digit number, not a 64-digit hexidecimal.

WTF?

Please help.  I have no idea why the computer would do this.  Is it a bug or some silly security layer?

---

### Post by andrewcd on 2009-08-19
I just booted in XP, and the telephone number works fine.  Somehow ubuntu is garbling my password.  Please help!  Google isn't giving me much.  Thanks!

---

### Post by andrewcd on 2009-08-19
Problem resolved independently:  [http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)

I have no idea what just happened, but now it works!

I also deleted my default keyring (I think that it is annoying and overly redundant).  When I rebooted and it prompted me, I left it with a blank password.  So!  It could have been that too!  Either the wpa_supplicant or the blank password on the keyring.

Who knows!  Woo!:guitar:

---

### Post by andrewcd on 2009-08-20
So I reboot and no dice, the **** is broke.  Still gives me the hex key.  Can somebody share a durable solution?

---

### Post by zot171 on 2009-08-21
hey, ive noticed that my 52 character string (WPA as well) gets garbled as well, but for me, it isnt the format (plain text vs hex key) but the encryption type that determines whether or not i can connect. what i found after much trial and error was that linux disagrees with TKIP, but does work with AES, so you may want to try switching your encryption type and retrying with the garbled pass. the garbled pass should work just the same

---

