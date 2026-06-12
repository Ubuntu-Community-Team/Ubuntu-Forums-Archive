---
title: "f5521gw  wwan/3g not working"
date: 2011-10-17
forum: Networking &amp; Wireless
---

### Post by handverbrennung on 2011-10-17
Hi,
i just bought a ThinkPad t520 with wwan/3g option. As far as i see an ericcson f5521gw is used. My Ubuntu 11.10 (amd64) recognizes it, it asks for the PIN an seems to find my homenetwork. But if i want to connect it just says "disconnected" after a second. The Number to dial should be *99#, APN is set. any ideas?

Regards, Enno

---

### Post by BlackAdderDK on 2011-10-17
Hi
I have had the same problem with my W520... try to use the script from [http://www.sakis3g.org/](http://www.sakis3g.org/) - it works great... you might have to try some different ports (mine were 3) - but it should work.

regards
'Adder

---

### Post by handverbrennung on 2011-10-17
Solved! Thanks. Not as nice as the gnome applet, but it works great.

---

### Post by BlackAdderDK on 2011-10-17
To simplify it a little - I made this script (was used in OpenSuSE and with another modem, but you should be able to adjust to you installation)

#!/usr/bin/expect -f
set timeout -1
spawn /usr/bin/sakis3g SIM_PIN="9999" connect --googledns USBINTERFACE="0" APN="internet" USBDRIVER="option" MODEM="12d1:1446 12d1:140c"`  
expect {
        Password: {send "Password\r" ; exp_continue}
        eof exit
}

.. and then use a desktop shortcut to this...  

If you have any problems let me know... I'm just about to make it work on my Ubuntu with the f5521gw modem

regards
'Adder

---

### Post by BlackAdderDK on 2011-10-17
Hi Again

When you have connected manually, you can choose "more options", and then "Generate success report" - there you will find the info you need... with my new mobile operator it won't work with the --googledns - but with my old, it wouldn't work without :)

My new scriptline is as follows: ./sakis3g SIM_PIN="9999" connect --pppd APN="apnname" USBINTERFACE="3" USBDRIVER="cdc_acm" USBMODEM="0bdb:1911" OTHER="USBMODEM" MODEM="OTHER"

regards
'Adder

---

