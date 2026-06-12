---
title: "Wifi on inspiron 8600"
date: 2010-07-07
forum: Networking &amp; Wireless
---

### Post by mcmatt1 on 2010-07-07
I know a little about computers, but not a lot so you guys will have to bear with me. Alright, I have an old computer that had viruses and spyware on it, so i decided to restore it using an old cd that i believe came with it. It installed fine and windows worked perfectly, but i could not access the internet. I'm sure if i hooked it up with cables to the internet it would work fine, but i need it to work on a wifi connection. Before clearing my computer it had a working wifi connection. I looked around on control panel and everyplace I could to find a way to connect to my wifi, but no luck. I know enough about computers that i would have found a way if there was one. I searched my problem and some people were saying i had to install the drivers for wifi but I could not find them online or on my cd. My computer is an inspiron 8600. If you have any idea how to get wifi to work please let me know, and if you have a link to the wifi driver that would help a lot. Thanks in advance

---

### Post by bkratz on 2010-07-07
Here is the Dell Windows driver page, but unless you want to try a lot of experimenting you need to know what card you have. 

[http://support.dell.com/support/downloads/driverslist.aspx?os=WW1&catid=5&dateid=-1&impid=-1&osl=EN&typeid=-1&formatid=-1&servicetag=&SystemID=INS_PNT_P4M_8600&hidos=WW1&hidlang=en&TabIndex=&scanSupported=False&scanConsent=False](http://support.dell.com/support/downloads/driverslist.aspx?os=WW1&catid=5&dateid=-1&impid=-1&osl=EN&typeid=-1&formatid=-1&servicetag=&SystemID=INS_PNT_P4M_8600&hidos=WW1&hidlang=en&TabIndex=&scanSupported=False&scanConsent=False)

---

### Post by mcmatt1 on 2010-07-07
how to i figure that out?

---

### Post by bkratz on 2010-07-08
I really don't know how to do that in Windows, but if you put your service tag number in that Dell page, it should tell you the correct drivers ( unless of course you added the card later).

---

### Post by KegHead on 2010-07-08
Hi!

See if chili555 is out there today.

He was a great help to me.

KegHead

---

### Post by mcmatt1 on 2010-07-08
I've tried all of the drivers on the page (when i type in my service tag number it gives me the same drivers) and the ones that were compatable with my computer didnt work.  When I go to device manager to check my network card it only says 1394 net adapter and broadcom 440x 10/100 integrated controller.  I know it had the ability to connect to wifi hardware wise because it worked before i installed the fresh windows os.  Any other ideas?

---

### Post by yaaarrrgg on 2010-07-08
I have that laptop, and vaguely recall the "dell wireless utility" had to be upgraded.  You'd want to use that tool for connecting, and not the built-in connection util from Microsoft.  There may have been another download for WPA as well I think (though that might be included in the service packs now).  Also, check your wi-fi router and turn off all security for initially testing (for example, if it's locked down by mac address, WPA), and gradually increase the security after each step is working.

Though, my laptop got so slow recently (possibly a virus), I just wiped it XP and installed Ubuntu 10.04.  It was less hassle to put on Linux, than try to rebuild XP.  Everything should work out of the box, even encrypted wireless.  Works better now for me.

---

### Post by mcmatt1 on 2010-07-08
Do you know what I need to do to upgrade this?  Could you maybe post a link?

---

### Post by yaaarrrgg on 2010-07-08
Unfortunately, I haven't quite figured it out with my new Dell laptop (running XP) either.  

The only other thing I'd recommend is ruling out a problem with the router.  Try it at a public access point.

Otherwise, the out-of-the-box wireless support in Windows XP is terrible IMO.

---

### Post by yaaarrrgg on 2010-07-09
By and far, dumping XP is the easiest way to make the machine work again.  Before I wiped XP, it would just thrash at 100% CPU usage, but was clean on all virus scans. Otherwise, you'll spend more time troubleshooting the problem, downloading drivers, than it would take to wipe the whole OS (<30 min).  :)

ETA: 

If you try Ubuntu, be sure to apply all the updates first.  Here's how to set up the wifi in Ubuntu 10.04:

[http://ubuntuforums.org/showpost.php?p=9574879&postcount=583](http://ubuntuforums.org/showpost.php?p=9574879&postcount=583)

For graphics:

 I tried the proprietary nvidia driver 173, but the screen seemed slow.   So I turned off the desktop effects (IIRC... right-click desktop-> Change Background -> Visual Effects -> none).  Now it works great with the proprietary driver.  I only have 1 GB of RAM so it probably isn't fast enough for the eye-candy.

---

