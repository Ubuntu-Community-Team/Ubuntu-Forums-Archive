---
title: "Pair Bluetooth Rocketfish Keyboard"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by rraman3110 on 2010-02-19
I am able to pair a rocketfish bluetooth mouse, but I am not able to pair the keyboard. I was wondering if anyone knew the correct pin. 

Or if anyone knew what I need to do.

---

### Post by ectospasm on 2010-03-01
I'm having the same problem.  It seems to be related to karmic.  In previous Ubuntu versions it was the other way around, the keyboard worked fine, but the mouse was partially functional (no scroll wheel).  Now, the mouse pairs OK (and has the scroll wheel working), but Ubuntu asks the user to input a random string of digits, and it doesn't seem to work with the rocketfish bluetooth keyboard.

---

### Post by Portmanteaufu on 2010-03-01
I'm having the same problem in Karmic. Has anyone submitted a bug report?

---

### Post by khaije1 on 2010-04-04
same sitch for me, are we all talking about kb model rf-btkb4 ?

on windows the setup procedure has the computer pop up some sort of sequence of characters and then they need to be typed out on the keyboard for a full connection to be established between pc and keyboard, which is different than i'd needed to do before. Anyone know if linux supports this extra step?

Also there were mentions of it working in previous versions of ubuntu, was this with the same version of the model? b/c when i google most of the references I see are to an older version of the hardware but under the same model name.

cheers all,

---

### Post by khaije1 on 2010-04-05
the syslog for when I try to connect the bt keyboard problem...

Apr  5 10:38:04 amalthea bluetoothd[2089]: Discovery session 0x7f2828125eb0 with :1.80 activated
Apr  5 10:38:08 amalthea bluetoothd[2089]: Stopping discovery
Apr  5 10:38:37 amalthea bluetoothd[2089]: Encryption failed: Permission denied(0x5)
Apr  5 10:39:42 amalthea bluetoothd[2089]: last message repeated 2 times


ok... update...

i looked around for a bit... this keyboard has enhanced security requiring a code generated on the computer be typed into the bt keyboard followed by hitting <enter> 

i was able to do this by installing blueman from the repo and running 'blueman-assistant' and going through the pairing steps as prompted.

hopefully this advice will help others in similar circumstances.

the sort of odd thing is, i think the built-in bt manager in kde4 had me do this when i first tried to bond the device but i thought it was a normal 'pair code' request and so i didn't enter the code on the kb also... i wonder if that would have prevented this problem. also i wonder why it never allowed me to do that again after the first time despite repeated un-pair/re-pair attempts.

anyway b/c im using kubuntu i'm going to test a bit to see it blueman plays nicely with the native-kde bt manager... if it does i think i'll keep both.

hope this experience helps

and yes, i need to change the bt keyboards layout settings b/c i cant capitalize or use the shift key at all, lol

---

### Post by khaije1 on 2010-04-14
i am still having that same weird problem where the bluetooth keyboard doesn't allow me to capitalize or access the special characters in the number row with the shift key. 

CAPS lock works okay as do all the multimedia keys lining the keyboard. idk what the deal is... i looked into changing the keymap and the keyboard model but havent yet met with success.

if anyone knows what the fix on this is please pm or post to the thread.

thanks a million!

---

