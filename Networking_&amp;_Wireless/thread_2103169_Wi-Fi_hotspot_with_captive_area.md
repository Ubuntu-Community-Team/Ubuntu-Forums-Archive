---
title: "Wi-Fi hotspot with captive area"
date: 2013-01-09
forum: Networking &amp; Wireless
---

### Post by msknight on 2013-01-09
Hi Folks,

Long story short, my home wi-fi router got hacked.

Someone in my neighbourhood knows what they're doing and with N coverage I don't stand much chance of working out who.

I have a low power PC which is on 24/7 and has Wi-Fi built in (FitPC3) and I'm hoping that I can set it up as a Wi-Fi hotspot, but with some form of captive access; ie. that once you're connected, you still have to enter a password in order to get anywhere.

ie. similar to things like BT OpenZone which is all over the place.

Also, I'm hoping for logging so that if someone does hack the authentication, that if they try to brute force access, I can be notified so I have a chance of doing something about it.

Also, the 24/7 machine handles e-mail and has shares to other services mounted, so if there is any risk that an attacker could get access to this, then this approach around the problem might be too risky.

I'm running 12.04 with Gnome Classic, (non-compiz) shell.

Opinions please?

---

### Post by haqking on 2013-01-09
> **msknight said:**
> Hi Folks,

Long story short, my home wi-fi router got hacked.

Someone in my neighbourhood knows what they're doing and with N coverage I don't stand much chance of working out who.

I have a low power PC which is on 24/7 and has Wi-Fi built in (FitPC3) and I'm hoping that I can set it up as a Wi-Fi hotspot, but with some form of captive access; ie. that once you're connected, you still have to enter a password in order to get anywhere.

ie. similar to things like BT OpenZone which is all over the place.

Also, I'm hoping for logging so that if someone does hack the authentication, that if they try to brute force access, I can be notified so I have a chance of doing something about it.

Also, the 24/7 machine handles e-mail and has shares to other services mounted, so if there is any risk that an attacker could get access to this, then this approach around the problem might be too risky.

I'm running 12.04 with Gnome Classic, (non-compiz) shell.

Opinions please?

use a strong key

create a random named SSID (not one that exists in the rainbow tables out there, max length 32 chrs)

Create a random 63 character wpa2 key using AES. [http://wolanski.eu/generator/](http://wolanski.eu/generator/)

it wont be worth their time

also depending on your router, enable wireless isolation if its available and enable mac address filtering and enter only the machines you own or want to access it (trivial to bypass but adds an extra layer)

if you have the infrastructure then set up 802.1x

---

### Post by chadk5utc on 2013-01-09
I agree with Haqking on the extra step to secure your router, strong key
random SSID, wpa2 key using AES,MAC filtering, will likely make it unattractive for the time it would take to break in. In addition if its something your able to do I would also consider a router with DD-WRT as there are a growing number available. Something else you can try is relocating the router within your living space away from windows/outside walls, this may not have much effect but can help reduce to coverage area.

---

### Post by lukeiamyourfather on 2013-01-09
I agree with the previous posts about add a MAC address filter. Depending on the router there are controls for the transmission power (attacker would need to be closer), radio scheduling (turn it on only when you're around), or simply turn off Wi-Fi and use only Ethernet connections if nothing else stops the attacks.

---

### Post by Hendry on 2013-01-09
> **lukeiamyourfather said:**
>  use only Ethernet connections if nothing else stops the attacks.

Ehhm.. how to use Wireless services then? For example.. if you have an iPad?:confused:

---

### Post by haqking on 2013-01-09
> **Hendry said:**
> Ehhm.. how to use Wireless services then? For example.. if you have an iPad?:confused:

the requirement to use iPad's wasnt mentioned.

If the OP "requires" wireless then using ethernet is obviously not applicable, it was offered as a suggestion if wireless wasnt required i presume.

---

### Post by lukeiamyourfather on 2013-01-09
> **haqking said:**
> the requirement to use iPad's wasnt mentioned.

If the OP "requires" wireless then using ethernet is obviously not applicable, it was offered as a suggestion if wireless wasnt required i presume.

Bingo. In my home I use Wi-Fi but I don't ***need*** Wi-Fi. If someone was attacking it and stealing bandwidth I'd just shut it down. Back to the original post, all of the public Wi-Fi authentication products that I know of are based on the MAC adress of the client wireless adapter. So that's no more secure than just setting the MAC address filter on the router (or access point).

---

### Post by haqking on 2013-01-09
> **lukeiamyourfather said:**
> Bingo. In my home I use Wi-Fi but I don't ***need*** Wi-Fi. If someone was attacking it and stealing bandwidth I'd just shut it down. Back to the original post, all of the public Wi-Fi authentication products that I know of are based on the MAC adress of the client wireless adapter. So that's no more secure than just setting the MAC address filter on the router (or access point).

If the attacker knows enough to crack WPA then MAC address filtering is trivial to bypass.

By far the most "secure" thing they can do is set a strong upto 63 chr key, random named ESSID etc.

But MAC Address filtering is a worthy addition just a simple extra layer for sure

Preferably 802.1x if infrastructure available

Peace

---

