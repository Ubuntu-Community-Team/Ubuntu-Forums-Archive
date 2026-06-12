---
title: "Need Help Connecting To Wireless With CLI"
date: 2010-04-15
forum: Networking &amp; Wireless
---

### Post by false_chicken on 2010-04-15
I am having difficulty getting my wireless to work. My adapter is supported and I can scan and see networks I just need to connect. I have done the following:

ifconfig wlan0 up

iwlist wlan0 scan

iwconfig wlan0 essid Mynetwork (It has no security)

But I need to enter a static ip. So dhclient wlan0 doesn't help
or work for some reason. I know my router is configured for it but the command just says: 

DHCPDISCOVER on wlan0 to 255.255.255.255 interval *(it changes)
Then it says no offers received.

Can anyone explain how to connect to a wireless network with CLI with a static ip? Thanks

---

### Post by perham on 2010-04-15
> **false_chicken said:**
> I am having difficulty getting my wireless to work. My adapter is supported and I can scan and see networks I just need to connect. I have done the following:

ifconfig wlan0 up

iwlist wlan0 scan

iwconfig wlan0 essid Mynetwork (It has no security)

But I need to enter a static ip. So dhclient wlan0 doesn't help
or work for some reason. I know my router is configured for it but the command just says: 

DHCPDISCOVER on wlan0 to 255.255.255.255 interval *(it changes)
Then it says no offers received.


Can anyone explain how to connect to a wireless network with CLI with a static ip? Thanks

try this:

```
 sudo ifconfig wlan0 [your static ip]
```

---

### Post by false_chicken on 2010-04-15
That worked for the Ip but it wont seem to associated with the access point. If i run iwconfig it says access point: not associated. The card works fully when connecting with the gui in gnome.

---

### Post by perham on 2010-04-16
> **false_chicken said:**
> That worked for the Ip but it wont seem to associated with the access point. If i run iwconfig it says access point: not associated. The card works fully when connecting with the gui in gnome.

use ping to see if you can see your access point after associating a static ip. then report back the results.

```

ping [your accesspoint ip]

```

---

