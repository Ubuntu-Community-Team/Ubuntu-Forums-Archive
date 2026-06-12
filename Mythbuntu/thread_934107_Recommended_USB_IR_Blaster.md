---
title: "Recommended USB IR Blaster?"
date: 2008-09-30
forum: Mythbuntu
---

### Post by obscure411 on 2008-09-30
I'm rebuilding my Mythbuntu backend with 8.04.1.  Last time I went through this process, I replaced the hardware entirely and went with a motherboard that had no serial ports.  This effectively killed my prior homebrew serial IR blaster setup.

Since then, I've just been capturing direct to my PVR-150(s), but I'd like to be able to record the pay channels that I have like I used to.

Is there a simple, preferably cheap, solution for changing channels via USB with mythbuntu?

Thanks in advance for any replies...

Regards,

o411

---

### Post by Eric Boring on 2008-09-30
Bullet Proof, but not cheap: Command IR Mini. Worked out of the box (with a clean install, but I had seriously borked up LIRC by the time I can up on the serial port and ordered the CommandIR. after that it was smooth sailing.

---

### Post by anonymousdog on 2008-09-30
You can get an MCE remote and blaster new for about $40 with shipping ([http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=1644435&CatId=358](http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=1644435&CatId=358)) or whatever you can get one for on Ebay ([http://cgi.ebay.com/Microsoft-MCE-wireless-remote-and-receiver_W0QQitemZ220287265180QQcategoryZ51086QQcmdZViewItem](http://cgi.ebay.com/Microsoft-MCE-wireless-remote-and-receiver_W0QQitemZ220287265180QQcategoryZ51086QQcmdZViewItem)).  Those work out of the box too.

---

### Post by dsbw on 2008-10-04
> **anonymousdog said:**
> You can get an MCE remote and blaster new for about $40 with shipping ([http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=1644435&CatId=358](http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=1644435&CatId=358)) or whatever you can get one for on Ebay ([http://cgi.ebay.com/Microsoft-MCE-wireless-remote-and-receiver_W0QQitemZ220287265180QQcategoryZ51086QQcmdZViewItem](http://cgi.ebay.com/Microsoft-MCE-wireless-remote-and-receiver_W0QQitemZ220287265180QQcategoryZ51086QQcmdZViewItem)).  Those work out of the box too.

I have this device, and curiously enough, the remote isn't quite "plugged in". Like the "back" key doesn't work! I figured it would work OOTB.

---

### Post by anonymousdog on 2008-10-04
I bet that if you run 'irw' and press that Back key, irw will return '000000037ff07bdc 00 Back mceusb' or similar.  There are a handful of keys that aren't mapped to any function in mythfrontend (or the other apps for which the MCC sets up lirc configuration).  Back is one of them.  You could map it to whatever you want.

---

### Post by dsbw on 2008-10-04
> **anonymousdog said:**
> I bet that if you run 'irw' and press that Back key, irw will return '000000037ff07bdc 00 Back mceusb' or similar.  There are a handful of keys that aren't mapped to any function in mythfrontend (or the other apps for which the MCC sets up lirc configuration).  Back is one of them.  You could map it to whatever you want.

I don't understand. Ya gotta go back, right? Folks gotta go back. What key's mapped to do that?

---

### Post by anonymousdog on 2008-10-04
Left or Replay do that IIRC.

---

### Post by dsbw on 2008-10-04
> **anonymousdog said:**
> Left or Replay do that IIRC.

No, oddly enough. It appears to be the STOP key. (I don't have a "replay" button that I can ID on this remote so maybe it's different for others.)

I still find it odd that the back button isn't mapped. Maybe for remotes without a back button?

---

### Post by dsbw on 2008-10-04
Let me amend this further: The left key *does* move you back, so long as you're not focused on a page/control that uses the left/right for navigation.

---

### Post by anonymousdog on 2008-10-04
Yeah, I'd like menu navigation with the remote to be a little more intuitive.

---

