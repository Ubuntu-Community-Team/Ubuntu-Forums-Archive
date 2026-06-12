---
title: "Belkin FD57050 version 5000 help"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by bg101 on 2009-04-06
I have installed Ubuntu 8.10 in dual boot mode alongside Vista.

This device did not work directly out of the box for me as others have reported so I ended up using ndiswrapper 1.54 and the XP drivers supplied on the original CD. My wireless network is detected but my 26 character kex WEP key keeps bouncing and hence I am unable to make a connection to the network. Any help would be greatly appreciated.

Should this thing really work out of the box?  Is ndiswrapper the wrong way to go even though it appears to be detecting my network?
 
Thanks for help.

---

### Post by inobe on 2009-04-07
i have several of these and they all worked out of the box with very little configuration !

i have recommended this usb wireless card to many friends and they too do not experience any issues.

just plugging the card in does the trick, then ubuntu prompts me of wireless networks in range.


btw welcome to the forums :)

---

### Post by bg101 on 2009-04-07
Thanks for you're response and welcome message.

I did some more research.  According to [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) the rtl8187 driver is not natively supported in < 2.6.27-11.  I am running 2.6.27-7 so am assuming that ndiswrapper is required.  That would seem to explain why it didn't work out of the box in my case.

Thanks.

---

### Post by bg101 on 2009-04-07
Just an FYI ... I managed to get this device working with ndiswrapper and the drivers supplied on the CD.  The problem seems to be related to WEP.  I disabled WEP and everything came together.

---

