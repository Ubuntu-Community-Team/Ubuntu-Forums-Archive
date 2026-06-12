---
title: "Problems with wlan/ndiswrapper"
date: 2006-06-25
forum: Networking &amp; Wireless
---

### Post by Badbunny on 2006-06-25
Hello,
I am trying to get my usb-wlan stick (by SMC) working on my 6.06 Kubuntu. I am following this howto: [http://www.ubuntuforums.org/showthread.php?t=31926](http://www.ubuntuforums.org/showthread.php?t=31926)

When type "sudo iwlist wlan0 scan" on console (step 5 of the howto) I get this error:
```

wlan0     Interface doesn't support scanning.

```

OK, next I tried to "sudo iwconfig", only to get this:
```

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

Now, that doesn't look all that promising? What am I doing wrong here?

---

### Post by H.E. Pennypacker on 2006-06-25
You're talking about a wireless card, right?  If that is the case, can you provide the entire name of the card, and not just the manufacturer?  Provide as much information as possible.

The following threads may help:

[http://ubuntuforums.org/showthread.php?t=67830&highlight=smc](http://ubuntuforums.org/showthread.php?t=67830&highlight=smc)

[http://ubuntuforums.org/showthread.php?t=200625&highlight=smc](http://ubuntuforums.org/showthread.php?t=200625&highlight=smc)

[http://ubuntuforums.org/showthread.php?t=134679&highlight=smc](http://ubuntuforums.org/showthread.php?t=134679&highlight=smc)

[http://ubuntuforums.org/showthread.php?t=195281&highlight=smc](http://ubuntuforums.org/showthread.php?t=195281&highlight=smc)

[http://ubuntuforums.org/showthread.php?t=63024&highlight=smc](http://ubuntuforums.org/showthread.php?t=63024&highlight=smc)

By the way, things may be a little difficult at first, as one SMC card user has said.

---

### Post by Badbunny on 2006-06-25
Sorry for not being more specific. The usb device is model SMCWUSBT-G EU. I'll try the links you provided, but it begins to look like I'll just buy another one, preferably one that is easier to use in linux :).

Thanks for the reply.

---

### Post by H.E. Pennypacker on 2006-06-25
[QUOTE=Badbunny]Sorry for not being more specific. The usb device is model SMCWUSBT-G EU. I'll try the links you provided, but it begins to look like I'll just buy another one, preferably one that is easier to use in linux :).

Thanks for the reply.[/QUOTE]

I do recommend sticking it to those companies that provide little or no support for Linux, but I recommend against buying a new card.  Before you buy a new card, let's see if we can get this card to work.

If absolutely nothing can be done, I highly suggest you email SMC to remind them their lack of concern for the Linux community is costing them money.

---

### Post by az on 2006-06-25
A few linux wireless drivers just don't do scanning.  If you enter the ssid by hand, though, they work fine.

---

