---
title: "Fixing the SierraWireless Mercury in Karmic"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by teh603 on 2010-01-20
For those of us who use the SierraWireless Mercury, I noticed a thread about fixing a related USB cell modem in Karmic.

The short version- go to the Network Manager, Edit Connections and then edit your connection. Mine is 'AT&T MediaNET 1'. Yours may be something like Cricket 1 or the like.

Click on the IPv4 tab, set the method to 'Automatic (DCHP) addresses only) and add the following DNSes to the list:

8.8.8.8
8.8.4.4

Click Apply, and then supply the Keychain password if needed.

More info: [http://code.google.com/speed/public-dns/docs/using.html]("http://code.google.com/speed/public-dns/docs/using.html")

Also, on the last page of this thread: [http://ubuntuforums.org/showthread.php?t=955832&highlight=SierraWireless&page=2]("http://ubuntuforums.org/showthread.php?t=955832&highlight=SierraWireless&page=2")

Slightly longer version: Basically, there's a faulty kernel module that prevents the cell modem from connecting to AT&T's DNS (or whoever provider you have- this device should work with other companies as well). SierraWireless has the relevant package available with an updated driver, but if you don't know how to compile a kernel you're kinda SOL. 

Thus, we need to provide the computer with the IP of a known DNS. Google has two of them, at the IPs listed above.

Please post if this solved your problem or not.

---

### Post by quickwitt on 2010-04-16
Setting the DNS servers solved my problem too. Tethering Samsung Mythic on 9.10. System recognized the modem and connected automatically but Firefox returned "server not found".

Changed DNS server to 8.8.8.8 and am browsing the internet now.

Thanks!

---

