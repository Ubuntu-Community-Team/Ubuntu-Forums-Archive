---
title: "Does this iwconfig print out tell me?..."
date: 2009-04-17
forum: Networking &amp; Wireless
---

### Post by Schammy on 2009-04-17
My wireless card doesn't seem to be working all of the sudden and I suspect that I turned it off with some combination of function keys on my gateway laptop keyboard.

Here's my iwconfig results...

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          [COLOR="Blue"]Power Management:off[/COLOR]
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Where it says "Power Management:off", does that mean the wireless card is turned off?  If not, what does it mean?

What does your iwconfig result look like?

Thanks!

---

### Post by lisati on 2009-04-17
What the output tells me is that a "logical" connection with a network hasn't been established. It's like a "landline" telephone: even though you might have the telephone, with all the proper wiring in place, if you're not using the phone there's no connection.

The power management part doesn't mean that the interface is switched off: it's a bit like the part of a cellphone which adjusts the phone's settings according to how strong the signal from the cellphone tower is.

---

### Post by Schammy on 2009-04-17
What about the little red 'X' in the wireless bars?  I'm not used to seeing that.  Does that just mean that the wireless is not turned on or just not available?

See below...

[IMG]http://img164.imageshack.us/img164/5715/wirelessgrayedout.png[/IMG]

Thanks.

---

### Post by t0mppa on 2009-04-17
The little cross just means that there's no connection currently in use. For what it's worth, on my system when I turn wireless off (has a button for this), it totally disappears from Ubuntu. It doesn't show up on iwconfig, lspci or dmesg and Ubuntu behaves as if it was never even there.

---

### Post by Schammy on 2009-04-17
Thanks!  I'll have to do some trouble shooting on my wireless network next.  Appreciate everyone's quick responses.

---

