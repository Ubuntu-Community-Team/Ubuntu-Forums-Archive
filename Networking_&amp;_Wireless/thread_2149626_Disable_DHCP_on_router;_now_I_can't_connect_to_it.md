---
title: "Disable DHCP on router; now I can't connect to it"
date: 2013-05-29
forum: Networking &amp; Wireless
---

### Post by PirateChef on 2013-05-29
While attempting to get my wireless router working (a Netgear WPN824 v3), I managed to turn the DHCP off. As a result, I now can't connect to 192.168.1.1 to change settings. After some research, I found out I would have to set a static IP; then I would be able to connect to the router again. However, all of my attempts at this have failed.

I went into settings, found my wired connection, and changed it from "DHCP (Automatic)" to "Manual", and then input 192.168.1.2 for IP Address, 255.255.255.0 for Subnet Mask, and 192.168.1.1 for Gateway. Still couldn't connect, even after restarting.

I have also tried unplugging the router, and then plugging it back in; and a hardware reset, by sticking a bent safety pin into the hole in the back of the router.

---

### Post by Hadaka on 2013-05-29
Hi, the router needs to be powered on when you do the reset
via the little hole in the back,also a saftey pin may be to sharp
try a paperclip,toothpick,with the power on, hold in the button for
about 20 seconds, you should see the lights flash and it will reset.
good luck.

---

### Post by PirateChef on 2013-05-29
No dice. I couldn't find a paperclip, so I tried the flat end of a needle this time. I could clearly feel the button depress, and the lights did flash and reset (as if I had just plugged it in). I held it in for about 20 seconds, but that didn't seem to change anything. I still can't access 192.168.1.1.

The error I keep getting from Rekonq and ping is "Host unreachable."

---

### Post by Hadaka on 2013-05-29
set it back to automatic dhcp..do a direct connect from the computer to the
router,at the browser do 192.168.1.1 once its connected...then you can go back to manual or whatever to
create your static ip...if that fails...you have other issues.

---

### Post by PirateChef on 2013-05-29
No, that doesn't work, either.

The back of the router has 4 black ports (numbered 1 through 4) and a yellow port, separated from those 4. According to a diagram I found on the web, the plug from the modem is supposed to be inserted there. That's the same port I used to plug it into the computer just now. Is that correct?

---

### Post by Hadaka on 2013-05-30
should be
ISP CABLE -------[MODEM]---yellow-----[Y  B B B B] <-any black to computer-----[COMPUTER]

When the Google page comes up...enter 192.168.1.1 in the top...enter address or search...area
top bar..upper left......not the center search area..
Netgear is...admin ...[.password]..is password.
and change your wired connection back to DHCP (automatic)
*undo every thing you did

---

### Post by PirateChef on 2013-06-03
Okay, I found out that my router hadn't been factory reset. I thought it was strange that the SSID hadn't been reset to NETGEAR. Apparently, I needed a paperclip instead of a safety pin...or maybe I just wasn't holding it in long enough. I finally got it reset, and now it's working again.

Thanks for your advice!

---

### Post by Hadaka on 2013-06-03
Great !..glad all is well now.
Please mark this thread solved.
How to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks.

---

