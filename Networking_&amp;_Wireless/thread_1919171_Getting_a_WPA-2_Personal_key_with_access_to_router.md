---
title: "Getting a WPA-2 Personal key with access to router."
date: 2012-02-02
forum: Networking &amp; Wireless
---

### Post by Mildare on 2012-02-02
I've got wired access to my connection's router, however, I don't know the password. I'd like to know if there's a quick terminal way of finding out the WPA-2 key assigned to it using the terminal.

---

### Post by wojox on 2012-02-02
Hold the reset button in on the back for about 10-15 seconds.

You could find the password using the terminal, but that would be more "cracking" which is forbidden.

---

### Post by TheFu on 2012-02-02
> **Mildare said:**
> I've got wired access to my connection's router, however, I don't know the password. I'd like to know if there's a quick terminal way of finding out the WPA-2 key assigned to it using the terminal.

So if I understand, you
* do not know the wifi SSID or the wifi passphrase stored in the router
* are able to get on the internet using a wired ethernet connection
* would like to use the wifi ethernet connection instead
* cannot ask the person who setup the router for the SSID and passphrase
* do not know the router administrative login (account/password)

WPA2 is practically uncrackable without thousands of years of effort.

If you know the router administrative login, use it to log into the router and look up the WPA2 SSID and passphrase.  Be certain to store this information somewhere safe, like inside your password manager - KeePassX or LastPass or similar so you can find it the next time.

If your router is part of the modem to your ISP, performing a factory reset it may disable all network connectivity, as most DSL routers have PPoE login credentials stored inside to authenticate your account/connection to the DSL provider.  Be certain that you know this data.

If you still don't know what you want, look up the router's defaults via google using the model - IP, admin password, etc.  and have your ISP login and password ready so you can call them for support, then perform a router firmware factory reset following the instructions you already downloaded or have handle.  After that, you can work through the router setup/configuration and have complete control over the router.

Anyone else using the router's wifi will know that you did this, since their connections will fail.

If your router uses an easy-setup mode, you can google to find possible bugs that will let you in. I don't know anything about that.

Good luck.  Be certain to write all the new settings down this time. Here's a wifi router security checklist: [http://blog.jdpfu.com/pages/wifi-security](http://blog.jdpfu.com/pages/wifi-security)

---

### Post by haqking on 2012-02-02
> **TheFu said:**
> 

**WPA2 is practically uncrackable without thousands of years of effort.**

[/URL]

Assuming it is a non dictionary or complex password/passphrase and the default key has been changed so not in a rainbow table that is, otherwise it being WPA2 has no bearing on how long it will take to crack ;-)



To the OP, if you are hard wired to it then login to it and view the key or change it, if you cant login into then reset it.

If you cant do any of these then it probably is not yours to mess with in which case ask the owner for the key.

Cheers

---

