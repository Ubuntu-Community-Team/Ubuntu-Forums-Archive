---
title: "Wireless working on server until I changed router."
date: 2012-09-05
forum: Networking &amp; Wireless
---

### Post by makeitfolky on 2012-09-05
I am running Ubuntu Server 12.04, and have what I think is an odd problem.

I had my server configured to wirelessly access my BT Home Hub and all was working fine, and all was fine until BT sent me a new HomeHub 3 router.  I changed the SSID and the key on all my devices (Mint laptop, Android Fone, macbook, print server etc etc) and all worked fine.  Except for the Server.  When I disable wireless security it connect OK, so the problem must be there somewhere.

Here's how It's configured in /etc/network/interfaces:
```

auto wlan0
iface wlan0 inet dhcp
wireless-essid XXXXXXXXX
wireless-key   xxxxxxxxx
wireless-channel 11
wireless-mode managed

```

I'm guessing there's something wrong with the key as it connects fine without it.

Security is set to WPA & WPA2 as default on the router.  Do I need to add something into the interfaces file to explicitly tell it the security method, or is something else going wrong?

Grateful for any pointers

MiF

---

### Post by chili555 on 2012-09-05
>  Do I need to add something into the interfaces file to explicitly tell it the security methodYep. Your interfaces file tells the system you want WEP, not WPA. Please try this:```
auto wlan0
iface wlan0 inet dhcp
wpa-essid XXXXXXXXX
wpa-psk xxxxxxxxx
```Even better, since it's a server and you want to know its IP, use:```
auto wlan0
iface wlan0 inet static
address 192.168.1.108 [COLOR="Red"]<--an address outside the DHCP range in the router[/COLOR]
netmask 255.255.255.0
gateway 192.168.1.1
wpa-essid XXXXXXXXX
wpa-psk xxxxxxxxx
```Of course, substitute your details here. 

You don't need the managed and channel declaration; the router will negotiate those details.

---

### Post by makeitfolky on 2012-09-05
Ah, OK.  Thanks for the pointer.  I have made the first changes you recommended for speed which hasn't solved the problem - However, I booted the server into Ubuntu 10.04 Desktop edition and that also couldn't connect to the router, which suggests to my mind that the problem is with the wireless card.  

Is it possible that is just doesn't support WPA/WPA2 ?

The card is a Broadcom BCM4318  (I know there are issues around the B43 cards, but I believe this has been resolved, as I have been able to connect to the other router)

---

### Post by chili555 on 2012-09-05
> The card is a Broadcom BCM4318Tell us more:```
lspci -nn | grep 0280
```You will probably have better luck with the router set to WPA2 only, not WPA and WPA2 mixed (up) mode.

Let's also see:```
sudo iwlist wlan0 auth
```>  I have made the first changes you recommended for speed which hasn't solved the problem Any clues here?```
sudo ifdown wlan0 && sudo ifup -vv wlan0
```

EDIT: You might try wpa-ssid instead of wpa-essid. Sorry; it's getting late and I need a beverage!

---

### Post by makeitfolky on 2012-09-05
> EDIT: You might try wpa-ssid instead of wpa-essid. 

That worked!  Many thanks.

> Sorry; it's getting late and I need a beverage!

It's getting late here too:  I just walked up to our local shop for a bottle of wine AND THEY CLOSED 5 MINUTES EARLY!  WHA????

Thanks again for the help, it's much appreciated

---

### Post by chili555 on 2012-09-05
> **makeitfolky said:**
> That worked!  Many thanks.



It's getting late here too:  I just walked up to our local shop for a bottle of wine AND THEY CLOSED 5 MINUTES EARLY!  WHA????

Thanks again for the help, it's much appreciatedI just poured myself a nice Beaujolais-Villages.

Three suggestions: first, institute static IP. Second, learn about namebench in the Ubuntu repositories and fine-tune your DNS nameserver. Put the tweaked nameservers in place like this:```
auto wlan0
iface wlan0 inet static
address 192.168.1.108 
netmask 255.255.255.0
gateway 192.168.1.1
wpa-ssid XXXXXXXXX
wpa-psk xxxxxxxxx
dns-nameservers 8.8.8.8 69.158.for.example 
```Last, use thread tools at the top to mark Solved.

---

