---
title: "How do I get madwifi wireless working? Ibis on Acer 5220."
date: 2009-03-08
forum: Networking &amp; Wireless
---

### Post by bobdobbs on 2009-03-08
Hi. 
I want to be able to use the madwifi drivers on my Acer 5220.
This laptop uses an Atheros wireless driver. lspci reveals:
```

04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```


I first removed the ndiswrapper tool and my current driver.


I have tried to follow instructions at this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

Googling lead me to believe that if I enabled backports, I could use the ath5k module. However, after I enabled backports and did apt-cache search ath5k, I got no results.
I did apt-cache search atheros, and got no results that seemed relevant.

So, it seems that an atheros driver is not available in any repository.

I then downloaded the madwidi build snapshot, thus:
```

svn co http://svn.madwifi-project.org/madwifi/branches/madwifi-0.9.4 madwifi-0.9.4

```
I then ran 'make' and 'make install', and loaded the modules.

```

me@localhost:~/wa/madwifi/madwifi-0.9.4$ lsmod  | grep ath
ath_pci                99104  0 
wlan                  211696  1 ath_pci
ath_hal               200528  1 ath_pci


```

Now, according to this document:
[https://help.ubuntu.com/community/AspireOne110L#WLan](https://help.ubuntu.com/community/AspireOne110L#WLan)
... "You should now have working wireless" after loading the modules.

That sounds good. But, I can't find any instructions anywhere on how to actually make a connection to a wireless network beyond this point.

The network applet offers no information about possible wireless connections.
Under System->Administration there is no way to configure wireless and no way to see any information about wireless configuration. So now that I've installed the madwifi drivers, I'm working blindly.

Where do I go from here ?
How do I put a wireless interface up and connect to my AP ?
And why aren't madwifi drivers available via synaptic ?

---

