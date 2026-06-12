---
title: "Mandriva wifi &quot;fun&quot; with obsolete driver"
date: 2008-08-25
forum: Mandriva/Mageia
---

### Post by Dremora on 2008-08-25
OK, I have now tried the following:

1. b43-fwcutter, included, what should be used but isn't.

2. ndiswrapper with Windows driver, complains that it can't open the driver file and gives me a really long URL in an error box that can't be copied or pasted. When I get to the URL, it does not exist.

3. bcm43xx-fwcutter with a copy of bcmwl5.sys I found, it cuts it, but won't use it, because it's not version 3, it's version 4, and it doesn't support version 4.

4. So I am now hunting for an obsolete version of the firmware to make the obsolete bcm43xx-fwcutter that ships with Mandriva happy, I suspect I will get carpal tunnel before I get working wifi, because every obvious or correct method only results in more errors.

:P

PS: This is after having to shut off Compiz because of display corruption and, kill -9'ing the update mechanism about 3-4 times cause it would make it so far and then freeze.

---

### Post by Dremora on 2008-08-25
[IMG]http://img522.imageshack.us/img522/6703/mdvwirelessnk4.png[/IMG]

---

### Post by Extreme Coder on 2008-08-25
So you managed to get it working? :)

---

### Post by Dremora on 2008-08-25
> **Extreme Coder said:**
> So you managed to get it working? :)

No, I didn't, I think I'm going to cut my losses and wrap this up, the last update nuked my spellcheck too and everything I type right now is underlined red. :popcorn:

---

### Post by Extreme Coder on 2008-08-25
Well, something seems to be badly wrong with your setups.. :/

---

### Post by Dremora on 2008-08-26
It's fresh off the CD, other than that, all I've done is try to make it work using the tools provided.

---

### Post by AdamWill on 2008-08-26
Dremora: the exact location of the correct firmware is already linked in the Release Notes section I pointed you to in the earlier discussion of this issue.

[http://wiki.mandriva.com/en/2008.1_Notes#Required_firmware_for_Broadcom_wireless_adapters](http://wiki.mandriva.com/en/2008.1_Notes#Required_firmware_for_Broadcom_wireless_adapters)

Links to:

[http://linuxwireless.org/en/users/Drivers/b43#fw-bcm43xx](http://linuxwireless.org/en/users/Drivers/b43#fw-bcm43xx)

which says:

wget [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)

that's the file you need. It's not a very difficult chain to follow.

As I've said repeatedly, the reason we use bcm43xx not b43 by default in 2008 Spring is because it works better. I know because I was one of the people who tested it. Call it obsolete all you like, I'll take something that's 'obsolete' and works well over something that's new and shiny, and doesn't. :) For 2009 we have tested again, b43 is working much better now, and so we will be using b43.

What Windows driver did you try and use for ndiswrapper, and can you take a screenshot of the error message? It should work fine with most of the versions of the driver called bcmwl5 . bcmwl5a and bcmwl6 are less likely to work. This is all down to ndiswrapper, there's little we can do about it.

---

